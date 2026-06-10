# 커스텀 CSS 메뉴얼

## 채팅
### HTML

    <div class="chat_box chat animated {user_streamer} {user_manager}" data-nickname="{닉네임}">
      <div class="inner_box">
        <p class="name">
          <img src="{뱃지 url}" class="badge">
          <span class="nick">{닉네임}</span>
        </p>
        <p class="text" data-content="{채팅 내용}">{채팅 내용}</p>
      </div>
    </div>

* **`.chat_box`**: 채팅 박스 전체를 감싸는 최상위 요소입니다.
    * `chat`: 일반 채팅임을 나타냅니다.
    * `animated`: 애니메이션 효과를 위한 기본 클래스입니다.
    * `user_streamer`: 스트리머 뱃지가 있을 경우 추가됩니다.
    * `user_manager`: 매니저 뱃지가 있을 경우 추가됩니다.
* **`data-nickname`**: 작성자의 닉네임이 담겨 있습니다.
* **`data-content`**: 채팅 내용이 HTML 이스케이프된 상태로 담겨 있습니다. (CSS `content: attr(data-content)` 등으로 활용 가능)

### css 샘플 양식

* CSS에 다음과 같은 형식의 주석을 삽입하면 대시보드 미리보기에서 해당 메세지가 나타납니다.
    
        /* testcase
        {
            "profile": {
                "nickname": "{닉네임}",
                "badges": [
                    {
                        "imageUrl": "{뱃지 링크}"
                    }
                ]
            },
            "content": "{채팅 내용}",
            "emojis": {
                "{이모지 코드}": "{이모지 링크}"
            }
        }
        */

## 도네이션 (후원)
### HTML

    <div class="chat_box donation animated {user_streamer} {user_manager}" data-nickname="{닉네임}">
      <div class="inner_box">
        <div class="donation_box donation_preset_{금액단위} donation_{금액} {donation_video}">
          <div class="top_box">
            <div class="nick">
              <img src="{뱃지 url}" class="badge">
              {닉네임}
            </div>
            <div class="msg" data-content="{후원 메시지}">{후원 메시지}</div>
          </div>
          <div class="bottom_box">
            <div class="amount_badge">
              <img src="https://raw.githubusercontent.com/serafi0620/chat-stopover-layer-images/main/chzzk/cheese.png" class="amount_icon">
              <span class="amount_value">{금액}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

* **`.chat_box.donation`**: 후원 메시지 박스입니다.
* **`.donation_box`**: 실제 후원 내용이 담긴 상자입니다.
    * `donation_preset_{1000/10000/100000/1000000}`: 금액 단위별 프리셋 클래스입니다.
    * `donation_{금액}`: 정확한 후원 금액이 클래스로 추가됩니다 (예: `donation_5000`).
    * `donation_video`: 영상 후원일 경우 추가되는 클래스입니다.

### css 샘플 양식

        /* testcase
        {
            "donationType": "CHAT",
            "donatorNickname": "{닉네임}",
            "payAmount": 1000,
            "donationText": "{후원 메시지}",
            "badges": [
                {
                    "imageUrl": "{뱃지 링크}"
                }
            ]
        }
        */

## 영상 도네이션 (영상 후원)
### HTML
* 구조는 **도네이션**과 동일하며, `.donation_box` 요소에 `donation_video` 클래스가 추가됩니다.

### css 샘플 양식

        /* testcase
        {
            "donationType": "VIDEO",
            "donatorNickname": "{닉네임}",
            "payAmount": 1000,
            "donationText": "{후원 메시지}",
            "badges": [
                {
                    "imageUrl": "{뱃지 링크}"
                }
            ]
        }
        */
