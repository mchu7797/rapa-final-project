# 프로젝트 컨텍스트

## 폴더 구조

```text
rapa-final-project/
├── README.md                 # 저장소 안내
├── docs/                     # RFP, 설계/검토 문서
├── images/                   # 토폴로지 이미지
├── pnet-project/             # PNETLab 프로젝트 파일
├── configs/                  # 장비별 최종 설정
│   ├── FB-1/
│   ├── FB-2/
│   ├── SSP/
│   └── EXT/
├── automation/
│   └── backup/               # 구성 백업 자동화 코드
├── config-temp/              # 팀원별 원본 수집본 (git 제외)
└── Final/                    # 프로젝트 내 PNET 추출본 (git 제외)
```

## 관리 기준

- README는 저장소 진입점으로 유지하고, 긴 문서는 `docs/`에 둔다.
- 토폴로지 이미지는 `images/` 아래에서 관리한다.
- PNETLab 프로젝트 파일은 `pnet-project/` 아래에서 관리한다.
- 장비 최종 설정 파일은 `configs/` 아래에서 관리한다.
- 백업 자동화 코드는 `automation/backup/` 아래에서 관리한다.
- 원본 수집본과 로컬 추출본은 git으로 추적하지 않는다.

## 장비 호스트네임 규칙

호스트네임은 `-` 구분자 기준으로 구성한다.

```text
{사이트}-{건물번호}-{장비타입}{인덱스}
예) FB-2-LF-1-1
```

- `FB-1`, `FB-2` 장비는 각각 `configs/FB-1/`, `configs/FB-2/`에 둔다.
- `SSP` 장비는 `configs/SSP/`에 둔다.
- 외부 연동 장비는 `configs/EXT/`에 둔다.

## 설정 파일 규칙

- 파일명: `[장비명].config`
- 예: `configs/FB-2/FB-2-LF-1-1.config`
- 최종 반영 대상은 `configs/` 아래의 `.config` 파일이다.
- 원본 수집본은 `config-temp/`에 `{날짜}-{장비명}-v{버전}.{확장자}` 형식으로 보관한다.

## 장비 현황

### FB-1

| 파일 | 장비 타입 |
|---|---|
| FB-1-LF-1.config | Leaf |
| FB-1-SP-1.config | Spine |
| FB-1-SP-2.config | Spine |

### FB-2

| 파일 | 장비 타입 |
|---|---|
| FB-2-BLF-1.config | Border Leaf |
| FB-2-LF-1-1.config | Leaf |
| FB-2-LF-1-2.config | Leaf |
| FB-2-LF-2-1.config | Leaf |
| FB-2-LF-2-2.config | Leaf |
| FB-2-SP-1.config | Spine |
| FB-2-SP-2.config | Spine |
| FB-2-SW-1.config | Switch |
| FB-2-SW-2.config | Switch |

### SSP

| 파일 | 장비 타입 |
|---|---|
| SSP-1.config | Super Spine |
| SSP-2.config | Super Spine |

### EXT

| 파일 | 장비 타입 |
|---|---|
| EXT-FW-1.config | Firewall |
| EXT-FW-2.config | Firewall |
| EXT-L3-1.config | External L3 |
| EXT-R.config | External Router |
| ISP.config | ISP Router |

## git 브랜치 규칙

- `main` 브랜치만 사용한다.
- 별도 브랜치는 사용자가 명시적으로 요청할 때만 생성한다.

## git 커밋 컨벤션

커밋 형식: `[팀원이름]: [커밋 내용]`

## config-temp → configs 반영 워크플로우

1. 사용자가 반영할 버전 번호와 변경 내용을 명시한다.
2. `config-temp/`에서 해당 버전 파일을 찾는다.
3. 대상 장비명에 맞춰 `configs/` 아래의 대응 `.config` 파일에 반영한다.
4. 반영 후 변경 파일을 검토하고 커밋한다.

## 백업 자동화 관리

- 백업 자동화 코드는 `automation/backup/` 아래에서 관리한다.
- 실제 장비 IP, 계정, 실행 결과 백업 파일은 저장소에 직접 남기지 않는다.
- 템플릿 파일과 실행 방법만 버전 관리한다.
