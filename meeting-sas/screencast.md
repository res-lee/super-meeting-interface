# screencast

{% swagger method="post" path="/{meetingId}/screencasts" baseUrl="meeting" summary="화면 공유 시작" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="meetingId" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="streamId" type="String" required="true" %}
공유 할 stream id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/{meetingId}/screencasts/{streamId}" baseUrl="meeting" summary="화면 공유 종료" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="meetingId" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="streamId" type="String" required="true" %}
공유 중인 stream id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

### 이벤트

#### 화면 공유 시작

* event
  * screencast\_started
* data
  * { streamId }

#### 화면 공유 종료

* event
  * screencast\_ended
