# 공지사항 모음

## Index

- [:loudspeaker: 0422 공지사항](#0422-공지사항)
- [:loudspeaker: 0423 공지사항](#0423-공지사항)

<br>

# 0422-공지사항

Mail_classify

sale_img <- 교차에 넣어야하나?

마이페이지
마이페이지 - 회원탈퇴

- 취소 -> 사용자 소개글 페이지로 이동

3. 취소 버튼

- 메인 페이지로 이동

취소시 어디로 가는지 모르겠음

커뮤니티
alert 메세지창 버튼 2개로 바꾸면 좋을듯함
OK / Cancel - OK버튼을 누르면 로그인창으로 이동

블라블라, 고민/상담에 더보기란 추가가 있었으면 좋겠습니다

인기글 - 인기글 카테고리 클릭시 어떤 카테고리의 인기글인지 알수 있으면 좋겠습니다

금칙어 리스트 하나 추가가

문의하기

- 자주묻는질문 <- 설명 추가 클릭시 링크이동

판매 나눔 페이지 (41)
레이아웃 관련물어보기

---

<깃 remote 만드는 법>

1. remote 추가
   git remote add [별명] https://github.com/wafflu/teamlog.git

2. remote 확인
   git remote -v

```
$ git remote -v
origin  https://github.com/[본인깃id]/teamlog.git (fetch) => 내꺼
origin  https://github.com/[본인깃id]/teamlog.git (push)
[별명]  https://github.com/wafflu/teamlog.git (fetch) => 팀장꺼
[별명]  https://github.com/wafflu/teamlog.git (push)
```

3. pull 하기
   git pull [별명] master

---

<테이블 수정>

    1. sale
    	- tag 컬럼 삭제
    	- biding 컬럼명 bid_cd로 변경

    2. sale_history에서
    	- addr_name을 varchar(20)로 수정
    	- addr_nm 삭제
    	- tag 컬럼 삭제
    	- trade_s_cd_2를 null로 변경
    	- buy_id를 null로 변경
    	- buy_nick을 null로 변경

    3. user_info1
    	- user_info1에서 user_info로 테이블명 수정

    4. addr_cd
    	- 사용상태 default값 빠짐

    5. biding_history
    	- grand_state 컬럼명을 grant_state로 변경
    	- price를 null로 변경
    	- grant_date를 null로 변경

# 0423-공지사항

DROP TABLE IF EXISTS `qty_conditions`;

CREATE TABLE `qty_conditions` (
`qty_name` varchar(50) NULL,
`qty` int,
`first_r_date` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
`first_idno` varchar(10) NOT NULL,
`last_r_date` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
`last_idno` varchar(10) NOT NULL
);

<테이블 변경 빠진거>

1. alter table sale change biding bid_cd char;
2. biding_history 테이블
   - grant_date를 null로 변경
     - alter table biding_history modify grant_date timestamp NULL;
3. sale 테이블
   - up_cnt를 hoist_cnt로 변경
     - alter table sale change up_cnt hoist_cnt int;
   - hoisting을 h_date로 변경
     - alter table sale change hoisting h_date timestamp;
   - prop_cnt를 bid_cnt로 변경
     - alter table sale change prop_cnt bid_cnt int;
   - app_cnt를 삭제
     - alter table sale drop column app_cnt;
4. hoisting_history 테이블
   - hoisting을 h_date로 변경
     - alter table hoisting_history change hoisting h_date timestamp;

# 0424-공지사항

#1 first_id - null 값 허용으로 변경

alter table Mail_classify MODIFY column first_id varchar(10) null;
alter table admin_login_history MODIFY column first_id varchar(10) null;
alter table admin_modify_history MODIFY column first_id varchar(10) null;
alter table biding_history MODIFY column first_id varchar(10) null;
alter table biding MODIFY column first_id varchar(10) null;
alter table blacklist MODIFY column first_id varchar(10) null;
alter table chat_msg MODIFY column first_id varchar(10) null;
alter table chat_room MODIFY column first_id varchar(10) null;
alter table comment MODIFY column first_id varchar(10) null;
alter table community_img MODIFY column first_id varchar(10) null;
alter table community_tag MODIFY column first_id varchar(10) null;
alter table event_record MODIFY column first_id varchar(10) null;
alter table event MODIFY column first_id varchar(10) null;
alter table hoisting_history MODIFY column first_id varchar(10) null;
alter table jjim MODIFY column first_id varchar(10) null;
alter table mail MODIFY column first_id varchar(10) null;
alter table mail_recode MODIFY column first_id varchar(10) null;
alter table post MODIFY column first_id varchar(10) null;
alter table addr_cd MODIFY column first_id varchar(10) null;
alter table commu MODIFY column first_id varchar(10) null;
alter table qnalist_board MODIFY column first_id varchar(10) null;
alter table qty_conditions change first_idno first_id varchar(10) null;
alter table question_board MODIFY column first_id varchar(10) null;
alter table question_category MODIFY column first_id varchar(10) null;
alter table report MODIFY column first_id varchar(10) null;
alter table review_comment MODIFY column first_id varchar(10) null;
alter table sale_history MODIFY column first_id varchar(10) null;
alter table sale_img MODIFY column first_id varchar(10) null;
alter table img MODIFY column first_id varchar(10) null;
alter table sale_tag MODIFY column first_id varchar(10) null;
alter table sale MODIFY column first_id varchar(10) null;
alter table administrative MODIFY column first_id varchar(10) null;
alter table sale_category MODIFY column first_id varchar(10) null;
alter table spamlist MODIFY column first_id varchar(10) null;
alter table standardcode MODIFY column first_id varchar(10) null;
alter table tag MODIFY column first_id varchar(10) null;
alter table tb_standard MODIFY column first_id varchar(10) null;
alter table user_info MODIFY column first_id varchar(10) null;
alter table user MODIFY column first_id varchar(10) null;
alter table user_login_history MODIFY column first_id varchar(10) null;
alter table user_modify_history MODIFY column first_id varchar(10) null;
alter table administer MODIFY column first_id varchar(10) null;
alter table img change st state char default 'Y' null;
