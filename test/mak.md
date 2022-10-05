<div id="header"># BookChat API Documentation

<div id="toc" class="toc2">

<div id="toctitle">Table of Contents</div>

* [공통 HTTTP Status Code](#_공통_htttp_status_code) * [토큰](#_토큰) * [엑세스 토큰 재발급](#_엑세스_토큰_재발급) * [사용자](#_사용자) * [사용자 기본 프로필 조회](#_사용자_기본_프로필_조회) * [사용자 닉네임 중복 체크](#_사용자_닉네임_중복_체크) * [사용자 회원가입](#_사용자_회원가입) * [사용자 로그인](#_사용자_로그인) * [도서](#_도서) * [ISBN 도서 검색](#_isbn_도서_검색) * [Title 도서 검색](#_title_도서_검색) * [Author 도서 검색](#_author_도서_검색) * [책장](#_책장) * [읽을 도서 등록](#_읽을_도서_등록) * [읽고 있는 도서 등록](#_읽고_있는_도서_등록) * [읽은 도서 등록](#_읽은_도서_등록) * [읽을 도서 조회](#_읽을_도서_조회) * [읽고 있는 도서 조회](#_읽고_있는_도서_조회) * [읽은 도서 조회](#_읽은_도서_조회)</div>

</div>

<div id="content">

<div class="sect1">## 공통 HTTTP Status Code

<div class="sectionbody">

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Status Code</td>

<td class="tableblock halign-left valign-top">Common Mean</td>

<td class="tableblock halign-left valign-top">Usage</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">200</td>

<td class="tableblock halign-left valign-top">Success</td>

<td class="tableblock halign-left valign-top">요청 정상 처리</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">400</td>

<td class="tableblock halign-left valign-top">Bad Request</td>

<td class="tableblock halign-left valign-top">요청이 부적절한 경우</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">401</td>

<td class="tableblock halign-left valign-top">UnAuthorized</td>

<td class="tableblock halign-left valign-top">인증되지 않은 사용자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">403</td>

<td class="tableblock halign-left valign-top">Forbidden</td>

<td class="tableblock halign-left valign-top">권한이 없거나 차단된 사용자</td>

</tr>

</tbody>

</table>

</div>

</div>

<div class="sect1">## 토큰

<div class="sectionbody">

<div class="sect2">### 엑세스 토큰 재발급

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Field</td>

<td class="tableblock halign-left valign-top">Type</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`refreshToken`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">리프레쉬 토큰</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">POST /v1/api/auth/token HTTP/1.1 Content-Type: application/json;charset=UTF-8 Content-Length: 223 Host: bookchat.link {"refreshToken":"eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJCb29rQ2hhdCIsInByb3ZpZGVyIjoiZ29vZ2xlIiwidXNlck5hbWUiOiJ0ZXN0R09PR0xFIiwiZXhwIjoxNjY2MTQxMDU4LCJlbWFpbCI6InRlc3RAZ2FtaWwuY29tIn0.lAKMFi6Rco_THkOfyJlEvXd1dwjmXPNgqdqLPGBl_FI"}</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`accessToken`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">엑세스 토큰</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`refreshToken`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">리프레쉬 토큰</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK Content-Type: application/json Content-Length: 444 {"accessToken":"eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJCb29rQ2hhdCIsInByb3ZpZGVyIjoiZ29vZ2xlIiwidXNlck5hbWUiOiJ0ZXN0R09PR0xFIiwiZXhwIjoxNjY0OTMyODU4LCJlbWFpbCI6InRlc3RAZ2FtaWwuY29tIn0.l2EsF_4N8nCpIa3tds1i0eZ2FC0gTv3EYsUIFrg9pwM","refreshToken":"eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJCb29rQ2hhdCIsInByb3ZpZGVyIjoiZ29vZ2xlIiwidXNlck5hbWUiOiJ0ZXN0R09PR0xFIiwiZXhwIjoxNjY2MTQxMDU4LCJlbWFpbCI6InRlc3RAZ2FtaWwuY29tIn0.lAKMFi6Rco_THkOfyJlEvXd1dwjmXPNgqdqLPGBl_FI"}</div>

</div>

</div>

</div>

</div>

<div class="sect1">## 사용자

<div class="sectionbody">

<div class="sect2">### 사용자 기본 프로필 조회

<div class="paragraph">`Request Header`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 50%;"> <col style="width: 50%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Name</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`Authorization`</td>

<td class="tableblock halign-left valign-top">Bearer [JWT token]</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Request`</div>

<div class="listingblock">

<div class="content">GET /v1/api/users/profile HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`userNickname`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">닉네임</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`userEmail`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">이메일</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`userProfileImageUri`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">프로필 사진 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`defaultProfileImageType`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">기본 이미지 타입</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK Content-Type: application/json X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY Content-Length: 136 {"userNickname":"nickname","userEmail":"test@gmail.com","userProfileImageUri":"somethingImageUrl@naver.com","defaultProfileImageType":1}</div>

</div>

* * *</div>

<div class="sect2">### 사용자 닉네임 중복 체크

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`nickname`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">사용자 nickname</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/users/profile/nickname?nickname=HiBs HTTP/1.1 Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK</div>

</div>

<div class="paragraph">`Error Response`</div>

<div class="listingblock">

<div class="content">HTTP/1.1 409 Conflict</div>

</div>

* * *</div>

<div class="sect2">### 사용자 회원가입

<div class="paragraph">`Request Header`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 50%;"> <col style="width: 50%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Name</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`Authorization`</td>

<td class="tableblock halign-left valign-top">Bearer [openid token]</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`provider_type`</td>

<td class="tableblock halign-left valign-top">프로바이더 타입 [KAKAO / GOOGLE]</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`nickname`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">닉네임</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`defaultProfileImageType`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">기본 이미지 타입</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`userProfileImage`</td>

<td class="tableblock halign-left valign-top">_true_</td>

<td class="tableblock halign-left valign-top">프로필 이미지</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingTastes`</td>

<td class="tableblock halign-left valign-top">_true_</td>

<td class="tableblock halign-left valign-top">독서 취향</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: Bearer eyJraWQiOiJhYmNlZGYiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwiaXNzIjoiaHR0cHM6Ly9rYXV0aC5rYWthby5jb20iLCJlbWFpbCI6InRlc3RAZ21haWwuY29tIn0.YHqXp3Noznet_pP-Umt3o4ifp81O052ELvst2DmbxN7soeHLCsDWnI79xxpstUhKfUZ1XGyqey8wyllu9fJJZpHyyHX1qBjRFtrJ0Ghj_4E6m8W_YB1b4Hwv0QlXNqxigPcT1p9xnr5XvoxarpslAyvl_IUNZKO6u4zQ7iFjCiV-4GCRB082ZktoIx4P8YZw3WqnGi2V3buSmWoG-evEQQbWQBJ6C9Y-vEyA2aCCSU-Vl2A3aN5-fbE_h2OiKXdm44nDye8GWak2r9pg84ufvB-pUMAP5PdkYNIvNMmVt0PDkww2uSNahz7odig83xSU8g-3FofxsNcmDPRkug88_w provider_type: KAKAO Host: bookchat.link Content-Type: application/x-www-form-urlencoded nickname=nick&defaultProfileImageType=1&readingTastes=PHILOSOPHY&readingTastes=DEVELOPMENT&readingTastes=DESIGN</div>

</div>

<div class="paragraph">`Response`</div>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK</div>

</div>

<div class="paragraph">`Error Response`</div>

<div class="paragraph">요청 오류(Authorization Header 없을 시)</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: Host: bookchat.link Content-Type: application/x-www-form-urlencoded nickname=nick&userEmail=kaktus418%40gmail.com&oauth2Provider=kakao&defaultProfileImageType=2</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request</div>

</div>

<div class="paragraph">요청 오류(Authorization Header에 빈 토큰으로 요청시)</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: Bearer provider_type: KAKAO Host: bookchat.link Content-Type: application/x-www-form-urlencoded nickname=nick&defaultProfileImageType=2</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request Content-Type: text/plain;charset=UTF-8 Content-Length: 35 유효하지 않은 요청입니다</div>

</div>

<div class="paragraph">요청 오류(Authorization Bearer 양식에 맞지 않을 때)</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: TearereyJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJ0ZXN0In0.ljsVdbOiejW1sUMDrUm_GS18V77pD_vpcVGpNA7SKQzVJHwaqX5tw6LUu7zHNfRJ63MczAUnvoVHCKZ_2gkMWdOPKyRNiyTC1X_7Sqe9_84neqJX-m9Pq1aj4yNtoZMIgxLCsDP7A9H80LmeQ0c6PQr2qZVIbZ7sVr9lCN9J5IBmuEK9mSrvBWCAY_rO6iVelhgqs5bpyQHnt12namP_4xCBXcz_gZSLfxrSD25Pzt1k0XqZaqpRCLK4GZg7xDd346xh80mEigo2O6kyAnFFk1HB1MV4zRJzJRd-tvUiwBnetXz-1Uc-KDpDSzxk9S0PFnuh_0lpL-EI7ERBtKKQLA provider_type: KAKAO Host: bookchat.link Content-Type: application/x-www-form-urlencoded defaultProfileImageType=1&nickname=testName</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request Content-Type: text/plain;charset=UTF-8 Content-Length: 35 유효하지 않은 요청입니다</div>

</div>

<div class="paragraph">만료된 토큰</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: Bearer eyJraWQiOiJhYmNkZWZnIiwiYWxnIjoiUlMyNTYifQ.eyJpc3MiOiJodHRwczovL2thdXRoLmtha2FvLmNvbSIsInN1YiI6InRlc3QiLCJleHAiOjB9.LZCwNer7fEt6pRnsRWAHPoLO6Hqb3XQyhOYUsJoWXUGGg8z48H474eACTgKVaRG6RrVu-bvm2tQ-BwAf81WQQsgU87xN4T4cz0lzRti4hMeM-G-yollDhDsFr39gg1ikpUzHzku4UsS_MMKy087pmVg7NhWvFyrdj1rDyoBBVXGSRo54rP7ACG9ZHtlvwO99Ts7xw3aVTqPIadQx0B15oIBP1-scQlghGJlssDwmWXSnflPE5tgboQQYi2gB3-kKjuX1zJ6ksv76F4pCIvBSYpv-jA5Pn49u0GSbj-OGSDo8_MC1uOcZ1gEDNI41-CcRQt3qJDqEYtWDJ7Jfv7Z_Wg provider_type: KAKAO Host: bookchat.link Content-Type: application/x-www-form-urlencoded nickname=nick&defaultProfileImageType=2</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 401 Unauthorized Content-Type: text/plain;charset=UTF-8 Content-Length: 36 유효하지 않은 토큰입니다.</div>

</div>

<div class="paragraph">올바르지 않은 요청 파라미터</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: Bearer eyJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJ0ZXN0In0.ljsVdbOiejW1sUMDrUm_GS18V77pD_vpcVGpNA7SKQzVJHwaqX5tw6LUu7zHNfRJ63MczAUnvoVHCKZ_2gkMWdOPKyRNiyTC1X_7Sqe9_84neqJX-m9Pq1aj4yNtoZMIgxLCsDP7A9H80LmeQ0c6PQr2qZVIbZ7sVr9lCN9J5IBmuEK9mSrvBWCAY_rO6iVelhgqs5bpyQHnt12namP_4xCBXcz_gZSLfxrSD25Pzt1k0XqZaqpRCLK4GZg7xDd346xh80mEigo2O6kyAnFFk1HB1MV4zRJzJRd-tvUiwBnetXz-1Uc-KDpDSzxk9S0PFnuh_0lpL-EI7ERBtKKQLA Host: bookchat.link Content-Type: application/x-www-form-urlencoded nickname=&userEmail=abcdefg&oauth2Provider=</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request</div>

</div>

</div>

<div class="sect2">### 사용자 로그인

<div class="paragraph">`Request Header`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 50%;"> <col style="width: 50%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Name</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`Authorization`</td>

<td class="tableblock halign-left valign-top">Bearer [openid token]</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`provider_type`</td>

<td class="tableblock halign-left valign-top">프로바이더 타입 [KAKAO / GOOGLE]</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Request`</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signin HTTP/1.1 Authorization: Bearer eyJraWQiOiJhYmNlZGYiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwiaXNzIjoiaHR0cHM6Ly9rYXV0aC5rYWthby5jb20iLCJlbWFpbCI6InRlc3RAZ21haWwuY29tIn0.YHqXp3Noznet_pP-Umt3o4ifp81O052ELvst2DmbxN7soeHLCsDWnI79xxpstUhKfUZ1XGyqey8wyllu9fJJZpHyyHX1qBjRFtrJ0Ghj_4E6m8W_YB1b4Hwv0QlXNqxigPcT1p9xnr5XvoxarpslAyvl_IUNZKO6u4zQ7iFjCiV-4GCRB082ZktoIx4P8YZw3WqnGi2V3buSmWoG-evEQQbWQBJ6C9Y-vEyA2aCCSU-Vl2A3aN5-fbE_h2OiKXdm44nDye8GWak2r9pg84ufvB-pUMAP5PdkYNIvNMmVt0PDkww2uSNahz7odig83xSU8g-3FofxsNcmDPRkug88_w provider_type: KAKAO Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`accessToken`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">Access Token</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`refreshToken`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">Refresh Token</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Error Response`</div>

<div class="paragraph">요청 오류(Authorization Header 없을 시)</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signup HTTP/1.1 Authorization: Host: bookchat.link Content-Type: application/x-www-form-urlencoded nickname=nick&userEmail=kaktus418%40gmail.com&oauth2Provider=kakao&defaultProfileImageType=2</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request</div>

</div>

<div class="paragraph">요청 오류(Authorization Header에 빈 토큰으로 요청시)</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signin HTTP/1.1 Authorization: Bearer provider_type: KAKAO Host: bookchat.link</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request Content-Type: text/plain;charset=UTF-8 Content-Length: 35 유효하지 않은 요청입니다</div>

</div>

<div class="paragraph">요청 오류(Authorization Bearer 양식에 맞지 않을 때)</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/signin HTTP/1.1 Authorization: Tearer eyJraWQiOiJhYmNlZGYiLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwiaXNzIjoiaHR0cHM6Ly9rYXV0aC5rYWthby5jb20iLCJlbWFpbCI6InRlc3RAZ21haWwuY29tIn0.YHqXp3Noznet_pP-Umt3o4ifp81O052ELvst2DmbxN7soeHLCsDWnI79xxpstUhKfUZ1XGyqey8wyllu9fJJZpHyyHX1qBjRFtrJ0Ghj_4E6m8W_YB1b4Hwv0QlXNqxigPcT1p9xnr5XvoxarpslAyvl_IUNZKO6u4zQ7iFjCiV-4GCRB082ZktoIx4P8YZw3WqnGi2V3buSmWoG-evEQQbWQBJ6C9Y-vEyA2aCCSU-Vl2A3aN5-fbE_h2OiKXdm44nDye8GWak2r9pg84ufvB-pUMAP5PdkYNIvNMmVt0PDkww2uSNahz7odig83xSU8g-3FofxsNcmDPRkug88_w provider_type: KAKAO Host: bookchat.link</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 400 Bad Request Content-Type: text/plain;charset=UTF-8 Content-Length: 35 유효하지 않은 요청입니다</div>

</div>

<div class="paragraph">만료된 토큰</div>

<div class="listingblock">

<div class="content">POST /v1/api/users/siginin HTTP/1.1 Authorization: Bearer eyJraWQiOiJhYmNkZWZnIiwiYWxnIjoiUlMyNTYifQ.eyJpc3MiOiJodHRwczovL2thdXRoLmtha2FvLmNvbSIsInN1YiI6InRlc3QiLCJleHAiOjB9.LZCwNer7fEt6pRnsRWAHPoLO6Hqb3XQyhOYUsJoWXUGGg8z48H474eACTgKVaRG6RrVu-bvm2tQ-BwAf81WQQsgU87xN4T4cz0lzRti4hMeM-G-yollDhDsFr39gg1ikpUzHzku4UsS_MMKy087pmVg7NhWvFyrdj1rDyoBBVXGSRo54rP7ACG9ZHtlvwO99Ts7xw3aVTqPIadQx0B15oIBP1-scQlghGJlssDwmWXSnflPE5tgboQQYi2gB3-kKjuX1zJ6ksv76F4pCIvBSYpv-jA5Pn49u0GSbj-OGSDo8_MC1uOcZ1gEDNI41-CcRQt3qJDqEYtWDJ7Jfv7Z_Wg provider_type: KAKAO Host: bookchat.link</div>

</div>

<div class="listingblock">

<div class="content">HTTP/1.1 401 Unauthorized X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY</div>

</div>

</div>

</div>

</div>

<div class="sect1">## 도서

<div class="sectionbody">

<div class="sect2">### ISBN 도서 검색

<div class="paragraph">`Request Header`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 50%;"> <col style="width: 50%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Name</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`Authorization`</td>

<td class="tableblock halign-left valign-top">Bearer [JWT token]</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`query`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">isbn 번호</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`size`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 번에 조회할 책의 수 - page 당 size</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`page`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 번에 조회할 page 수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`sort`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">조회시 정렬 옵션</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/books?query=1231513&size=5&page=1&sort=ACCURACY HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Resopnse`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].isbn`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">ISBN</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].title`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].author[]`</td>

<td class="tableblock halign-left valign-top">`Array`</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].publisher`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">책 표지 이미지</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.is_end`</td>

