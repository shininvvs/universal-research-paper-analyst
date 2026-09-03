# universal-research-paper-analyst

분야를 가리지 않는 **논문 · 구현 코드 분석** Claude Code 스킬.

논문 하나를 "요약"하는 게 아니라 **이해**하게 만드는 것이 목적이다.
연구 질문 → 선행연구 → 핵심 아이디어 → 방법 → 수식 → 실험 → 한계 → 구현 코드까지
하나로 잇고, 저장소가 있으면 실제 실행 흐름을 추적해 논문 개념과 짝지어 준다.

## 설치

### 방법 1 — 개인 스킬로 clone (권장)

어느 디렉터리에서 작업하든 쓸 수 있고, `git pull` 로 갱신된다.

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/shininvvs/universal-research-paper-analyst.git \
  ~/.claude/skills/universal-research-paper-analyst
```

### 방법 2 — 파일만 복사

```bash
mkdir -p ~/.claude/skills/universal-research-paper-analyst
curl -fsSL https://raw.githubusercontent.com/shininvvs/universal-research-paper-analyst/main/SKILL.md \
  -o ~/.claude/skills/universal-research-paper-analyst/SKILL.md
```

### 방법 3 — 특정 프로젝트에서만

프로젝트 저장소 안에 두면 그 저장소에서 일할 때만 적용된다. 팀원은 clone 만 하면 된다.

```bash
mkdir -p <프로젝트>/.claude/skills/universal-research-paper-analyst
cp SKILL.md <프로젝트>/.claude/skills/universal-research-paper-analyst/
```

설치 후 **Claude Code 를 새로 켜야** 목록에 잡힌다. 세션 시작 시점에 스킬을 읽기 때문이다.

## 쓰는 법

새 세션에서 `/universal-research-paper-analyst` 로 직접 부르거나,
논문이나 저장소 분석을 시키면 알아서 불러온다.

```
이 논문 분석해줘: https://arxiv.org/abs/XXXX.XXXXX
이 저장소가 논문의 어느 수식을 어디서 구현하는지 짚어줘
Figure 3 이 뭘 보여주는 건지 데이터 흐름으로 설명해줘
이거 재현하려면 뭐부터 해야 해?
```

## 이 스킬이 지키는 원칙

- **위에서 아래로.** 코드를 첫 줄부터 읽는 것으로 시작하지 않는다.
  연구 문제 → 핵심 아이디어 → 구조 → 세부 기제 → 수식 → 실험 → 구현 순서로 내려간다.
- **근거를 구분한다.** `논문에 쓰여 있음` / `코드가 실제로 그렇게 함` / `합리적 추론` / `모름`
  을 갈라 놓는다. 추론을 사실로 바꾸지 않는다.
- **논문과 구현이 같다고 가정하지 않는다.** 공개 코드가 논문과 어긋나는 경우는 흔하다.
- **표준 부품을 새롭다고 부르지 않는다.** 기여 / 엔지니어링 / 기존 기법 재사용을 나눈다.
- **지어내지 않는다.** 텐서 모양, 저장소 동작, 실험 결과 모두. 모르면 모른다고 한다.
- **초보자를 압도하지 않는다.** 기본값은 중급 입문자 눈높이, 필요하면 단계적으로 깊어진다.

## 구성

44개 절. 목표 파악(Phase 0)부터 한 문장 요약, 문제 정의, 선행연구, 기여, 구조, 그림,
수식, 알고리즘, 저장소 구조, 실행 진입점, 데이터 흐름, 텐서 모양 추적, 논문↔코드 대응표,
학습/추론, 실험, 절제, 한계, 계산량, 재현, 수정 가이드, 연구자 관점, 논문 비교까지.

ML/CV/NLP/생성모델/강화학습/그래프/로보틱스/멀티모달/시스템/이론/수학/물리/생물의학까지
분야별 적응 지침을 포함한다. ML 이 아닌 논문에 ML 식 분석을 강요하지 않는다.

## 라이선스

MIT
