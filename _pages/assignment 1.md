---
title: "Assignment 1"
permalink: /assignment1/
author_profile: false
layout: single
classes: wide centered
---
## Preface

I worked on this alongside [Marcos Hernández](mailto:mdh8552@nyu.edu) but are writing these essays individually. We both used LLM's, Copilot and Claude, to aid with writing code but not for interpreting the data.

## Introduction

From the beginning Marcos and I knew we wanted to analyze specific time periods of the corpus and compare it to other time periods. We were both interested in war so we thought let's compare the books published in each time period of war to books in other periods and books that were published outside of war. What differences or similarities might we see? We would later simplify our analysis but this was our initial interest.

| Country        | Author count | Share (%) |
|:---------------|-------------:|----------:|
| United States  |           75 |      94.9 |
| United Kingdom |            2 |       2.5 |
| Canada         |            1 |       1.3 |
| Montserrat     |            1 |       1.3 |

*Figure 1*

- Cory Doctorow from Canada
- M. P. Shiel (Matthew Phipps Shiell) was from Montserrat
- Mary Wollstonecraft Shelley from the United Kingdom
- H. G. Wells from the United Kingdom

We looked at where the authors were from and found that an overwhelming majority were from the United States of America (94.9%) with a few exceptions (see bullet points). Seeing this we decided to focus on wars that we hypothesized would be impactful on the culture of the United States.

The publication dates of the books in the corpus ranged from 1817 to 2009. We generated a table using Claude of significant wars of that time period and then filtered it to wars relevant to the United States:

1. American Civil War (1861-1865)
2. WW1 (1914-1918, when the US entered)
3. WW2 (1939-1945)
4. Korean War (1950-1953)
5. Vietnam War (1965-1973)
6. Iraq War (2003-2011)

Due to the scope of this assignment we simplified; we focused primarily on books published during WW2 and compared it to the rest of the corpus.

We hypothesized that the books published in the WW2 era would have the war tag more often and there would be more key words related to war or violence compared to books published before or after.

## Method

### Frequent Words

![Top 15 most frequent words before, during and after WW2]({{ site.baseurl }}/assets/assignment1/frequent_words_top15.png)

*Figure 2*

We started by looking at the top 15 most frequent words per 1000 words (excluding stop words) before, during and after. We did this mostly as an experiment but knowing we wouldn't use this as our main point of analysis. In the graph we can see that across all three periods the most frequent word is *time* interestingly. Other than time we can see a lot more overlap such as life, light, eyes. With frequent words it is expected that there will be more overlap since frequent words are often those which come up in regular prose rather than being unique to a text. Instead, it would be more useful to compare words that are unique to a text, i.e. distinctive words.

### TF-IDF

![Top 15 distinctive words before, during and after WW2]({{ site.baseurl }}/assets/assignment1/distinctive_words_top15.png)

*Figure 3*

TF-IDF stands for Term Frequency-Inverse Document Frequency. In laymen terms it's the most distinctive words across a corpus. In this graph we have the three periods like last time but instead we're looking at the distinctive words. This time there is almost no overlap but the issue is that many of the words are the names of characters: Malone, Tarzan, Haynes, Vince, Ron, Kenneth. Names are not enough to know if the topics between the periods are similar or different.

We could go one by one and remove each name but we decided it would be easier and more effective to increase the list from 15 to 50. It is not as easy to read as the previous one but when zooming in we began to see a theme.

![Top 50 distinctive words before, during and after WW2]({{ site.baseurl }}/assets/assignment1/distinctive_words_top50.png)

*Figure 4*

We found that the theme of space was becoming more frequent where before WW2 it wasn't. Before the WW2 words such as germany, russia, russian, italian, austria, france are mentioned whereas during and after WW2 the books in the corpus almost none of the distinct words were countries or nationalities. Instead terms that refer to people from planets such as earthling, plutonian, mercurians, callistans, venusians, became far more prevalent during the WW2 era. After WW2 the word aliens became a distinct word. However, the number of distinct character names in the corpus after WW2 appeared to have increased because there are far more books in the corpus after the WW2 period as shown:

| Period                  |   n |
|:------------------------|----:|
| Before WW2 (<1939)      | 246 |
| During WW2 (1939–1945)  | 113 |
| After WW2 (>1945)       | 638 |

*Figure 5*

As for overlap there isn't much overlap between before WW2 and during WW2, but after WW2 one interesting overlap was the word spaceport. The word radar is distinct to the period after WW2. Despite radar being invented in 1886 (National Weather Service) it was because of the second world war and only afterwards did the word begin to enter the mainstream presumably because it was no longer classified information as it was during WW2 and began to see use in civilian aircraft immediately after WW2 in 1946 (Federal Aviation Administration).

