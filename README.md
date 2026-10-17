# 앨런 튜링 페르소나 AI 실습

> **"1951년, 맨체스터 대학의 앨런 튜링을 만나 대화해 보자!"**
> 팀 속전속결의 수업 자료입니다. AI 챗봇을 앨런 튜링 페르소나로 만들고, 로블록스 게임에 연결해 튜링 NPC와 대화합니다.

VESSL GPU에서 실행하는 언어 모델 하나를 **터미널(CLI), 웹 브라우저, Roblox Studio**에서
각각 불러 앨런 튜링 페르소나와 대화하는 실습 프로젝트입니다.

📘 **선생님용 쉬운 안내서:** [`TEACHER_GUIDE.md`](TEACHER_GUIDE.md)

## 실습 선택

| 실습 | 안내서 | 결과 |
| --- | --- | --- |
| 터미널 대화 | [`persona-core/README.md`](persona-core/README.md) | 검은 화면에서 튜링과 글로 대화 |
| 웹 채팅 | [`web-chat/README.md`](web-chat/README.md) | 브라우저 채팅 화면 |
| Roblox 채팅 | [`roblox-chat/README.md`](roblox-chat/README.md) | 게임 속 튜링 NPC 말풍선 |
| 3D 캐릭터 | [`assets/3d/`](assets/3d/) | Roblox에 넣을 튜링 3D 모델(OBJ) |

## 페르소나 설정 한눈에 보기

| 항목 | 내용 |
| --- | --- |
| 시대 | 1951년 말, 영국 맨체스터 대학 |
| 말투 | 차분하고 정중한 합니다체 ("반갑습니다", "흥미로운 질문입니다") |
| 모르는 것 | 1951년 이후의 일, '인공지능'·'튜링 테스트' 같은 이후에 생긴 말 |
| 역사 자료 | [`persona-core/data.json`](persona-core/data.json) 19건 (출생, 튜링 기계, 에니그마·봄브, ACE, 모방 게임, 마라톤 등) |
| 시스템 프롬프트 | [`persona-core/app.py`](persona-core/app.py)의 `SYSTEM_PROMPT` |

## 공통 실행 환경

VESSL Workspace는 `Torch 2.9.1 (CUDA 13.0.1, Python 3.13)` 컨테이너와
`A100 SXM 80GB x 1` GPU를 사용합니다. 웹과 Roblox 실습은 외부 접속을 위해
각 안내서에 적힌 HTTP 포트도 추가해야 합니다.

모든 실습은 `LGAI-EXAONE/EXAONE-4.5-33B` 모델을 텍스트 전용·비추론 모드로 사용합니다.

> ⚠️ 실습이 끝나면 VESSL Workspace를 꼭 **Stop** 하세요. 브라우저만 닫으면 GPU 요금이 계속 나갑니다.

## 저장소 구조

```text
persona-core/             # 공통 페르소나(시스템 프롬프트·역사 자료)와 터미널 대화 실습
web-chat/                 # 웹 채팅 서버와 화면
roblox-chat/
  TuringAI/               # Roblox Studio 프로젝트와 Luau 코드 (NPC 이름: Turing)
  vessl-server/           # Roblox용 Python API 서버
assets/3d/                # 앨런 튜링 3D 모델(OBJ + 텍스처)과 미리보기
TEACHER_GUIDE.md          # 선생님용 쉬운 안내서
```

설치, 서버 실행, 외부 주소 연결 방법은 선택한 실습의 README를 따릅니다.

## 다른 인물로 바꾸고 싶다면

1. `persona-core/app.py`의 `WELCOME`, `OPENING`, `SYSTEM_PROMPT`를 새 인물에 맞게 고칩니다.
2. `persona-core/data.json`의 역사 자료를 새 인물 자료로 바꿉니다. (`id`, `content`, `keywords` 형식 유지)
3. 웹 화면 문구는 `web-chat/views/chat.py`, Roblox 문구는 `roblox-chat/TuringAI/` 안의 Luau 파일에서 바꿉니다.

## 참고

- 앨런 튜링의 모습과 말투는 EBS 「부활수업」 앨런 튜링 편을 참고했습니다. 영상 화면은 이 저장소에 넣지 않았습니다.
- 3D 모델과 아바타 이미지는 이 실습을 위해 새로 만든 단순화된 캐릭터입니다.
