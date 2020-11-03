---
title: 'Makeover Monday week 43'
subtitle: 'Apparel exports to the US plummeting due to Covid-19'
date: 2020-10-25 00:00:00
description: Starting with a MakeOverMonday project to improve my Tableau and analytic skills.
featured_image: '/images/MakeOverMondayWk43.png'
---

![](/images/MakeOverMondayWk43.png)

MakeOverMonday Week 43

After finishing my Tableau Desktop Specialist exam, it is time to practice my skills. <a href="https://data.world/makeovermonday/2020w44">Makeover Monday</a> has weekly datasets and visualizations to improve. Watching the visualizations of other participants in how they interpretet the assigment and data is inspiring and helps with giving ideas how to approach data and how to make your analysis visible. 

Here you can find the original dataset and visualization: <a href="https://data.world/makeovermonday/2020w43-apparel-exports-to-us">data.world</a>
and a link to my visualization: <a href="https://public.tableau.com/profile/ronald.bodderij#!/vizhome/MakeOverMondayWk43Year2020/MakeOverMondayWk43">Tableau Public</a>

What I've noticed first was that month and year were in two seperate columns and could not be used as a datefield. After some googling I decided to go with a new calculated field MonthYear (DATE(DATEPARSE ( "MMMM.yyyy", [Month]+ "." +STR([Year]) ))). 

After trying out different visualizations i noticed that showing the exports for each years was not giving enough information. To visualize the change i needed to be able to show the difference between the months of each year. But to be able to make a year-over-year comparison I needed to do some more research on how to do that. I came up with the following calculated fields:

- 2019 ((IF [Year] = 2019 THEN [Exports (USD Millions)] ELSE NULL END)*1000000)
- 2020 ((IF [Year] = 2020 THEN [Exports (USD Millions)] ELSE NULL END)*1000000)
- Difference (SUM([2020])-SUM([2019]))

The times million at the end was to make it possible to show the amount with M for million in the visualization. 

Now I was able to show the comparison and the difference between the two years. I chose the Bart Chart, so I could really show the difference for each Country and period. 
