> Author : Mohammed Nauman Siddique
> Course : CS 725/825
> Fall 2017

# Clean Up Country Names

> I created a text facet to see the all the data in the Country Names column.
> Steps to Create a Text Facet:
> Select Country column -> Facet->Text Facet

## Variations found in Country Names:

* Two records contains a comma (,) instead of a real country name.
* Canada has three variations with one containing the country name, second variation has address appended to it and the last variation has address and phone number appended to it.
* Two records contain Cura%C3%A7ao.
* England and Scotland both have three variations, one has only the country name, second variation has UK appended to it and the last variation has United Kingdom appended to it.
* One row contains names of places in USA rather than the country name itself.
* In my opinion Russia also has three variations with one being Rossija in country name, second is the country name and the last has Russian Federation.
* One row contains Satellite Locations instead of a country name.
* The Netherlands is not exactly naming a country name, as it should have been Netherland.
* Two other variations contain UK and United Kingdom.
* Two records display their name as Utopia.

# Exploring Data with Scatter Plot

![alt text](get-scatterplot.png)

# Is the 27 Club Real?

> Out of approximately 12,000 records about 350 records show that the musicians died around the age of 27 (considering 26 and 28). 
  This shows that the ratio for the number of musicians died around 27 to all the records present in dataset is too small and 
  hence,the initial hypothesis about 27 club does not seem real to me.
  
* Initially we have to create a single cell from multiple birthdate and deathdate columns.

```
forNonBlank(cells.birthdate1.value, v1, v1, forNonBlank(cells.birthdate2.value, v2, v2, forNonBlank(cells.birthdate3.value, v3, v3, null)))
forNonBlank(cells.deathdate1.value, v1, v1, forNonBlank(cells.deathdate2.value, v2, v2, forNonBlank(cells.deathdate3.value, v3, v3, null)))
```

* This command copies the values of each column into the other, thus creating three duplicate rows for birthdate as well as for beathdate.
* Delete all the duplicate birthdate and deathdate columns and rename the final birthdate column and deathdate column.
* Get the years for both the columns birthdate as well as deathdate by below command:

```
value.match(/.*(\d{4}).*/)[0]
```

* Remove all the empty deathdate records by creating a numeric facet and deleting those records.
* For convenience convert the values of deathdate and birthdate into numbers.
* Create a new column Death Age with the command below:

```
cells.deathdate.value - cells.birthdate.value
```
