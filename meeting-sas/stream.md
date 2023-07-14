---
description: sdk --> signaling server
---

# stream

{% swagger method="post" path="publish" baseUrl="socketIO " summary="stream 송출" expanded="false" fullWidth="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="media" type="MediaOptions" required="true" %}
{type: "audio" | "video",&#x20;

source: "camera" | "mic" | "screen-cast"| ...,

mid: string}\

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="{transportId: string, id: string(SessionId)}" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="unpublish" baseUrl="socketIO " summary="stream 송출 중단" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Session Id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="subscribe" baseUrl="socketIO " summary="stream 구독" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="media" type="MediaSubOptions" required="true" %}
{from: string (track or stream id),

mid: string}
{% endswagger-parameter %}

{% swagger-parameter in="body" name="transportId" type="string" required="false" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="{transportId: string, id: string(SessionId)}" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="unsubscribe" baseUrl="socketIO " summary="stream 구독 중단" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Session Id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="patch" path="stream-control" baseUrl="socketIO " summary="published stream 제어" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Session Id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="operation" type="string" required="true" %}
"play" | "pause" 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="string" required="true" %}
"audio" | "video" | "av"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="stream" baseUrl="socketIO " summary="stream notification" %}
{% swagger-description %}
스트림 추가, 제거, mute
{% endswagger-description %}

{% swagger-parameter in="body" name="status" type="string" required="true" %}
"add" | "update" | "remove"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="id" required="false" type="string" %}
Session Id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="object" required="true" %}
streamInfo | \
\
streamUpdate{\
field: "audio.status" | "video.status" ...

value: "active" | "inactive" ...}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path=" soac" baseUrl="socketIO" summary="session signaling" %}
{% swagger-description %}
SDP exchange, ICE candidates...
{% endswagger-description %}

{% swagger-parameter in="body" name="transportId" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="signaling" type="object" required="true" %}
OfferAnswer{

\


type: "offer" | answer",

\


sdp: string} |

\




\


Candidate{

\


type: "candidate",

\


candidate: string,

\


sdpMid: string,

\


sdpMLineIndex: string}

\




\



{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="progress" baseUrl="socketIO " summary="session progress notification" %}
{% swagger-description %}
SDP exchange, ICE candidate, session status
{% endswagger-description %}

{% swagger-parameter in="body" name="data" type="object" required="true" %}
TrannsportProgress: {

\


id: string(transport id),

\


status: "soac" | "ready" | "error",

\


data: OfferAnswer | Candidate | null} |

\




\


SessionProgress: {

\


id: string(session id),

\


status: "ready" | "error"}

\



{% endswagger-parameter %}
{% endswagger %}
