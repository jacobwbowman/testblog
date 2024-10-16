---
layout: dark
title: About
example: This is an example value.
---

Here's a description of my website using Markdown.

## About

An about page is common within websites and let's visitors know the details of the site.

- The focus of this exact site is solely to give me exposure to Markdown for the purpose of eventually creating a professional website
- My name is Jacob Bowman and I am the person who built this measely communication vehicle
- I am using Jekyll and Markdown through Github to do this, and thus far it is surprisingly easy

I am now using Liquid to code these following parts, such as inserting the title of my webpage, {{ site.title }}, and my name, {{ site.author.name }}. I used the prefix "site." to add these to my webpage, because they are information located in the _config.yml file, while I will use the prefix "page." to add information located in the YAML front matter at the top of this About page file, such as the example I typed, {{ page.example }}. 

Now I'm including a photo on my about page with code from the _includes folder. You should see that below:

{% include bull-trout.html %}

## More playing with Liquid will commence henceforth. Ooooh a for loop through a CSV file. I'll use this to show how much each snack food was consumed.

{% for snack in site.data.animal %}
- The {{ snack.food }} were consumed {{ snack.amount_eaten }} times.
{% endfor %}

## Now an if statement to specifically bold the least enjoyable food on my list of snacks:

{% for snack in site.data.animal %}
{% if snack.amount_eaten == "1" %}
- <strong style="enjoyment: {{ snack.enjoyment }};">{{ snack.food }}</strong>
{% else %}
- <small>{{ snack.food }}</small>
{% endif %}
{% endfor %}

## Toying around again, now with the use of Liquid filters to subset data and reveal the most enjoyable snack.

{% assign enjoyable_foods = site.data.animal | where: "enjoyment", "10" %}
{% for snack in enjoyable_foods %}
- {{ snack.food | upcase }}
{% endfor %}

