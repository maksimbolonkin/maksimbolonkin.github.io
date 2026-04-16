---
layout: post
title:  Is the SCOTUS partisan? Data Science approach.
description: Data analysis of how many of the SCOTUS decisions are actually partisan
categories: [data science]
---

With the current polarization of political life in the United States, one common accusation we see across both mass and social media is that the Supreme Court is extremely partisan. This generally means that the Justices of the Supreme Court render decisions along party lines rather than based on the merits of the case or the actual meaning of the Constitution. But is that true, and was it always the case?

Data Collection

To analyze this question, I collected data on the composition of the court and the voting outcomes in the cases this court decided. Cases organized by Justices and their votes can be found  here. This file contains detailed information about each case decided by the SCOTUS from 1946 to 2023, including which Justice voted which way (with the majority or dissenting). I also manually scraped data on Justices from the covered period. For each Justice in the list of all Justices, I identified the judge's party affiliation. The implicit assumption about SCOTUS nominations and confirmed Justices is that they are non-partisan and impartial. However, the question that we are trying to analyze is to what extent the accusations of partisanship are substantiated. Therefore, I will be using the party affiliation of the President who nominated a judge as a proxy for the party affiliation of that judge.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-total-cases.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

We can see that the total number of decided cases has been going down since the 1980s to about 60-70 per year. The reason for this decline in productivity is unclear and frankly is out of the scope of this post.

We can look at the composition of the court now.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-composition.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

In 1946-1952, all of the judges on the highest bench in the country were appointed by Democratic Presidents Franklin D. Roosevelt and Harry S. Truman. Starting with Chief Justice Earl Warren, nominated by Dwight D. Eisenhower, Republican Justices have increased in number and, since the 1970s, have never been in the minority. A few cases in which the total number exceeded 9 are due to years in which both an outgoing (retiring or deceased) and a newly appointed Justice were active.

Voting Pattern Analysis

First, we can look at how many cases are decided unanimously or near-unanimously (with only one dissenting judge).

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-unanimous.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

In 30% to 45% of cases, there is no major split in opinions. If we add near-unanimous decisions in which one judge was not persuaded by the majority, we estimate that easily half of the cases are decided by consensus. Which already indicates that if there is a level of partisanship in the decision-making, it is not very high. Before we look any further, we can check who that lone dissenter is.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-single-dissenter.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

Turns out, on average, it can be anyone: both Republican and Democratic Justices can be a lonely voice of the opposition. Two notable deviations from this rule: before 1953, there were no Republican judges on the bench to dissent, and there is also an unexplained dip in the middle of the 1980s. One would think that when Democratic judges are vastly outnumbered by Republican judges, we would see more dissents from the Democratic Justices, but that is not the case.

But let’s look further, what if the other half of the cases is decided exclusively along party lines? We are interested in how many cases judges with the same affiliation vote together (we consider only years from 1953, when more than one party was represented).

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-party-total.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

We can see that Democratic judges used to vote together much more than conservative judges from 1970 to 2010. In the early 1990s on all the cases, Democratic judges were united (which is not very surprising since there were only two of them). After 2010 levels are roughly the same. But we have to adjust for unanimous decisions as well: in these, all judges vote together but not along party lines.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-party-adjusted-for-unanimous.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

Trends are similar, albeit smaller in absolute values. Which, again, is not surprising, since roughly around the same time conservative judges were in an uninterrupted majority, with only two liberal judges (or sometimes even one). One thing to note is the drastic increase in conservative unanimity from 2010 onward, which somewhat aligns with the rise in political and societal polarization.

Now, if we assume some sort of partisanship in decisions, clearly, whenever there is an imbalance of more than 5:4 to one of the sides, judges from the larger group can feel less pressured to vote in line with other judges from the same group. They can dissent without compromising the desired outcome. We can adjust for such cases by adding cases in which one of 6 or 7 judges in the majority group dissented.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-party-adjusted-for-single-dissenter.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

We can see that the gap between parties has narrowed: in many cases, each party votes together to win, leaving some leeway for one to dissent without changing the majority decision. However, again, liberal judges seem to vote together more often than conservative judges. But how often do they vote against each other? We can look at cases where the vote split exactly along party lines.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-party-division.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

Turns out, this does not happen very often: only around 10% of cases are decided that way. More interestingly, this happens more often when the imbalance in court composition is greater: the dip in the 2010s aligns with the period when the court was 4:5 liberal to conservative.

Individual Voting Patterns

As an additional exercise, we can examine the voting patterns of individual Justices. For example, we can check which judge agrees with the majority most or least often.

| Justice | % cases | |Justice | % cases |
| :— | :------------- | |:------------ | :------------ |
| Kavanaugh       | 93.9       | | Douglas       | 71.3       |
| Kennedy       | 91.7       | | Marshall       | 72.0       |
| Barrett       | 90.8      | | Harlan       | 72.0       |

Justice Kavanaugh is the most agreeable judge on the bench so far, while William O. Douglas was the most disagreeable over his record long 36.6 year long tenure. Coincidentally, William O. Douglas and John Marshall Harlan II are the judges who were the most often lone dissenting voices in their cases. On the opposite, Kavanaugh, Kagan, Barrett, and Goldberg never dissented from the unanimous majority.

When it comes to agreement among individual judges, the highest level is between Kavanaugh and Roberts, who agree on 95% of the cases before them. On the opposite end of the spectrum, judges Douglas and Rehnquist disagreed on 57% of the cases.

Finally, if we look at the percentage of agreement and disagreement for the current Supreme Court, we can clearly see a division between the liberal and conservative Justices.

<div align=center>

    {% include figure.html path="assets/img/2024-03-05-agreement.png" class="img-fluid rounded z-depth-1" zoomable=true %}

    {% include figure.html path="assets/img/2024-03-05-disagreement.png" class="img-fluid rounded z-depth-1" zoomable=true %}

</div>

Conclusion

In conclusion, even though the amount of partisan voting among Supreme Court Justices increased in recent years, it is not as prevalent as people might think. The impression of partisanship is likely stemming from a small number of very politicized cases, such as Dobbs v. Jackson Women’s Health Organization, that are intensively covered by the media.