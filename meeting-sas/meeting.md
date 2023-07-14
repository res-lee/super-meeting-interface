# meeting

{% swagger method="post" path=" " baseUrl="/meetings" summary="회의실 생성" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="roomId" required="true" type="String" %}
와플 룸 ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" required="true" type="String" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="host" required="true" type="String" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="start" required="true" type="String" %}
yyyy-mm-ddThh:mm:ss
{% endswagger-parameter %}

{% swagger-parameter in="body" name="end" required="true" type="String" %}
yyyy-mm-ddThh:mm:ss
{% endswagger-parameter %}

{% swagger-parameter in="body" name="noteOption" type="NoteOption" required="true" %}
회의록 사용여부, 산출물 저장방식
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recordOption" type="RecordOption" required="true" %}
녹화권한
{% endswagger-parameter %}

{% swagger-parameter in="body" name="invitees" type="String []" required="true" %}
초대인 WAPL ID | 이메일
{% endswagger-parameter %}

{% swagger-parameter in="body" name="invitationMessage" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="repeatOption" type="String" %}
매일 | 매주 | 매월 | 매년
{% endswagger-parameter %}

{% swagger-parameter in="body" name="template" type="MeetingTemplate " required="false" %}
2차 반영 

~~UXComponentId, type, layout~~
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="회의실 생성 성공" %}
```
{
  meetingId: "123-456-7890"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/{meetingId}" baseUrl="/meetings" summary="회의실 정보 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="meetingId" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="요청 성공" %}
```
{
    roomId,
    meetingId,
    name,
    host,
    start,
    end,
    repetitionRules,
    invitees,
    meetingStatus,
    noteOption,
    recordOption,
    template,
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="patch" path="/{meetingId}" baseUrl="/meetings" summary="회의실 재설정" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="name" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="noteOption" type="NoteOption" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="recordOption" type="RecordOption" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="meetingId" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="template" type="MeetingTemplate" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/{meetingId}" baseUrl="/meetings" summary="회의실 종료 또는 삭제" %}
{% swagger-description %}
시작 시각 전이면, 초대인들에게 취소 알림 전송
{% endswagger-description %}

{% swagger-response status="200: OK" description="회의실 종료 성공" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/{meetingId}/send-invitation" baseUrl="/meetings" summary="미팅 중, 추가 초대 발송" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="invitees" type="String []" required="true" %}
WAPL userIds
{% endswagger-parameter %}

{% swagger-parameter in="body" name="message" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="patch" path="/{meetingId}/schedule" baseUrl="/meetings" summary="회의실 일정 수정" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="start" type="String" required="true" %}
yyyy-mm-ddThh:mm:ss
{% endswagger-parameter %}

{% swagger-parameter in="path" name="meetingId" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="end" type="String" %}
yyyy-mm-ddThh:mm:ss
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}
