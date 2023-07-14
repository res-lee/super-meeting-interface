# room(룸) event(일정) meeting(회의실)

* 예약 혹은 바로 만들기를 통해 meeting을 만들게 되면,
  * WAPL event 등록 & meeting 생성이 진행된다.
  * event id와 meeting id가 모두 생성된다.
  * meeting 내용 중
    * 일정과 관련된 부분은 wapl에 저장되며,
    * meeting 설정과 관련된 부분은 meeting에 저장된다.
* meeting 수정시,
  * 일정과 관련된 부분은 wapl을 수정하며,
  * meeting 설정과 관련된 부분은 meeting을 수정한다.
  * 반복되는 미팅의 경우, 일정 혹은 meeting 설정 중  한 부분만 변경되어도 둘다 재생성한다.
