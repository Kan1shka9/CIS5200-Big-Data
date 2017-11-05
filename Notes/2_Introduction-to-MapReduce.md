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

###### MapReduces Flow

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

![mr](images/2/9.png)

![mr](images/2/10.png)

- ``Upper Case Mapper``

![mr](images/2/11.png)

- ``Explode Mapper``

![mr](images/2/12.png)

- ``Filter Mapper``

![mr](images/2/13.png)

- ``Changing keyspaces``

![mr](images/2/14.png)

- ``Identity Mapper``

![mr](images/2/15.png)

###### Reducers

- ``Shuffle & Sort``

![mr](images/2/16.png)

- ``Reducer``

![mr](images/2/17.png)

- ``Reducer - Sum Reducer``

![mr](images/2/18.png)

- ``Reducer - Average Reducer`` 

![mr](images/2/19.png)

- ``Reducer - Identity Reducer``

![mr](images/2/20.png)

###### Mapper and Reducer

- Mapper
	- Maps input data to intermediate key/value pairs
	- Parse, Filter, Transform
- Reducer
	- Processes Mapped output into final key/value pairs
	- Aggregates data into key/value pairs
             