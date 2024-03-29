## Georgia Gaming Compliance Reports 
Based on the amendments to the Law of Georgia “On Organising Lotteries, Games of Chance and Other Prize Games” certain obligations have been identified for the purpose of control of the gambling industry. The Law identifies the right and framework of implementation and operation of Unified Control System by the Selected Person.

The Selected Person is Random Systems Georgia, a company incorporated according to the laws of Georgia, with ID code: 405323948).

As part of the monitoring and reporting requirments, a set of XML-based reports are required to be submitted on a periodic basis by approved operators and game service providers.

**The latest schema is: Version 4.0.0 (28/03/2021) Official Release [See below]**

**SWITCH TO Ver-4.0 BRANCH FOR VERSION 4.0** 

### Uploading Reports
Reports must be uploaded daily before 8am (local time) to earp.rsi.ge. You need a username and password to be bale to upload reports. These are issued by RSG administrator on request. Only one account per licensee is allowed.

### Format of the Schema
The schema is loosely based on the upcoming European standard for monitoring of online gaming. It uses different levels of schema that differentiates between data types. Each level inherets from the previous level, where level 0 is the most fundamental level.

- Level 0  To represent fundamental simple types such as email, time stamp, URL, currency, etc. These are defined by global standards and are unlikely ever to change.
- Level 1  To represent complex types made of Level 0 simple types such as Address, personal details, personal identification, etc. 
- Level 2  To represent Complex types that pertain to the Georgian reporting mecahnism such as Header.
- Level 3  Complete reports such as the Gross Gaming Revenue Summary Report. 

### Naming Convention of data types (simple and complex)
We try to keep to a convention when naming data types to aid developers in what we are expecting. The following are general helpful hints:

- **Ttl** means **Total** - We are expecting a value that is a summation of detailed records (SQL statement: SELECT SUM(column_name)... )
- **Amt** means **Amount** - We expect a decimal number that represent a financial amount (in GEL)
- **Nmbr** means **Number** - We expect a positive integer
- **Smry** means **Summary** - Means that this data object represent summaries ie its content is always in SUMS and COUNTS.
- **Dtld** means **Detailed** - Means that this data object represents detailed information. We are expecting transaction level information.

The combination of the above also holds:

-**TtlNmbr** means **Total Number** - We expect a count  (SQL statement: SELECT Count(column_name)... )

### Gross Gaming Revenue Report
The first report is a statutory report that needs to be submitted by B2C operators on a **daily basis**. It includes totals across each game vertical. Full documentation can be found [here](https://www.rsi.ge/schema/2_0/GGRSmry/B2CSmryCompliance.html)

### Version 2.0.0 (12/02/2021)
After our meetings with authorities this week on the reporting requirements, we realized that more data is required for sport betting. Rather than mofifying the orginal schema, we added a new one to deal only with betting submissions. This means that Version 1.3 has been superceeded by Version 2.0 which is now available as an RFC (Request for Comments) until it becomes official on (20/02/2021).

The new schema is [BettingSmryCompliance.xsd](https://github.com/RS-Georgia/schema/blob/main/2_0/GGRSmry/BettingSmryCompliance.html)

With this version there also structural changes:
1. The Schema naming convention will be in full i.e ...Compliance.xsd, etc. The use of short names (like ...comp.xsd) is depracted. 
2. The file naming convention of an XML report shall start with the **license number issued by RS related to the specific gaming activity**. Operators normally have two licenses issued by RS - one for betting and another for other games. Use the license number for betting on BettingSmryCompliance.xsd  and the other license number for B2CSmryCompliance.xsd

### Clarifications on the BettingSmryCompliance Schema
We have recieved a number of queires surrounding the betting schema. The following explanation might help clarify the terms used in the rpeort:

#### Sales Channels
There are predominantly two sales channels in Georgia
1. Online, and
2. Lanbased

Operators must distinguish between these two sales channels when reporting betting summaries.

#### Meaning of Terms
- **Total Stake Amount** - total amount of **new** bets (new stakes) in the reported period (24-hours)
- **Total PayOut Amount** - total amount of wins paid out on settled bets to players in the reported period. 
- **Total Voided Amount** - total amount of stakes voided due to cancelled events or market suspension,etc.  in the reported period. 
- **Total Stake Pending Amount** - total amount held in **all** open bets to-date.
- **Total Number of BetSlips Sold** - total number of betslips sold during the reported period. This includes also any betslips opened that were closed during the same reported period (for example live betting).
- **Total Number of BetSlips Settled** - total number of settled betslips during the reported period
- **Total Number of BetSlips Voided**  - total number of betslips rejected due to cancelled events or market suspension,etc
- **Total Number of Bets Placed** - total number of new bets (that is, the bets in the betslips above)
- **Total Number of P2P Bets Placed** – (*Only for operators who offer such games*) total number of bets placed on P2P (betting exchange)
- **Total P2P Stake Amount** – Total Amount of bets taken on Betting Exchanges during the reported period
- **Total Number of Virtual Bets** - Total Number of bets taken on Virtual Games (i.e games that are not in real life)
- **Total Virtual Bets Amount** - Total Amount of bets taken on Virtual Games during the reported period

### Version 3.0.0 (17/02/2021) Release Candidate
This version launches the reporting schema for B2B operators. It does not affect B2C operators and as such Version 2 and Version 3 are interchangeable for B2C operators. This version necesstated renaming some elements in Level 2 Schema so that it accomodates for the new B2B requirements.

There is detailed dcoumentation under the the same folder as the schema. Note that as a Release Candidate the new Schema is still as a branch on this repo. Make sure that you switch from the main barcnh to Version 3.

### Version 3.1.0 (28/03/2021) Official Release
Version 3.1 is the Official Release and all operators are expected to load their files from March 1st using this version. There is only ONE change from 3.0 but is significant as to the functionaity of the reporting platfrom:

The `Document Header` element now includes a mandatory element `VrsNb` which is of datatype `counter`. The `VrsNb` element holds the report version number and **must** be the same as the version number in the filename. Reports must always start with report version 1 (01 or V01). Every time a report for the same day needs to be re-uploaded for some reason, the version number must be incremented by 1.

Our API allows quering the Document Headers of uploaded reports that have been already accepted by the system. Therefore the client side can be designed as stateless. 

### Version 3.1.1 (29/03/2021)
Corrected an error in `TtlNmbrVirtualBets` element spelling in B2BTp2Compliance Schema.
We have added more Vertical Gaming Types to include the following:

			<xs:enumeration value="Casino"/>
			<xs:enumeration value="Sportsbetting"/>
			<xs:enumeration value="Poker"/>
			<xs:enumeration value="Live Gaming"/>
			<xs:enumeration value="Tournament"/>
			<xs:enumeration value="P2P Games"/>
			<xs:enumeration value="Other"/>

These enumarations do not affect technically the schema but they affect the operators finacially as certain games GGR is based on commission not Coin In - Coin Out so the wokings for the fees will be wrong. Update B2CTp2Compliance report accordingly. 

- `Use `Tournament` for all games that are held in Tournaments inlcuding poker, slots tournaments and black jack tournaments.

- Use `Pools` for parimutuel games normally in horseracing events.

- Use `P2P Games` for games such as dominoes, backgammon, rummy, etc.

We have also discovered an error in the Sales Channel Types in the B2CTp2Compliance Report. Please update this field to  `online` and not `sportsbetting`.

