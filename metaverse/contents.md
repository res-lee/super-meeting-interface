# contents

{% swagger method="get" path=" " baseUrl="/templates" summary="메타버스 미팅 템플릿 조회 (static, dynamic 모두)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```json
{
    templates: {
        UXComonentId,
        type
    } []
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/{userId}" baseUrl="/arvatars" summary="메타버스 미팅 아바타 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="userId" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    avartars: {
        id
    } []
}
    
```
{% endswagger-response %}
{% endswagger %}
