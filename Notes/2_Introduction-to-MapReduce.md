#### 2. Introduction to MapReduce

###### Features of MapReduce

- Automatic parallelization and distribution
- Fault-tolerant
- Clear abstraction for programmers
	- Written in JAVA
	- Can be written in other languages using ``Hadoop Streaming``
- MapReduce abstracts all the ``housekeeping`` away from developer
	- Developers can simply concentrate on writing ``Map`` and ``Reduce`` function

![mr](images/2/1.png)

###### Mapreduces Flow

![mr](images/2/2.png)

###### WordCount Example

![mr](images/2/3.png)

- WordCount Mapper

![mr](images/2/4.png)

![mr](images/2/5.png)

- WordCount Shuffle and Sort

![mr](images/2/6.png)

- SumReducer

![mr](images/2/7.png)

![mr](images/2/8.png)

###### Mappers

