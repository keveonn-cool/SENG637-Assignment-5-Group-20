**SENG 637- Dependability and Reliability of Software Systems\***

**Lab. Report \#5 – Software Reliability Assessment**

| Group \#:      |     |
| -------------- | --- |
| Student Names: |     |
| Gopal Sharma   |     |
| Jubayer Ahmed  |     |
| Usman Liaqat   |     |
| Raveen Parmar  |     |
| Ehsan Liaqat   |     |

# 1. Introduction

The lab’s aim was to enhance our grasp of assessing tool reliability and using tools like C-SFRAT and the Reliability Demonstration Chart through Excel. It also covered failure reliability growth testing, which tracks how a product improves over time. We learned about failure data too, which is key in learning from past issues to prevent future ones. These concepts have deepened our understanding of the role of reliability testing in software testing processes.

# 2. Assessment Using Reliability Growth Testing

## a) Result of Model Comparison (Selecting Top Two Models)

To evaluate the reliability of our software, we used the C-SFRAT tool to compare different models. We aimed to find the two best-fitting models based on their ability to predict software failures.

## b) Model Selection Process

We considered several models and looked at various statistics to judge how well they fit our data. The two main statistics we used were the Akaike Information Criterion (AIC) and the Bayesian Information Criterion (BIC). A lower AIC or BIC value generally means a better model fit, considering the number of parameters in the model.

## c) Results

After running the analysis, we found that the two models that best fit our data were:

1. The model labeled as DW3 with covariate 'F', which had the lowest AIC and BIC values among the models considered.
2. The IFRGSB model, also with covariate 'F', showed a good fit according to its log-likelihood value, which is a measure of how likely it is to observe our data given the model.

These models are represented in the screenshots provided.
![](./media/AllModels.png)

The first screenshot shows the graph of all models' fits to the data. As seen in the provided graph , the selected models closely follow the trend of the imported failure data, indicating a strong fit

![](./media/ModelComaprisionTable.png)

The second screenshot lists the models and their corresponding AIC and BIC values.In terms of numerical comparison, the detailed statistics of AIC and BIC scores for these models can be seen in the accompanying table , where the superiority of DW3 and IFRGSB models is evident due to their lower scores compared to other models

## d) Conclusion

The DW3 and IFRGSB models stood out in our analysis. These models are the most suitable for our data, as they provide a balance between accurately fitting our past failure data and avoiding overly complex models that are difficult to generalize. They will be used to inform our understanding of the software's reliability and guide future testing efforts.

## e) Result of range analysis (an explanation of which part of data is good for proceeding with the analysis)

Using the following formula we were able to determine the laplace value for each k value.

![](./media/laplace.png)

The Laplace trend test applied to model DW3(F) yielded a result of u(31) = -0.8, falling within the range of -2 to 2, indicating that data within intervals [0,31] is considered acceptable. The above figure illustrates the application of the Laplace trend test to the DW3(F) model. Furthermore, the above figure demonstrates reliability growth, as the u(k) values consistently fall below zero within the interval [3,31].

![](./media/uk1.png)

The Laplace trend test conducted on the IFRGSB(E,F) model yielded a result of u(31) = -0.54, falling within the acceptable range of -2 to 2. This implies that the data within intervals [0,31] is deemed acceptable. The figure below illustrates the application of the Laplace trend test to the IFRGSB(E,F) model. Moreover, the figure below indicates reliability growth, as the u(k) values consistently remain below zero within the interval [27,31].

![](./media/uk2.png)

## f) Plots for failure rate and reliability of the SUT for the test data provided

### MVF Graph for Model 1:

![](./media/MVFGraph1.png)

### Intensity Graph for Model 1:

![](./media/IntensityGraph1.png)

### MVF Graph for Model 2:

![](./media/MVFGraph2.png)

### Intensity Graph for Model 2:

![](./media/IntensityGraph2.png)

### Reliability Graph Prediction (SRTAT):
    ******Pending*******

### Reliability Graph Prediction (C-SFRAT):
    ******Pending*******

## g) A discussion on decision making given a target failure rate
In this stage of our assessment, we focused on establishing a target failure rate, which serves as a critical benchmark for the reliability of the software. This target is derived by analyzing the frequency of observed failures over the operational hours of the system. A crucial aspect of this analysis was to determine a failure rate that ensures user safety while maintaining the functional integrity of the software.

By employing the predictive capabilities of C-SFRAT and cross-validating with SRTAT, we were able to set a failure rate target. This rate was calculated by dividing the total number of observed failures by the cumulative operational hours. The goal was to identify a rate that would not only be realistic but also indicative of a high-reliability standard.

Our targeted failure rate is oriented toward minimizing system downtime and ensuring a seamless user experience. With the reliability models' lowest failure intensities in mind, we set an ambitious yet achievable target. This target underpins our commitment to rigorous testing and continuous improvement, ensuring that the software meets the robust reliability criteria we have set forth before it is released to our end-users.
    

## h) A discussion on the advantages and disadvantages of reliability growth analysis
### Advantages of Reliability Growth Analysis
    
    
1. Predictive Insights: Reliability growth models are powerful in providing predictive insights into system behavior. By analyzing trends over time, organizations can forecast potential failures and plan for maintenance, which aids in resource allocation and downtime reduction.

2. Trend Identification: These models are adept at identifying patterns in failure data. They can discern whether the software's reliability is improving due to successful debugging and whether new releases are contributing to or detracting from reliability.

