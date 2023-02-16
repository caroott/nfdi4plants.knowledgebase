---
layout: docs
title: "Study"
published: 2022-12-13
add toc: true
add support: false
add sidebar: _sidebars/arcCommanderManualSidebar.md
todo: Update design, factor, and protocol sections
---

## Adding a study

> :warning: Make sure to close all isa.*.xlsx files before submitting a new command to the command line, as otherwise the information cannot be saved by the ARC Commander.
  
- An investigation may contain several studies, which in turn can include multiple assays.
- There is no need for a folder structure that represents a study since all data are associated with assays. Studies can be created to group related assays within an investigation. A study consists of a single isa.study.xlsx file, can be created by using `arc s init`.
- An existing study can be registered to the investigation by using `arc s register`.
- To create the isa.study file and afterwards register the new study `arc s add` can be used. This command combines init and register.

> :warning: A study identifier also defines the isa file name, so ensure to avoid special characters!

| Field                   | Description                                                                                                                                                                                             | Input                                                                                         |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Identifier (Mandatory)  | A unique identifier, either a temporary identifier supplied by users or one generated by a repository or other database. For example, it could be an identifier complying with the LSID specification.  | GelBasedProteomicsWT                                                                          |
| Title                   | A concise phrase used to encapsulate the purpose and goal of the study.                                                                                                                                 | Gel-based proteomics of wild type cells                                                       |
| Description             | A textual description of the study, with components such as objective or goals.                                                                                                                         | Study to investigate the proteins of wild type yeast cells under standard growth conditions.  |
| SubmissionDate:         | The date on which the study is submitted to an archive.                                                                                                                                                 |                                                                                               |
| PublicReleaseDate:      | The date on which the study SHOULD be released publicly.                                                                                                                                                |                                                                                               |

If no study identifier is given, a study is created with the assay identifier as study identifier. Instead of using the editor, the following command can be used:  
`arc s add --identifier Test --title "Gel-based proteomics of wild type cells" --description " Study to investigate the proteins of wild type yeast cells under standard growth conditions."`

## Listing and inspecting registered studies

- Registered assays can be listed by `arc s list`.
- To get detailed information about a specific entry use `arc s get`. If no arguments are specified an editor will request a study identifier to print all registered information into the shell.

## Editing study information

- A study can be edited using `arc s edit`.
  - If no further arguments are specified an editor opens, that asks for the study identifier that should be edited.
  - If the study exists, another editor opens with information already known for the respective study. The required values can be edited.
- Instead of using the editor, the following command can be used. To circumvent editor pop ups, not arc s edit, but `arc s update` must be used:  
`arc s update --identifier GelBasedProteomicsWT --submissiondate "13.04.2020"`

## Removing a study

- A study can be unregistered from the investigation by using `arc s unregister`.
- A study folder structure can be deleted by using `arc s delete`.
- To both, delete the assay folder structure and unregister it from the investigation `arc a remove` can be used.

## Registering persons to a study

- Every person, that is involved in a study can be registered with personal information using `arc s person register`.

| Field                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Input                                                                           |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| StudyIdentifier (Mandatory)  | Identifier of the study the person is associated with                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | GelBasedProteomicsWT                                                            |
| LastName (Mandatory)         | The last name of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Doe                                                                             |
| FirstName (Mandatory)        | The first name of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | John                                                                            |
| MidInitials                  | The middle initials of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | P                                                                               |
| Email                        | The email address of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | jpdoe@mail.com                                                                  |
| Phone                        | The telephone number of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | +49(0)631 205 3045                                                              |
| Fax                          | The fax number of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                 |
| Address                      | The address of a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Paul Ehrlich Straße 23, 67663 Kaiserslautern, Germany                           |
| Affiliation                  | The organization affiliation for a person associated with the investigation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Department of M21 Measurements, Technische Universität Kaiserslautern, Germany  |
| Roles                        | Term to classify the role(s) performed by this person in the context of the investigation, which means that the roles reported here need not correspond to roles held withing their affiliated organization. Multiple annotations or values attached to one person can be provided by using a semicolon (;) Unicode (U0003+B) as a separator (e.g.: submitter;funder;sponsor). The term can be free text or from, for example, a controlled vocabulary or an ontology. If the latter source is used the Term Accession Number and Term Source REF fields below are required.  | supervisor                                                                      |
| RolesTermAccessionNumber     | The accession number from the Term Source associated with the selected term.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                 |
| RolesTermSourceREF           | dentifies the controlled vocabulary or ontology that this term comes from. The Source REF has to match one of the Term Source Names declared in the Ontology Source Reference section.  RolesTermSourceREF:                                                                                                                                                                                                                                                                                                                                                                     |                                                                                 |

