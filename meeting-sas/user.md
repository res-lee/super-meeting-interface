# user

{% swagger method="get" path="/{userId}/meetings?start&end" baseUrl="/users" summary="유저 회의 일정 조회 " %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="start" type="String" required="true" %}
yyyy-mm-dd
{% endswagger-parameter %}

{% swagger-parameter in="query" name="end" type="String" required="true" %}
yyyy-mm-dd
{% endswagger-parameter %}

{% swagger-parameter in="path" name="userId" type="String" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="조회 성공" %}
```
{
    meetings: {
        roomId,
        meetingId,
        name,
        host,
        start,
        end,
        repeatRule,
        invitees,
        meetingStatus,
        noteOption,
        recordOption,
        template
    } []
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/{meetingId}/users" baseUrl="/meeetings" summary="미팅 참여자 생성 (입장하기)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" required="true" type="String" %}
wapl id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" required="true" type="String" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="meetingId" required="true" type="String" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    meetingStatus, // 'standby' | 'meeting' | 'app_sharing' | 'screencast'...
    participants: {
        id,
        name
    } [],
    streams: {
        streamId,
        userId
    } []
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="" %}
```javascript
{
    error: "Duplicate user name"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/{meetingId}/users/{userId}" baseUrl="/meeetings" summary="미팅 참여자 삭제 (나가기)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="meetingId" required="true" type="String" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="userId" required="true" type="String" %}

{% endswagger-parameter %}
{% endswagger %}

{% swagger method="patch" path="/{meetingId}/users/{userId}" baseUrl="meetings" summary="참여자 상태 업데이트" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="name" type="String" required="false" %}

{% endswagger-parameter %}

{% swagger-response status="403: Forbidden" description="" %}
```javascript
{
    error: "Duplicate user name"
}
```
{% endswagger-response %}
{% endswagger %}

```javascript
// 다른 참여자 입장 이벤트
userAdded
{
    id,
    name
}

// 다른 참여자 퇴장 이벤트
userLeft
{
    id
}

// 다른 참여자의 name 변경 이벤트
userUpdated
{
    name?
}
```
