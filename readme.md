## Georgia Gaming Compliance Reports 
Based on the amendments to the Law of Georgia “On Organising Lotteries, Games of Chance and Other Prize Games” certain obligations have been identified for the purpose of control of the gambling industry. The Law identifies the right and framework of implementation and operation of Unified Control System by the Selected Person.

The Selected Person is Random Systems Georgia, a company incorporated according to the laws of Georgia, with ID code: 405323948).

As part of the monitoring and reporting requirments, a set of XML-based reports are required to be submitted on a periodic basis by approved operators and game service providers.

**The latest schema is: Version 2_0**

### Format of the Schema
The schema is loosely based on the upcoming European standard for monitoring of online gaming. It uses different levels of schema that differentiates between data types. Each level inherets from the previous level, where level 0 is the most fundamental level.

- Level 0  To represent fundamental simple types such as email, time stamp, URL, currency, etc. These are defined by global standards and are unlikely ever to change.
- Level 1  To represent complex types made of Level 0 simple types such as Address, personal details, personal identification, etc. 
- Level 2  To represent Complex types that pertain to the Georgian reporting mecahnism such as Header.
- Level 3  Complete reports such as the Gross Gaming Revenue Summary Report. 

### Gross Gaming Revenue Report
The first report is a statutory report that needs to be submitted by B2C operators on a **daily basis**. It includes totals across each game vertical. Full documentation can be found [here](https://www.rsi.ge/schema/2_0/GGRSmry)

#### Version 2.0 (12/02/2021)
After our meetings with authorities this week on the reporting requirements, we realized that more data is required for sport betting. Rather than mofifying the orginal schema, we added a new one to deal only with betting submissions. This means that Version 1.3 has been superceeded by Version 2.0 which is now available as an RFC (Request for Comments) until it becomes official on (20/02/2021).

The new schema is [BettingSmryCompliance.xsd](https://github.com/RS-Georgia/schema/blob/main/2_0/GGRSmry/BettingSmryCompliance.html)

With this version there also structural changes:
1. The Schema naming convention will be in full i.e ...Compliance.xsd, etc. The use of short names (like ...comp.xsd) is depracted. 
2. The file naming convention of an XML report shall start with the **license number issued by RS related to the specific gaming activity**. Operators normally have two licenses issued by RS - one for betting and another for other games. Use the license number for betting on BettingSmryCompliance.xsd  and the other license number for B2CSmryCompliance.xsd

