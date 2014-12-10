SAS to Python guide
===================

`proc freq`
-----------

```SAS
proc freq data=mydata;
    tables myvar / nocol nopercent nocum;
run;
```

```python
mydata.myvar.value_counts().sort_index()
```


#### sort by frequency ####

```SAS
proc freq order=freq data=mydata;
	tables myvar / nocol nopercent nocum;
run;
```

```python
mydata.myvar.value_counts()
```


#### with missing ####

```SAS
proc freq order=freq data=mydata;
    tables myvar / nocol nopercent nocum missing;
run;
```

```python
mydata.myvar.value_counts(dropna=False)
```


`proc means`
------------

```SAS
proc means data=mydata n mean std min max p25 median p75;
    var myvar;
run;
```

```python
mydata.myvar.describe()
```


#### more percentiles ####

```SAS
proc means data=mydata n mean std min max p1 p5 p10 p25 median p75 p90 p95 p99;
	var myvar;
run;
```

```python
mydata.myvar.describe(percentiles=[.01, .05, .1, .25, .5, .75, .9, .95, .99])
```


`data` step
-----------

#### concatenate datasets ####

```SAS
data concatenated;
    set mydata1 mydata2;
run;
```

```python
concatenated = pandas.concat([mydata1, mydata2])
```


`proc contents`
---------------

```SAS
proc contents data=mydata;
run;
```

```python
mydata.info()
```

#### save output ####

```SAS
proc contents noprint data=mydata out=contents;
run;
```

```python
contents = mydata.info()  # check this is right
```


Misc
----

#### number of rows in a datastep ####

```SAS
* haha nice try. Try this for size: http://www2.sas.com/proceedings/sugi26/p095-26.pdf;
```

```python
len(mydata)
```
