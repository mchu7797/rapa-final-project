# 프로젝트 컨텍스트

## 폴더 구조

```
rapa-final-project/
├── FB-1/          # FB 건물 1번 장비 설정
├── FB-2/          # FB 건물 2번 장비 설정
├── config-temp/   # 팀원별 원본 수집본 (git 제외)
└── README.md
```

## 장비 호스트네임 규칙

호스트네임은 `-` 구분자 기준 3개 토큰으로 구성된다.

```
{사이트}-{건물번호}-{장비타입}{인덱스}
예) FB-2-LF-1-1
```

- **카테고리 (폴더)**: 토큰 1~2번 → `FB-1`, `FB-2`
- **예외 - SSP 장비**: 토큰 1~3번이 카테고리 (예: `FB-1-SSP`)

## 설정 파일 규칙

- 파일명: `[장비명].config` (예: `FB-2-LF-1-1.config`)
- 원본은 `config-temp/`에 `{날짜}-{장비명}-v{버전}.{확장자}` 형식으로 보관
- 루트 배치 시 v1 버전 기준

## 장비 현황

### FB-1
| 파일 | 장비 타입 |
|------|-----------|
| FB-1-LF-1.config | Leaf |
| FB-1-SP-1.config | Spine |
| FB-1-SP-2.config | Spine |

### FB-2
| 파일 | 장비 타입 |
|------|-----------|
| FB-2-BLF-1.config | Border Leaf |
| FB-2-LF-1-1.config | Leaf |
| FB-2-LF-1-2.config | Leaf |
| FB-2-LF-2-1.config | Leaf |
| FB-2-LF-2-2.config | Leaf |
| FB-2-SP-1.config | Spine |
| FB-2-SP-2.config | Spine |

## config-temp 팀원 분담

| 폴더 | 팀원 | 담당 장비 |
|------|------|-----------|
| 02_대경 | 대경 | FB-2-LF-1-1, FB-2-LF-1-2, FB-2-SP-1 |
| 03_하진 | 하진 | FB-1-SP-2 |
| 04_영탁 | 영탁 | FB-1-LF-1, FB-1-SP-1 |
| 05_민석 | 민석 | FB-2-BLF-1, FB-2-LF-2-1, FB-2-LF-2-2, FB-2-SP-2 |

## git 브랜치 규칙

- **main 브랜치만 사용**한다. 별도 브랜치를 생성하지 않는다.

## git 커밋 컨벤션

초기 설정 커밋 형식: `[팀원이름]: 장비 초기설정`
