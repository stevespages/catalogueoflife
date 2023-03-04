# Catalogue of Life

[COL](https://www.catalogueoflife.org/) maintains a checklist of over two million of the world's species. The number of published scientific species names is far higher as there are many synonyms for the accepted names. COL participates with taxonomic communities to decide which names are accepted. The lists drawn up by the various taxonomic communities are merged to create the COL checklist of species for all life. New information and revision of old information result in new versions of the COL checklist being released monthly with major versions released annually.

In addition to providing a list of accepted names for living things, COL classifies them. The basis for this classification is described in a paper titled: [A Higher Level Classification of All Living Organisms](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4418965/). The classification is intended to be a consensus view. It attempts to reflect phylogenetic relatedness of organisms but recognizes that in many areas this is unclear and therefore other criteria are also used.

Linnaeus, working in the 1700s, classified animals and plants into kingdom, class, order, genus, species and subspecies. COL uses these taxonomic ranks plus some others. The COL classification has two superkingdoms: the Prokaryota, which include bacteria, and the Eukaryota which includes amoebas and Homo sapiens. The Prokaryota include 2 kingdoms and the Eukaryota include 5 kingdoms. Not all taxonomic ranks are used in the different parts of the classification. For example some of the kingdoms are made up of subkingdoms whereas others do not contain subkingdoms and have phyla as their next lower taxonomic rank.

## Accessing the COL Checklist

### Browse

At www.catalogueoflife.org the 7 kingdoms that COL recognizes as well as the 7 realms of viruses are listed. Clicking on the name of each kingdom, for example Animalia, opens a page about Animalia. Clicking on the arrow before the kingdom name reveals all the phyla in that kingdom. The names of these phyla can be clicked on to open a page about that phyla or the arrow by the phylum name can be clicked to reveal the next rank. Using this approach one can drill down to the species level.

### Search

If you know the name of the species or other taxon you are interested in there is a search page at https://www.catalogueoflife.org/data/search. Various filters can be applied to the search to make it more specific. For example it can be limited to accepted names or to a certain taxonomic rank. Fuzzy searching is possible and extinct organisms can be included or excluded.

### Application Program Interface API

The COL ChecklistBank API can be found at https://api.checklistbank.org/. It allows programs to read from the COL checklist and write to it and other checklists which share the same format as the COL Checklist. The format is called the [COL Data Package format](https://github.com/CatalogueOfLife/coldp) (ColDP).

Many people writing websites and other software may want the application they are building to be able to make repeated requests for information to the COL checklist but perhaps with different parameters for each request. For example a website may allow users to request information on a species. The user would enter the name of the species and the application would use that as a parameter to make an API call to the COL checklist to return information about the species. This would provide similar functionality to that offered by COL in their search page. The wide range of API calls that COL make available allow for a great variety of uses which the COL checklist can be put to using the API.

In addition to accessing data using the API it is possible, with the necessary authentication, to add new data, modify data and delete data. This could involve checklists that will be part of the next COL checklist when it is released or it could be data in other checklists which conform to the ColDP format.

There are a number of different ways of making an API call although typically they use the Hypertext Transfer Protocol (HTTP) which is used for for browsing the world wide web. It is therefore possible to make an API call by typing an appropriate address into the address bar of a browser such as Chrome, Firefox, Edge or Safari.

The following URL *https://api.catalogueoflife.org/dataset/1005/taxon/32/classification* can be entered into the address bar of a browser and will result in data from the COL Checklist being sent to the browser. The data is is in JSON format which is suitable for use by software. Normally the data would either be sent to a server where it would be processed and then sent to the user's browser or it may be sent directly to the user's browser but modified by JavaScript code before being displayed in the browser in a more human friendly way.

![screenshot of JSON response from API call](https://github.com/stevespages/catalogueoflife/blob/main/assets/photos/json-from-api-call.png?raw=true "screenshot of JSON response from API call")

The URL which we made an API call with in the previous paragraph specifies the *api* subdomain of the *catalogueoflife.org* domain. The URL goes on to specify dataset 1005 which is one of the checklists in COL ChecklistBank. It further specifies the taxon with an ID number of 32. Finally the word *classification* in the URL indicates the type of information which is being requested. That is information relating to the classification of the taxon with ID of 32.

### Download the whole COL Checklist

Perhaps the most powerful way to access data in the COL Checklist is to download it to your own computer and then use various types of sofware to access it. The COL Checklist can be downloaded from https://www.catalogueoflife.org/data/download. Various formats are available but the recommended one is ColDP.

The downloaded COL Checklist could be analyzed in a spreadsheet or spreadsheets. The huge size of the COL Checklist may be too much for spreadsheets but they could certainly be feasable for subsets of the data.

The statistical computing sofware package called *R* can be used to investigate the data in powerful ways and also output graphical representations of the data.

Various database systems can be used to investigate the data. Relational Database Management Software (RDBMS) is particularly suitable as the COL Checklist data is distributed among various related tables.

One advantage of downloading the COL Checklist and extracting the data of interest on your own local computer or remotely on your own server is that the request for the data of interest and the returned data do not have to travel over the internet. Therefore the performance of software that takes this approach can be better than using the API. It is likely that COL uses RDBMS software to handle the API requests it receives.



COL recommends the COL Data Package Archive (ColDP) format although other formats for example Darwin Core are available. The ColDP schema and information relating to it can be found at https://github.com/CatalogueOfLife/coldp. The specification describes what constitutes a valid ColDP format for people who want to construct a species list using their own data. Therefore the specification for the format is broader than that actually used by the ColDP archive itself. For example comma separated files as well as tab separated files are acceptable for the format but the archive only actually uses tab separated files (suffixed with the *.csv* file extension). 

Downloading ColDP archive file and extracting it gives the following files and (one) directory:

```console
total 2.1G
361M file 	6b9f4398-1968-42ac-bbce-640b77d288d4.zip
112M file 	Distribution.tsv
 72K file 	logo.png
 108 file 	Media.tsv
938K file 	metadata.yaml
 16M file 	NameRelation.tsv
1.1G file 	NameUsage.tsv
198M file 	reference.json
326M file 	Reference.tsv
4.0K directory	source
 37K file 	SpeciesEstimate.tsv
 112 file 	SpeciesInteraction.tsv
  81 file 	TaxonConceptRelation.tsv
 259 file 	TypeMaterial.tsv
 23M file 	VernacularName.tsv
```

The files above are for the simpler version of ColDP (see https://github.com/CatalogueOfLife/coldp) in which the *Taxon*, *Synonym* and *Name* entities have been merged into *NameUsage*. Note that I am lacking  *Treatment* file which is shown on the schema.

## Glossary

- Catalogue of Life (COL)

  https://www.catalogueoflife.org/

  https://en.wikipedia.org/wiki/Catalogue_of_Life

  https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4418965/

- Catalogue of Life Plus (COL+)

  See the links for COL as well as:



- COL API

  https://api.checklistbank.org/

- COL Checklist

  https://www.catalogueoflife.org/about/colusage

- COL ChecklistBank

- COL Data Package (ColDP)

  https://github.com/CatalogueOfLife/coldp/blob/master/README.md

## Glossary of related terms

- Digital Object Identifier (DOI)

- Application Program Interface (API)