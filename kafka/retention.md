Kafka doesn't neccessarily delete messages after retention time passed.
السلام عليكم :wave: 
من كام يوم اكتشفت حاجة غريبة في Kafka وهي ان فيه new Kafka consumer بيجيله old messages عدى عليها ال retention period باسبوع!
استغربت جدا وافتكرت Kafka فيها bug وفضلت ادور ازاي حاجة زي دي حصلت لحد ما لقيت السبب في المقالة دي
https://dalelane.co.uk/blog/?p=3993
The summary is that Kafka stores messages in segments, and it only appends to a segment or deletes it, but doesn't update or delete individual messages in it.

Kafka deletes segments only when every message in the segment has passed the retention period.

So there is a case where a segment may contain old messages that passed the retention period and new messages that didn't pass the retention period yet, and Kafka won't delete the segment because at least one message hasn't passed the retention period.

So, when a new Kafka consumer is up, it will receive all the messages in the segment, including old messages that should have been deleted because they passed the retention period.

This was totally unexpected to me and took me a couple of hours until I stumbled upon the mentioned article, which explained everything in a very simple way.

I hope this new information is useful to you, as I don't think many people who use Kafka know about this (including old me!).
#apachekafka

