# Parsing Configurations Files in Python
Configuration files, you either love them or love to hate them. When it comes to configuration files,
Python hasn't been the easiest to work with. Yes, we can parse the file `yaml`, `json`, or `pyhocon`
but parsing these types of files can be choir and extremely verbose if you want to build in type
safety. However, our friends writing in Scala have been able to use libraries like `pureconfig` and
`hocon` to easily parse their config files into case classes.

# Demo
In this demo, we have two notebooks available. The first notebook `demo_dataconf` shows the parsing of
a `json`, `yaml`, and `hocon` using their respective libraries and `dataconf` with `hocon`. With both
`json` and `yaml`, we get a dictionary returned whereas with `dataconf` we have type safety and a 
nice dataclass object to work. In the second notebook, `demo_data`, we look at slim down, trivial 
data parsing example one might encounter in data analytics. That is, what if I can receive data from 
multiple different sources, how can content for this using a config file? In this case, we just look
at two possible options for parsing with `pandas`; however, this could be expanded to `spark` dataframes
and other source types. Moreover, with the dataconf, we can use method calls in the dataclasses to 
facilate some actions. In this case, I have the method `load_df` which I can call with each implementation
to return the data from the correct source.

# Improvements 
There are a few necessary improvements that should be added but the library is still useable. For one,
`dataconf` cannot parse config files using `-` and needs underscores only. It should be able to handle
this similar to Scala and json and yaml parsers in Python. Next, when replicating the case class 
behavior using `dataclasses`, the naming inside each class should be able to handle some identical names.
See the following issues filed to track the progress or even submit a PR to improve the code. Additionally, 
if the `__parse` method is really parse from `ConfigTree`. That is, updating method names and usage to mimic a 
cleaner convention such as `loads` to `from_string`, `load` to `from_file`, and `__parse` to `from_config`
would be beneficial.

* [Parsing dashes](https://github.com/zifeo/dataconf/issues/20)
* [Identical names in data classes](https://github.com/zifeo/dataconf/issues/19)