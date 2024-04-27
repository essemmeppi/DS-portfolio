# Hi, I'm Simone Maria Parazzoli 👋

I'm a public policy graduate turned `data scientist`. I hold an MPP from Sciences Po and Bocconi University (_cum laude_) and I'm currently a Junior Researcher at [ISI Foundation](https://isi.it/en/home), where I'm developing a dashboard for policymakers to assess reforms' public acceptability through online data.

If you want to know more on my education and experience, please have a look at my resume.

<!--## Education

- **Bocconi University** $|$ MSc Public Policy (_cum laude_, 03/23)
- **Sciences Po** | Master in Public Policy (_cum laude_, 06/22)
- **University of Bologna** | BA Political Science (_cum laude_, 07/20)

## Experience
- **ISI Foundation** | Junior Data Scientist (05/23 - Present)
- **OECD Observatory of Public Sector Innovation** | Intern (10/22 - 03/23)
- **Digital Policy Alert** | Consultant (07/22 - 09/23)
- **Bocconi LEAP** | Research Assistant (04/21 - 07/21)and -->

# Data Science Projects

## Understanding Public Acceptability Through Multi-Channel Analysis
Developed in partnership with the [OECD](https://www.oecd.org), the project aimed to assess public acceptability of policy reforms using online data. Unfortunately, access to X/Twitter users' data was cut off a few weeks before the project started, hence we decided to rely on news media articles as our main data source. We also used parliamentary speeches to characterise the difference between how the media and politicians discussed the reform. We worked retrospectively on the case study of the [2023 French pension reform](https://en.wikipedia.org/wiki/2023_French_pension_reform_law).

To assess public acceptability, we used an OECD framework that identifies four main dimensions of public acceptability: economic, fairness, risk and time, and process. We operationalised this framework by having subject matter experts create four lists of keywords for the dimensions, which helped us navigate the textual data (and the corresponding embedding space).

After downloading and preprocessing media data from [GDELT](https://www.gdeltproject.org) through Google BigQuery and parliamentary speeches from the open data portal of the French Parliament, the main steps of the analysis were:
- Assess how close each document (article or speech) is to each of the four dimensions of public acceptability (inspired by [Mitra et al., 2016](https://doi.org/10.48550/arXiv.1602.01137));
  - Train Word2Vec with [gensim](https://radimrehurek.com/gensim/index.html) and obtain doc embeddings calculated as the centroid of the word vectors in each document;
  - Compute the cosine similarity between the doc embeddings and each vector associated with the keywords of the four dimensions.

![Public Acceptability Dimensions](/DS-portfolio/assets/img/publicacceptability_timeseries_new.png)

- Obtain a subset of the most representative documents for each dimension and detect latent topics within them using NMF topic modelling with [scikit-learn](https://scikit-learn.org/stable/index.html); 
  - Filter relevant articles by considering the number of keywords their position in the distribution of similarity with the four dimensions (in the picture above, the time series of the number of weekly articles identified for each dimension);
  - Explore sub-themes within each dimension by training an NMF topic model on the four subsets of articles.

![Public Acceptability Dimensions](/DS-portfolio/assets/img/publicacceptability_dimensions.png)

- Understand how the reform was discussed differently in the media and in parliament by comparing corpora with coupled matrix factorisation ([matcouply](https://matcouply.readthedocs.io/en/latest/) package). The same was done to explore the different discourses in left and right leaning media outlets.
  - Factorise with NMF topic modeling both corpora and detect latent topics;
  - Assess how much each corpora covered each topic by vertically summing the weights in the doc-topic matrix of the two corpora and measuring the gap in coverage.

![Public Acceptability Dimensions](/DS-portfolio/assets/img/corpuscomparison_parl&media.png)

![Public Acceptability Dimensions](/DS-portfolio/assets/img/corpuscomparison_left&rightmedia.png)

You can find my code for this project [here](https://github.com/essemmeppi/DS-portfolio/blob/main/code/publicacceptability_dimensions.ipynb) (identifying documents related to the four dimensions and exploring them with topic modeling) and [here](https://github.com/essemmeppi/DS-portfolio/blob/main/code/publicacceptability_corpuscomparison.ipynb) (comparing media and parliamentary corpora).

## Mental Health and Mobility in COVID-19 Recovery
In November 2023, I organised a 72-hour social data science hackathon with the junior researchers of ISI. We asked our seniors colleagues to share interesting datasets with us, and we ended up combining:
- Mobility data from mobile phones in the US ([Kang et al., 2020](https://www.nature.com/articles/s41597-020-00734-5));
- Twitter posts by authors geolocated in the US ([Mejova & Manikonda, 2023](https://doi.org/10.48550/arXiv.2305.11398));
- The results of a survey conducted on Facebook examining COVID-19 impact ([Salomon et al., 2021](https://pubmed.ncbi.nlm.nih.gov/34903656/));
- Information on policy response to the pandemic (Oxford COVID-19 Government Response Tracker, [OxCGRT](https://www.nature.com/articles/s41562-021-01079-8)).

We manipulated the county-level origin-destination matrices, which provide information on mobility, in two steps. First, we calculated each county's mobility (both in-out and out-in) based on a base period of 2019. We then aggregated county mobility to obtain mobility at the state level.

We used Twitter data to quantify daily mental distress for each of the 51 states. We did this using a lexicon-based approach ([EmoLex](https://saifmohammad.com/WebPages/NRC-Emotion-Lexicon.htm)), which allowed us to assess how each tweet was associated with eight basic emotions: anger, fear, anticipation, trust, surprise, sadness, joy, and disgust.

We used the survey's questions about feelings of depression or anxiety to obtain a self-reported measure of mental health at the state level. Finally, we used the OxCGRT data to know how strict the government response was each day, and thus to understand when social restrictions were relaxed.

Using regressions, we found that self-reported mental distress, such as anxiety and depression, had a negative significant relationship with mobility. Further, we found that they Granger-caused the recovery of mobility in different states after the initial restriction was lifted. Hence, the changes over time of self-reported mental health significantly preceded the changes in mobility. This finding suggests that mental distress may serve as predictor of mobility recovery during the relaxation phase of interventions. As such, it matters a lot and it should be incorporated into the design of public health interventions.

We are finalising a paper that will soon be submitted to a peer-reviewed journal.

![Public Acceptability Dimensions](/DS-portfolio/assets/img/mobility_mentalhealth_map.png)
 
## The Office US: Why you try to go beyond the first season
In April 2023, I decided to leave the OECD Observatory of Public Sector Innovation ([OPSI](https://oecd-opsi.org)) and change my career trajectory towards data science. I wanted to get back on Python and decided to have some fun with a toy project. As a fan of The Office US and a data enthusiast who had never scraped the web, I knew there was one simple silly thing that I could do.

I scraped IMDB with [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/) and extracted the rating of each episode of every season of The Office. And, _et voilà_, I had the evidence I needed. The first season consistently received low ratings. Hence, potential fans should really make an effort and get beyond the first season. Then, they will find what made everyone fall in love with the series (and you can skip some episodes of the last two seasons, just go straight to the last three episodes).

![The Office Ratings](/DS-portfolio/assets/img/theoffice.png "The Office US Ratings on IMDB")

## Diving into French Presidential Discourses
In 2022 I took the course that made me realize I wanted to pursue a career in data science: _Diving in the Digital Public Space_ by [Jean-Philippe Cointet](https://medialab.sciencespo.fr/equipe/jean-philippe-cointet/) (Sciences Po) and [Márton Karsai](https://networkdatascience.ceu.edu/people/marton-karsai) (Central European University). For the final project, I studied the discourses of candidates to the 2022 French presidential elections with two colleagues, combining my political science and (limited) data science knowledge with their anthropology background. We were then invited to present this research at the 2022 Digital Democracy Workshop at the University of Zurich.

The study aimed to elicit the difference in meaning attributed to key words in political discourse, which have the potential to betray latent politics of the candidates in question. The discourses of 7 candidates for the French presidential election of 2022 were analysed by comparing the variable word-embedding models trained on each candidates’ corpora. The corpora were made of the Twitter activity of candidates, the Twitter activity of around 15 affiliates for each candidate, and each candidate’s campaign manifesto. 

We qualitatively compared the word vectors of key shared words, analysing the most similar words to them in the variable word-embedding spaces to find different political inclinations. We concluded that the difference in political meaning of key concepts is palpable, yet that our method must be paired with a strong qualitative-interpretive approach in order to be analytically and socially relevant.

The technical pipeline involved:
- Scraping candidates and their affiliates' tweets with [minet](https://github.com/medialab/minet);
- Train a Word2Vec for each candidate with [gensim](https://radimrehurek.com/gensim/index.html);
- Explore the meaning of selected keywords considering the most similar word vectors.

You can fine the code and the paper of this project [here](https://github.com/essemmeppi/diving-into-french-presidential-discourses/tree/main).
