# OntoUML/UFO Catalog

<p align="center"><img src="https://user-images.githubusercontent.com/8641647/223740939-1abcd2af-e954-4d19-b087-56f1be4417c3.png" width="500">

The FAIR Model Catalog for Ontology-Driven Conceptual Modeling Research, short-named **OntoUML/UFO Catalog**, is a structured and open-source catalog that contains OntoUML and UFO ontology models. It was conceived to allow collaborative work and to be easily accessible to all its users.

Our goal with this catalog is to support empirical research in OntoUML and UFO, as well as for the general conceptual modeling area, by providing high-quality curated, structured, and machine-processable data on *why, where, and how* different modeling approaches are used.

The catalog offers a diverse collection of models, created by modelers with varying modeling skills, for a range of domains, and for different purposes. The models are available in machine-readable formats (JSON and Turtle) and are accessible via permanent identifiers.

This document is displayed as follows:

- [Catalog structure](#catalog-structure)
  - [Metadata vocabularies](#metadata-vocabularies)
  - [Catalog's persistent URLs](#catalogs-persistent-urls)
- [How to contribute](#how-to-contribute)
  - [Contribute by submitting an ontology](#contribute-by-submitting-an-ontology)
  - [Contribute by reporting an ontology](#contribute-by-reporting-an-ontology)
  - [Contribute by reporting an application](#contribute-by-reporting-an-application)
  - [Other ways to contribute](#other-ways-to-contribute)
- [Related software applications](#related-software-applications)
- [Works citing and using the OntoUML/UFO Catalog](#works-citing-and-using-the-ontoumlufo-catalog)
- [Catalog administration](#catalog-administration)
- [How to cite this catalog](#how-to-cite-this-catalog)
- [Acknowledgements](#acknowledgements)
- [License disclaimer](#license-disclaimer)

The catalog github repository is associated with the permanent URL <https://purl.org/ontouml-models>.

## Catalog structure

The whole catalog is hosted on a GitHub repository whose root directory contains: 

1. `catalog.ttl`: is the file encoding the catalog itself in a triple-based format - i.e., the aggregated data of all ontologies that are part of the catalog - its permanent identifier is https://w3id.org/ontouml-models/catalog;
2. `metadata-catalog.ttl`: a Turtle file containing the catalog's metadata;
3. `metadata.ttl`: a Turtle file containing the catalog's metadata and the metadata from all its composing models;
4. list of folders - each one including all the information related to an OntoUML/UFO-based model.

We provide below a representation of the catalog directory tree:

```
catalog/
|   catalog-metadata.ttl
|   catalog.ttl
|   metadata.ttl
+---ontology-1_folder/
|   |   metadata.ttl
|   |   metadata.yaml
|   |   ontology.json
|   |   ontology.ttl
|   |   ontology.vpp
|   |   references.bib
|   +---new diagrams/
|   |       diagram1.png
|   |       diagram2.png
|   +---original diagrams/
|           diagram1.png
|           diagram2.png
+---ontology-2_folder/
+---ontology-3_folder/
...
+---ontology-N_folder/
```

Each ontology folder is composed of the following files:

1. `ontology.vpp`: the Visual Paradigm project of the model; 
2. `ontology.json`: contains the JSON serialization of the model exported via the [ontouml-vp-plugin](https://github.com/OntoUML/ontouml-vp-plugin);
3. `ontology.ttl`: uses the [OntoUML Metamodel in OWL](https://purl.org/ontouml-models/vocabulary) to map the model's data. This is a vocabulary designed to support the serialization and exchange of OntoUML models in compliance with the [ontouml-schema](https://purl.org/ontouml-schema), which is a specification of how to serialize OntoUML models as JSON objects. This file provides a specific URI for all data from the model. These URIs are generated according to the following template: `https://purl.org/ontouml-models/<folderName>`, and its publication allows anyone to access and manipulate all the model's instances;
4. `metadata.yaml`: contains the model's metadata;
5. `metadata.ttl`: is an rdf-based version in turtle syntax of metadata.yaml; 
6. `references.bib`: contains the BibTeX citation data for each publication about the model (this file is not required for unpublished models);
7. `original diagrams/`: is a folder containing images in PNG format of the diagrams created by the authors of the model;
8. `new diagrams/`: is a folder containing images in PNG format of all diagrams rebuilt on Visual Paradigm (keeping the names matching the original ones);

Note that the `.vpp`, the `.yaml`, and the `.bib` files are the ones provided by the collaborators. In contrast, the `.json` file is automatically generated for each model using the OntoUML [ontouml-vp-plugin](https://github.com/OntoUML/ontouml-vp-plugin/). The `.png` files hosted in the `new diagrams/` folder are automatically generated by the catalog; the same for all the `.ttl` files.

### Metadata vocabularies

Following the practice of implementing [FAIR principles](https://www.go-fair.org/fair-principles/), the OntoUML/UFO catalog schema (see image below) was built by using:
- [Data Catalog Vocabulary v2](https://www.w3.org/TR/vocab-dcat-2/) (DCAT)
- [Dublin Core Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/) (DCT)
- [Simple Knowledge Organization System](https://www.w3.org/TR/skos-reference/) (SKOS)
- [Metadata for Ontology Description and Publication](https://www.isibang.ac.in/ns/mod/2.0/index-en.html) (MOD)
- [Friend of a Friend](http://xmlns.com/foaf/spec/) (FOAF)

![catalog-schema](https://user-images.githubusercontent.com/8641647/176878091-1caf6503-da50-4e37-bf7d-ba6ba21e1f2c.png)

The catalog (`dcat:Catalog`) is maintained by a community of users (`foaf:Agent`) and composed of a set of models (instances of `mod:SemanticArtefact`). These models are described by the [metadata presented in this link](https://github.com/unibz-core/ontouml-models/wiki/How-to-Contribute#the-ontology-metadata-file).

### Catalog's persistent URLs

We created persistent URLs for the following resources:

- GitHub repository: https://purl.org/ontouml-models
- OntoUML vocabulary: https://purl.org/ontouml-models/vocabulary
- Aggregated data: https://w3id.org/ontouml-models/catalog
- Ontology data: `https://purl.org/ontouml-models/<folderName>`

## How to contribute

Your contribution is fundamental to the catalog's success. We highly encourage authors to submit their models and tools to this catalog. With that, you will be supporting research in (ontology-driven) conceptual modeling, ontology engineering, software design, and several others.

***We greatly appreciate your contribution to this project!***

### Contribute by submitting an ontology

The easiest way to contribute to this catalog is to simply send us the following: 
1. your ontology model project; 
2. the model's metadata information; and 
3. the model's associated bibliography (when available).

If you wish to contribute to this initiative by submitting your ontology, please follow the instructions available in [our wiki](https://github.com/unibz-core/ontouml-models/wiki).

Note that we also include anonymous ontologies in the catalog. So, if you don’t want your name to be displayed in your ontology’s metadata, you just have to inform us and we will keep the model’s authorship anonymous. It is important that, in such case, you must be the owner of the ontology’s legal rights.

If you wish to contribute by submitting another ontology, please chose one entry from the "*Not Started*" or "*Started*" sheets from the [List of UFO and OntoUML Ontology Models](https://docs.google.com/spreadsheets/d/1JXEA3k58yAkV_jbmEc7HP9QK7RgZC5Jk1y8MR7ylFyQ/edit?usp=sharinghttps://docs.google.com/spreadsheets/d/1JXEA3k58yAkV_jbmEc7HP9QK7RgZC5Jk1y8MR7ylFyQ/edit?usp=sharing) and follow the instructions available in [our wiki](https://github.com/unibz-core/ontouml-models/wiki). Ontologies in the *Started* sheet already have files available in a branch (informed in the spreadsheet), simplifying the collaboration process.

For providing high-quality data, submissions are required to comply with the defined rules to be accepted as part of the catalog. If you have any questions about submitting new models or reusing those available in this catalog, please [create an issue](https://github.com/unibz-core/ontouml-models/issues).

### Contribute by reporting an ontology

If you know a UFO or OntoUML ontology to be included in the catalog, please share this information with us! This can be done through the [catalog's contribution form](https://forms.gle/wNSMfaJfkS3hi69o7) or by [creating an issue](https://github.com/unibz-core/ontouml-models/issues).

We provide a [List of UFO and OntoUML Ontology Models](https://docs.google.com/spreadsheets/d/1JXEA3k58yAkV_jbmEc7HP9QK7RgZC5Jk1y8MR7ylFyQ/edit?usp=sharinghttps://docs.google.com/spreadsheets/d/1JXEA3k58yAkV_jbmEc7HP9QK7RgZC5Jk1y8MR7ylFyQ/edit?usp=sharing) (read-only) that registers models to be further included in the catalog. The information received from collaborators is going to be included in this list.

### Contribute by reporting an application

If you wish to contribute to this initiative by **creating and reporting an application** for the catalog, please inform us through the [catalog's contribution form](https://forms.gle/wNSMfaJfkS3hi69o7) or [create an issue](https://github.com/unibz-core/ontouml-models/issues).

### Other ways to contribute

If you find any problems in the repository or have ideas for its improvement, please let us know through the [catalog's contribution form](https://forms.gle/wNSMfaJfkS3hi69o7) or by [creating an issue](https://github.com/unibz-core/ontouml-models/issues).

## Related software applications

Up to this moment, we have no reported applications for querying, data manipulation, or evaluation. If you want to contribute, please refer to this document's section ["Contributing by reporting an application"](#contributing-by-reporting-an-application).

## Works citing and using the OntoUML/UFO Catalog

The list of works that use the data provided by the OntoUML/UFO Catalog to test algorithms and perform other tasks grows over time. Instead of keeping a manual list in this document, we recommend you access its [Google Scholar](https://scholar.google.com/scholar?cites=3857815022699931555&as_sdt=2005&sciodt=0,5&hl=en) and [ResearchGate](https://www.researchgate.net/publication/364289037_A_FAIR_Model_Catalog_for_Ontology-Driven_Conceptual_Modeling_Research/citations) citation lists to obtain more updated information.

## Catalog administration

The OntoUML/UFO Catalog is maintained by UFO and OntoUML researchers at the Free University of Bozen-Bolzano and at the University of Twente, in particular by:

- Dr. Pedro Paulo Favato Barcelos [[GitHub]](https://github.com/pedropaulofb) [[LinkedIn]](https://www.linkedin.com/in/pedro-paulo-favato-barcelos/)
- Dr. Tiago Prince Sales [[GitHub]](https://github.com/tgoprince) [[LinkedIn]](https://www.linkedin.com/in/tiago-sales/)
- Dr. Mattia Fumagalli [[GitHub]](https://github.com/Matt-81) [[LinkedIn]](https://www.linkedin.com/in/mattiafumagalli/)
- Dr. Claudenir Morais Fonseca [[GitHub]](https://github.com/claudenirmf) [[LinkedIn]](https://www.linkedin.com/in/claudenir-fonseca-52b251216/)

Feel free to get in contact with the administrators using the links provided. For questions or issues, you can [open an issue](https://github.com/unibz-core/ontouml-models/issues) at this repository.

Relevant instructions for administrating the OntoUML/UFO Catalog are presented on this specific [Wiki page](https://github.com/unibz-core/ontouml-models/wiki/Instructions-for-the-catalog's-administrators).

## How to cite this catalog

Please cite the OntoUML/UFO Catalog as: 

*Barcelos, P. P. F., Sales, T. P., Fumagalli, M., Fonseca, C. M., Sousa, I. V., Romanenko, E., Kritz, J., & Guizzardi, G.* (2022). **A FAIR Model Catalog for Ontology-Driven Conceptual Modeling Research**. 41st International Conference Proceedings (ER 2022), 17-20 October 2022. <https://purl.org/ontouml-models/>

For creating citations using different formats, refer to the [webpage of the paper's publisher](https://link.springer.com/chapter/10.1007/978-3-031-17995-2_1#citeas) for getting the paper's complete information. 

For obtaining the paper's complete BibTeX record, we recommend downloading this information on [the same webpage](https://citation-needed.springer.com/v2/references/10.1007/978-3-031-17995-2_1?format=bibtex&flavour=citation) or accessing it on the [DBLP BibTeX record](https://dblp.org/rec/conf/er/BarcelosSFFSRKG22.html?view=bibtex).

<!--- Insert link to ER Paper as soon as it is on ResearchGate--->

This paper reflects the state of the catalog as of June 2022.

## Acknowledgements

We would like to thank all of the [contributors](https://github.com/unibz-core/ontouml-models/graphs/contributors) to the OntoUML/UFO Catalog, as well as all of the modelers who shared their work and allowed us to include it here.

## License disclaimer

Although the OntoUML/UFO Catalog is an open project with a permissive license, special attention must be given to the following licensing clauses:

* The OntoUML/UFO Catalog is a noncommercial work created strictly for academic research purposes.
* This license only applies to the catalog structure itself, not to the models included in the repository.
* Information about licensing of individual ontologies included in the catalog can be found on their related metadata.yaml file.
* The models included in the repository were obtained directly from the authors or academic sources using open or valid licensed access.
* This license by no means overwrites the license of the models included in the repository, which maintain their original license.
* All catalog ontologies that are without explicit licensing information on their associated metadata.yaml file must be interpreted as being private and having a restrictive license.
* License holders sending their models to the OntoUML/UFO Catalog expressly agree that the sent content is going to be hosted and made available for other users in the terms of this license.
* Whoever uses the OntoUML/UFO Catalog expressly understands and agrees with its licensing information.

Ontologies are going to be immediately removed from the catalog in case of a request by the original license holders. For content removal, please [create an issue](https://github.com/unibz-core/ontouml-models/issues) or report it through the [catalog's contribution form](https://forms.gle/wNSMfaJfkS3hi69o7).

Please access [the OntoUML/UFO Catalog's LICENSE file](https://raw.githubusercontent.com/unibz-core/ontouml-models/master/LICENSE) for the complete licensing information.
