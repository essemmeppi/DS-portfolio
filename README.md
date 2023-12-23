# Hi, I'm Simone Maria Parazzoli.

I'm a public policy graduate turned data scientist. I hold an MPP from Sciences Po and Bocconi University (_cum laude_) and I'm currently working at [ISI Foundation](https://isi.it/en/home), where I'm developing a dashboard for policymakers to assess reforms' public acceptability through online data.

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

## Data Science Projects

### Understanding Public Acceptability Through Multi-Channel Analysis

Developed in partnership with the OECD, the project aimed to assess public acceptability of policy reforms using online data. Our main data source was media articles -- X/Twitter would have been much better, but access to users' data was shut down a few weeks before the start of the project. We also used parliamentary speeches to characterise the difference between the media and politicians' discussions of the reform. We worked retrospectively on the case study of the 2023 French pension reform.

To assess public acceptability, we used an OECD framework that identifies four main dimensions of public acceptability: economic, fairness, risk and time, and process. We operationalised this by having subject matter experts create four lists of keywords for the dimensions, which helped us navigate the textual data (and the corresponding embedding space).

The main steps of the analysis were
- Assessing how close each document (article or speech) is to each of the four dimensions of public acceptability;
  - Train Word2Vec and obtain doc embeddings calculated as the centroid of the word vectors in each document
  - Compute cosine similarity between the doc embeddings and each vector associated to the keywords of the four dimensions
- Obtain a subset of the most representative documents for each dimension and detect latent topics within them using NMF topic modelling;
  - Filter relevant articles by considering the number of keywords they contained and their percentile position in the distribution of similarity with the four dimensions
  - Explore sub-themes within each dimension by training a NMF topic model
- Understand how the reform was discussed differently in the media and in Parliament by comparing corpora using topic modelling.
  - Train a single NMF topic model with news media articles and parliamentary speeches
  - Assess how much each corpora covered each topic by summing vertically the weights of the two corpora in the doc-topic matrix and measure the difference in coverage

### Mental Distress and Mobility in COVID-19 Recovery

### The Office: Why you try to go beyond the first season

### Diving into French Presidential Discourses
