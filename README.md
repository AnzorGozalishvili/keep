# KEEP - Keyphrase Extraction Evaluation Package

KEEP is a Python package that enables to extract keyphrases from documents (single or multiple documents) by applying a number of algorithms, the big majority of which provided by [pke](http://www.aclweb.org/anthology/C16-2015) an [open-source package](https://github.com/boudinfl/pke). Differently from PKE, we provide a ready to run code to extract keyphrases not only from a single document, but also in batch mode (i.e., several documents). More to the point, we consider 20 state-of-the-art datasets from which keyphrases may be extracted, and the corresponding  dfs and lda pre-computed models (which constrasts with pke as only semeval-2010 models are made available). Finally, and more importantly, we provide a schema to evaluate the results obtained through state-of-the-art metrics, thus easing the work of researchers interested in evaluating the algorithms provided (see a complete list below). 

KEEP is available on Dockerhub (ready to run) or available for download (in which case, some configurations need to be done). In any case, we provide a set of jupyter notebooks to ease the process of extracting keyphrases and evaluating the different algorithms. More on this on the Installation section.

## List of Datasets

KEEP can extract keyphrases from 20 <a href="https://github.com/LIAAD/KeywordExtractor-Datasets" target="_blank">datasets</a>:

- 110-PT-BN-KP (110 docs; PT)
- 500N-KPCrowd-v1.1 (500 docs; EN)
- cacic (888 docs; ES)
- citeulike180 (183 docs; EN)
- fao30 (30 docs; EN)
- fao780 (779 docs; EN)
- Inspec (2000 docs; EN)
- kdd (755 docs; EN)
- Krapivin2009 (2304 docs; EN)
- Nguyen2007 (209 docs; EN)
- pak2018 (50 docs; PL)
- PubMed (500 docs; EN)
- Schutz2008 (1231 docs; EN)
- SemEval2010 (243 docs; EN)
- SemEval2017 (493 docs; EN)
- theses100 (100 docs; EN)
- wicc (1640 docs; ES)
- wiki20 (20 docs; EN)
- WikiNews (100 docs; FR)
- www (1330 docs; EN)

<br>
Note however that more datasets can be added as long as they follow the coming structure:

- keys: a folder that contains for each document a file with the corresponding keywords (ground-truth)
- docsutf8: a folder that contains the documents text
- lan.txt: a file that specifies the language of the document (e.g., EN). Used to load the stopwords
- language.txt: a file that specifies the language of the document (e.g., english). Used in convert2trec.py in case the user wants to do stemming when comparing the results obtained and the ground-truth. Currently the system considers the following languages: english, spanish, french, polish, portuguese (which are the languages of the datasets being used). If more datasets are added, user's should guarantee that a proper stemming is available in case they want to apply this option in the evaluation step.

## Keyphrase Extraction Algorithms


### Unsupervised Algorithms
#### Statistical Methods

- TF.IDF. By PKE
- RAKE (Ref: Rose S, Engel D, Cramer N, Cowley W (2010). [Automatic Keyword Extraction from Individual Documents](https://onlinelibrary.wiley.com/doi/abs/10.1002/9780470689646.ch1)). By PKE
- KP-Miner (Ref: El-Beltagy S, Rafea A (2009). [KP-Miner: A Keyphrase Extraction System for English and Arabic Documents](https://www.sciencedirect.com/science/article/abs/pii/S0306437908000537). By PKE
- YAKE! (Ref: Campos R, Mangaravite V, Pasquali A, Jorge A, Nunes C, Jatowt A (2019). [YAKE! Keyword Extraction from Single Documents using Multiple Local Features](https://www.sciencedirect.com/science/article/pii/S0020025519308588?via%3Dihub); (2018) [A Text Feature Based Automatic Keyword Extraction Method for Single Documents](https://link.springer.com/chapter/10.1007/978-3-319-76941-7_63); [Demo](http://yake.inesctec.pt))

#### Graph-based Methods

- TextRank (Ref: Mihalcea R, Tarau P (2004). [TextRank: Bringing Order into Texts](https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf)). By PKE
- SingleRank (Ref: Wan X, Xiao J (2008). [Single Document Keyphrase Extraction Using Neighborhood Knowledge](https://pdfs.semanticscholar.org/8a99/634e0b418ee61c9bd81f61d334b80486dc53.pdf)). By PKE
- TopicRank (Ref: Bougouin A, Boudin F, Daille B (2013). [TopicRank: Graph-Based Topic Ranking for Keyphrase Extraction](http://www.aclweb.org/anthology/I13-1062)). By PKE
- TopicalPageRank (Ref: Sterckx L, Demeester T, Deleu J, Develder C (2015). [Topical Word Importance for Fast Keyphrase Extraction](https://core.ac.uk/download/pdf/55828317.pdf)). By PKE
- PositionRank (Ref: Florescu C, Caragea C (2017). [PositionRank: An Unsupervised Approach to Keyphrase Extraction from Scholarly Documents](http://people.cs.ksu.edu/~ccaragea/papers/acl17.pdf)). By PKE
- MultipartiteRank (Ref: Boudin F (2018). [Unsupervised Keyphrase Extraction with Multipartite Graphs](http://www.aclweb.org/anthology/N18-2105)). By PKE

### Supervised Algorithms
- KEA (Ref:	Witten I, Paynter G, Frank E, Gutwin C, Nevill-Manning C, (1999). [KEA: Practical Automatic Keyphrase Extraction](https://www.cs.waikato.ac.nz/ml/publications/2005/chap_Witten-et-al_Windows.pdf)). By PKE

## Installing KEEP
### Option 1: Docker

#### Install Docker
First, install docker. 

- Windows
<br>
Docker for Windows requires 64bit Windows 10 Pro with Hyper-V available. 
If you have this, then proceed to download [here](https://docs.docker.com/docker-for-windows/install/#download-docker-for-windows) and click on Get Docker for Windows (Stable)
<br><br>
If your system does not meet the requirements to run Docker for Windows (e.g., 64bit Windows 10 Home), you can install Docker Toolbox, which uses Oracle Virtual Box instead of Hyper-V. In that case proceed to download [here](https://docs.docker.com/toolbox/overview/#ready-to-get-started) and click on Get Docker Toolbox for Windows
<br><br>
- Mac
<br>
Docker for Mac will launch only if all of these requirements are [met](https://docs.docker.com/docker-for-mac/install/#what-to-know-before-you-install).
If you have this, then proceed to download [here](https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac) and click on Get Docker for Mac (Stable)
<br><br>
If your system does not meet the requirements to run Docker for Mac, you can install Docker Toolbox, which uses Oracle Virtual Box instead of Hyper-V. In that case proceed to download [here](https://docs.docker.com/toolbox/overview/#ready-to-get-started) and click on Get Docker Toolbox for Mac
<br><br>
- Linux
<br>
Proceed to download [here](https://docs.docker.com/engine/installation/#server)

#### Pull the image
Execute the following command on your docker machine: docker pull liaad/keep

#### Run the image
On your docker machine run the following to launch the image: docker run -p 9999:8888 --user root liaad/keep

Then go to your browser and type in the following url: http://<DOCKER-MACHINE-IP>:9999, where the IP may be the localhost or 192.168.99.100 if you are using a Docker Machine VM.
  
You will be required a token which you can find on your docker machine prompt. It will be something similar to this: http://eac214218126:8888/?token=ce459c2f581a5f56b90256aaa52a96e7e4b1705113a657e8. Copy paste the token (in this example, that would be: ce459c2f581a5f56b90256aaa52a96e7e4b1705113a657e8) to the browser, and voilá, you will have KEEP ready to run.

#### Run the jupyter notebooks
Once you logged in, proceed by running the 6 notebooks that we have prepared for you. Note that the first three are there only for informative purposes.

### Option 2: Standalone Installation
## Install KEEP library and Dependency Packages

pip install git+https://github.com/rncampos/keep
<br>

Dependencies:<br>
pip install git+https://github.com/rncampos/pke.git
<br>
pip install git+https://github.com/LIAAD/yake.git

## Install External Resources

### Spacy Language Models

PKE makes use of Spacy for the pre-processing stage. Currently Spacy supports the following languages: 

- 'en': 'english',
- 'pt': 'portuguese',
- 'fr': 'french',
- 'es': 'spanish',
- 'it': 'italian',
- 'nl': 'dutch',
- 'de': 'german',
- 'el': 'greek'

In order to install these language models you need to open your command line (e.g., anaconda) in administration mode. Otherwise they will be installed, but will return an error later on. <br>

python -m spacy download en <br>
python -m spacy download es <br>
python -m spacy download fr <br>
python -m spacy download pt <br>
python -m spacy download de <br>
python -m spacy download it <br>
python -m spacy download nl <br>
python -m spacy download el <br>

If you want to make sure that everything was properly installed go to site-packages\spacy\data and check if a shortcut for every language is found there.

Datasets with languages other than the ones above listed will be handled (in the pre-processing stage) as if they were "english".

PKE also gives the possibility of applying stemming in the pre-processing stage to the coming languages (by applying snowballStemmer):

- 'en': 'english',
- 'pt': 'portuguese',
- 'fr': 'french',
- 'es': 'spanish',
- 'it': 'italian',
- 'nl': 'dutch',
- 'de': 'german',
- 'da': 'danish',
- 'fi': 'finnish',
- 'da': 'danish',
- 'hu': 'hungarian',
- 'nb': 'norwegian',
- 'ro': 'romanian',
- 'ru': 'russian',
- 'sv': 'swedish'

Stemming will not be applied (even if defined as a parameter9) for languages different then the above referred.

### NLTK Stopwords

In terms of stopwords, PKE considers the NLTK stopwords of the following languages:

- 'ar': 'arabic',
- 'az': 'azerbaijani',
- 'da': 'danish',
- 'nl': 'dutch',
- 'en': 'english',
- 'fi': 'finnish',
- 'fr': 'french',
- 'de': 'german',
- 'el': 'greek',
- 'hu': 'hungarian',
- 'id': 'indonesian',
- 'it': 'italian',
- 'kk': 'kazakh',
- 'ne': 'nepali',
- 'nb': 'norwegian',
- 'pt': 'portuguese',
- 'ro': 'romanian',
- 'ru': 'russian',
- 'es': 'spanish',
- 'sv': 'swedish',
- 'tr': 'turkish'

In order to download these stopwords please procede as follows:

python -m nltk.downloader stopwords

In addition to this, we make use of an extended list of stopwords which can be found within the KeywordExtractors package. These are naturally instaled upon installing the package.


## Create folder Data and Download Keyword Extractor Models

Create a folder named 'data' (wherever you want to) with the following structure: 

* conversor: folder where the output (i.e., the .qrel and .out files) will be saved. You can create this folder manually, or simply wait for the system to automatically create it.
* Datasets: folder where the datasets should go in. You may already find 20 datasets ready to download <a href="https://github.com/LIAAD/KeywordExtractor-Datasets" target="_blank">here</a>. Each dataset should be unzipped to this folder. For instance if you want to play with the Inspec dataset you should end up with the following structure: Datasets\Inspec
* Keywords: folder where the keywords are to be written by the system. For instance, if later on you decide to run YAKE! keyword extractor algorithm on top of the Inspec collection, you will end up with the following structure: Keywords\YAKE\Inspec. In any case, it is not mandatory to manually create 'Keywords' folder as this will be automatically created, shouldn't exists.
* Models: Some algorithms (such as TopicRank, KEA, TF.IDF, KPMiner, etc) require a number of models in order to run (e.g., document frequency models, LDA, etc). The models needed to run the algorithms on top of each of the 20 datasets, are divided into a supervised and an unsupervised folder and are already available <a href="https://github.com/rncampos/KeywordExtractors-Models" target="_blank">here</a> for download (and should be put inside the 'Models' folder). In case you decide not to download them, the system will automatically create the 'Models' folder and the corresponding models will be put inside. Note however, that this will take you much time, thus downloading them in advance is a better option.

## Extract Keywords from a Single Doc

Inside the KeywordExtractors folder you may find a testing file (named 'test_SingleDoc.py') to extract keywords from a single document for all the algorithms herein considered. By default the system is extracting keywords from a french document, but you may also find there examples (which are commented) to extract keywords from an english, portuguese, spanish or a polish document. Note: in order to run the code, please replace the 'pathData' by the path where you have put the data folder.


## Extract Keywords from several Docs (batch mode)

Inside the KeywordExtractors folder you may find a testing file (named 'test_Batch.py') to extract keywords from several documents for all the algorithms herein considered. By default, the system is extracting keywords from all the collections for all the algorithms (this may take days in order to conclude). Note: in order to run the code, please replace the 'pathData' by the path where you have put the data folder.

## Jupyter Notebook

Instead of resorting to the previous file, you can also extract keywords (single or batch mode) by using the 'run.ipynb' jupyter notebook that you can find in our package. Therein you can find instructions on how to extract keywords from the notebook, but also from the command line. In addition, we also provide instructions on how to evaluate the results of each of the algorithms.
