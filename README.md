# thesis
This repo contains notebooks used to prepare Terry Pratchett novels for processing and statistical tests. Below is a description of each of these notebooks:

`0-data_preparation`: I load TEI XML files containing Pratchett's books and their respective metadata, such as Prachett's age at publication, the novel's date of publication, whether a novel was a young adult novel (young adult novels ended up being excluded from analysis in the final verion), wordcount, cleaned and tokenized texts, and raw texts (raw texts are used in propositional idea density analysis). Metadata and texts are stored in the file "pratchett_metadata.csv".

`1a-vocabularysize_metrics`: I extract measures of vocabulary size (mean type-token ratios, rates of indefinite word tokens, and mean rates of maximal repeated phrase types). Type-token ratios and maximal repeated phrase type rates are highly sensitive to sample size (larger texts allow for more repetitions, leading to higher repeated phrase type rates and lower type-token ratios). So, I calculate mean type-token ratio and mean maximal repeated phrase type rate for each book from 5000-token segments. Extracting mean type-token ratios and mean maximal repeated phrase type rates is based on the assumption that these metrics do not vary significantly with the position of the segment in the book. To test this assumption in each book and note it as a limitation in my paper, I also calculate Kendall's tau between segment order and mean type-token ratio, and mean maximal repeated phrase type rates. 

Mean type-token ratios, indefinite word rates, and mean maximal repeated phrase type rates are stored in `1-vocabulary_richness.csv` (this file also contains a list of the books where type-token ratio and maximal repeated phrase type rates vary with segment order). 

`1b-vocabularysize_metrics_sigtesting`: I test measures of vocabulary size - mean type-token ratio, indefinite word rate, and mean maximal repeated phrase type rate (extracted in 1a-vocabularysize_metrics) as significant predictors of age at publication, using multivariate linear regression. I also test to see if each measure of vocabulary size is correlated significantly with age with Kendall's tau. 

`2a-prop_idea_density`: I extract the propositional idea density of each book using Kairit Sirt's DEPID software. I also extract mean DEPID-R (rate of unique propositions) from books, divided into non-overlapping segments of 100 paragraphs. I don't use full texts to calculate DEPID-R because repetition rate is highly sensitive to the length of a text - longer texts allow authors to repeat themselves more. 

DEPID, mean DEPID-R, and books where DEPID-R varies with segment order are stored in `2-propositional_ID_df.csv`.

`2b-prop_idea_density_sigtesting`: I test propositional idea density (DEPID) and mean rates of unique propositions (DEPID-R) as significant predictors of age using multivariate linear regression. Kendall's tau is calculated for DEPID, mean DEPID-R, and age at publication. 

`3a-semantic_wordcategory`: For each novel, I extract rates of tokens from each of the lexico-semantic word categories: spatial preposition (e.g., 'inside'), form (e.g. 'round'), color (e.g., 'red'), number (e.g., 'twelve'), and function word (e.g. 'also'). "Number" is the only lexico-semantic word category with no pre-defined list - instead, number tokens are counted using the StandfordNLP features tagger. The function word token list is constructed by getting a list of the 300 most common words from all of Pratchett's novels (stored in the file `mostcommon300list.txt`) and manually removing content words from this list. 

Rates of spatial preposition, color, form, number, and function word tokens from full texts are stored in `3-lexicosemantic_wordcategory.csv`.

`3b-semantic_wordcategory_sigtesting`: I test rates of tokens from each lexico-semantic word category as predictors of age at publication in a multivariate linear regression model. Kendall's tau is also calculated between age at publication and each of the lexico-semantic word token rates. 