- Instead of using the editor, the following command can be used:  
`arc s person register -s GelBasedProteomicsWT -l Doe -f John -m P --email jpdoe@mail.com --phone "+49(0)631 205 3045" --address "Paul-Ehrlich-Straße 23, 67663 Kaiserslautern" --affiliation "Department of M21 Measurements, Technische Universität Kaiserslautern, Germany" --roles "supervisor"`

### Listing and inspecting registered persons

- Registered persons can be listed by `arc s person list`.
- To get detailed information about a specific entry use `arc s person get`. If no arguments are specified an editor will request a study identifier, a first and last name (mandatory) and optionally mid name initials to print all registered information into the shell.

### Editing person information

- A person can be edited using `arc s person edit`.
  - If no further arguments are specified an editor opens, that asks for the person that should be edited.
  - If the person exists, another editor opens with information already known for the respective person. The required values can be edited.
- Instead of using the editor, the following command can be used. To circumvent editor pop ups, not `arc s person edit`, but `arc s person update` must be used:  
`arc s person update -s GelBasedProteomicsWT -l Kunze -f Heinz-Rudolf --email hrkunze@mail.com --address "Herzstraße 5, 12345 Musterstadt"`

### Removing a person

- A person can be removed from a study using `arc s person unregister`. An editor will request the study identifier, first and last name (mandatory) and optionally mid name initials to unregister the person from the study in isa.investigation.xlsx.
- Instead of using the editor, the following command can be used:  
`arc s person unregister -s GelBasedProteomicsWT -l Doe -f John -m P`

## Registering publications to studies

- If studies result in publications, they can be registered to the corresponding study.
- Study publications can be registered by `arc s publication register`.

| Field                        | Description                                                                                                                                                                                 | Input                  |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------|
| StudyIdentifier (Mandatory)  | Identifier of the study the publication is associated with                                                                                                                                  | GelBasedProteomicsWT   |
| DOI (Mandatory)              | A Digital Object Identifier (DOI) for that publication (where available).                                                                                                                   | 2021_ARC05_S01_01tmp   |
| PubMedID                     | The PubMed IDs of the described publication(s) associated with this investigation.                                                                                                          |                        |
| AuthorList                   | The list of authors associated with that publication.                                                                                                                                       | Lara Fox; Peter Croft  |
| Title                        | The title of publication associated with the investigation.                                                                                                                                 |                        |
| Status                       | A term describing the status of that publication (i.e. submitted, in preparation, published).                                                                                               | in preparation         |
| StatusTermAccessionNumber    | The accession number from the Term Source associated with the selected term.                                                                                                                |                        |
| StatusTermSourceREF          | Identifies the controlled vocabulary or ontology that this term comes from. The Source REF has to match one the Term Source Name declared in the in the Ontology Source Reference section.  |                        |

- Instead of using the editor, the following command can be used:  
`arc s publication register -s GelBasedProteomicsWT -d 2021_ARC05_S01_01tmp --authorlist "John P Doe; Eva Muller" --title "abc"`

### Listing and inspecting registered publications

- Registered publications can be listed by `arc s publication list`.
- To get detailed information about a specific entry use `arc s publication get`. If no arguments are specified an editor will request the study identifier and doi to print all registered information into the shell.

### Editing publication information

- A publication can be edited using `arc s publication edit`.
  - If no further arguments are specified an editor opens, that asks for the study identifier and publication doi that should be edited.
  - If the publication exists, another editor opens with information already known for the respective publication. The required values can be edited.
- Instead of using the editor, the following command can be used. To circumvent editor pop ups, not `arc s publication edit`, but `arc s publication update` must be used:  
`arc s publication update -s "GelBasedProteomicsWT" -d 2021_ARC05_Pub01tmp --title "The peroxisomal Flux-Compensator-Cycle is heavily dependent on P09 accumulation under redox stress.".`

### Removing a publication

- A publication can be removed from a study using `arc s publication unregister`. An editor will request the study identifier and DOI to unregister the publication from the study in the isa.investigation file.
- Instead of using the editor, the following command can be used:  
`arc s publication unregister -s GelBasedProteomicsWT -d 2021_ARC05_Pub01tmp`

## Registering Design Types to Studies

- The design type of your study can be registered using `arc s design register`.
  - If no further arguments are specified an editor opens that asks for a term allowing the classification of the study based on the overall experimental design, e.g cross-over design or parallel group design.
  - Additionally you are asked to supply the accession number from the term source and the Term Source REF if available.
- Instead of using the editor, the following command can be used:
`arc s design register -s "GelBasedProteomicsWT" -d "YourDesignType"`