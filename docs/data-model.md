## Data Model

Partition key generically named 'pk' and sort key generically named 'sk'. The access patterns are -

- Get list of suburbs to display on home page by pk=state
- Get suburb by pk=suburbName and sk=state
- Get hospital by pk=hospitalsId and sk=state
- Get universities by pk=universitiesId and sk=state
- Get demographics by pk=demographicsId and sk=state
- Get other info by pk=otherInfoId and sk=state
- Get user shortlisted suburbs by pk=customerId
- Add suburb to user's shortlist

Since state is being used both as pk and sk, we require a reverse lookup GSI (Global Secondary Index) where sk=state becomes the pk.

There will be a score added to each suburb based on demographics, universities and other info. That becomes that second sort key and requires the creation of a local secondary index based on score attribute.

The files in the stubs folder show the various values used for pk depending on type of data being used.