<td class="tableblock halign-left valign-top">`Boolean`</td>

<td class="tableblock halign-left valign-top">마지막 페이지 여부</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.pageable_count`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">가져온 페이지 수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.total_count`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">총 페이지 수</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK Content-Type: application/json X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY Content-Length: 203 {"bookDtos":[{"isbn":"213123","title":"effectiveJava","author":["Joshua"],"publisher":"testPublisher","bookCoverImageUrl":"bookCoverImageUrl"}],"meta":{"is_end":false,"pageable_count":5,"total_count":5}}</div>

</div>

* * *</div>

<div class="sect2">### Title 도서 검색

<div class="paragraph">`Request Header`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 50%;"> <col style="width: 50%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Name</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`Authorization`</td>

<td class="tableblock halign-left valign-top">Bearer [JWT token]</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`query`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">도서명</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`size`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 번에 조회할 책의 수 - page 당 size</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`page`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 번에 조회할 page 수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`sort`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">조회시 정렬 옵션</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/books?query=effectiveJava&size=5&page=1&sort=LATEST HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].isbn`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">ISBN</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].title`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].author[]`</td>

<td class="tableblock halign-left valign-top">`Array`</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].publisher`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">책 표지 이미지</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.is_end`</td>

<td class="tableblock halign-left valign-top">`Boolean`</td>

