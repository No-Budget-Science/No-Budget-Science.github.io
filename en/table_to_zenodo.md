#  How to publish your biocuration spreadsheet on Zenodo

A biocuration spreadsheet in this situation is a table that came from a curation effort. The end goal is to have a table published on Zenodo, like: 
- [https://zenodo.org/record/4589519#.YIDHRnVKi00](https://zenodo.org/record/4589519#.YIDHRnVKi00)
- [https://zenodo.org/record/4631221#.YIDHR3VKi00](https://zenodo.org/record/4631221#.YIDHR3VKi00)

![image](https://user-images.githubusercontent.com/7917951/142673342-58ecdf6f-8841-4761-a817-49af02e2df30.png)

*Example of a spreadsheet published on Zenodo downloaded more than 100 times in 9 months*

 Note: it does not need to be English! You are the one publishing, so you choose the language. 

## Pre-processing:

  - Clean up the dataset (as much as you like, it is your call) 
  - Don't be afraid to remove columns that are not relevant for other people 
  - On a text file, add a short explanation of what your dataset is about
  - Below the explantation, write a _dictionary_ ("__Columns__" session), mapping the names of the column headers to some explanation. This will end up on the description on Zenodo, and will be part of the description of your dataset on the plataform.  

For example:

---
**EXAMPLE**

__Description__:

A set of transcriptomics studies on the Gene Expression Omnibus (GEO) platform somehow related to infectious or neurodegenerative diseases.

__Columns__:

  - __Study__: The study number in the Gene Expression Omnibus. End {$1} of the URL: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc={$1}.
  - __Disease__: The disease of interest in the study
  - __Platform__: The technology used to obtain the data. End {$1} of the URL: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc={$1}.
  - __Sample type__: The cell type or tissue type used for the analysis
  - __PMID__: The PubMed ID of the article that describes that study. End {$1} of the URL: https://pubmed.ncbi.nlm.nih.gov/{$1}.
  - __Control sample__: The label of the control samples in the dataset
  - __Perturbed sample__: The label of the perturbed samples in the dataset

**EXAMPLE**

---

## Uploading to Zenodo:
  Download your table  in the format of preference. If you are using Excel/Google Sheets, we recommend two formats: _.xlsx_ and _.tsv_ format.The _.tsv_ format is more machine readable, while .xlsx (the Excel format) is more common among human beings.  
  
  On [https://zenodo.org/](https://zenodo.org/):
  - Login or sign up (you may login with your ORCID)
  - Click on _Upload_ (on the top) 

![image](https://user-images.githubusercontent.com/7917951/142673613-b196c318-479f-4279-b0b3-3bed95b20a41.png)

*The upload button*

  - Click on _New upload_ (green button)
  - Add both files (.tsv and .xlsx) that were downloaded previously.
  - Click on the green button _Start upload_
  - Skip the _Communities_ section (it is reserved for specific projects)
  - Select upload type "_dataset_"
  - Add the basic information (no need to assign a DOI, one will be assigned automatically to your table). Add a title, your credentials (and of the other people that worked in the dataset)
  and the text file you have prepared (the one one with the description and the dictionary. 
  - Add a version tag (you might want to update it in the future!). 
  - Add the primary language used on your table.
  - Add a couple keywords. For each new keyword, click on "+ Add another keyword". If possible, also add a tag "biocuration" 
  - Add a license. Release it in open access for maximal reuse of your curation.  
The default "CC-BY" license is good for some purposes, but ideally you should release it under the public domain ([CC0](https://creativecommons.org/publicdomain/zero/1.0/) for maximum reuse. 
For that you will have to upload a file containing the CC0 license text and stating your wish for the community to reuse it widely.  
  - _Skip everything after the license part._ (Well, you can add more optional info, if you have time)
  - Click "Save" and click "Publish". 

Congratulations, you've made the world a bit better! Now the dataset is openly available. Also jot a DOI: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4573573.svg)](https://doi.org/10.5281/zenodo.4573573), 
thus it can be shared and cited, and will soon be indexed and visible to [Google Dataset Search](https://datasetsearch.research.google.com/). 

![image](https://user-images.githubusercontent.com/7917951/142674268-25eaf281-01a5-493a-8798-a42fe618ba9b.png)


## Reconciling to Wikidata

tl;dr: Send tiago.lubiana.alves at usp.br and email, and he (I) will either help you with the process or just do it all. 

Now the dataset is super searchable, what is great. 
However, we can extract even more value from the curation effort. 

We often represent concepts (such as diseases, cell types and tissues) by _strings_, natural language, human-readable words.

Words are tricky, and can hold many meanings. 
Moreover, they are meaningful to people, but very shallow to computers. 

One modern advancement is the use of Universal Resource Identifiers to map concepts to unique resources. 

This technique is on the base of virtually all biomedical ontologies, like the Gene Ontology. 
Wikidata is an open, general-use knowledgebase where people can find (and create!) identifiers for their concepts of interest.

[Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) is linked to thousands of other bases. 
Thus, linking to Wikidata effectively raises the information to state-of-the-art information sharing, or what Tim Berner-Lee (the inventor of the web) would call 5- star linked ofen data. 

First we need to choose which columns to reconcile to Wikidata. 

In our example we have concepts findable on Wikidata, like: 

  - __Disease__: The disease of interest in the study
  - __PMID__: The PubMed ID of the article that describes that study. End {$1} of the URL: https://pubmed.ncbi.nlm.nih.gov/{$1}.

First we will:

- Find/Create Wikidata identifiers for each of the concepts on the table
- Add them to the Wikidata database citing the Zenodo dataset. 

### Finding the Wikidata identifiers

Using the Google Sheets Add-On Wikipedia and Wikidata, I do the following:

* Copy all disease terms to the first column
* In the second column, use the formula `=WIKIDATASEARCH(A1)` to get the Wikidata ID by searching that word on Wikidata. Extend it to all rows.
* In the third column, use the formula `=WIKIDATADESCRIPTIONS(A1)` to verify if the description is accurate. Extend it to all rows. 

In this case, the row "c9orf72-associated and sporadic ALS" did not have a match on Wikidata. I simplify it, then, to "ALS".

The tool found IDs for all diseases.

Now I want to find the Wikidata identifiers for all articles on that table.

The Google Sheets Add On does not work with PMIDs, so I'll need to use programatic tools. 
There is a shiny app available to do exactly that reconciliation at https://lubianat.shinyapps.io/doi2wiki/. 
It might not be up in the future, but the code for the Shiny App will always (I hope!) be at https://github.com/lubianat/doi2wiki.

I download the "csv" via the Google Sheets and feed it to the doi2wiki app. 
The app returns a tsv with the original table plus the Wikidata IDs found. 

### Updating file version on Zenodo

Our curation table is now enriched with Wikidata ids. 
Let's add "(with Wikidata)" to the title and a note to the descriptio saying:

Column names followed by __"_QID"___ hold the Wikidata IDs relative to that column. 

On Zenodo, I click on "Upload" and on the dataset we uploaded in the previous session. Then, on "New Version" I can add the new tables.
I won't change the ones that are already there. What I do, then is :

* Upload the new files (a "wikidata_reconciled" sheet and the .xlsx). ("Choose Files" + "Start Upload")
* Add the new column details the Zenodo description.  
* Add the link to the Google Sheet: [https://docs.google.com/spreadsheets/d/1LjF4h8n6Sy4PgTJoC-fJ7mGnqGCvqmWiatf2zD-5RM8](https://docs.google.com/spreadsheets/d/1LjF4h8n6Sy4PgTJoC-fJ7mGnqGCvqmWiatf2zD-5RM8). 
* Bump the file version to 1.1 

- Click "Save"
- Click "Publish"

### Adding information to Wikidata

Now we have a set of diseases and the articles that talk about them. 
We can add that directly to the Wikidata database using a property called "main subject", which is basically a way to say "keyword" in the Wikidata universe. 

For that, we will use a syntax called "Quickstatements V1". 
On a spreadsheet, we use the columns to build a series of "statements" like:

Q35073924	P921	Q12156	S854	"https://zenodo.org/record/4573573#.YEaYGnVKi00"
																					
Which means that this specific article (Q35073924) is about (P921) malaria (Q12156) as said in the url (S854) "https://zenodo.org/record/4573573#.YEaYGnVKi00".

On a new sheet, we add a column of "P921" between articles and diseases and the 2 reference columns in the end. 

These "statements" are pasted into the Quickstatements system (<https://quickstatements.toolforge.org/#/batch>) which is a way to make batch edits to Wikidata. 

(To use the system, you need 100 manual edits in the system. One way of achieving that is adding aliases on Wikidata for a few terms here and there). 

On Quickstatements:

* Log in with your Wikidata account
* Click on New Batch
* Paste your series of commands in the format above
* Click on "Import V1 commands"
* Check if everything looks at expected (the system will render human-readable statements for you to check)
* If it looks ok, click on "Run" 

Nice, now your curation is live on Wikidata!

Everyone can benefit from it, including you. 

To showcase the power, I will reconcile the column with the Gene Expression Omnibus IDs to Wikidata. 
For that, I'll use the "external data" (P1325) property. The triples go like this:

Q35073924	P1325	"https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE5418"	S854	"https://zenodo.org/record/4589519"

Which reads like this specific article (Q35073924) has external data (P1325) at the url "https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE5418" as said in the url (S854) "https://zenodo.org/record/4589519".

I follow once more the steps on Quickstatements to add to Wikidata. 

### Using the power of Wikidata for your curation

Now we can use the Wikidata query system and the ontological structure to make very useful queries. 

For example, let's look for articles about any neurodegenerative disease and their external datasets. 

For that, we build a query in the SPARQL language at <https://query.wikidata.org>, which can be acessed here: <https://w.wiki/34rP>. 

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Fitem%20%3FitemLabel%20%3FdiseaseLabel%20%3Fdata%0AWHERE%20%0A%7B%0A%20%20%3Fitem%20wdt%3AP921%20%3Fdisease.%0A%20%20%3Fdisease%20wdt%3AP279%2a%20wd%3AQ1755122.%0A%20%20%3Fitem%20wdt%3AP1325%20%3Fdata.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

As of March 8 2021, Wikidata has 18 matches for that query, some of which came from my curation, and some that were already there. 

SPARQL queries are very flexible, and allow us to navigate this sea of knowledge. 

In this simple example, it already helped me to discover new datasets. 

Now imagine that all mini tables, like the ones you already have, were represented on Wikidata? 

That could have a transformative change in the daily life of _all_ researchers, streamlining biocuration and saving millions of person/hours per year. 
  














##### *This page was made with [GitHub Pages](https://pages.github.com)*
