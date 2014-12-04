SAS to Python guide
===================

`proc freq`
-----------

#### basic ####

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


Misc
----

#### number of rows in a datastep ####

```SAS
* haha nice try. Try this for size: http://www2.sas.com/proceedings/sugi26/p095-26.pdf;
```

```python
len(mydata)
```