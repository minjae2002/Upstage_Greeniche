# **그리니치 Greeniche** 

<div>
  <img src="https://github.com/minjae2002/Upstage_Green-Niche/blob/main/Green-niche-symbol.png" alt="로고" align="left" width="75" style="margin-right: 30px;">
  <p>
    이 서비스는 사용자와의 자연스러운 대화를 통해 ESG(환경, 사회, 지배구조) 기준에 대한 명확한 답변을 제공하여 정보 검색의 효율성을 높이는 것을 목표로 합니다. 특히, ESRS(유럽 지속 가능성 보고 표준)과 GRI(글로벌 보고 이니셔티브) 각각의 기준 및 그 사이의 변환에 대한 전문적인 지식을 제공하여 사용자의 이해를 돕습니다.
  </p>
</div>
<br>

<div align="center">
  <img src="https://github.com/minjae2002/Upstage_Green-Niche/blob/main/WORKLOAD.png" alt="내부 작업" width="1500"/>
</div>

## ⚙️ 주요 기능
*   **RAG 기반 질의응답**: RAG(검색 증강 생성)를 활용해 사용자가 업로드한 문서에서 관련 정보를 검색하고, 맥락에 맞는 정확한 답변을 실시간으로 제공합니다. 이를 통해 사용자에게 최적의 검색 경험을 제공합니다.
  
*   **프롬프트 엔지니어링(Prompt Engineering)**: 프롬프트 최적화 기법을 적용하여, 사용자 질문에 대한 답변의 정확성과 일관성을 높이며, 질문 의도를 정확히 반영한 결과를 제공합니다.
  
*   **API 및 웹 통합**: Solar API를 통해 Pinecone 임베딩을 실행하고, Streamlit 기반의 직관적이고 사용자 친화적인 웹 인터페이스에서 쉽게 질문을 입력하고 답변을 받을 수 있도록 합니다. 이로 인해 빠르고 효율적인 정보 검색이 가능합니다.

*   **문서 및 대화 관리**: 사용자는 다양한 형식의 문서(.txt, .md, .pdf)를 업로드할 수 있으며, 이 문서들을 파싱하여 중요 정보를 추출합니다. 대화 기록은 세션 상태로 저장되어, 사용자가 이전 대화 맥락을 유지할 수 있으며, 필요시 대화 흐름을 초기화할 수도 있습니다.

*   **모델 관리**: RAG 시스템을 통해 문서 업로드 및 데이터 갱신을 지속적으로 수행할 수 있습니다. 이는 협업을 가능하게 하며, 프로젝트의 데이터베이스를 최신 상태로 유지하여 모델의 성능을 극대화합니다.
<br>

## 데모 설명 및 사용 방법
### 📃 파일 설명
  - app.py: 전체 앱의 메인 파일로, 페이지 전환 및 전체 흐름을 관리합니다.
  - main.py: 메인 페이지의 인터페이스 및 메뉴를 구성합니다.
  - QA.py: 챗봇 페이지로, 문서의 업로드와 질의응답을 담당합니다.
  - docparser.py: 업로드된 문서를 파싱하여 텍스트로 변환합니다.
  - info.py: GRI 관련 pdf 파일을 다운로드할 수 있는 정보 페이지입니다.
  - rag.py: RAG 체인을 초기화하고 질문에 대한 답변을 생성하는 코드입니다.


### 🔧 설치 방법
#### RAG 모델을 설치하고 실행하기 위해 아래의 단계를 따르세요:

1. **필요한 라이브러리 설치**:
  - 필요한 Python 라이브러리를 설치합니다. 터미널이나 명령 프롬프트에서 다음 명령어를 실행하세요:

    ```bash
    pip install langchain-pinecone
    pip install langchain
    pip install openai
    pip install pinecone-client
    pip install langchain_openai
    pip install langchain-community
    pip install langchain_upstage
    pip install langchain_core
    pip install streamlit
    pip install bs4
    ```
    - 이 명령어는 `langchain`, `pinecone-client`, `openai`, `streamlit` 등 RAG 모델 실행과 웹 인터페이스 구성을 위한 필수 라이브러리를 설치합니다.  

2. **API 키 설정**:
  - Upstage와 Pinecone API 키를 설정합니다. 이 키들은 외부 서비스와의 통신을 위해 필요합니다.

     ```python
     UPSTAGE_API_KEY = "your-upstage-api-key"
     PINECONE_API_KEY = "your-pinecone-api-key"
     ```
    - UPSTAGE_API_KEY는 Upstage 서비스와, PINECONE_API_KEY는 Pinecone 임베딩 서비스와 연결하는 데 필요합니다.

### 🔓 실행 방법

1. **Streamlit 실행**:
  - app.py를 실행하여 Streamlit 서버를 시작합니다.

    ```bash
    streamlit run app.py
    ```
    - 앱이 실행된 후 브라우저에서 제공된 링크를 클릭하여 인터페이스에 접근할 수 있습니다. 인터페이스에서는 문서를 업로드하고, 챗봇에게 질문을 할 수 있습니다.

2. **문서 업로드 및 파싱**:
  - 파일 업로드: .txt, .md, .pdf 형식의 문서를 업로드할 수 있습니다.
  - 문서가 업로드되면 API를 통해 문서가 파싱되고, 텍스트로 변환된 내용이 챗봇의 답변에 사용됩니다.
    ```pyhton
    uploaded_file = st.file_uploader("Upload a document (.txt, .md, .pdf)", type=("txt", "md", "pdf"))
    if uploaded_file:
        with st.spinner("문서 분석 중 ..."):
          parsed_text, raw_data = parse_document(uploaded_file)
          st.success("문서 업로드에 성공했습니다!")
    ```

3. **질문 입력 및 답변 생성**:
  - 문서가 성공적으로 파싱된 후, 챗봇에게 질문을 입력하여 답변을 생성할 수 있습니다:
    ```python
    question = st.text_area("챗봇 그리니에게 질문하세요:", placeholder="궁금하신 ESRS나 GRI 지표에 대해 질문하세요!")
    if question:
        response = ask_question(st.session_state.qa_chain, question)
        st.markdown(response)
    ```

4. **Groundedness 체크**:
  - 답변이 문서에 근거한 내용인지 확인하기 위해 Groundedness 체크를 할 수 있습니다:
    ```python
    groundedness_check = UpstageGroundednessCheck(upstage_api_key=UPSTAGE_API_KEY)
    request_input = {
        "context": st.session_state.parsed_text,
        "answer": response,
    }
    groundedness_response = groundedness_check.invoke(request_input)
    if "grounded" in groundedness_response:
        st.write("해당 ESG 지표를 참고한 답변입니다.")
    else:
        st.write("출처가 불분명한 답변입니다. 확인이 필요합니다.")
    ```
