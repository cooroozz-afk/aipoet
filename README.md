# 🎭 AI 시인 (AI Poet)

LangChain과 Streamlit을 활용한 한국어 시 생성 웹 애플리케이션

## 📋 프로젝트 개요

이 프로젝트는 OpenAI의 GPT-4o-mini 모델을 사용하여 사용자가 입력한 주제에 대한 아름다운 한국어 시를 자동으로 생성하는 웹 애플리케이션입니다.

## ✨ 주요 기능

- 🖊️ 주제 기반 한국어 시 자동 생성
- 🔐 안전한 API 키 입력 시스템
- 🎨 직관적인 Streamlit 웹 인터페이스
- ⚡ LangChain을 활용한 효율적인 프롬프트 체인
- 🛡️ 포괄적인 에러 핸들링

## 🛠️ 기술 스택

- **Frontend**: Streamlit 1.51.0
- **AI Framework**: LangChain 1.0.5
- **LLM**: OpenAI GPT-4o-mini
- **Language**: Python 3.x

## 📦 설치 방법

### 1. 저장소 클론 (또는 파일 다운로드)

```bash
git clone <repository-url>
cd ai-poet
```

### 2. 가상환경 생성 (권장)

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. 의존성 패키지 설치

```bash
pip install -r requirements.txt
```

## 🚀 실행 방법

### 1. 애플리케이션 실행

```bash
streamlit run app.py
```

### 2. 웹 브라우저에서 접속

기본적으로 `http://localhost:8501`에서 실행됩니다.

### 3. 사용 방법

1. **사이드바에서 OpenAI API 키 입력**
   - OpenAI 계정에서 API 키 발급: https://platform.openai.com/api-keys
   - `sk-`로 시작하는 API 키를 입력

2. **시의 주제 입력**
   - 메인 화면에서 원하는 주제 입력
   - 예: "가을", "사랑", "고향", "우정" 등

3. **시 생성 요청**
   - "시 작성 요청하기" 버튼 클릭
   - AI가 생성한 시를 확인

## 📁 프로젝트 구조

```
ai-poet/
│
├── app.py              # 메인 애플리케이션 파일
├── requirements.txt    # Python 의존성 패키지 목록
└── README.md          # 프로젝트 문서 (이 파일)
```

## 🔧 주요 코드 설명

### LangChain 체인 구조

```python
# 프롬프트 템플릿 생성
prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful assistant that writes beautiful Korean poetry."),
    ("user", "{input}")
])

# 체인 구성: 프롬프트 → LLM → 출력 파서
chain = prompt | llm | output_parser

# 실행
result = chain.invoke({"input": f"{content}에 대한 아름다운 시를 써 줘"})
```

### 주요 컴포넌트

- **ChatPromptTemplate**: 시스템 프롬프트와 사용자 입력을 구조화
- **init_chat_model**: OpenAI GPT-4o-mini 모델 초기화
- **StrOutputParser**: LLM 출력을 문자열로 파싱
- **Streamlit**: 사용자 인터페이스 구성

## ⚙️ 환경 변수

애플리케이션은 다음과 같이 API 키를 처리합니다:

```python
os.environ['OPENAI_API_KEY'] = api_key
```

또는 `.env` 파일을 생성하여 관리할 수 있습니다:

```env
OPENAI_API_KEY=sk-your-api-key-here
```

## 🚨 에러 처리

애플리케이션은 다음 상황에 대한 에러 처리를 제공합니다:

- ❌ API 키 미입력
- ❌ 주제 미입력
- ❌ 잘못된 API 키
- ❌ API 호출 오류
- ❌ 네트워크 오류

## 📝 사용 예시

### 입력
```
주제: 가을
```

### 출력
```
생성된 시

주제: 가을

단풍잎 붉게 물들고
찬바람 살랑이는 계절
...
```

## 🔒 보안 주의사항

- API 키는 절대 코드에 하드코딩하지 마세요
- `.env` 파일은 `.gitignore`에 추가하세요
- API 키는 password 타입 입력으로 숨겨집니다
- 사용하지 않는 API 키는 비활성화하세요

## 📚 참고 자료

- [LangChain 공식 문서](https://python.langchain.com/)
- [Streamlit 공식 문서](https://docs.streamlit.io/)
- [OpenAI API 문서](https://platform.openai.com/docs/)

## 🤝 기여

이슈 제보와 풀 리퀘스트를 환영합니다!

## 📄 라이선스

이 프로젝트는 MIT 라이선스를 따릅니다.

## 👨‍💻 개발자

프로젝트에 대한 질문이나 제안사항이 있으시면 언제든지 연락주세요.

---

**Happy Coding! 🎉**