<td class="tableblock halign-left valign-top">마지막 페이지 여부</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.pageable_count`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">가져온 페이지 수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.total_count`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">총 페이지 수</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK Content-Type: application/json X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY Content-Length: 203 {"bookDtos":[{"isbn":"213123","title":"effectiveJava","author":["Joshua"],"publisher":"testPublisher","bookCoverImageUrl":"bookCoverImageUrl"}],"meta":{"is_end":false,"pageable_count":5,"total_count":5}}</div>

</div>

* * *</div>

<div class="sect2">### Author 도서 검색

<div class="paragraph">`Request Header`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 50%;"> <col style="width: 50%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Name</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`Authorization`</td>

<td class="tableblock halign-left valign-top">Bearer [JWT token]</td>

</tr>

</tbody>

</table>

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`query`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">작가명</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`size`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 번에 조회할 책의 수 - page 당 size</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`page`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 번에 조회할 page 수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`sort`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">조회시 정렬 옵션</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/books?query=Joshua&size=5&page=1&sort=LATEST HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].isbn`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">ISBN</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].title`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].author[]`</td>

<td class="tableblock halign-left valign-top">`Array`</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].publisher`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookDtos[].bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">책 표지 이미지</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.is_end`</td>

<td class="tableblock halign-left valign-top">`Boolean`</td>

