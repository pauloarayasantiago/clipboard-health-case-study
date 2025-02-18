# Leveraging CMS Data to Understand Nursing Home Staffing
## Q2 2024 Nursing Home Staffing Trends
### Paulo Araya Santiago February 15th 2025

# Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Context](#2-context)
   - [2.1 Datasets](#21-datasets)
   - [2.2 Important Metrics Created](#22-important-metrics-created)
     - [2.2.1 Contract Ratio](#221-contract-ratio)
     - [2.2.2 High Contract Days](#222-high-contract-days)
3. [Key Findings](#3-key-findings)
4. [Analysis](#4-analysis)
   - [4.1 Facilities](#41-facilities)
   - [4.2 Staffing](#42-staffing)
   - [4.3 High Contract Days](#43-high-contract-days)
   - [4.4 High Contract Days in Hours](#44-high-contract-days-in-hours)
   - [4.5 Confusing Contradiction?](#45-confusing-contradiction)
5. [Conclusions and Recommendations](#5-conclusions-and-recommendations)
   - [5.1 Conclusions](#51-conclusions)
   - [5.2 Recommendations](#52-recommendations)

# 1. Executive summary

This report presents a targeted analysis that seeks to leverage publicly available CMS datasets in order to pinpoint opportunities for Clipboard Health's sales division. It accomplishes this by examining staffing patterns in nursing homes across the U.S, focusing primarily on temporary staffing utilization. The findings presented in this report highlight characteristics of these facilities' operations that serve as opportunities for sales to target.

# 2. Context 

## 2.1 Datasets

The datasets used for this analysis come from Centers for Medicare & Medicaid Services (CMS) public datasets. For this study, two payroll datasets on daily nursing home staffing were utilized. These are submitted by the facilities and provide staffing hours and daily resident census. The staffing hours are divided into nursing staff and non-nursing, which we will call support staff for the sake of this analysis. The nursing staff dataset was narrowed into three subsets: registered nurse (RN), licensed practical nurse (LPN) and certified nursing assistant (CNA); given that they form the bulk of this archetype. The non-nursing staff was used in its totality, with every role contributing to support metrics.

## 2.2 Important Metrics Created

### 2.2.1 Contract Ratio
	
All of the selected subsets of nursing staff were assigned a ratio for every single day logged. This ratio consists of how many hours of the total hours worked by the staff of that particular subset were done by contract staff. The importance of this metric is highlighted by the fact that this is the particular niche that Clipboard is looking to insert itself in. Contract ratios represent the primary market share the sales team might seek to replace with Clipboard Health Affiliates by offering a more reliable alternative.

Contract Ratio (Staff Type) = Contract Hours for That Staff Type/Total Hours for That Staff Type

### 2.2.2 High Contract Days
	
High contract days are a phenomenon where any of the subsets of staff clocks in with almost a totality of contract staff on that particular day. The exact measurement decided on was any day with over 99% of the hours covered by contract staff, or in other words, any day with a contract ratio over 0.9. One hundred percent was not picked because it might be too strict on some measures after transformation. The nature of these days present a unique opportunity if their patterns can be determined and honed into precise marketing targets.

# 3. Key Findings

* Support staff shows the highest contract ratios overall. Often more than doubling the ratios of nursing staff.
* Smaller facilities have the higher percentages of high contract days across all staffing types. This might suggest they are more likely to experience extreme staffing situations.
* Most of the high contract days occur on the weekends (~65%). 
* Although contract staffing only represents about 4% of the total hours registered for both datasets, this 4% represents ~4 million hours across more than 7000 different facilities.

# 4. Analysis

## 4.1 Facilities
	
Each individual facility is represented by provider number and contributed approximately ninety-one days of data to the datasets. There are a total of 14,546 facilities, which were binned into four sizes: small, medium, large, and very large. They reported census ranging from 1 to 732 occupants. The maximum number of occupants reported hints at the possibility of overflowing facilities given that the largest facilities tend to range between the 200s; alternatively, domain research suggests that these facilities might be multi-compound facilities reporting under the same name. The smallest facilities with fewer than 50 average residents represent almost a fourth of the total distribution.

### 4.1.1 The Numbers

Total Facilities:
* 14,564 total facilities (per the bar chart legend)
* Each facility contributed about 91 days of data

Size Categories:
* Small (< 50 residents): 3,551 facilities (24.4 percent of total)
* Medium (50–104 residents): 7,337 facilities (50.4 percent)
* Large (104–200 residents): 3,315 facilities (22.8 percent)
* Very Large (> 200 residents): 361 facilities (2.5 percent)

Census Range:
* Minimum reported: ~1 or 1.4 residents (depending on rounding)
* Maximum reported: ~732 residents

## 4.2 Staffing

These plots demonstrate the daily trends of the different staffing types with regards to the amount of temporary staff. Nursing subsets oscillate between ~6-9% throughout the week, with licensed practical nurses presenting the higher percentages. RN, LPN and CNA, all show a significant spike on weekends, with increases of about ~20%. On the other hand support staff by default presents a much higher ratio throughout the week, representing an almost compounded sum of the percentages of its counterparts (although it decreases on weekends). This highlights two points; weekends represent a consistent rise in contract nursing staff and support staff presents a considerable consistent need for temporary staff.

### 4.2.1 The Numbers

Nursing Staff (RN, LPN, CNA):
* Percent Contract Usage Ranges (Weekdays vs. Weekends)
  * RN: ~ 6–7 percent on weekdays, rising to ~ 7.8–7.9 percent on Saturday/Sunday
  * LPN: ~ 7.9–8.6 percent on weekdays, climbing to 9.9–10 percent by Sunday
  * CNA: ~ 5.7–6.5 percent on weekdays, up to ~ 7.7–7.9 percent on weekends
* Weekend Increase (comparing weekend to weekday average):
  * RN: + 19.3 percent
  * LPN: + 19.3 percent
  * CNA: + 23.3 percent

Support Staff:
* Average contract usage during weekdays: around 26–27 percent
* Weekend usage drops to ~ 25 percent on Saturday and 23.1 percent on Sunday
* Net weekend change: – 8.7 percent compared to weekdays

## 4.3 High Contract Days
	
Following the time analysis, almost 65% of high contract days occur on the weekends. That is two days in which most of these particular opportunities to fill in temporary slots occur. Given that there are over 79000 of these days, it can be implied that they represent at least as many shifts that need filling.

More than 7000 unique facilities experience high contract days. Across all facility sizes support staff holds the highest percentage of high contract days, with RN's a not so close second. However, small facilities display the highest percentages of high contract days when compared to its peers. In context these differences can add up to be significant, but further analysis into how many hours of labor they represent is required. Although lower than the rest, the largest facilities still require a significant amount of RN and support; pending exploring how many hours these percentages actually represent.

A smaller percentage of high contract doesn't necessarily mean fewer hours as the facility size can compound into larger sums. Caution arises from the plots which demonstrates that more high contract days does not imply more contract hours(~6% high contract days only sum up to about ~4% of hours).

### 4.3.1 The Numbers

* Total "High Contract" Days: ~ 79,219
* Weekend vs. Weekday Share
  * 65 percent of these high‐contract days fall on weekends
  * Saturday: ~ 32.6 percent
  * Sunday: ~ 32.4 percent
  * Only ~ 35 percent happen Monday–Friday combined
* Number of Facilities with High‐Contract Days: 7,072 unique facilities
* By Staff Type (Small Facilities example)
  * Support: 4.5 percent of days at ≥ 99 percent
  * RN: 3.0 percent
  * LPN: 2.6 percent
  * CNA: 0.3 percent
* Hours vs. Days
  * High‐contract days make up 6 percent of facility‐days but only 4 percent of total staff hours (pie charts)

## 4.4 High Contract Days in Hours

When you add up all the hours that high contract days represent, you reach a total of more than ~4 million hours of contract work. Neither large facilities with their big staff sizes nor small facilities with their high ratios, take the number one spot in total hours. Medium facilities almost double their competition. This is unsurprising being the largest pool of facilities, but what is interesting is that the demographic that needs the most amount of contract hours throughout all facilities sizes, are certified nursing assistants. Here we have found our true niche in the data, certified nursing assistant are across the board sought after positions that need temporary filling; rising especially on the weekends. Considering their size, it is also worth mentioning that small facilities amount to a staggering accumulation of contract hours; matching large facilities in their needs of CNA's.

### 4.4.1 The Numbers

Total Contract Hours on High‐Contract Days:
* All facilities combined: just over 4 million contract hours on high‐contract days.

Medium Facilities Dominate Total Hours:
* Medium facilities: 1,923,321 total contract hours (nearly double the next‐largest total)
* Small facilities: 1,004,766 total hours
* Large facilities: 863,591 total hours
* Very Large facilities: 201,425 total hours

CNAs Are the Most In‐Demand Group:
* Across all facility sizes on high‐contract days, CNA hours are consistently the single biggest chunk of total contract hours. For example:
  * Small facilities: ~ 420,000 hours (out of 1.0 million total)
  * Medium facilities: ~ 850,000 hours (out of 1.92 million total)
  * Large facilities: ~ 350,000 hours (out of 0.86 million total)
  * Very Large facilities: ~ 100,000 hours (out of 0.20 million total)
* These CNA hours spike further on weekends, where nursing roles (including CNAs) generally see a ~ 20 percent increase in contract usage

Small Facilities Accumulate Big CNA Hours:
* Despite their smaller size, Small facilities use over 1 million total contract hours (very close to the 0.86 million for Large facilities)
* Within those small‐facility hours, CNA contract hours exceed 400,000—comparable to (or even outpacing) the CNA total in larger facilities

## 4.5 Confusing contradiction?

How is it possible that CNA accounts for so many hours with such a small percentage of high contract days?

Well that is explained in the way high contract days were calculated in the beginning of this analysis. A high contract days represents when ANY of the categories has over 99% contract usage... This is to emphasize the days the facilities might be short staffed or to detect particular staffing practices. Regardless, this doesn't disprove the enormous need for temporary CNA's across the board. They are needed on Tuesdays, Sundays, small and large. Even though the very large facilities don't amount any temporary CNA hours on high contract days, that does not mean that further analysis won't uncover that any given day they do require plenty.

![Percentage of Total Hours](plots/percentage-total-hour.png)

# 5. Conclusions and Recommendations

## 5.1 Conclusions

The data demonstrates that no matter how you look at it, there is a substantial system-wide reliance on temporary staff, over 4 million hours; and these are high contract days only! Sheer numbers allows medium-sized facilities to dominate these particular needs, but the sizable chunk that small facilities are able to represent is not to be ignored. This is especially true when we take a look at their CNA needs. Although most facilities require temporary CNA's the most, these small facilities definitely rack up quite a bill for their size. These facilities seem to have a significant resource gap, particularly on the weekends, waiting to be filled.

## 5.2 Recommendations

### 5.2.1 Recommendation #1

A weekend focused solution: Weekends are a particular pain point for all facilities in all shapes and sizes. Position the platform to be readily available to fill in those unexpected (expected) gaps that arise in this fluctuating pattern. Forecasting into absenteeism will play a particularly useful role in predicting and nailing those complicated shortages. Offering stability might relieve some of the pressure.

### 5.2.2 Recommendation #2

Give the little guy a hand: Smaller facilities rely heavily on temporary staffing and offering a piece of with a stable supply mind might be just what they need. Small facilities also tend to be owned by individual entities and not as many organizations as the other sizes. Tailored and personalized messaging might go a long way. It might require more effort to target an individual facility but given the proportion in which they use temporary staffing, this approach might be more fruitful than a wide net.

### 5.2.3 Recommendation #3

Two birds one stone: Bottom line, facilities need CNA's more than anything. These are a type of staffing that Clipboard assists with (first one on the list in the website too). Addressing this need by onboarding more CNA's with the data backing up that they will very likely get shifts, allows the Clipboard to up on usage on both sides of the platform.
