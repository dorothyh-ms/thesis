# thesis
This repo contains notebooks used to prepare Terry Pratchett novels for processing and statistical tests. Below is a description of each of these notebooks:

**0-data_preparation**: I load TEI XML files containing Pratchett's books and their respective metadata, such as Prachett's age at publication, the novel's date of publication, whether a novel was a young adult novel (young adult novels ended up being excluded from analysis in the final verion), wordcount, and cleaned and tokenized texts, and raw texts (raw texts are used in propositional idea density analysis). Metadata and texts are stored in the file "pratchett_metadata.csv".

**1a-vocabularysize_metrics**: I extract measures of vocabulary size (mean type-token ratios, rates of indefinite word tokens, and mean rates of maximal repeated phrase types). Type-token ratios and maximal repeated phrase type rates are highly sensitive to sample size (larger texts allow for more repetitions, leading to higher repeated phrase type rates and lower type-token ratios). So, I calculate mean type-token ratio and mean maximal repeated phrase type rate for each book from 5000-token segments. Extracting mean type-token ratios and mean maximal repeated phrase type rates is based on the assumption that these metrics do not vary significantly with the position of the segment in the book. To test this assumption in each book and note it as a limitation in my paper, I also calculate Kendall's tau between segment order and mean TTR, and mean maximal repeated phrase type rates.

**1b-vocabularysize_metrics_sigtesting**: I test measures of vocabulary size (extracted in 1a-vocabularysize_metrics) as significant predictors of age using multivariate linear regression. I also test to see if they are correlated significantly with age. 

**2a-prop_idea_density**: I extract the propositional idea density of each book using Kairit Sirt's DEPID software. I also extract mean DEPID-R (rate of unique propositions) from books, divided into segments of 100 paragraphs. I don't use full texts to calculate DEPID-R because repetition rate is highly sensitive to the length of a text, as described above. 