Regardless we began to see that space became a more prevalent topic seemingly more than war or violence. But we wanted to investigate this further by using the tags since it does include space travel as one of the tags.

### Tags

![Tag comparison before, during and after WW2]({{ site.baseurl }}/assets/assignment1/tag_comparison_before_during_after_ww2.png)

*Figure 6*

Looking at the graph space travel was by far the most frequent tag when looking at the three periods. 81.4% of the texts during the WW2 period were tagged as being space_travel related compared to 23.6% before, and 59.4% afterwards. Interestingly, war and action was slightly more frequent. For war before WW2 47.2% were tagged as being war related, 53.1% during WW2, and 29.2% after WW2. For action it was 78% before WW2, 94.7% during WW2, and 84.6% after WW2.

Across all the tags I would claim that space travel is the only significant difference. This is however anecdotal as I have not done a t-test or statistical analysis to determine whether it is a significant difference.

### Average Book lengths and number of books

Seeing the number of books from before and also wondering how much of an impact it might have made on our TF-IDF results we wondered if the book lengths may be relevant. We could only assume what the average book length would be. In the top 50 distinctive words there are a lot more character names which led us to believe that there would be a lot more books or if there was less or the same amount of books then the average length would be shorter. We looked at the length of each book, and the number of books for before, during and after WW2.

In each of the following scatter plots next to most points is the title of the book and in square brackets the most distinctive word of that book.

![Length of each book before WW2]({{ site.baseurl }}/assets/assignment1/book_length_scatter_before_ww2.png)

*Figure 7*

![Length of each book during WW2]({{ site.baseurl }}/assets/assignment1/book_length_scatter_during_ww2.png)

*Figure 8*

![Length of each book after WW2]({{ site.baseurl }}/assets/assignment1/book_length_scatter_after_ww2.png)

*Figure 9*

| Period                 | Books | Average words | Median words | Shortest | Longest |
|:-----------------------|------:|--------------:|-------------:|---------:|--------:|
| Before WW2 (<1939)     |   246 |         61153 |        61604 |      119 |  468922 |
| During WW2 (1939–1945) |   113 |         14529 |         9730 |      954 |   98797 |
| After WW2 (>1945)      |   638 |         15640 |         7206 |      321 |  181784 |

*Figure 10*

What immediately stood out was the book "The Outline of History: Being a Plain History of Life and Mankind" written in 1920 by Wells H.G. It is the longest book in the entire corpus being 468,922 words long. Secondly, the average words for the books During and After WW2 were fairly similar. With the average words being effectively equal for the books during and after WW2 it explains why there are many more character names in the distinct words list.

From the scatter plots you can also see which books contributed which distinctive word in the top 50 list. For example "The War That Will End War" written in 1914 at the start of WW1 again written by Wells H.G, the most distinctive word was Germany. This makes me wonder whether our hypothesis would have been correct if we had chosen the WW1 period.

## Summary

Marcos and I were interested in exploring the theme of war in the corpus. We chose to look at books published during the WW2 period and compared it to the rest of the corpus; before, and after. We looked at the top 15 most frequent words, but switched to distinctive words. Distinctive words are a more effective tool at comparing the periods since it excludes words that are used regularly in common prose. When looking at the top 50 distinctive words the theme of space became more apparent rather than war. Upon further investigation the space travel tag was the highest for the books published during WW2 at 81.4% with the closest being 59.4% for the period after WW2. We then looked at average word lengths for each period to see whether it had influenced the words that appeared in the top 50 distinctive words since a majority were character names. Unsurprisingly most of the books in the corpus were published after WW2 (638 books) and the average length was similar to during WW2.

## Conclusion

Rather than themes of war and violence, the books published during WW2 were predominately space themed. Moreover, the theme of space continued in the books written after WW2. There is still room for improvement: We didn't investigate whether the difference in tags was statistically significant, how much of a difference excluding the book "The Outline of History: Being a Plain History of Life and Mankind" would have made on the average length, and what we would have seen if we had excluded character names from the distinctive words list.

## References

Federal Aviation Administration. "From Civil Aeronautics Authority (CAA) to FAA \| Federal Aviation Administration." *Faa.Gov*, 2022, [www.faa.gov/about/history/photo_album/caa_to_faa](https://www.faa.gov/about/history/photo_album/caa_to_faa). Accessed 11 Oct. 2026.

National Weather Service. "History of RADAR." *Weather.Gov*, 2019, [training.weather.gov/nwstc/NEXRAD/RADAR/Section1-1.html](https://training.weather.gov/nwstc/NEXRAD/RADAR/Section1-1.html). Accessed 11 Oct. 2026.