3. Impact Analysis: Reliability growth analysis can pinpoint when significant changes occur within the system, such as an increase in failure rates after a new version release. Understanding these impacts allows teams to refine their development and testing processes.

4. Decision Making: The graphical representation of data enables a clear visual of the software's reliability over time, guiding strategic decisions related to product releases, feature updates, and resource investment in quality assurance.

5. Development Feedback: By correlating the changes in the reliability trend with specific development activities, teams can gain feedback on the efficacy of their development practices and testing protocols.

### Disadvantages of Reliability Growth Analysis
1. Complexity and Tediousness: Constructing the required graphs for analysis can be complex and time-consuming. It requires meticulous attention to detail and significant expertise in statistical analysis.

2. Tool Discrepancy: Different tools may interpret the same data differently due to varying underlying algorithms and modeling techniques. This inconsistency can lead to confusion and make it challenging to draw definitive conclusions.

3. Model Variability: The predictions made by reliability growth models can vary based on their mathematical underpinnings. Some models may be overly optimistic or pessimistic, skewing the perception of software reliability.

4. Data Entry: The process of entering failure data, especially for complex systems with extensive historical data, can be very time-consuming. When using tools like C-SFRAT, which may require data to be formatted in a specific way, the task becomes even more daunting.

5. Interpretation Skills: Analyzing the outputs of reliability growth models often requires a high level of expertise. Misinterpretation of the graphs can lead to poor decision-making and a false sense of security about the system's reliability.

# 3. Assessment Using Reliability Demonstration Chart

![](./media/RDC1.jpeg)

The figure above shows that with a risk tolerance set at 1 failure every 10 seconds and a discrimination ratio of 2, the system will be deemed acceptable if it achieves a Failure Intensity Object of 1.5 failures per second. Therefore, both developers and customers require the software to not exceed one failure every 10 seconds.

The discrimination ratio is used to indicate the level of error tolerated in the calculations and corresponds to the gap between the acceptance and rejection thresholds. For the software to be considered satisfactory by developers and customers, it must reach a minimum Failure Intensity Object of 1.5 failures per second.

![](./media/RDC2.jpeg)

The figure above demonstrates what happens to the Failure Intensity Object (FIO) when it is halved. The reset of failure data in the continuation of the graph indicates that the FIO data neither meets nor fails the risk requirements. Instead, it remains undetermined due to the allowable error introduced by the discrimination ratio. For example, if the discrimination ratio were reduced, the failure data would be rejected under those conditions.

![](./media/RDC3.jpeg)

The figure above illustrates the effect of doubling the Failure Intensity Object (FIO), raising it to 3. This increase results in failure data significantly exceeding the acceptance rate. With an FIO of 3, the system clearly surpasses both customer and developer expectations.


# Comparison of Results
   After delving into the Reliability Demonstration Chart (RDC) analysis and contrasting the outcomes with the reliability growth testing performed in Part 1 using tools like C-SFRAT, several insights emerged. The RDC provided a straightforward evaluation of whether the system's failure rate was within acceptable risk tolerance levels. This binary 'pass' or 'fail' assessment was particularly valuable in making high-level reliability decisions.

In contrast, Part 1’s reliability growth analysis offered a more detailed trajectory of the software’s improvement over time, giving us a nuanced understanding of how reliability evolved with each development cycle. While the RDC outcomes were instrumental in validating the software against a set failure rate target, the reliability growth analysis provided actionable insights into specific areas requiring attention.

The synergy of these two analyses equips us with a comprehensive reliability profile of our software. The RDC results anchor our reliability expectations, and the growth analysis from Part 1 informs our ongoing improvement strategies.

# Discussion on Similarity and Differences of the Two Techniques

Exploring the various techniques and noting their differences was enlightening. Both methods differ yet provide visual analyses of failure rates in relation to expected values. Reliability Growth Testing offered a comprehensive view of the entire dataset over the specified timeframe, whereas the Reliability Demonstration Chart specifically facilitated comparisons between clearly accepted and rejected conditions.

The Reliability Demonstration Chart primarily highlights the system’s reliability, while Reliability Growth Testing not only enhances system reliability but also identifies overall system deficiencies. Employing these diverse techniques further enables a more complete understanding of the issues at hand and promotes improvements across various aspects simultaneously.

# How the team work/effort was divided and managed

We divided into two pairs, with each duo focusing primarily on either part one or part two of the project. Despite the division, we consistently communicated with the other pair to ensure a comprehensive understanding of the entire lab and to provide assistance whenever necessary. We arranged regular meetings every few days to review our progress and determine if further support was required. Although each team was assigned different sections, we made efforts to collaborate whenever possible.

# Difficulties encountered, challenges overcome, and lessons learned

SRTAT and the Excel sheet did not function as outlined in the lab handout, necessitating the use of C-SFRAT for the first part of the lab. Additionally, the lab instructions were not clear. Initially, the RDC spreadsheet was challenging to operate and understand, especially as it required editing privileges for modifications. However, after reviewing the instructions, using the RDC program became much simpler.

# Comments/feedback on the lab itself
The lab presented significant challenges due to the lack of detailed instructions and helpful tips, making it difficult to navigate and use the provided tools effectively. For instance, in the RDC section, the abundance of data and its disorganized presentation made it confusing to determine which values needed adjustment and which data required attention. Clearer guidance and more specific details on key areas to focus on would have greatly enhanced our ability to proceed with the lab tasks.
