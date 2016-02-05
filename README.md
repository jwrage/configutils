**** configutils ****

configutils is a simple set of utilities that enables quick and easy interaction with the RIC One config service. Please note that none of the utilities perform safety or sanity checks at this time; they're basically just a convenient wrapper for CURL and JQ. Use at your own risk!


** ENVIRONMENT AND AUTHENTICATION **

config.txt	Establishes the config environment to connect to, asks for the config user name and password, and obtains an auth token. 


** ONBOARDING PROCESS UTILITIES **

mkvendor	Creates a new vendor based on input parameters. Values with quotes or shell interprettable characters must be double-quoted ("value").

		Syntax: mkvendor <vendor website URL> (string:url) \ 
				 <status> (string) \
				 <vendor name> (string) \
				 <vendor id> (string:unique) \
				 <enabled> (true | false)

mkapp		Creates a new app for a vendor based on input parameters. Values with quotes or shell interprettable characters must be double-quoted ("value").

		Syntax: mkapp <app long description> (string) \
			      <app name> (string) \
			      <profile_id> (profile_id) \
			      <vendor_id> (vendor_id) \
			      <icon URL> (string:url) \
			      <title> (string) \
			      <id> (string:unique)

lnappdist	Links an app to a district.

		Syntax: lnappdist <app_id> <districtid>
 

** GENERIC CONFIG UTILITIES **

getconfig	GETs resources from the config service based on the specified resource/service path.
		
		Syntax: getconfig <resource>

lsapp		Lists all apps or, optionally, districts by app. 

		Syntax: lsapp = lists all apps
			lsapp -district <app_id> = list districts associated with the specific app_id

lsdistrict	Lists all districts or, optionally, apps by district.

		Syntax: lsdistrict = list all districts
			lsdistrict -app <district_id> = lists all apps associated with the specific district

lsprofile	Lists all profiles.

		Syntax: lsprofile

lsprovider	Lists all providers.

		Syntax: lsprovider

lsvendor	Lists all vendors or, optionally, apps by vendor.

		Syntax: lsvendor = list all vendors
			lsvendor -app <vendor_id> = lists all apps by the specified vendor		 

getkv		Returns objects whose keys equal the specified value.

		Syntax: getkv <resource> <key> <value>

getkvc		Returns objects whose key contains the specified value.

		Syntax: getkvc <resource> <key> <value>

postfconfig	POSTs a JSON file to the specified resource (create new)

		Syntax: postfconfig <resource> <file>

putfconfig	PUTs a JSON file to the specific resource (update).

		Syntax: putfconfig <resource> <file>

postconfig	POSTs JSON from an input parameter (create new).

		Syntax: postconfig <resource> <JSON string>

putconfig	PUTs JSON from an input parameter (update existing resource). 

		Syntax: putconfig <resource> <JSON string>

rmconfig	DELETEs a resource from the config service.

		rmconfig <resource/id>

setkv		Sets and updates the value of a field in a resource instance.
		Booleans are a known special case; other undiscovered special cases may exist.

		Syntax: setkv <resource> <key> <value>

