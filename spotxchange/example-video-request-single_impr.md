# Video Request for a Single Impression with a Private Deal

The following example illustrates a bid request for a video impression
with two companion ad slots (1 expandable). Additionally, the video
content itself is described in the "content" object.

*A few notes about specific fields in the example:*

- `protocol`: Only VAST 2.0 and 3.0 are allowed. Note that a wrapper response is not allowed in this example.
- `sequence`: it is not explicitly included so the default of '1' should be assumed.
- `battr`: User interactive and alert type ads (value '13' and '14', respectively) are explicitly being blocked for both the video and its companions.
- `pos`: Indicates this opportunity is "above the fold".
- `api`: Indicates that VPAID 1.0 containers are explicitly supported. As such, the mime types supported for VPAID are only `application/x-shockwave-flash` and `application/javascript`. Note that there is an implicit resitrction as to which protocol is allowed in which mimetype. JavaScript support was not specificed until VPAID 2.0, while Flash supports both VPAID 1.0 and 2.0.
- `companiontype`: Indicates only static or HTML resources are allowed.
- `pmp`: This is a private auction and restricted to only the deals enumerated.
- `ext`: an exchange-specific deals extension is passed to inform the bidder of the priority assigned deals.

```json
{
  "id": "1234567893",
  "at": 2,
  "tmax": 120,
  "imp": [
    {
      "id": "1",
      "bidfloor": 0.03,
      "pmp": {
        "private_auction":1,
        "deals": [
          {
            "id":"1452f.eadb4.7aaa",
            "bidfloor":2.5,
            "at":1,
            "wseats":[],
            "ext": {
              "priority":1,
              "wadvs":[]
            }
          }
        ]
      },

      "video": {
        "mimes": [
          "video/x-flv",
          "video/mp4",
          "application/x-shockwave-flash",
          "application/javascript"
        ],

        "battr":           [13,14],
        "boxingallowed":   true,
        "delivery":        [2],
        "h":               480,
        "linearity":       1,
        "maxbitrate":      1500,
        "maxduration":     30,
        "maxextended":     30,
        "minbitrate":      300,
        "minduration":     5,
        "playbackmethod":  [1,3],
        "pos":             1,
        "protocol":        [2,3],
        "startdelay":      0,
        "w":               640,

        "companionad": [
          {
            "id": "1234567893-1",
            "w": 300,
            "h": 250,
            "pos": 1,
            "battr": [13,14],
            "expandable": [2,4]
          },
          {
            "id": "1234567893-2",
            "w": 728,
            "h": 90,
            "pos": 1,
            "battr": [13,14]
          }
        ],
        "companiontype": [1,2],
        "api": [1,2]
      }
    }
  ],
  "site": {
    "id": "1345135123",   	
    "name": "Site ABCD", 	
    "domain": "siteabcd.com",
    "cat": [
      "IAB2-1",
      "IAB2-2"
    ],
    "page": "http://siteabcd.com/page.htm",
    "ref": "http://referringsite.com/referringpage.htm",
    "privacypolicy": true,
    "publisher": {
      "id": "pub12345",
      "name": "Publisher A"
    },
    "content": {

      "cat":      ["IAB2-2"],
      "episode":  23,
      "id":       "1234567",
      "keyword":  ["keyword a", "keyword b", "keyword c"],
      "season":   2,
      "series":   "All About Cars",
      "title":    "Car Show"

    }
  },
  "device": {
    "ip": "64.124.253.1",
    "ua": "Mozilla/5.0 (Mac; U; Intel Mac OS X 10.6; en-US; rv:1.9.2.16) Gecko/20140420 Firefox/3.6.16",             	
    "os": "OS X",
    "flashversion": "10.1",
    "js": 1
  },
  "user": {
    "uid": "456789876567897654678987656789",                   	
    "buyeruid": "545678765467876567898765678987654",
    "data": [
      {
        "id": "6",
        "name": "Data Provider 1",
        "segment": [
          {
            "id": "12341318394918",
            "name": "auto intenders"
          },
          {
            "id": "1234131839491234",
            "name": "auto enthusiasts"		
          }
        ]
      }
    ]
  }
}
```
