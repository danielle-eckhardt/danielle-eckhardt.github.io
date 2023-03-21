## Clothing Store Database & Stats: An analysis using SQL

**Project description:** In this case study, I am hired as a marketing analyst to interpret the research about a company’s consumers and their buying habits.

### Data Set
This data set was analyzed in SQLiteStudio 3.4.3 and came from the [BreakIntoTech Data Analytics Course](https://howtobreakintotech.com/data-analytics-certificate-program/). 

[Database File](https://www.dropbox.com/s/cvsasmtr8syq2c2/BIT_DB?dl=0)

### Analysis

- How many orders were placed in January?

```SQL
SELECT count(*)
FROM bit_db.jansales
WHERE length(orderID) = 6 
AND orderID <> 'Order ID'; 
```
Here, you can see in my code there was a bit of data cleaning that needed to be included to avoid mis-calculated results. There are several entries were the 'orderID' is not a proper 6 digit code and they needed to be filtered out in the calculation.

There are 9681 orders placed in January.

- 

```SQL
if (isAwesome){
  return true
}
```

### Key Takeaways

<img src="images/dummy_thumbnail.jpg?raw=true"/>

### 4. Provide a basis for further data collection through surveys or experiments

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
