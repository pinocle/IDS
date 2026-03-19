## 프로젝트 구조
이 프로젝트는 다중 다계층 네트워크의 동적 신뢰 연결 및 지능적 관제 기술 개발 연구가 목표이다. 현재 네트워크 이상 탐지 관련 연구 진행 중이다. 
프로젝트 디렉토리 구조는 다음을 무조건 따를 것.

/app
├── config/{version}/
|   ├── local.yaml
|   ├── prod.yaml
├── data/
|   ├── 01_raw/{공통}
|   ├── 02_processed/{version}/
|   ├── 03_features/{version}/
|   ├── 04_predictions/{version}/
├── entrypoints/{version}/
|   ├── inference.py
|   ├── train.py
├── notebooks/
|   ├── EDA.ipynb
|   ├── Baseline.ipynb
├── src/{version}/
|   ├── pipelines/
|   |   ├── init.py
|   |   ├── feature_eng_pipeline.py
|   |   ├── inference_pipeline.py
|   |   ├── training_pipeline.py
|   ├── utils.py
├── tests/{version}/
|   ├── init.py
|   ├── test_training.py
├── docker-compose.yml(compose.yml)
├── Dockerfile
├── env.yaml
├── env-dev.yaml
├── README.md
├── requirements.txt
├── requirements-dev.txt

- config/ -> config files
    Separate params from code. (local.yaml, prod.yaml)
- data/ -> full data lifecycle
    raw->preprocessed->features->predictions
- entrypoint/ -> main scripts
    train.py (pipeline)
    inference.py (batch/real-time)
- notebooks/ -> exploration only
    EDA, analysis - never production logic
- src/ -> core ML code
    feature engineering, training, inference (modular + testable)
- tests/ -> automated checks
    prevent silent failures
- docker + env files -> reproducibility
    same setup on any machine/CI
- pinned dependencies -> stability
    exact versions -> consistent results

## 코딩 스타일
PEP 8 스타일을 따라 작성할 것. https://peps.python.org/pep-0008/ 공식 문서 참고.