<td class="tableblock halign-left valign-top">마지막 페이지 여부</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.pageable_count`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">가져온 페이지 수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`meta.total_count`</td>

<td class="tableblock halign-left valign-top">`Number`</td>

<td class="tableblock halign-left valign-top">총 페이지 수</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">HTTP/1.1 200 OK Content-Type: application/json X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY Content-Length: 203 {"bookDtos":[{"isbn":"213123","title":"effectiveJava","author":["Joshua"],"publisher":"testPublisher","bookCoverImageUrl":"bookCoverImageUrl"}],"meta":{"is_end":false,"pageable_count":5,"total_count":5}}</div>

</div>

</div>

</div>

</div>

<div class="sect1">## 책장

<div class="sectionbody">

<div class="sect2">### 읽을 도서 등록

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Field</td>

<td class="tableblock halign-left valign-top">Type</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`isbn`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">ISBN</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`title`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`authors[]`</td>

<td class="tableblock halign-left valign-top">Array</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`publisher`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_true_</td>

<td class="tableblock halign-left valign-top">책 커버 이미지 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingStatus`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">WISH</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">POST /v1/api/bookshelf/books HTTP/1.1 Content-Type: application/json;charset=UTF-8 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Content-Length: 191 Host: bookchat.link {"isbn":"124151214","title":"effectiveJava","authors":["Joshua"],"publisher":"oreilly","bookCoverImageUrl":"bookCoverImage.com","readingStatus":"WISH","star":null,"singleLineAssessment":null}</div>

