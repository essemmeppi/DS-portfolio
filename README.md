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
Developed in partnership with the [OECD](https://www.oecd.org), the project aimed to assess public acceptability of policy reforms using online data. Our main data source was media articles -- X/Twitter would have been much better, but access to users' data was cut off a few weeks before the project started. We also used parliamentary speeches to characterise the difference between how the media and politicians discussed the reform. We worked retrospectively on the case study of the [2023 French pension reform](https://en.wikipedia.org/wiki/2023_French_pension_reform_law).

To assess public acceptability, we used an OECD framework that identifies four main dimensions of public acceptability: economic, fairness, risk and time, and process. We operationalised this by having subject matter experts create four lists of keywords for the dimensions, which helped us navigate the textual data (and the corresponding embedding space).

The main steps of the analysis were:
- Assess how close each document (article or speech) is to each of the four dimensions of public acceptability (inspired by [Mitra et al., 2016](https://doi.org/10.48550/arXiv.1602.01137));
  - Train Word2Vec and obtain doc embeddings calculated as the centroid of the word vectors in each document;
  - Compute the cosine similarity between the doc embeddings and each vector associated with the keywords of the four dimensions;
- Obtain a subset of the most representative documents for each dimension and detect latent topics within them using NMF topic modelling; 
  - Filter relevant articles by considering the number of keywords they contain and their percentile position in the distribution of similarity with the four dimensions.
  - Explore sub-themes within each dimension by training an NMF topic model on the four subsets of articles
- Understand how the reform was discussed differently in the media and in parliament by comparing corpora using topic modelling. 
  - Train a single NMF topic model with media articles and parliamentary speeches
  - Assess how much each corpora covered each topic by vertically summing the weights in the doc-topic matrix of the two corpora and measuring the gap in coverage.

## Mental Distress and Mobility in COVID-19 Recovery
In November 2023, we - the juniors at ISI Foundation - decided to run a 72-hour social data science hackathon. We asked seniors at ISI to share interesting datasets with us, and we ended up combining:
- Mobility data from mobile phones in the US ([Kang et al., 2020](https://www.nature.com/articles/s41597-020-00734-5));
- Twitter posts by authors geolocated in the US ([Mejova & Manikonda, 2023](https://doi.org/10.48550/arXiv.2305.11398));
- The results of a survey conducted on Facebook examining COVID-19 impact ([Salomon et al., 2021](https://pubmed.ncbi.nlm.nih.gov/34903656/));
- Information on policy response to the pandemic (Oxford COVID-19 Government Response Tracker, [OxCGRT](https://www.nature.com/articles/s41562-021-01079-8)).

We manipulated the county-level origin-destination matrices, which provide information on mobility, in two steps. First, we calculated each county's mobility (both in-out and out-in) based on a base period of 2019. We then aggregated county mobility to obtain mobility at the state level.

We used Twitter data to quantify daily mental distress for each of the 51 states. We did this using a lexicon-based approach ([EmoLex](https://saifmohammad.com/WebPages/NRC-Emotion-Lexicon.htm)), which allowed us to assess how each tweet was associated with eight basic emotions: anger, fear, anticipation, trust, surprise, sadness, joy, and disgust.

We used the survey's questions about feelings of depression or anxiety to obtain a self-reported measure of mental health at the state level. Finally, we used the OxCGRT data to know how strict the government response was each day, and thus to understand when social restrictions were relaxed.

Using regressions, we found that self-reported mental distress, such as anxiety and depression, had a negative significant relationship with mobility. We also found that they Granger-caused the recovery of mobility in different states after the initial restriction was lifted. This finding suggests that mental distress may serve as a valuable proxy and predictor of mobility recovery during the relaxation phase of interventions. For this reason, mental health should be incorporated into the design of public health interventions.

We are finalising a paper that will soon be published on arXiv.
 
## The Office US: Why you try to go beyond the first season
In April 2023, I decided to leave the OECD Observatory of Public Sector Innovation ([OPSI](https://oecd-opsi.org)) and change my career trajectory towards data science. I wanted to get back on Python and decided to have some fun with a toy project. As a fan of The Office US and a data enthusiast who had never scraped the web, I knew there was one simple silly thing that I could do.

I scraped IMDB with BeautifulSoup and extracted the rating of each episode of every season of The Office. And, _et voilà_, I had the evidence I needed. The first season consistently received low ratings. Hence, potential fans should really make an effort and get beyond the first season. Then, they will find what made everyone fall in love.

## Diving into French Presidential Discourses
In 2022 I took the course that made me fall in love with social data science: _Diving in the Digital Public Space_ by [Jean-Philippe Cointet](https://medialab.sciencespo.fr/equipe/jean-philippe-cointet/) (Sciences Po) and [Márton Karsai](https://networkdatascience.ceu.edu/people/marton-karsai) (Central European University). For the final project, two colleagues and I studied the discourses of candidates to the 2022 French presidential elections. We were then invited to present this research at the 2022 Digital Democracy Workshop at the University of Zurich.

The study aims to elicit the difference in meaning attributed to key words in political discourse, which have the potential to betray latent politics of the candidates in question. The discourses of 7 candidates for the French presidential election of 2022 are analysed by comparing the variable word-embedding models trained on each candidates’ corpora. The corpora are made of the Twitter activity of candidates, the Twitter activity of around 15 affiliates for each candidate, and each candidate’s campaign manifesto. We qualitatively compare the word vectors of key shared words, analysing the most similar words to them in the variable word-embedding spaces to find different political inclinations. We conclude that the difference in political meaning of key concepts is palpable, yet that our method must be paired with a strong qualitative-interpretive approach in order to be analytically and socially relevant.

The project was performed by:
- 
