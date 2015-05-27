Content Enrichment

Content Enrichment provides functions to create, distribute and play interactive video content across platforms and devices by making objects in the video clickable for their viewers. It also provides interfaces to incorporate Web 2.0 capabilities and community functionalities. Thus, the enabler acts as a common building block in future video and multimedia infrastructures. It allows seamless, platform-independent and convenient enrichment of any type of video content using any type of device for a plurality of application cases.

Content Enrichment SE API Specification
In general there are always the same types of functions available:

SAVE, ADD, UPDATE, DELETE, GET and GET-LIST

SAVE is a shortcut for Update OR Add and uses the presence of numeric “ID” fields to determine the appropriate action. it is currently only used for “Config”
ADD and UPDATE take the current object via $data in JSON format. UPDATE requires an ID for the top object but not for lower level objects (if $recursive is used)
GET returns the requested object
GET-LIST returns a list of objects for the given parent object
$data consists of the adressed object in JSON form
only ONE object is contained in $data but it can contain multiple objects of sub-categories (e.g. addAppearance can have 1 or more KeyFrames attached if $recursive=true is used)
$Param is special for Config but is essentially equal to $ID elsewhere because each parameter can only be there once per video
Function list

saveAppearance ( $data, [$recursive = false] )
addAppearance ( $data, [$recursive = false] )
updateAppearance ( $data, [$recursive = false] )
deleteAppearance ( $ID )
getAppearance ( $ID )
getAppearanceList ( $Object_ID )

saveConfig ( $data )
deleteConfig ( $Param, $Video_ID )
getConfig ( $Param, $Video_ID )
getConfigList ( $Video_ID )

saveObject ( $data, [$recursive = false] )
addObject ( $data, [$recursive = false] )
updateObject ( $data, [$recursive = false] )
updateDoLink ( $ID, $DirectOpen )		// special: updates "direct open link", now known as "quick link". requires the TYPE of the link or an empty string to reset it
deleteObject ( $ID )
getObject ( $ID )
getObjectList ( $Video_ID )

saveLink ( $data )
addLink ( $data )
updateLink ( $data )
deleteLink ( $ID )
getLink ( $ID )
getLinkList ( $Object_ID )

copyVideo ( $ID, [$API_to = false] )		// special: allows to copy a video from one api to the next. current api is assumed as target if no second parameter is provided
copyVideoUID ( $UID, [$API_to = false] )	// special: same as copyVideo() but with UID instead of ID

saveVideo ( $data, [$recursive = false] )
addVideo ( $data, [$recursive = false] )
updatePublic ( $ID, $Public )			// special: requires the Video-ID and the Public-state (0/1)
updateVideo ( $data, [$recursive = false] )
deleteVideo ( $ID )
getVideo ( $ID, $recursive )
getVideoByUID ( $UID, [$recursive = true] )	// special: same as getVideo but for UIDs
getVideoList ( [$recursive = false] )
getVideos ( [$extended = false] )		// special: only returns UID, Name and Public (and ID and Duration in extended mode)

savePoint ( $data )
addPoints ( $ID, $dataArr )			// special: used to add a point to all keyframes of the current appearace at once, reducing round-trips. 
						// $ID is the array-index of the point, $dataArr is and ARRAY of {"Shape_ID":keyFrame.ID, "X":keyFrame.points[$ID]["X"], "Y":keyFrame.points[$ID]["Y"]} 
						// --> client must find all keyframes for the current appearance or this will cause errors!
updatePoint ( $data )
deletePoints ( $ID, $KeyFrame_IDs )		// special: deletes a point with given ID from all provided keyframes at once
						// --> client must find all keyframes for the current appearance or this will cause errors!
getPoint ( $ID, $KeyFrame_ID )
getPointList ( $KeyFrame_ID )

saveKeyframe ( $data, [$recursive = false] )
addKeyframe ( $data, [$recursive = false] )
updateKeyframe ( $data, [$recursive = false] )
deleteKeyframe ( $ID )
getKeyframe ( $ID )
getKeyframeList ( $Appearance_ID )
General video description

{
   ID: "1234",
   URI: "http://yourdomain.com/content.mp4",
   W: "1280",
   H: "720",
   Duration: "254360",
   Name: "myVideo",
}
Representation of an object point

{
   ID: "0",
   X: "0.26634614944458",
   Y: "0.360165852720845",
}
Representation of an object time stamp

{
   ID: "3553",
   Hash: "6c068bf8a7c9e963995802584b4d4fec7eb7104778c0e",
   URI: "http://yourdomain.com/content.mp4",
   Type: "hd",
   Video_ID: "1234"
}
Representation of content related to objects

{
   ID: "7644",
   Name: "myName",
   Description: "myDescription",
   Tags: "",
   IconUri: "",
   WidgetName: "",
}


Licence summary

Content Enrichment is based on Fraunhofer FOKUS background technology to support non-linear-video (NLV). All project partners can use it during the term of the FI-PPP projects for testing and experimentation. For any other use (e.g. commercial use) please contact us.

Licence type

Open source: No
Proprietary: Yes
Evaluation licence: No
Licence features

Commercial use: Yes
Modifications allowed: Yes
Distribution allowed: Yes
Include copyright: Required
Include original: Not required
State changes: Not required
Disclose source code: Not required
Licence fee

Content Enrichment technology is commercially available via Fraunhofer FOKUS spinoff company BitTubes GmbH. If you are interested in licensing NLV please contact hello@bittubes.com. Prices are:: Starter package includes a) <500.000 player requests b) 1TB storage c) 10TB traffic – 5.000€ per month flat fee, Each additional 1GB storage – 1€ , Each additional 1GB traffic – 0,25€

Copyright statement

Copyright (c) 2013 Fraunhofer Institute for Open Communication Systems FOKUS.

Full licence

Full licence may be provided on request and needs to be negotiated on a case-by-case basis.

Contact person(s)

For licensing information:

Robert Seeliger
Fraunhofer-Institute for Open Communication Systems FOKUS
robert.seeliger@fokus.fraunhofer.de


©Fraunhofer FOKUS