</div>

<div class="paragraph">`Response`</div>

<div class="listingblock">

<div class="content">HTTP/1.1 201 Created X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY</div>

</div>

* * *</div>

<div class="sect2">### 읽고 있는 도서 등록

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Field</td>

<td class="tableblock halign-left valign-top">Type</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`isbn`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">ISBN</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`title`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`authors[]`</td>

<td class="tableblock halign-left valign-top">Array</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`publisher`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_true_</td>

<td class="tableblock halign-left valign-top">책 커버 이미지 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingStatus`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">READING</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">POST /v1/api/bookshelf/books HTTP/1.1 Content-Type: application/json;charset=UTF-8 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Content-Length: 194 Host: bookchat.link {"isbn":"124151214","title":"effectiveJava","authors":["Joshua"],"publisher":"oreilly","bookCoverImageUrl":"bookCoverImage.com","readingStatus":"READING","star":null,"singleLineAssessment":null}</div>

</div>

<div class="paragraph">`Response`</div>

<div class="listingblock">

<div class="content">HTTP/1.1 201 Created X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY</div>

</div>

* * *</div>

<div class="sect2">### 읽은 도서 등록

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"> <col style="width: 25%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Field</td>

<td class="tableblock halign-left valign-top">Type</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`isbn`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">ISBN</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`title`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`authors[]`</td>

<td class="tableblock halign-left valign-top">Array</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`publisher`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_true_</td>

<td class="tableblock halign-left valign-top">책 커버 이미지 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingStatus`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">COMPLETE</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`star`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">평점</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`singleLineAssessment`</td>

