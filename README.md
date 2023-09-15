# PALdb

The Public Affairs Document (PAL) database is a large dataset of public affairs documents, of which the layout is annotated with bounding boxes, and handcrafted features were extracted for each individual layout component. The source of the documents are 24 data sources from the Spanish Administration. The database contains annotations for 4 different layout components: 1) *Table*, 2) *Image*, 3) *Link*, and 4) *Text block*. Furthermore, text block were classified into one among four different semantic classes: 1) *Identifier*, 2) *Summary*, 3) *Title*, and 4) *Body Text*. Layout components were extracted using two different PDFMiners, [PyMuPDF](https://pymupdf.readthedocs.io/en/latest/) and [Camelot](https://pypi.org/project/camelot-py/). For each layout component, we extracted the following features:

- **Block**: Type of block detected (0 for *Image*, 1 for *Table*, 2 for *Link*, and 3 for *Text*). 

- **Page**: Page number in which the block was detected, starting from 0.
 
- **Position**: A 4-tuple (x<sub>0</sub>, y<sub>0</sub>, x<sub>1</sub>, y<sub>1</sub>) bounding box that defines the block’s region in the page.

- **Centroid**: A 2-tuple (x<sub>c</sub>, y<sub>c</sub>) with the block's mean point.

- **Distances**: A 4-tuple (d<sub>left</sub>, d<sub>top</sub>, d<sub>right</sub>, d<sub>bottom</sub>) with the block distance to each limit of the page.

Figure 1 illustrates some the coordinate system of the database, and the previous positional features

![](https://github.com/BiDAlab/PALdb/blob/master/data/PALdb-LAYOUT-SC.png)
**Figura 1. Coordinate system and positional features. Color codes for the annotations are gren for Identifier, cyan for Summary, pink for Title, and black for Body.**

Furthermore, based on the information obtained with the PDFMiners from the text blocks, we defined the following handcrafted text features:

- **Information**: The text itself, with a basic cleaning preprocessing.

- **Uppercase**: Proportion of capital letters in the text block.

- **Bold**: Proportion of bold tokens in the text block.
  
- **Italic**: Proportion of italic tokens in the text block.

- **Tokens**: Number of elements separated by simple space in the text block.

- **Font**: A tuple with the different font types in the text block.

- **Size**: Average font size of the text block.

The previous feature names are the keys for each attribute within the annotation files. We also define a layout **Label** attribute, with the annotations considering the semantic classes defined (0 for *Table*, 1 for *Image*, 2 for *Link*, 3 for *Identifier*, 4 for *Summary*, 5 for *Title*, and 6 for *Body Text*). The use of the **Label** attribute or the **Block** attribute as annotation depends on whether you want to use the semantic text classes defined in PAL or not

PAL is divided into a train and a valiation set. Text labels for the validation set were all validated by human supervisors. Text labels for the train set were obtained using Random Forests models trained on the validation set.

More details can be foun in our paper [``Document Layout Annotation: Database and Benchmark in the Domain of Public Affairs´´](https://link.springer.com/chapter/10.1007/978-3-031-41501-2_9).

## INSTRUCTIONS FOR DOWNLOADING PAL database
1) [Download license agreement](http://atvs.ii.uam.es/atvs/licenses/HuMidb_License_Agreement.pdf), send by email one signed and scanned copy to **atvs@uam.es** according to the instructions given in point 2.
 
 
2) Send an email to **atvs@uam.es**, as follows:

   *Subject:* **[DATABASE: PAL database]**

   Body: Your name, e-mail, telephone number, organization, postal mail, purpose for which you will use the database, time and date at which you sent the email with the signed license agreement.
 

3) Once the email copy of the license agreement has been received at BiDA-Lab, you will receive an email with a username, a password, and a time slot to download the database.
 

4) [Download the DATABASE](http://atvs.ii.uam.es/atvs/intranet/free_DB/HuMIDB/), for which you will need to provide the authentication information given in step 2. After you finish the download, please notify by email to **atvs@uam.es** that you have successfully completed the transaction.
 

5) For more information, please contact: **atvs@uam.es**

  
#### REFERENCES

Please remember to reference the following article on any work made public, whatever the form, based directly or indirectly on any part of the PAL database:

```
@InProceedings{pena2023pal,
author={Pe{\~{n}}a, Alejandro
and Morales, Aythami
and Fierrez, Julian
and Ortega-Garcia, Javier
and Grande, Marcos
and Puente, I{\~{n}}igo
and Cordova, Jorge
and Cordova, Gonzalo},
title={Document Layout Annotation: Database and Benchmark in the Domain of Public Affairs},
booktitle={Document Analysis and Recognition -- ICDAR 2023 Workshops},
year={2023},
publisher={Springer Nature Switzerland},
pages={123--138},
}
```
