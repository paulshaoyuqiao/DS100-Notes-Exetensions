# Sampling Bias

During the data collection process, we sometimes risk imposing **sampling bias** on the dataset we gather. 

More precisely, **sampling bias** is a bias where among all the samples we have collected in the dataset, **some members have a lower sampling probably than others**. Intuitively, it means that if we randomly choose one sample from the dataset, some samples have a higher chance of being chosen than others. 

You may wonder that realistic, shouldn't all samples be unique? Theoretically, yes; but practically speaking, each individual sample we collect is really just **an individual collection of characteristics (factors) we observe/measure**. This means **we cannot comprehensively cover every characteristic for each sample (and we probably won't either, for ones that don't really address our problems)**. 

The **sampling bias** results in a biased sample, which can cause our model to predict differently and erroneously about the true population (because of the un-even distribution within our sampling dataset). What concerns us more is the fact that when people aren't aware of this bias, **they can falsely attribute the results to the phenomenon in the study and infer something intrinsically wrong about the samples rather than raise doubts about the method of sampling**.

# Types of Sampling Bias

Here's a few different sampling biases that results from different stages in an experiment:
- Selection from a **specific location**
- **Self-selection bias**:
  - This means in the conducted experiment, **the participants have forms of control over whether to actually participate**. 
  - Their decision to participate may actually **correlate with features of the model, which makes the participants a non-representative and non-generalizable sample**.
- **Exclusion bias**:
  - This happens when we **exclude particular groups from the sample**.
  - This usually occurs not because we intentionally avoid their representation in the sample databset (hopefully), but we **have great difficulty (high cost / rare to access and measure / lack of response ) obtaining valid data for those particular groups**.
- **Survivorship bias**:
  - This happens when we only select the "surviving" objects to be included in the dataset, neglecting those that fell out of view.
  - A concrete example could be: if we build a model that analyze the factors contributing to the profit margins of pharmaceutical companies, we will likely only have access largely to **detailed financial records of the current companies in the market**, **not the ones that have closed down**. However, those who close down could contain equally valuable information for us to build an accurate model.