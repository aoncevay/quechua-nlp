# quechua-nlp

### Motivation

Machine learning models for NLP requires a large amount of annotated data for a specific target language. For instance, in Machine Translation (MT), we need large amount of parallel corpora (aligned translations between two languages). Besides, monolingual data written in a language (without any aligned translation) can be exploited in severla ways (e.g. to gain generation fluency, or to translate synthetic data for machine translation). 

One of the main sources to extract parallel or monolingual texts is the Web. Nevertheless, there are languages, like Quechua, which presence in the Web is not significative ([Joshi et al., 2020](https://www.aclweb.org/anthology/2020.acl-main.560/); [Bustamante et al., 2020](https://www.aclweb.org/anthology/2020.lrec-1.356/)). This happens for different reasons, such as that the language does not have a long writing tradition, or there is not enough support (from the Gov.) to encourage the implementation of multilingual web platforms (e.g. e-commerce or Government sites in Europe are multilingual). 

There is, however, potential sources to extract data for under-represented languages like Quechua: 
- Firstly, the Bible and Jehova Witnessess (JW300; [Agic and Vulic, 2019](https://www.aclweb.org/anthology/P19-1310/)) translations were useful sources, although their religious context is limited, as the lexical coverage is not enough to work in other domains, such as in education or tourism. Moreover, previous attempts to extract the translations has missalignments and quality issues ([Caswell et al., 2021](https://arxiv.org/abs/2103.12028)). 
- Secondly, the whole Internet archive (WARC or Web ARChive file format) may have websites with Quechua texts that have not been labelled properly, as the standard language identification (LangID) tools does not cover all languages in the world ([Caswell et al., 2020](https://www.aclweb.org/anthology/2020.coling-main.579/)). A LangID that includes Quechua ([Espichán and Oncevay, 2018](https://link.springer.com/chapter/10.1007/978-3-319-90596-9_7)) might be beneficial to overcome this issue. 
- Thirdly, language activists and native speakers are using social media (e.g. Twitter, Facebook), and there is a potential source of (public) posts that can be obtained to increase the amount of text written in Quechua or other languages. A LangID tool might be useful in this aspect too, as the standard social media platforms can only filter a constrained set of languages. 

Note: Quechua is a language family that includes several variants. For pragmatic reasons, this effort focuses in the standard Southern Quechua (Quechua Ayacucho or Quechua Chanka). 

### Goals
Main goal: to obtain quality (Standard Southern) Quechua data for NLP applications, such as Machine Translation

Questions to address:
- How much written texts in Quechua is there in the Web (websites, social media feed, ...)? Can we crawl it?
- Can we filter the data by their quality?
- Can we enhance the performance of a machine translation model with the additional data extracted? (Probing task: we check whether the new data is useful in an external task, in this case, machine translation).

## 1) Review and correct current data

### Auditing data quality
Review Quechua-Spanish parallel corpora from the Bible and JW300 ([Caswell et al., 2021](https://arxiv.org/abs/2103.12028)). 

### Sentence aligner
The main isssue in the JW300 dataset are the missalingments between the source and target (Spanish and Quechua sentences). We can follow the approach used recently for Bengali ([Hasan et al., 2020](https://www.aclweb.org/anthology/2020.emnlp-main.207/))

## 2) New monolingual data

### Crawling Internet archive
To use WARC (Web Internet Archive) tools to process the Internet Archive. For instance, with [warc2text](https://github.com/bitextor/warc2text), it might be possible to replace the current language identification tool ([CLD2](https://github.com/bitextor/cld2/tree/1b3d0bc2059ebb2b5abbdcb319e7d8a566cf5578) with the LangID tool that includes Quechua ([Espichán and Oncevay, 2018](https://link.springer.com/chapter/10.1007/978-3-319-90596-9_7)).

### Wikipedia dump
To obtain the Wikipedia pages written in Quechua, and retain only the pages with significant content (e.g. there are many pages that are only the definitions of specific numbers).

### PDF extraction
To extract monolingual texts from PDF books, following the approach in [Bustamante et al. (2020)](https://www.aclweb.org/anthology/2020.lrec-1.356/) for the repository of educational books from PeruEduca and MINEDU.

### Other sources (social media)
With social media APIs, we can use specific keywords (e.g. most frequent words in Quechua that are very distinctive) and/or map user accounts that publish textual content in Quechua or other languages. The data should be cleaned and processed with a LangID.

### Optional: re-train the LangID
The LangID tool that includes Quechua and other languages spoken in Peru was trained using data from the Bible mostly ([Espichán and Oncevay, 2018](https://link.springer.com/chapter/10.1007/978-3-319-90596-9_7)). Using more recent data, such as texts from PDF books ([Bustamante et al., 2020](https://www.aclweb.org/anthology/2020.lrec-1.356/)), could improve the performance of the language identification. Also, it might be important to make it work faster, as we expect to use it for a large amount of web documents.

## 3) New parallel data

### Lexicons
To obtain the dictionary entries from different sources, including their examples (translated sentences between Spanish and Quechua). Even definitions in Quechua only can serve as monolingual data. There are dictionaries collected in: https://www.dic.qichwa.net/#/dictionaries

## 4) Machine translation: probing task
It has been organised a Shared Task (competition) for machine translation between Spanish and Quechua in the First Workshop on NLP for the Indigenous Languages of the Americas ([AmericasNLP 2021](http://turing.iimas.unam.mx/americasnlp/st.html)). By the end of April (2021), the official results are going to be published, including a benchmark for Quechua-Spanish. This could be used as a baseline:
- Baseline: Train a machine translation model using only the data available for the Shared Task, and evaluate the model with the official Test set of the competition.
- Our approach: Beides the available training data, we can add the extracted data (from different sources) to the training, and evaluate whether the performance of the machine translation system is statistically better than the baseline.
