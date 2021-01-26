## Georgia Gaming Compliance Reports 
Based on the amendments to the Law of Georgia “On Organising Lotteries, Games of Chance and Other Prize Games” certain obligations have been identified for the purpose of control of the gambling industry. The Law identifies the right and framework of implementation and operation of Unified Control System by the Selected Person.

The Selected Person is Random Systems Georgia, a company incorporated according to the laws of Georgia, with ID code: 405323948).

As part of the monitoring and reporting requirments, a set of XML-based reports are required to be submitted on a periodic basis by approved operators and game service providers.

The latest schema is:  Version 1.2. 

###Format of the Schema
The schema is loosely based on the upcoming European standard for monitoring of online gaming. It uses different levels of schema that differentiates between data types. Each level inherets from the previous level, where level 0 is the most fundamental level.

- Level 0  To represent fundamental simple types such as email, time stamp, URL, currency, etc. These are defined by global standards and are unlikely ever to change.
- Level 1  To represent complex types made of Level 0 simple types such as Address, personal details, personal identification, etc. 
- Level 2  To represent Complex types that pertain to the Georgian reporting mecahnism such as Header.
- Level 3  Complete reports such as the Gross Gaming Revenue Summary Report.