<td class="tableblock halign-left valign-top">String</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한 줄 평</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">POST /v1/api/bookshelf/books HTTP/1.1 Content-Type: application/json;charset=UTF-8 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Content-Length: 204 Host: bookchat.link {"isbn":"124151214","title":"effectiveJava","authors":["Joshua"],"publisher":"oreilly","bookCoverImageUrl":"bookCoverImage.com","readingStatus":"COMPLETE","star":"FOUR","singleLineAssessment":"very good"}</div>

</div>

<div class="paragraph">`Response`</div>

<div class="listingblock">

<div class="content">HTTP/1.1 201 Created X-Content-Type-Options: nosniff X-XSS-Protection: 1; mode=block Cache-Control: no-cache, no-store, max-age=0, must-revalidate Pragma: no-cache Expires: 0 Strict-Transport-Security: max-age=31536000 ; includeSubDomains X-Frame-Options: DENY</div>

</div>

* * *</div>

<div class="sect2">### 읽을 도서 조회

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingStatus`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">WISH</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`size`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">page 당 size</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`page`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한번에 조회할 page수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`sort`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">등록순-id</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/bookshelf/books?readingStatus=WISH&size=5&page=1&sort=id,DESC HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`[].title`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">책 커버 이미지 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].authors[]`</td>

<td class="tableblock halign-left valign-top">`Array`</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].publisher`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].star`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">평점</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].singleLineAssessment`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">한 줄 평</td>

</tr>

</tbody>

</table>

* * *</div>

<div class="sect2">### 읽고 있는 도서 조회

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingStatus`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">READING</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`size`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">page 당 size</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`page`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한번에 조회할 page수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`sort`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">등록순-id</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/bookshelf/books?readingStatus=READING&size=5&page=1&sort=id,DESC HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`[].title`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">책 커버 이미지 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].authors[]`</td>

<td class="tableblock halign-left valign-top">`Array`</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].publisher`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].star`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">평점</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].singleLineAssessment`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">한 줄 평</td>

</tr>

</tbody>

</table>

* * *</div>

<div class="sect2">### 읽은 도서 조회

<div class="paragraph">`Request`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">Parameter</td>

<td class="tableblock halign-left valign-top">Optional</td>

<td class="tableblock halign-left valign-top">Description</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`readingStatus`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">COMPLETE</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`size`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">page 당 size</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`page`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">한번에 조회할 page수</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`sort`</td>

<td class="tableblock halign-left valign-top">_false_</td>

<td class="tableblock halign-left valign-top">등록순-id</td>

</tr>

</tbody>

</table>

<div class="listingblock">

<div class="content">GET /v1/api/bookshelf/books?readingStatus=COMPLETE&size=5&page=1&sort=id,DESC HTTP/1.1 Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0IiwicHJvdmlkZXIiOiJHT09HTEUiLCJuYW1lIjoiZ29vZ2xlMTIzIiwiZW1haWwiOiJ0ZXN0QGdtYWlsLmNvbSJ9.MFg4fTS3TFWfASSpOkHx5Q85oqiyehXDtvEC-v2z7dE Host: bookchat.link</div>

</div>

<div class="paragraph">`Response`</div>

<table class="tableblock frame-all grid-all stretch"><colgroup><col style="width: 33.3333%;"> <col style="width: 33.3333%;"> <col style="width: 33.3334%;"></colgroup>

<thead>

<tr>

<th class="tableblock halign-left valign-top">Path</th>

<th class="tableblock halign-left valign-top">Type</th>

<th class="tableblock halign-left valign-top">Description</th>

</tr>

</thead>

<tbody>

<tr>

<td class="tableblock halign-left valign-top">`[].title`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">제목</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].bookCoverImageUrl`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">책 커버 이미지 URI</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].authors[]`</td>

<td class="tableblock halign-left valign-top">`Array`</td>

<td class="tableblock halign-left valign-top">저자</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].publisher`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">출판사</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].star`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">평점</td>

</tr>

<tr>

<td class="tableblock halign-left valign-top">`[].singleLineAssessment`</td>

<td class="tableblock halign-left valign-top">`String`</td>

<td class="tableblock halign-left valign-top">한 줄 평</td>

</tr>

</tbody>

</table>

* * *</div>

</div>

</div>

</div>

<div id="footer">

<div id="footer-text">Last updated 2022-10-05 09:46:49 +0900</div>

</div>

<script>if (!hljs.initHighlighting.called) { hljs.initHighlighting.called = true ;[].slice.call(document.querySelectorAll('pre.highlight > code')).forEach(function (el) { hljs.highlightBlock(el) }) }</script>
