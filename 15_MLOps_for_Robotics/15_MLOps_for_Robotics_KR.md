**Volume10. AMR Engineering Process and Development Manual**

# Chapter 15. MLOps for Robotics

## 15.01 Robot MLOps Architecture

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

로봇 머신러닝 운영 아키텍처(Robot MLOps Architecture)는 로봇 시스템 내부에서 동작하는 머신러닝 모델(Machine Learning Model)을 개발하고, 학습하고, 검증하고, 배포하고, 모니터링하며, 지속적으로 개선하기 위한 통합 엔지니어링 프레임워크(Integrated Engineering Framework)이다. 일반적인 클라우드 기반 머신러닝(Cloud-Based Machine Learning)과 달리 로봇 머신러닝 운영(Robot MLOps)은 데이터센터(Data Center), 개발 환경(Development Environment), 시뮬레이션 플랫폼(Simulation Platform), 엣지 컴퓨터(Edge Computer), 임베디드 제어기(Embedded Controller), 플릿 관리 시스템(Fleet Management System), 그리고 실제 환경에서 운용되는 물리적 로봇(Physical Robot)을 연결해야 한다. 아키텍처는 현장 데이터(Field Data), 데이터셋(Dataset), 학습 코드(Training Code), 모델 버전(Model Version), 소프트웨어 릴리스(Software Release), 하드웨어 구성(Hardware Configuration), 그리고 관측된 로봇 동작(Observed Robot Behavior) 사이의 추적성(Traceability)을 유지해야 한다.

로봇 머신러닝 운영 플랫폼(Robot MLOps Platform)은 모델 개발(Model Development), 로봇 소프트웨어 개발(Robot Software Development), 운용 배포(Operational Deployment)를 명확하게 분리하면서도 이들 사이에 통제된 연결 관계를 유지하는 것에서 시작해야 한다. AI 엔지니어는 인지(Perception), 예측(Prediction), 이상 탐지(Anomaly Detection), 또는 내비게이션 모델(Navigation Model)을 개발할 수 있으며, 로봇 엔지니어는 미들웨어(Middleware), 위치추정(Localization), 경로 계획(Planning), 제어(Control), 안전(Safety), 하드웨어 인터페이스(Hardware Interface)를 관리한다. 이러한 활동은 서로 다른 도구와 릴리스 주기를 사용하지만 최종 제품은 이들의 통합에 의존한다. 따라서 아키텍처는 모델과 소프트웨어를 조정하되 어떠한 산출물도 공식 릴리스 절차 외부에서 조용히 변경되지 않도록 해야 한다.

전체 생명주기(Lifecycle)는 로봇, 시뮬레이션, 시험 시설(Test Facility), 운영자(Operator), 엔지니어링 도구(Engineering Tool)가 생성하는 데이터에서 시작된다. 센서 기록(Sensor Recording), 미션 로그(Mission Log), 모델 출력(Model Output), 시스템 상태(System State), 개입 이벤트(Intervention Event), 장애(Failure), 환경 메타데이터(Environmental Metadata)는 관리형 저장소(Managed Storage)와 데이터셋 카탈로그(Dataset Catalog)로 전송된다. 선택된 데이터는 이후 처리되고, 라벨링되고, 검증되며, 버전 관리된 데이터셋(Versioned Dataset)으로 조립된다. 학습 파이프라인(Training Pipeline)은 후보 모델(Candidate Model)을 생성하며, 후보 모델은 오프라인 평가(Offline Evaluation), 시뮬레이션, 통합 시험(Integration Testing), 통제된 배포(Controlled Deployment), 플릿 모니터링(Fleet Monitoring), 피드백 기반 개선(Feedback-Driven Improvement)을 거친다. 모든 단계는 전체 생명주기를 재구성할 수 있는 기록을 생성해야 한다.

로봇 머신러닝 운영은 모델이 물리적 세계(Physical World)와 직접 상호작용하기 때문에 일반적인 머신러닝 운영(MLOps)과 다르다. 온라인 추천 시스템(Online Recommendation System)의 오류는 사용자 경험에 영향을 줄 수 있지만, 이동 로봇의 인지 또는 제어 모델 오류는 위험한 정지, 충돌 위험, 미션 중단(Blocked Mission), 장비 손상(Damaged Equipment), 또는 운용 장애(Operational Disruption)를 유발할 수 있다. 따라서 모델 검증(Model Validation)은 물리적 안전(Physical Safety), 시간 동작(Timing Behavior), 하드웨어 호환성(Hardware Compatibility), 환경 강인성(Environmental Robustness), 장애 복구(Failure Recovery)를 포함해야 한다. 성능은 정적인 벤치마크(Static Benchmark)에서 측정된 평균 정확도나 손실값만으로 평가해서는 안 된다.

아키텍처는 학습 기반 구성요소(Learning Component)와 결정론적 안전 기능(Deterministic Safety Function) 사이의 경계를 정의해야 한다. 머신러닝은 객체 분류(Object Classification), 주행 가능성 추정(Traversability Estimation), 이상 탐지, 움직임 예측(Motion Prediction), 또는 위치추정을 지원할 수 있지만, 안전에 중요한 제한은 인증된 센서(Certified Sensor), 안전 제어기(Safety Controller), 속도 제한(Speed Limit), 비상 정지 회로(Emergency Stop Circuit), 결정론적 모니터링 로직(Deterministic Monitoring Logic)에 의해 유지될 수 있다. 이러한 분리는 하나의 모델이 위험 동작을 방지하는 유일한 보호 수단이 되는 것을 방지한다. 머신러닝 운영 시스템은 어떤 판단이 권고형(Advisory), 운용형(Operational), 안전 관련(Safety Relevant), 또는 직접적인 모션 제어(Motion Control)와 연결되는지를 기록해야 한다.

계층형 아키텍처(Layered Architecture)는 복잡성을 관리하는 데 유용하다. 데이터 계층(Data Layer)은 원시 기록(Raw Recording), 메타데이터(Metadata), 라벨(Label), 품질 보고서(Quality Report), 데이터셋 릴리스(Dataset Release)를 저장한다. 개발 계층(Development Layer)은 특징 공학(Feature Engineering), 학습(Training), 실험 추적(Experiment Tracking), 평가(Evaluation), 협업(Collaboration)을 지원한다. 검증 계층(Validation Layer)은 시뮬레이션, 재생(Replay), 하드웨어 인 더 루프 시험(Hardware-in-the-Loop Testing), 물리적 시험 시설(Physical Test Facility)을 연결한다. 배포 계층(Deployment Layer)은 모델을 런타임 의존성(Runtime Dependency)과 함께 패키징하고 승인된 릴리스를 배포한다. 운용 계층(Operations Layer)은 플릿 성능(Fleet Performance), 시스템 상태(System Health), 모델 동작(Model Behavior), 데이터 드리프트(Data Drift), 사고(Incident)를 모니터링한다. 거버넌스(Governance)와 보안(Security)은 모든 계층에 걸쳐 적용된다.

데이터 적재 계층(Data Ingestion Layer)은 개별 로봇, 시험 플릿(Test Fleet), 개발 플랫폼(Development Platform), 시뮬레이션 시스템(Simulation System)에서 생성되는 정보를 수용해야 한다. 업로드는 지속적으로 수행되거나, 충전 중에 수행되거나, 유선 전송 스테이션(Wired Transfer Station)을 통해 수행되거나, 미션 종료 후 수행될 수 있다. 적재 서비스(Ingestion Service)는 파일 무결성(File Integrity), 세션 완전성(Session Completeness), 메타데이터, 타임스탬프(Timestamp), 캘리브레이션 참조(Calibration Reference), 모델 버전, 소프트웨어 빌드(Software Build), 로봇 구성을 검증해야 한다. 유효하지 않거나 불완전한 세션은 공식 데이터셋에 포함되기 전에 격리되어야 한다. 신뢰할 수 있는 적재 과정은 학습과 장애 분석이 신뢰성 있는 원본 자료에 기반하도록 한다.

중앙 데이터 카탈로그(Central Data Catalog)는 로컬 서버(Local Server), 네트워크 저장소(Network Storage), 객체 저장소(Object Storage), 클라우드 지역(Cloud Region), 아카이브 시스템(Archival System)에 분산된 로봇 데이터에 논리적으로 접근할 수 있게 한다. 엔지니어는 로봇, 미션, 위치, 센서, 환경, 소프트웨어 버전, 모델 버전, 장애 이벤트, 주석 상태(Annotation State), 품질 상태(Quality Status)를 기준으로 데이터를 검색할 수 있어야 한다. 안정적인 식별자(Stable Identifier)는 원시 세션, 파생 파일(Derived File), 라벨, 실험, 릴리스를 서로 연결해야 한다. 카탈로그가 없으면 가치 있는 데이터가 폴더 구조 안에 숨겨져 효율적인 모델 개발이나 근본 원인 분석(Root-Cause Analysis)에 활용되지 못한다.

데이터셋 버전 관리(Dataset Versioning)는 재현 가능한 로봇 머신러닝 운영(Reproducible Robot MLOps)의 핵심 기반 중 하나이다. 모든 학습, 검증, 시험, 시뮬레이션, 회귀 데이터셋(Regression Dataset)은 고유 식별자(Unique Identifier), 구성 매니페스트(Content Manifest), 온톨로지 버전(Ontology Version), 전처리 설정(Preprocessing Configuration), 품질 상태, 변경 이력(Change History)을 가져야 한다. 데이터는 새로운 샘플이 추가될 때마다 내용이 바뀌는 가변 폴더(Mutable Folder)를 통해 참조되어서는 안 된다. 모델 결과는 정확한 입력 데이터셋을 재현할 수 있을 때에만 의미를 가진다. 버전 관리된 데이터셋은 성능 향상이 더 나은 데이터 때문인지 알고리즘 변경 때문인지를 구분하는 데도 도움을 준다.

원시 로봇 데이터(Raw Robot Data)는 적재가 성공적으로 완료된 이후 원칙적으로 변경되지 않아야 한다. 왜곡 보정 이미지(Rectified Image), 동기화된 센서 패키지(Synchronized Sensor Package), 필터링된 포인트 클라우드(Filtered Point Cloud), 익명화된 영상(Anonymized Video), 추출된 특징(Extracted Feature), 변환된 형식(Converted Format)은 원본과 연결된 파생 데이터(Derived Data)로 관리되어야 한다. 처리 파이프라인(Processing Pipeline)은 코드 버전(Code Version), 파라미터 값(Parameter Value), 실행 환경(Runtime Environment), 출력 체크섬(Output Checksum)을 기록해야 한다. 이러한 구조를 통해 알고리즘이 개선되거나 처리 오류가 발견된 경우에도 원본 증거를 수정하지 않고 파생 데이터셋을 다시 생성할 수 있다.

학습 파이프라인(Training Pipeline)은 가능한 한 자동화되고 선언적(Declarative)이어야 한다. 하나의 파이프라인은 고정된 데이터셋 버전을 가져오고, 전처리를 적용하고, 모델을 초기화하고, 학습을 실행하고, 체크포인트(Checkpoint)를 평가하고, 보고서를 생성하고, 후보 산출물(Candidate Artifact)을 등록할 수 있다. 설정에는 모델 구조(Model Architecture), 하이퍼파라미터(Hyperparameter), 데이터 증강(Data Augmentation), 손실 함수(Loss Function), 난수 시드(Random Seed), 연산 자원(Compute Resource), 종료 조건(Stopping Condition)이 정의되어야 한다. 수동 노트북 작업(Manual Notebook Step)은 탐색에 유용할 수 있지만, 공식 실험은 다른 엔지니어나 자동화 서비스가 반복할 수 있는 재현 가능한 파이프라인을 통해 실행되어야 한다.

실험 추적(Experiment Tracking)은 최종 성능 점수 이상의 정보를 기록해야 한다. 각 실행(Run)은 소스 코드 버전, 데이터셋 버전, 설정, 하드웨어, 소프트웨어 환경, 학습 시간, 지표(Metric), 산출물, 로그, 사용자 또는 서비스 신원(Service Identity)을 기록해야 한다. 실험 비교는 실행 간 변경점을 보여주고 어떤 파라미터가 결과에 영향을 주었는지 식별할 수 있어야 한다. 로봇 분야에서는 검출 정확도(Detection Accuracy), 위치 오차(Localization Error), 지연 시간(Latency), 메모리 사용량(Memory Usage), 전력 소비(Power Consumption), 장애물 미탐률(Missed Obstacle Rate), 불필요한 정지율(False-Stop Rate), 복구 시간(Recovery Time), 시나리오별 안전 지표(Scenario-Specific Safety Measure)를 포함할 수 있다.

모델 레지스트리(Model Registry)는 머신러닝 산출물을 통제하는 공식 원천(Controlled Source) 역할을 한다. 등록된 모델은 식별자, 버전, 아키텍처, 가중치(Weight), 입출력 명세(Input and Output Specification), 런타임 요구사항(Runtime Requirement), 지원 하드웨어(Supported Hardware), 학습 데이터셋, 검증 결과(Validation Result), 승인 상태(Approval Status), 알려진 제한사항(Known Limitation)을 포함해야 한다. 레지스트리 상태는 실험용(Experimental), 후보(Candidate), 검증됨(Validated), 승인됨(Approved), 배포됨(Deployed), 제한됨(Restricted), 폐기됨(Deprecated), 보관됨(Archived)으로 구성할 수 있다. 승인된 모델만 운영용 패키징(Production Packaging) 대상으로 지정되어야 한다. 모델 레지스트리는 맥락이나 승인 정보 없이 익명의 가중치 파일이 유통되는 것을 방지한다.

모델 패키징(Model Packaging)은 산출물이 대상 로봇 컴퓨터(Target Robot Computer)에서 일관되게 실행되도록 해야 한다. 패키지에는 모델 가중치, 런타임 엔진(Runtime Engine), 전처리 및 후처리 로직(Preprocessing and Postprocessing Logic), 캘리브레이션 참조, 설정 스키마(Configuration Schema), 의존성(Dependency), 무결성 서명(Integrity Signature)이 포함될 수 있다. ONNX, TensorRT, 또는 다른 최적화 런타임 형식으로 변환하면 수치적 동작(Numerical Behavior)이 변경될 수 있으므로, 패키징된 모델은 원래 학습 체크포인트와 별도로 평가되어야 한다. 패키지는 지원 GPU, 가속기(Accelerator), 메모리 요구사항, 정밀도 모드(Precision Mode)를 명시해야 한다.

로봇 배포(Robot Deployment)는 이기종 하드웨어(Heterogeneous Hardware)를 포함하는 경우가 많다. 하나의 플릿은 서로 다른 GPU 세대, 임베디드 컴퓨터, 센서 구성, 메모리 용량, 로봇 모델을 포함할 수 있다. 배포 시스템은 호환성 규칙(Compatibility Rule)을 정의하고 지원되지 않는 플랫폼에 산출물이 설치되는 것을 방지해야 한다. 하드웨어 프로파일(Hardware Profile)은 프로세서(Processor), 가속기, 운영체제(Operating System), 드라이버(Driver), 미들웨어, 센서 구성, 사용 가능한 자원(Available Resource)을 설명할 수 있다. 하나의 논리적 모델 버전(Logical Model Version)을 유지하면서도 여러 대상 장치에 맞춘 최적화 패키지가 필요할 수 있다.

지속적 통합(Continuous Integration)은 모델 관련 코드에 의미 있는 변경이 제출될 때마다 시험을 수행해야 한다. 정적 분석(Static Analysis), 단위 시험(Unit Test), 스키마 검사(Schema Check), 전처리 시험(Preprocessing Test), 모델 로딩 시험(Model-Loading Test), 수치 비교(Numerical Comparison), 소규모 기준 평가(Small Reference Evaluation)는 결함을 조기에 탐지할 수 있다. 통합 시험은 입력 메시지(Input Message), 텐서 형상(Tensor Shape), 좌표계(Coordinate Frame), 라벨, 출력이 로봇 소프트웨어와 계속 호환되는지를 확인해야 한다. 독립적인 모델 성능이 우수하더라도 인터페이스 불일치(Interface Mismatch)나 메시지 정의 변경으로 인해 실패할 수 있으므로 소프트웨어-모델 통합 시험(Software-Model Integration Testing)이 필수적이다.

지속적 학습(Continuous Training)은 새로 수집된 모든 샘플이 자동으로 운영 모델(Production Model)을 생성한다는 의미가 아니다. 자동 파이프라인은 데이터셋을 준비하고 후보 모델을 학습할 수 있지만, 운영 승격(Promotion)은 품질 통제와 승인 정책(Approval Policy)에 따라야 한다. 새로운 데이터에는 라벨링 오류, 비정상 분포(Unusual Distribution), 개인정보 제한(Privacy Restriction), 해결되지 않은 사고(Unresolved Incident)가 포함될 수 있다. 아키텍처는 지속적인 데이터 준비와 후보 모델 생성은 지원하되 통제된 릴리스 게이트(Controlled Release Gate)를 유지해야 한다. 이를 통해 물리적 로봇 시스템에 필요한 주의와 개발 속도를 함께 확보할 수 있다.

시뮬레이션(Simulation)은 현장 배포 전에 모델과 로봇 동작을 평가할 수 있는 확장 가능한 환경을 제공한다. 후보 모델은 다양한 조명, 날씨, 객체 배치(Object Arrangement), 센서 노이즈(Sensor Noise), 교통, 장애, 희귀 시나리오에서 시험될 수 있다. 시뮬레이션은 반복 가능성과 기준 정답(Ground Truth)을 제공하지만 실제 센서 특성이나 사람의 행동을 완전히 재현할 수는 없다. 따라서 머신러닝 운영은 시뮬레이션을 비공식적인 시각적 시연으로 취급하지 말고, 시나리오, 시뮬레이터 버전(Simulator Version), 자산 버전(Asset Version), 난수 시드, 평가 결과를 통제된 산출물로 관리해야 한다.

로그 재생(Log Replay)은 새로운 모델과 소프트웨어가 이전에 기록된 로봇 데이터를 반복 가능한 조건에서 처리하도록 한다. 재생 시스템(Replay System)은 센서 메시지, 타임스탬프, 미션 상태, 환경 맥락(Environmental Context)을 재현하고 비교를 위한 출력을 수집할 수 있다. 이는 알려진 장애에 대한 회귀 시험과 위험하거나 비용이 높은 현장 이벤트를 반복하지 않고 후보 모델을 평가하는 데 특히 유용하다. 재생 결과는 정확한 기록, 전처리 경로(Preprocessing Path), 런타임 버전, 평가 로직(Evaluation Logic)을 식별하여 성능 차이를 정확하게 추적할 수 있어야 한다.

소프트웨어 인 더 루프 시험(Software-in-the-Loop Testing)은 물리적 제어 하드웨어 없이 로봇 알고리즘을 평가하며, 하드웨어 인 더 루프 시험(Hardware-in-the-Loop Testing)은 실제 연산 장치, 네트워크, 제어기, 센서 인터페이스를 포함한다. 하드웨어 인 더 루프 검증은 시뮬레이션만으로는 발견하기 어려운 지연, 열 스로틀링(Thermal Throttling), 메모리 압박(Memory Pressure), 드라이버 비호환성(Driver Incompatibility), 메시지 손실(Message Loss), 시간 동작을 확인할 수 있다. 성숙한 머신러닝 운영 파이프라인은 후보 모델을 점진적으로 현실적인 환경으로 승격하고, 가상 시험에서 통제된 물리 시험으로 이동하기 전에 명확한 승인 조건을 적용해야 한다.

실제 로봇은 기계적 진동(Mechanical Vibration), 휠 슬립(Wheel Slip), 센서 오염(Sensor Contamination), 변화하는 조명, 네트워크 변동(Network Variation), 열 조건(Thermal Condition), 사람과의 상호작용을 경험하므로 물리적 시험 시설(Physical Test Facility)은 여전히 필요하다. 현장 검증(Field Validation)은 통제된 시나리오에 따라 수행되고 각 릴리스 후보에 대한 완전한 증거를 수집해야 한다. 시험 결과는 모델, 소프트웨어, 로봇, 지도, 센서, 캘리브레이션 버전과 연결되어야 한다. 모델은 성공적인 시연만으로 승인되어서는 안 되며 반복 가능한 시나리오, 품질 기준, 장애 처리 기대사항(Failure-Handling Expectation)을 충족해야 한다.

단계적 배포 전략(Staged Deployment Strategy)은 운용 위험을 줄인다. 새로운 모델은 먼저 실시간 데이터를 처리하지만 로봇 판단에는 영향을 주지 않는 섀도 모드(Shadow Mode)에서 실행될 수 있다. 엔지니어는 후보 모델의 출력과 현재 활성 모델 및 실제 시스템 동작을 비교한다. 이후 후보 모델은 시험 로봇(Test Robot), 통제된 현장(Controlled Site), 소규모 플릿, 광범위한 배포 순서로 활성화될 수 있다. 각 단계는 모니터링 요구사항(Monitoring Requirement), 성공 기준(Success Threshold), 최대 노출 범위(Maximum Exposure), 롤백 조건(Rollback Condition)을 정의해야 한다. 이를 통해 검증되지 않은 하나의 업데이트가 전체 플릿에 영향을 주는 것을 방지할 수 있다.

섀도 배포(Shadow Deployment)는 새로운 모델이 안전 관련 인지, 위치추정, 행동 예측(Behavior Prediction)에 영향을 줄 때 특히 유용하다. 현재 운영 시스템이 제어를 유지하는 동안 후보 모델은 검출 결과, 위험도 추정(Risk Estimate), 또는 궤적(Trajectory)을 생성할 수 있다. 차이는 장면, 클래스, 거리, 환경, 장애 유형별로 분석할 수 있다. 섀도 모드는 런타임 성능, 자원 사용, 예상하지 못한 현장 분포(Field Distribution)도 확인할 수 있다. 그러나 섀도 결과는 로봇의 행동이 다른 모델에 의해 제어되었고 그로 인해 관찰된 시나리오가 달라질 수 있음을 고려해야 한다.

카나리 배포(Canary Deployment)는 승인된 후보 모델을 제한된 수의 로봇이나 미션에 적용한다. 선택된 그룹은 사업 및 안전 노출을 제한하면서도 의미 있는 운용 조건을 대표해야 한다. 모니터링은 모델 지표, 운용 성능, 사람의 개입, 장애, 미션 결과를 기준으로 카나리 로봇과 기준 그룹(Baseline Group)을 비교해야 한다. 사전에 정의된 조건을 충족하는 증거가 확보될 때에만 배포 범위를 확대해야 한다. 중요한 지표가 허용 기준을 초과하면 카나리 릴리스는 자동으로 중단되거나 롤백되어야 한다.

블루-그린 배포(Blue-Green Deployment)는 두 개의 완전한 소프트웨어 및 모델 환경을 유지하는 방식으로 로봇 시스템에 적용할 수 있다. 하나의 환경은 활성 상태로 유지되고, 다른 환경은 새로운 릴리스를 설치하고 검증한다. 준비 상태 검사(Readiness Check)가 완료된 이후에만 로봇이나 플릿 시스템이 새로운 환경으로 전환된다. 이 접근은 롤백을 단순화하고 부분 업데이트 상태(Partial-Update State)를 줄일 수 있다. 그러나 엣지 장치는 클라우드 서버보다 자원이 제한적이므로 저장 공간, 부팅 시간(Boot Time), 하드웨어 용량, 동기화 제약을 고려해야 한다.

무선 모델 전달(Over-the-Air Model Delivery)은 인증되고, 암호화되고, 무결성이 검증된 채널을 사용해야 한다. 패키지는 로봇이 출처를 확인하고 전송 중 변경되지 않았음을 검증할 수 있도록 서명(Signature)되어야 한다. 업데이트 서비스(Update Service)는 설치 전에 배터리 수준, 연결 상태(Connectivity), 사용 가능한 저장 공간, 현재 미션 상태, 하드웨어 호환성, 안전 조건을 확인해야 한다. 특별히 설계된 경우가 아니라면 업데이트가 중요한 운용을 중단시켜서는 안 된다. 설치, 활성화, 실패, 롤백 이벤트는 플릿 관리 시스템에 보고되어야 한다.

원자적 업데이트(Atomic Update)는 모델 패키지의 일부는 새 버전이고 다른 일부는 이전 버전인 불일치 상태를 방지한다. 시스템은 활성화 전에 전체 패키지를 다운로드하고 검증하며, 현재 정상 동작 버전을 보존하고, 통제된 트랜잭션(Controlled Transaction)을 통해 전환해야 한다. 시작 시험(Startup Test)에 실패하면 이전 패키지를 계속 사용할 수 있어야 한다. 서로 의존하는 모델, 설정, 전처리, 후처리 구성요소는 함께 버전 관리되고 동시에 활성화되어야 한다.

롤백(Rollback)은 핵심 안전 및 신뢰성 기능이다. 새로운 모델이 오류, 과도한 지연, 비정상적인 자원 사용, 미션 성능 저하, 안전 우려를 유발할 경우 로봇은 신속하게 검증된 정상 릴리스(Known-Good Release)로 복귀할 수 있어야 한다. 롤백 기준은 중앙에서 정의되거나 통신이 불가능할 때 로컬에서 작동할 수 있다. 시스템은 엔지니어가 원인을 조사할 수 있도록 실패한 릴리스의 증거를 보존해야 한다. 롤백은 검증을 대체하지 않지만 시험을 통과한 이후에도 발생할 수 있는 결함의 영향을 제한한다.

기능 플래그(Feature Flag)와 런타임 설정(Runtime Configuration)은 특정 로봇, 현장, 미션, 조건에서 모델 또는 기능의 활성 여부를 제어할 수 있다. 이를 통해 전체 소프트웨어 패키지를 다시 빌드하지 않고 문제가 있는 기능을 비활성화할 수 있다. 그러나 통제되지 않은 플래그 조합은 검증되지 않은 구성을 만들 수 있다. 머신러닝 운영 플랫폼은 설정을 버전 관리하고, 허용된 조합만 사용하도록 제한하고, 변경을 기록하며, 현장 결과를 정확한 활성 설정과 연결해야 한다. 설정은 릴리스의 일부이며 비공식적인 운용 세부사항으로 취급해서는 안 된다.

런타임 모니터링(Runtime Monitoring)은 머신러닝 동작과 로봇 시스템 성능을 모두 관찰해야 한다. 모델 관련 지표에는 신뢰도 분포(Confidence Distribution), 클래스 빈도(Class Frequency), 예측 안정성(Prediction Stability), 분포 외 점수(Out-of-Distribution Score), 추론 지연(Inference Latency), 메모리 사용량, 입력 누락률(Missed Input Rate)이 포함될 수 있다. 로봇 지표에는 비상 정지, 사람의 개입, 경로 완료(Route Completion), 도킹 성공(Docking Success), 위치추정 초기화(Localization Reset), 안전 제어기 작동(Safety-Controller Activation), 미션 지연(Mission Delay), 에너지 소비(Energy Consumption)가 포함될 수 있다. 두 관점을 결합하면 모델이 기술적으로는 정확하지만 운용에 해로운지, 또는 오프라인 지표가 변했음에도 운용에는 유용한지를 판단할 수 있다.

데이터 드리프트(Data Drift)는 현장 데이터가 학습 및 검증에 사용된 데이터와 달라질 때 발생한다. 변화는 조명, 날씨, 객체 유형(Object Type), 시설 배치(Facility Layout), 카메라 특성(Camera Characteristic), 센서 노화(Sensor Aging), 로봇 속도, 사람 행동, 고객 프로세스(Customer Process)에 나타날 수 있다. 드리프트 모니터링은 특징 분포(Feature Distribution), 임베딩(Embedding), 모델 신뢰도, 클래스 빈도, 환경 메타데이터를 비교할 수 있다. 모든 분포 변화가 재학습을 요구하는 것은 아니지만, 중대한 드리프트는 검토, 목표 수집(Targeted Collection), 또는 새로운 시나리오 평가를 유발해야 한다.

개념 드리프트(Concept Drift)는 입력과 올바른 출력 사이의 관계가 변할 때 발생한다. 이전에는 임시 장애물로 처리하던 객체가 영구적인 공정의 일부가 되거나, 시설 내부 교통 규칙(Traffic Rule)이 변경될 수 있다. 새로운 장비나 작업 방식(Work Practice)은 센서 외형이 유사하더라도 기대되는 로봇 동작을 변경할 수 있다. 개념 드리프트는 단순한 데이터 드리프트보다 탐지하기 어렵다. 기준 정답, 운영자 피드백, 결과 분석(Outcome Analysis)이 필요하기 때문이다. 머신러닝 운영은 운용 변화(Operational Change)를 데이터셋 및 모델 검토와 연결해야 한다.

분포 외 탐지(Out-of-Distribution Detection)는 알려진 학습 조건과 크게 다른 장면을 식별할 수 있다. 모델은 비정상적인 센서 패턴, 객체 조합, 환경 상태를 표시하고 보수적인 동작(Conservative Behavior)이나 사람의 지원을 요청할 수 있다. 시스템은 이러한 이벤트를 이후 분석과 하드 케이스 데이터셋(Hard-Case Dataset) 포함을 위해 기록해야 한다. 분포 외 점수는 위험하지 않은 변화에 과도하게 반응하거나 실제 위험한 미지 상황을 놓칠 수 있으므로 반드시 검증해야 한다. 이는 위험 관리를 위한 지표이지 모든 낯선 상황을 보장해서 탐지하는 수단은 아니다.

운용 피드백(Operational Feedback)은 자유 서술형 보고서에만 의존하지 않고 구조화되어야 한다. 운영자는 불필요한 정지, 장애물 미탐, 비효율적인 경로 선택(Poor Route Choice), 도킹 실패, 위치추정 문제, 비정상 동작을 정의된 범주로 분류하고 타임스탬프 및 로봇 세션과 연결할 수 있다. 원격 지원(Remote Assistance)과 수동 인계(Manual Takeover) 이벤트는 주변 데이터를 자동으로 보존해야 한다. 구조화된 피드백을 통해 데이터 엔지니어와 AI 팀은 반복 패턴을 찾고, 수집 우선순위를 정하며, 실제 현장 문제를 모델 및 소프트웨어 버전과 연결할 수 있다.

사고 관리(Incident Management)는 머신러닝 운영 아키텍처와 통합되어야 한다. 안전 사고, 근접 사고(Near Miss), 개인정보 사고(Privacy Incident), 비정상 모델 동작, 주요 미션 실패는 통제된 데이터 보존과 조사를 요구한다. 사고 기록은 로봇 데이터, 로그, 모델 버전, 소프트웨어 릴리스, 환경, 사용자 행동(User Action), 수정 조치와 연결되어야 한다. 관련 산출물은 제한된 접근이나 법적 보존(Legal Hold)이 필요할 수 있다. 목표는 민감한 운용 데이터의 통제되지 않은 복사본을 생성하지 않으면서 근본 원인 분석을 지원하는 것이다.

모델 설명 가능성(Model Explainability)은 모델과 작업에 따라 활용 가치가 달라지지만 디버깅, 검증, 이해관계자 검토(Stakeholder Review)를 지원할 수 있다. 어텐션 맵(Attention Map), 특징 중요도(Feature Importance), 검출 시각화(Detection Visualization), 신뢰도 분석(Confidence Breakdown), 궤적 오버레이(Trajectory Overlay), 유사 학습 사례(Nearest Training Example)는 엔지니어가 모델 동작을 이해하는 데 도움이 될 수 있다. 그러나 이러한 도구를 모델이 안전하거나 정확하다는 증거로 취급해서는 안 된다. 설명은 성능 지표, 시나리오 시험, 시스템 로그, 도메인 지식(Domain Knowledge)과 함께 해석해야 하는 추가 증거이다.

로봇 컴퓨터는 엄격한 전력, 메모리, 열, 시간 제약 아래에서 동작하므로 자원 모니터링(Resource Monitoring)이 필요하다. 후보 모델은 정확도 목표를 만족하면서도 과도한 GPU 메모리를 사용하거나, 배터리 수명을 감소시키거나, 다른 소프트웨어를 지연시키거나, 열 스로틀링을 유발할 수 있다. 프로파일링(Profiling)은 실제 대상 플랫폼에서 평균 및 최악 지연(Average and Worst-Case Latency), 프로세서 사용률(Processor Utilization), 가속기 사용률(Accelerator Utilization), 메모리, 온도, 전력, 시작 시간을 측정해야 한다. 자원 승인 기준(Resource Acceptance Criteria)은 모델 승격 결정에 포함되어야 한다.

추론 시간(Inference Timing)은 신경망 실행 시간만 측정하지 말고 종단 간(End-to-End)으로 평가해야 한다. 전체 경로에는 센서 획득(Sensor Acquisition), 메시지 전송(Message Transport), 전처리, 모델 실행, 후처리, 융합(Fusion), 경로 계획, 명령 생성(Command Generation)이 포함될 수 있다. 큐 지연(Queue Delay)과 동기화 문제는 순수 추론 시간보다 더 큰 영향을 줄 수 있다. 따라서 머신러닝 운영 보고서는 모델 실행 시간과 전체 의사결정 지연(Total Decision Latency)을 구분하고, 격리된 벤치마크가 아니라 최대 시스템 부하(Peak System Load) 조건에서도 동작을 평가해야 한다.

신뢰성 시험(Reliability Testing)은 모델이나 런타임이 실패할 때의 동작을 평가해야 한다. 가능한 실패에는 입력 누락(Missing Input), 손상된 텐서(Corrupt Tensor), 사용 불가능한 가속기(Unavailable Accelerator), 메모리 고갈(Memory Exhaustion), 수치 불안정성(Numerical Instability), 런타임 충돌(Runtime Crash), 유효하지 않은 출력(Invalid Output), 장시간 추론(Prolonged Inference)이 포함된다. 로봇은 이러한 상태를 탐지하고 정의된 대체 동작(Fallback), 제한 기능(Reduced Capability), 안전 정지(Safe Stop), 사람 지원 모드(Human-Assistance Mode)로 전환해야 한다. 장애 주입 시험(Failure-Injection Testing)은 모니터링과 대체 메커니즘이 설계대로 작동하는지를 검증할 수 있다. 검증된 장애 동작 없이 모델 릴리스는 완전하지 않다.

대체 모델(Fallback Model)은 기본 모델이 사용 불가능하거나 불확실할 때 제한적이지만 신뢰할 수 있는 기능을 제공할 수 있다. 단순한 검출기(Simple Detector), 보수적인 주행 가능성 규칙(Conservative Traversability Rule), 기하학적 장애물 계층(Geometric Obstacle Layer), 또는 이전에 검증된 모델이 대체 기능을 수행할 수 있다. 아키텍처는 대체 모델이 언제 활성화되고, 얼마나 오랫동안 유지되며, 어떤 운용 제한이 적용되고, 이벤트가 어떻게 보고되는지를 정의해야 한다. 여러 런타임을 유지하면 복잡성이 증가하므로 대체 동작도 기본 운용과 동일한 수준으로 시험하고 버전 관리해야 한다.

플릿 수준 관측성(Fleet-Level Observability)은 엔지니어가 로봇 모델, 현장, 고객, 소프트웨어 버전, 환경 조건별 성능을 비교할 수 있도록 해야 한다. 대시보드는 배포 범위(Deployment Coverage), 활성 버전(Active Version), 업데이트 상태(Update Status), 모델 상태(Model Health), 사고, 사람의 개입, 드리프트 신호(Drift Signal), 운용 결과를 요약할 수 있다. 집계 지표(Aggregate Metric)는 개별 이벤트를 조사할 수 있는 능력을 유지해야 한다. 평균값은 특정 현장의 장애를 숨길 수 있으므로 아키텍처는 플릿 추세(Fleet Trend)에서 정확한 세션과 센서 데이터까지 상세 분석(Drill-Down)을 지원해야 한다.

중앙 모니터링(Central Monitoring)은 로컬 자율성(Local Autonomy)과 균형을 이루어야 한다. 로봇은 네트워크 연결을 잃거나, 제한된 환경에서 운용되거나, 민감한 데이터를 업로드할 수 없을 수 있다. 로컬 상태 모니터링(Local Health Monitoring)은 클라우드 접근에 의존하지 않고 중요한 장애를 탐지하고 안전 동작을 강제해야 한다. 로봇은 전송이 가능해질 때까지 요약 지표(Summarized Metric)와 이벤트 버퍼(Event Buffer)를 저장할 수 있다. 따라서 배포 및 모니터링 아키텍처는 상시 연결(Connected), 간헐 연결(Intermittently Connected), 완전 분리(Fully Isolated) 운용 모드를 모두 지원하면서 추적성을 유지해야 한다.

보안(Security)은 로봇 머신러닝 운영 전반에 적용되는 공통 요구사항이다. 학습 데이터, 모델, 업데이트 패키지, 소스 코드, 인증정보(Credential), 플릿 인터페이스(Fleet Interface)는 가치가 높고 안전과도 관련될 수 있다. 접근은 최소 권한 원칙(Least Privilege)을 따라야 하며 모든 동작은 로그에 기록되어야 한다. 모델 산출물은 서명되고 검증되어야 하며, 파이프라인은 승인되지 않은 코드 또는 의존성 변경(Dependency Change)으로부터 보호되어야 한다. 소프트웨어 공급망 통제(Software Supply-Chain Control)는 각 릴리스와 관련된 제3자 라이브러리, 컨테이너(Container), 기본 이미지(Base Image), 런타임 엔진, 취약점(Vulnerability)을 추적해야 한다.

개인정보 보호 통제(Privacy Control)는 데이터 수집, 라벨링, 학습, 모니터링, 사고 분석 전 과정에 적용되어야 한다. 원시 카메라 또는 음성 데이터에는 익명화, 제한된 접근, 지역별 저장(Regional Storage), 제한된 보존 기간이 필요할 수 있다. 모델 개발은 각 데이터셋에 연결된 허용 목적(Permitted Purpose)과 고객 조건(Customer Condition)을 문서화해야 한다. 운영 대시보드는 불필요한 개인정보를 노출해서는 안 된다. 기술적으로 성공한 파이프라인이라도 개인정보 의무, 데이터 주권(Data Sovereignty), 계약 조건을 위반한다면 허용될 수 없다.

승인 워크플로(Approval Workflow)는 모델의 위험 수준과 의도된 기능을 반영해야 한다. 중요도가 낮은 이상 분류기(Non-Critical Anomaly Classifier)는 AI 및 운영 승인이 필요할 수 있지만, 움직임 판단(Motion Decision)에 영향을 주는 인지 모델은 로봇, 안전, 보안, 도메인, 제품 검토도 필요할 수 있다. 워크플로는 데이터셋, 평가, 시뮬레이션, 현장 시험, 자원 프로파일링(Resource Profiling), 장애 분석의 증거를 보여주어야 한다. 조건부 승인(Conditional Approval)은 특정 현장, 속도, 환경, 로봇 구성에만 릴리스를 제한할 수 있다.

문서화(Documentation)는 최종 단계에서 별도로 작성하기보다 파이프라인의 일부로 생성되어야 한다. 모델 릴리스 패키지(Model Release Package)에는 모델 카드(Model Card), 데이터셋 참조, 평가 요약(Evaluation Summary), 호환성 매트릭스(Compatibility Matrix), 알려진 제한사항, 안전 가정(Safety Assumption), 배포 지침(Deployment Instruction), 모니터링 계획(Monitoring Plan), 롤백 절차(Rollback Procedure), 승인 기록이 포함될 수 있다. 자동으로 입력되는 항목은 누락을 줄이고, 엔지니어는 해석과 위험 설명(Risk Statement)을 제공한다. 좋은 문서는 운영 및 지원 팀이 무엇이 변경되었고 릴리스를 어떻게 관리해야 하는지 이해할 수 있게 한다.

아키텍처는 시간에 따른 재현성(Reproducibility Across Time)을 지원해야 한다. 학습 환경, 런타임 의존성, 컴파일러(Compiler), 가속기 라이브러리(Accelerator Library), 외부 패키지는 빠르게 변한다. 컨테이너, 환경 잠금 파일(Environment Lock File), 산출물 저장소(Artifact Repository), 소스 제어 태그(Source-Control Tag), 인프라 정의(Infrastructure Definition)는 실행 조건을 보존할 수 있다. 장기간 운용되는 로봇 제품에서는 최초 릴리스 수년 후 모델을 다시 빌드하거나 분석해야 할 수 있다. 따라서 재현성은 소프트웨어 환경뿐 아니라 하드웨어 가정(Hardware Assumption), 캘리브레이션, 데이터셋 가용성(Dataset Availability)도 포함한다.

로봇 머신러닝 운영은 많은 저장 공간, 네트워크 대역폭(Network Bandwidth), 라벨링 인력(Labeling Labor), 시뮬레이션 자원, GPU 연산을 사용할 수 있으므로 비용 관리(Cost Management)가 중요하다. 플랫폼은 프로젝트, 실험, 데이터셋, 배포별 자원 사용량(Resource Consumption)을 추적해야 한다. 캐싱(Caching), 계층형 저장소(Tiered Storage), 선택적 업로드(Selective Upload), 이벤트 기반 수집(Event-Triggered Collection), 스팟 연산(Spot Compute), 최적화된 파이프라인은 비용을 줄일 수 있다. 그러나 비용 절감을 위해 필수적인 검증이나 모니터링을 제거해서는 안 된다. 목표는 가장 높은 엔지니어링 및 안전 가치를 제공하는 데이터와 시험에 자원을 배분하는 것이다.

조직 역할(Organizational Role)은 명확하게 정의되어야 한다. 데이터 엔지니어(Data Engineer)는 적재, 저장, 메타데이터, 데이터셋을 관리한다. AI 엔지니어(AI Engineer)는 모델과 학습 파이프라인을 개발한다. 로봇 엔지니어(Robotics Engineer)는 모델을 미들웨어, 경로 계획, 제어, 하드웨어와 통합한다. 플랫폼 엔지니어(Platform Engineer)는 연산 자원, 배포, 모니터링, 자동화를 운영한다. 안전, 보안, 개인정보 보호, 품질, 제품, 운영 팀은 요구사항과 승인을 제공한다. 명확한 책임은 중요한 작업이 다른 조직의 책임이라고 오해되어 누락되는 것을 방지한다.

성숙한 로봇 머신러닝 운영 아키텍처(Robot MLOps Architecture)는 현장 운용에서 엔지니어링으로, 그리고 다시 안전하게 플릿으로 이어지는 폐쇄형 학습 루프(Closed Learning Loop)를 만든다. 로봇은 정상 동작, 어려운 시나리오, 장애, 드리프트, 사용자 개입에 관한 증거를 생성한다. 관리형 파이프라인은 이러한 증거를 검증된 데이터셋과 후보 모델로 변환한다. 시뮬레이션, 재생, 통합 시험, 통제된 현장 배포는 후보 모델을 평가한다. 모니터링과 거버넌스는 하나의 릴리스가 계속 허용 가능한 상태인지 판단한다. 이러한 루프는 추적성, 안전, 보안, 운용 안정성을 희생하지 않으면서 지속적인 개선을 가능하게 한다.

## 15.02 Model Training and Experiment Tracking

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

모델 학습(Model Training)과 실험 추적(Experiment Tracking)은 로봇 머신러닝 운영(Robot MLOps) 워크플로(Workflow)의 핵심 운영 요소를 구성한다. 모델 학습은 정제된 데이터셋(Curated Dataset), 알고리즘(Algorithm), 설정(Configuration), 연산 자원(Computing Resource)을 후보 머신러닝 모델(Candidate Machine Learning Model)로 변환하는 과정이며, 실험 추적은 각 후보 모델이 생성되고 평가된 정확한 조건을 기록하는 역할을 수행한다. 자율이동로봇(Autonomous Mobile Robot, AMR) 개발에서는 이러한 과정이 인지(Perception), 위치추정(Localization), 예측(Prediction), 주행 가능성 분석(Traversability Analysis), 이상 탐지(Anomaly Detection) 등 다양한 학습 기능을 지원해야 한다. 궁극적인 목표는 단순히 높은 정확도를 얻는 것이 아니라 모델의 출처, 동작 특성, 한계, 자원 요구사항, 검증 근거를 언제든지 재구성할 수 있는 체계를 구축하는 것이다.

모델 학습은 명확하게 정의된 엔지니어링 목표(Engineering Objective)에서 시작되어야 한다. 모델은 보행자(Pedestrian) 검출, 주행 가능 영역(Segmented Drivable Terrain) 분할, 깊이 추정(Depth Estimation), 바닥 상태(Floor Condition) 분류, 사람의 이동 예측(Human Motion Prediction), 센서 이상 탐지(Sensor Fault Detection), 정밀 도킹(Precise Docking) 지원 등 다양한 목적을 가질 수 있다. 각각의 작업은 서로 다른 라벨(Label), 데이터 분포(Data Distribution), 평가 지표(Evaluation Metric), 운용 제약(Operational Constraint)을 요구한다. 학습을 시작하기 전에 대상 기능(Target Function), 입력과 출력, 배포 환경(Deployment Environment), 안전 관련성(Safety Relevance), 허용 가능한 지연 시간(Acceptable Latency), 지원 하드웨어(Supported Hardware), 성능 기준(Performance Threshold)을 문서화해야 한다. 이를 통해 기술적으로 뛰어난 결과가 실제 로봇 문제를 해결하지 못하는 상황을 방지할 수 있다.

공식 실험(Official Experiment)을 시작하기 전에 학습 데이터셋(Training Dataset)은 반드시 고정(Fixed)되고 버전 관리(Versioning)되어야 한다. 학습 중에 내용이 변경되는 가변 폴더(Mutable Folder)를 사용하면 결과를 재현하거나 비교하기 어렵다. 하나의 데이터셋 릴리스(Dataset Release)는 고유 식별자(Unique Identifier), 원본 세션(Source Session), 온톨로지 버전(Ontology Version), 전처리 설정(Preprocessing Configuration), 품질 상태(Quality Status), 학습·검증·시험 분할(Train-Validation-Test Split), 알려진 제한 사항(Known Limitation), 접근 제한(Access Restriction)을 포함해야 한다. 실험 기록은 반드시 해당 데이터셋 버전을 참조해야 한다. 이후 데이터가 추가되거나 수정되거나 재라벨링될 경우에는 기존 버전을 변경하는 대신 새로운 데이터셋 버전을 생성해야 한다.

모델의 동작은 데이터 분포에 크게 영향을 받기 때문에 학습 전에 데이터셋 구성(Dataset Composition)을 검토해야 한다. 클래스 빈도(Class Frequency), 시나리오 커버리지(Scenario Coverage), 환경 다양성(Environmental Diversity), 센서 품질(Sensor Quality), 거리 분포(Distance Distribution), 객체 크기(Object Size), 가림(Occlusion), 날씨, 조명, 로봇 속도, 현장 대표성(Site Representation)을 분석해야 한다. 데이터셋이 매우 크더라도 거의 동일한 프레임이 반복되거나 안전에 중요한 희귀 상황(Rare but Safety-Critical Situation)이 부족하다면 충분하지 않다. 학습 팀은 어떤 운용 조건이 충분히 포함되어 있고, 어떤 조건은 부족하며, 어떤 조건이 검증이나 보호된 시험을 위해 의도적으로 제외되었는지를 명확히 이해해야 한다.

학습(Training), 검증(Validation), 시험(Test) 데이터는 데이터 누출(Data Leakage)을 방지하는 규칙에 따라 분리되어야 한다. 동일한 경로(Route), 연속 프레임(Consecutive Frame), 동일 미션(Mission), 하나의 연출된 이벤트(Staged Event)는 매우 높은 유사성을 가질 수 있다. 따라서 프레임 단위(Random Frame-Level Split) 무작위 분할은 실제보다 과도하게 높은 성능을 만들어낼 수 있다. 미션, 경로, 현장, 기간(Time Period), 로봇, 시나리오 단위로 그룹화(Grouping)하는 방식이 일반적으로 더 적절하다. 분할 논리(Split Logic), 난수 시드(Random Seed), 제외 조건(Exclusion), 보호된 시험 사례(Protected Test Case)는 실험과 함께 저장되어야 한다.

데이터 전처리(Data Preprocessing)는 단순한 준비 작업이 아니라 모델의 일부로 취급되어야 한다. 이미지 크기 조정(Image Resizing), 정규화(Normalization), 색상 변환(Color Conversion), 렌즈 왜곡 보정(Lens Correction), 포인트 클라우드(Point Cloud) 필터링, 복셀화(Voxelization), 좌표 변환(Coordinate Transformation), 시간 정렬(Temporal Alignment), 특징 추출(Feature Extraction), 라벨 변환(Label Conversion)은 모두 성능에 큰 영향을 미친다. 전처리 파이프라인은 버전 관리되는 코드(Version-Controlled Code)로 구현되고 명시적인 파라미터(Parameter)를 통해 관리되어야 한다. 학습과 추론(Inference)은 동일한 전처리 과정을 사용해야 하며, 서로 다른 전처리는 아무리 정확한 모델이라도 실제 운용에서 성능을 무효화할 수 있다.

데이터 증강(Data Augmentation)은 학습 샘플에 통제된 변형을 적용하여 모델의 강인성(Robustness)을 높일 수 있다. 카메라 데이터(Camera Data)는 밝기(Brightness), 대비(Contrast), 흐림(Blur), 자르기(Crop), 크기 변경(Scale), 노이즈(Noise), 그림자(Shadow), 날씨, 가림 등을 적용할 수 있다. 포인트 클라우드는 회전(Rotation), 이동(Translation), 점 제거(Dropout), 노이즈, 밀도 변화(Density Change), 센서 인공물(Sensor Artifact) 등을 사용할 수 있다. 증강은 실제 현장에서 발생 가능한 조건을 반영해야 하며, 비현실적인 변형은 클래스 의미를 왜곡하거나 잘못된 동작을 학습시킬 수 있다.

증강 파라미터(Augmentation Parameter)는 모든 실험과 함께 기록되어야 한다. 동일한 데이터셋과 모델 구조를 사용하더라도 증강 확률(Probability), 강도(Intensity), 적용 순서(Order), 난수 시드에 따라 결과는 크게 달라질 수 있다. 실험 추적 시스템은 어떤 변환이 적용되었는지, 학습에만 사용되었는지, 검증에도 적용되었는지를 기록해야 한다. 특정 증강 전략이 어떤 시나리오에서는 성능을 높이지만 다른 시나리오에서는 성능을 저하시킬 수 있으므로 시나리오 수준의 평가를 함께 수행해야 한다. 이러한 근거는 데이터 증강을 무작위 요소가 아니라 체계적인 엔지니어링 활동으로 발전시키는 데 도움을 준다.

모델 아키텍처(Model Architecture)의 선택은 작업(Task), 대상 하드웨어(Target Hardware), 지연 시간 예산(Latency Budget), 메모리 용량(Memory Capacity), 요구 정확도(Required Accuracy)를 반영해야 한다. 대형 모델은 오프라인에서는 높은 성능을 보일 수 있지만 추론 지연(Inference Delay), 전력 소비(Power Consumption), 열 부하(Thermal Load) 때문에 임베디드 로봇 컴퓨터에는 적합하지 않을 수 있다. 벤치마크 정확도가 약간 낮더라도 빠른 응답성과 플릿 확장성(Fleet Scalability)이 더 중요한 경우에는 경량 모델(Compact Architecture)이 더 적합하다. 실험에는 모델 계열(Model Family), 계층 구성(Layer Configuration), 입력 해상도(Input Resolution), 파라미터 수(Parameter Count), 계산 복잡도(Computational Complexity), 구조 변경 사항(Architectural Modification)이 기록되어야 한다.

사전학습 모델(Pretrained Model)은 원본 표현(Source Representation)이 로봇 작업과 관련성이 있다면 학습 시간을 줄이고 성능을 향상시킬 수 있다. 그러나 사전학습 가중치(Pretrained Weight)의 출처(Origin), 라이선스(License), 학습 도메인(Training Domain), 아키텍처, 보안(Security)은 반드시 문서화되어야 한다. 인터넷 일반 영상으로 학습된 모델은 산업 현장, 물류창고, 실외 환경, 안전이 중요한 환경을 충분히 대표하지 못할 수 있다. 초기 계층 고정(Freezing Early Layers), 점진적 해제(Gradual Unfreezing), 차등 학습률(Differential Learning Rate), 전체 재학습(Full Retraining) 등의 미세조정(Fine-Tuning) 전략을 실험적으로 비교해야 한다. 사전학습이 현장 일반화(Field Generalization)를 자동으로 보장한다고 가정해서는 안 된다.

하이퍼파라미터(Hyperparameter)는 모델이 학습하는 방식을 정의하며 구조화된 설정(Configuration)으로 관리되어야 한다. 학습률(Learning Rate), 최적화기(Optimizer), 모멘텀(Momentum), 가중치 감소(Weight Decay), 배치 크기(Batch Size), 에포크(Epoch) 수, 스케줄러(Scheduler), 워밍업(Warm-Up), 손실 가중치(Loss Weight), 정규화(Regularization), 그래디언트 클리핑(Gradient Clipping), 조기 종료(Early Stopping) 조건 등이 포함된다. 이러한 설정은 노트북이나 코드 내부에 숨겨져 있어서는 안 되며, 별도의 설정 파일(Configuration File)로 저장되어 다른 엔지니어가 동일한 실험을 재현할 수 있어야 한다. 하이퍼파라미터 변경은 실험 비교에서 명확하게 표시되어야 한다.

손실 함수(Loss Function)는 수학적 문제뿐 아니라 실제 운용에서 오류가 미치는 영향을 함께 고려해야 한다. 객체 검출(Object Detection)에서는 보행자를 놓치는 것(Missed Pedestrian)이 일부 추가적인 오검출(False Positive)보다 훨씬 심각할 수 있다. 주행 가능성 추정(Traversability Estimation)에서는 위험한 지면을 주행 가능하다고 판단하는 것이 보수적으로 거부하는 것보다 더 위험하다. 클래스 가중치(Class Weight), 초점 손실(Focal Loss), 경계 손실(Boundary Loss), 불확실성 기반 손실(Uncertainty-Aware Loss), 다중 작업 목적 함수(Multi-Task Objective)를 이러한 우선순위를 반영하도록 사용할 수 있다. 실험 기록에는 손실 함수가 어떻게 결합되었고 왜 해당 가중치를 선택했는지가 설명되어야 한다.

배치 크기(Batch Size)는 최적화(Optimization), 메모리 사용량(Memory Usage), 학습 속도(Training Speed)에 영향을 준다. 큰 배치는 하드웨어 활용률을 높일 수 있지만 학습률 조정이 필요하며 일반화 성능이 감소할 수도 있다. 작은 배치는 고해상도 이미지나 포인트 클라우드 처리에 적합하지만 그래디언트(Gradient)의 변동성이 커지고 학습 속도가 느려질 수 있다. 그래디언트 누적(Gradient Accumulation)은 메모리가 제한된 환경에서 큰 배치 효과를 구현하는 데 사용할 수 있다. 실제 배치 크기(Effective Batch Size), 장치 수(Number of Devices), 누적 단계(Accumulation Step), 분산 학습(Distributed Training) 설정은 모두 기록되어야 한다.

무작위성(Randomness)은 가능한 한 통제되어야 한다. 가중치 초기화(Weight Initialization), 데이터 셔플(Data Shuffling), 증강(Augmentation), 샘플링(Sampling), 드롭아웃(Dropout), 병렬 계산(Parallel Computation)은 실행마다 다른 결과를 만들 수 있다. 난수 시드(Random Seed)를 고정하면 반복성이 향상되지만 일부 GPU 연산과 분산 시스템은 여전히 비결정적(Non-Deterministic)일 수 있다. 실험 기록에는 시드 값, 프레임워크 설정, 알려진 비결정적 연산을 포함해야 한다. 중요한 결론은 하나의 성공적인 실행이 아니라 반복 실험을 기반으로 도출되어야 한다.

소프트웨어 환경(Software Environment)은 정확하게 기록되어야 한다. 프레임워크 버전(Framework Version), CUDA 라이브러리, 드라이버, 운영체제, Python 패키지, 컴파일러 설정, 컨테이너 이미지(Container Image), 사용자 정의 확장(Custom Extension)은 학습과 수치 결과에 영향을 줄 수 있다. 특정 환경에서 정상적으로 학습된 모델도 의존성(Dependency)이 변경되면 다른 결과를 생성하거나 실행되지 않을 수 있다. 컨테이너, 잠금 파일(Lock File), 환경 매니페스트(Environment Manifest), 산출물 저장소(Artifact Repository)는 공식 실험의 실행 환경을 보존하는 데 활용되어야 한다.

학습에 사용된 소스 코드(Source Code) 버전도 반드시 기록해야 한다. 각 실험은 소스 제어(Source Control)의 커밋(Commit), 브랜치(Branch), 태그(Tag), 또는 패키징된 코드 산출물(Packaged Code Artifact)을 참조해야 한다. 공식 실험에서는 커밋되지 않은 로컬 수정(Local Modification)을 사용하지 않는 것이 원칙이며, 불가피한 경우에는 패치(Patch) 형태로 함께 저장해야 한다. 학습 파이프라인은 작업 디렉터리(Working Directory)의 상태와 사용된 설정 파일(Configuration File)도 기록해야 한다. 데이터셋과 하이퍼파라미터를 알고 있더라도 코드 계보(Code Lineage)가 없으면 실험은 재현될 수 없다.

연산 하드웨어(Computing Hardware)도 학습 결과와 비용에 영향을 준다. 실험 추적 시스템은 GPU 또는 가속기(Accelerator)의 종류, 개수, 메모리, CPU, 시스템 메모리, 저장장치(Storage), 네트워크, 분산 학습 토폴로지(Distributed Training Topology)를 기록해야 한다. 혼합 정밀도(Mixed Precision), 텐서 코어(Tensor Core), 데이터 로더(Data Loader) 워커 수, 인터커넥트(Interconnect) 구성도 학습 속도와 수치 안정성에 영향을 줄 수 있다. 이러한 정보는 효율성 비교, 향후 자원 계획, 특정 하드웨어 의존성 분석에 활용된다.

학습 파이프라인은 공통 작업을 일관되게 수행할 수 있도록 자동화되어야 한다. 일반적인 파이프라인은 데이터셋을 가져오고, 설정을 검증하고, 환경을 준비하고, 학습을 시작하고, 체크포인트(Checkpoint)를 저장하고, 중간 모델을 평가하고, 지표(Metric)를 생성하고, 산출물을 저장하며, 결과를 등록한다. 자동화는 수작업 오류를 줄이고 대규모 실험을 효율적으로 관리할 수 있게 한다. 그러나 파이프라인은 입력, 처리 단계, 로그(Log)를 투명하게 제공해야 하며 실패 시 원인이 데이터인지, 코드인지, 인프라인지, 모델 자체인지 명확히 보여주어야 한다.

체크포인트 관리(Checkpoint Management)는 장시간 또는 고비용 학습에서 매우 중요하다. 주기적인 체크포인트는 중단된 학습을 이어서 수행할 수 있게 하고, 학습 단계별 비교도 가능하게 한다. 저장 시점은 시간, 에포크, 성능 향상, 또는 고정 간격에 따라 정의될 수 있다. 모든 체크포인트를 영구 보관할 필요는 없지만 최종 모델, 최고 성능 모델, 분석에 중요한 모델은 보존되어야 한다. 체크포인트 메타데이터(Checkpoint Metadata)는 학습 단계, 성능 지표, 최적화기 상태(Optimizer State), 스케줄러 상태(Scheduler State), 호환성 정보를 포함해야 한다.

조기 종료(Early Stopping)는 검증 성능이 향상되지 않을 때 불필요한 연산을 줄이고 과적합(Overfitting)을 방지할 수 있다. 그러나 어떤 지표를 사용할지, 허용 기간(Patience), 최소 향상값(Minimum Improvement), 평가 주기를 신중하게 선택해야 한다. 평균 검증 성능이 향상되더라도 안전에 중요한 특정 시나리오에서는 성능이 저하될 수 있다. 따라서 하나의 평균 지표만으로 조기 종료를 결정해서는 안 되며 여러 지표를 함께 관리해야 한다. 종료 규칙은 명확하고 재현 가능해야 한다.

분산 학습(Distributed Training)은 학습 시간을 단축할 수 있지만 복잡성도 증가시킨다. 데이터 병렬(Data Parallel) 또는 모델 병렬(Model Parallel) 방식은 실제 배치 크기, 동기화(Synchronization), 샘플링, 수치 동작을 변경할 수 있다. 네트워크 장애, 워커 불균형(Worker Imbalance), 초기화 오류는 전체 학습을 실패하게 만들 수 있다. 실험에는 노드(Node) 수, 장치 배치(Device Assignment), 통신 백엔드(Communication Backend), 그래디언트 동기화, 장애 복구(Fault Recovery) 설정이 기록되어야 한다.

실험 추적(Experiment Tracking)은 모든 실행(Run)에 고유 식별자(Unique Identifier)를 부여해야 한다. 각 기록은 프로젝트(Project), 사용자(User), 코드(Code), 데이터셋(Dataset), 설정(Configuration), 하드웨어, 실행 환경(Environment), 시작 및 종료 시간, 상태(Status), 지표(Metric), 체크포인트, 보고서, 로그를 연결해야 한다. 실패하거나 취소된 실행도 삭제하지 말고 유지해야 한다. 이러한 기록은 불안정한 설정이나 비효율적인 접근 방법을 이해하는 데 중요한 근거가 된다.

실행 이름(Run Name)과 태그(Tag)는 일관된 규칙을 따라야 한다. 태그에는 작업(Task), 모델 계열(Model Family), 데이터셋 버전, 현장(Site), 센서 구성, 실험 목적, 브랜치, 최적화 방식, 릴리스 대상 등이 포함될 수 있다. 자유로운 이름만으로는 검색과 비교가 어렵기 때문에 구조화된 태그가 필요하다. 이를 통해 아키텍처, 데이터 버전, 증강 전략, 대상 하드웨어 등을 기준으로 실험을 쉽게 비교할 수 있다.

성능 지표(Metric)는 학습 종료 시점뿐 아니라 전체 학습 과정에서 기록되어야 한다. 학습 손실(Training Loss), 검증 손실(Validation Loss), 학습률, 그래디언트 노름(Gradient Norm), 정밀도(Precision), 재현율(Recall), 클래스별 성능, 위치 오차, 예상 지연 시간, 자원 사용량을 지속적으로 기록하면 과적합이나 불안정성을 쉽게 발견할 수 있다. 기록 주기는 분석 가치와 저장 비용 사이의 균형을 고려해야 하며 모든 프로젝트에서 동일한 이름과 단위를 사용하는 것이 바람직하다.

전체 평균 성능(Global Metric)뿐 아니라 시나리오별(Scenario-Specific) 및 클래스별(Class-Specific) 평가도 함께 수행되어야 한다. 평균 정확도가 높더라도 작은 보행자, 반사 물체, 저조도, 비, 원거리 객체, 부분 가림, 특수 노면에서 성능이 크게 저하될 수 있다. 따라서 로봇 모델 검증은 운용 조건별 성능을 보고해야 한다. 실험 추적 시스템은 혼동 행렬(Confusion Matrix), 정밀도-재현율 곡선(Precision-Recall Curve), 거리 구간(Distance Bin), 환경별 성능 분석, 실패 사례(Failure Case)를 저장해야 한다.

정성적 산출물(Qualitative Artifact)은 모델의 동작을 이해하는 데 매우 중요하다. 객체 검출 결과(Detection Overlay), 분할 결과(Segmentation Image), 포인트 클라우드 시각화(Point-Cloud Visualization), 궤적(Trajectory), 어텐션 맵(Attention Map), 오검출(False Positive), 미검출(False Negative), 어려운 장면 요약(Difficult Scene Summary)은 숫자로 표현되지 않는 문제를 보여준다. 실험 추적 시스템은 원본 샘플과 연결된 대표 사례를 함께 저장해야 한다. 가장 좋은 사례뿐 아니라 일반적인 사례와 실패 사례도 함께 포함되어야 하며, 정성적 평가는 정량적 평가를 보완하는 역할을 수행해야 한다.

학습 안정성(Training Stability)은 수치적 지표와 시스템 지표를 함께 모니터링해야 한다. 그래디언트 폭주(Exploding Gradient), 그래디언트 소실(Vanishing Gradient), NaN 값, 갑작스러운 손실 증가, 메모리 누수(Memory Leak), 데이터 로더 정지(Data-Loader Stall), 하드웨어 오류, 체크포인트 손상은 실험을 무효화할 수 있다. 자동 경고(Alert)는 중요한 이상이 발생하면 학습을 중단하거나 표시해야 한다. 추적 시스템은 진단 로그(Diagnostic Log)와 최근 성능 지표를 함께 저장하여 원인 분석을 지원해야 한다.

검증(Validation)은 고정된 데이터셋과 표준화된 평가 코드(Standardized Evaluation Code)를 사용해야 한다. 평가 스크립트가 변경되면 모델이 실제로 개선되었는지 비교하기 어렵다. 평가기는 버전 관리되어야 하며 임계값(Threshold), 매칭 규칙(Matching Rule), 좌표계(Coordinate Convention), 무시 영역(Ignored Region), 불확실성 처리(Uncertainty Handling)를 명확하게 정의해야 한다. 평가 로직이 변경되면 이전 모델도 다시 평가하여 공정성을 유지해야 한다.

시험 데이터(Test Data)는 반복적인 최적화 대상으로 사용되어서는 안 된다. 최종 시험 세트를 반복적으로 확인하면 개발 과정이 간접적으로 시험 데이터에 과적합될 수 있다. 일상적인 모델 개발은 학습 및 검증 데이터로 수행하고, 시험 데이터는 주요 마일스톤(Milestone), 공식 릴리스, 성능 비교에서만 사용해야 한다. 보호된 시험 데이터는 접근 권한을 제한하거나 자동화된 방식으로 관리할 수 있다.

기준 모델(Baseline Model)은 발전 정도를 평가하기 위한 안정적인 기준이다. 현재 운영 모델, 단순 알고리즘, 이전 릴리스, 동일 데이터셋으로 학습된 표준 모델이 기준이 될 수 있다. 모든 후보 모델은 동일한 평가 절차를 통해 기준 모델과 비교되어야 한다. 평균 정확도뿐 아니라 지연 시간, 메모리, 운용 시나리오, 장애 사례도 함께 비교해야 한다. 특정 지표가 향상되더라도 안전에 중요한 성능이 저하되면 더 우수한 모델이라고 판단해서는 안 된다.

소거 연구(Ablation Study)는 실제 성능 향상에 기여하는 요소를 확인하는 데 사용된다. 특정 특징, 증강 기법, 손실 함수, 센서 입력, 아키텍처 모듈, 데이터셋 일부를 제거한 후 결과를 비교할 수 있다. 실험 추적은 관련 실험을 체계적으로 관리하고 설정 차이를 쉽게 비교할 수 있게 한다. 이를 통해 직관에 의존한 불필요한 복잡성을 제거하고 성능 향상이 데이터, 구조, 전처리, 학습 전략 중 어디에서 비롯되었는지를 분석할 수 있다.

하이퍼파라미터 탐색(Hyperparameter Search)은 수동 방식, 격자 탐색(Grid Search), 무작위 탐색(Random Search), 베이지안 최적화(Bayesian Optimization), 집단 기반 방법(Population-Based Method)으로 수행할 수 있다. 자동 탐색도 제한된 자원과 파라미터 범위 안에서 이루어져야 한다. 모든 실험은 동일한 데이터셋과 평가 방식을 사용해야 하며, 검색 과정에서 생성되는 수많은 실험은 태그, 그룹, 보존 정책으로 관리되어야 한다. 최고의 성능을 보인 하나의 실행만으로 모델을 선택해서는 안 되며 강인성(Robustness), 분산(Variance), 자원 사용량도 함께 평가해야 한다.

학습 결과의 변동성이 큰 경우 반복 실험(Repeated Trial)이 중요하다. 한 번 우수한 성능을 보인 설정도 반복해서 동일한 결과를 내지 못할 수 있다. 여러 난수 시드를 사용한 반복 실행은 성능 분포를 제공하고 개선 효과의 신뢰도를 높인다. 실험 추적 시스템은 평균, 분산, 최고 성능, 최저 성능을 함께 요약해야 한다.

클래스 불균형(Class Imbalance)은 의도적으로 처리해야 한다. 희귀하지만 안전에 중요한 클래스는 데이터가 부족한 반면 일반 배경이나 흔한 장애물은 과도하게 많을 수 있다. 샘플링 전략(Sampling Strategy), 클래스 가중치, 초점 손실(Focal Loss), 목표 증강(Targeted Augmentation), 어려운 사례 학습(Hard-Example Mining), 추가 데이터 수집 등을 사용할 수 있다. 선택된 방법은 모두 기록되고 비교되어야 하며, 희귀 클래스의 재현율이 향상될 때 발생하는 오검출 증가도 함께 평가해야 한다.

어려운 사례 학습(Hard-Example Mining)은 모델이 자주 틀리거나 낮은 신뢰도로 예측하는 샘플에 집중한다. 가림, 작은 객체, 특수 조명, 센서 오류, 복잡한 배경 등이 대상이 될 수 있다. 이러한 사례는 기존 데이터셋에서 선택하거나 새로운 현장 수집(Field Collection)을 통해 확보할 수 있다. 선택 규칙과 데이터셋 버전도 함께 기록되어야 하며, 특정 어려운 사례만 과도하게 학습하여 과적합되지 않도록 일반 데이터와 균형을 유지해야 한다.

전이 학습(Transfer Learning)은 어떤 계층이 재사용되고, 고정되고, 다시 초기화되며, 미세조정(Fine-Tuning)되었는지를 명확히 구분해야 한다. 사전학습 계층과 신규 계층은 서로 다른 학습률을 사용할 수 있다. 도메인 적응(Domain Adaptation)은 라벨이 없는 데이터(Unlabeled Data), 적대적 학습(Adversarial Objective), 자기 학습(Self-Training), 특징 정렬(Feature Alignment)을 사용할 수도 있다. 이러한 선택은 모두 성능과 안정성에 영향을 주므로 실험 기록에 포함되어야 한다.

자기지도학습(Self-Supervised Learning)과 준지도학습(Semi-Supervised Learning)은 대량의 라벨 없는 로봇 데이터를 활용하여 수작업 라벨 의존성을 줄일 수 있다. 사전 과제(Pretext Task), 대조 학습(Contrastive Learning), 마스킹 예측(Masked Prediction), 의사 라벨(Pseudo-Label), 일관성 학습(Consistency Training)이 활용될 수 있다. 그러나 자동 생성된 라벨은 체계적인 오류(Systematic Error)를 포함할 수 있으므로 데이터 출처, 신뢰도 기준(Confidence Threshold), 교사 모델(Teacher Model), 반복 과정(Iteration Step)을 함께 기록해야 한다.

다중 작업 학습(Multi-Task Learning)은 객체 검출, 분할, 깊이 추정, 움직임 예측, 주행 가능성 추정 등을 하나의 모델에서 함께 수행할 수 있다. 공유 표현(Shared Representation)은 효율성을 높일 수 있지만 작업 간 간섭(Task Interference)이 발생할 수도 있다. 손실 가중치, 작업 샘플링(Task Sampling), 공유 계층, 작업별 출력(Task-Specific Head), 그래디언트 균형(Gradient Balancing)을 모두 추적해야 한다. 모든 작업의 성능을 개별적으로 보고해야 하며 독립 모델과의 실행 시간(Runtime) 및 복잡성도 비교해야 한다.

교육 과정 학습(Curriculum Learning)은 쉬운 데이터부터 어려운 데이터 순서로 학습시키는 방법이다. 예를 들어 밝은 낮 장면에서 시작하여 저조도, 가림, 악천후, 희귀 객체를 점진적으로 추가할 수 있다. 학습 단계(Curriculum Schedule), 난이도 정의(Difficulty Definition), 전환 기준(Transition Criteria), 데이터셋 구성도 기록해야 한다. 이러한 방식은 수렴을 개선할 수 있지만 실제 운용 환경을 제대로 반영하는지 시나리오 수준에서 검증해야 한다.

모델 압축(Model Compression)은 로봇 배포 제약을 만족시키기 위해 학습 중 또는 이후에 수행될 수 있다. 가지치기(Pruning), 양자화 인식 학습(Quantization-Aware Training), 지식 증류(Knowledge Distillation), 저랭크 적응(Low-Rank Adaptation), 아키텍처 축소(Architecture Reduction)를 사용할 수 있다. 압축 모델은 정확도뿐 아니라 안정성, 하드웨어 성능까지 원본 모델과 비교되어야 하며 독립적인 산출물로 관리되어야 한다.

지식 증류(Knowledge Distillation)는 큰 교사 모델(Teacher Model)의 출력을 이용해 작은 학생 모델(Student Model)을 학습시키는 방법이다. 실험에는 교사 모델 버전, 학생 모델 구조, 온도(Temperature), 증류 손실(Distillation Loss), 실제 정답 손실(Ground-Truth Loss), 데이터 버전, 가중치 전략이 기록되어야 한다. 학생 모델은 더 작은 연산량으로 유사한 성능을 제공할 수 있지만 교사 모델의 오류도 함께 전달받을 수 있으므로 독립 모델과 함께 비교 평가해야 한다.

신뢰도 보정(Confidence Calibration)은 로봇이 모델 신뢰도를 기반으로 대체 동작(Fallback), 사람 개입(Human Assistance), 보수적 경로 계획(Conservative Planning)을 수행하는 경우 매우 중요하다. 높은 정확도를 가진 모델도 잘못된 신뢰도를 출력할 수 있다. 신뢰도 다이어그램(Reliability Diagram), 기대 보정 오차(Expected Calibration Error), 임계값 곡선(Threshold Curve), 시나리오별 신뢰도 분석을 함께 기록해야 한다. 보정 기법(Calibration Method)은 모델과 함께 버전 관리되어야 한다.

후보 모델은 자원 프로파일링(Resource Profiling)도 함께 수행해야 한다. 대상 엣지 컴퓨터(Edge Computer) 또는 대표 하드웨어에서 추론 지연(Inference Latency), 처리량(Throughput), 메모리, CPU 및 GPU 사용률(Utilization), 온도, 전력, 시작 시간을 측정해야 한다. 실험 추적은 오프라인 학습 결과와 실제 배포 성능을 연결하여 정확도뿐 아니라 실제 운용 적합성까지 평가할 수 있도록 해야 한다.

종단 간 평가(End-to-End Evaluation)는 전체 처리 체인을 검증해야 한다. 센서 입력, 디코딩(Decoding), 전처리, 모델 추론, 후처리, 메시지 발행(Message Publication), 융합(Fusion), 후속 로봇 제어까지 모두 포함된다. 신경망 추론 속도만 만족한다고 전체 시스템이 빠르게 동작하는 것은 아니다. 전체 파이프라인 지연(Total Pipeline Latency)을 현실적인 시스템 부하에서 평가해야 한다.

실험 비교(Experiment Comparison)는 설정과 결과 차이를 쉽게 이해할 수 있어야 한다. 엔지니어는 코드, 데이터셋, 전처리, 모델 구조, 하이퍼파라미터, 성능 지표, 산출물, 하드웨어, 비용을 동시에 비교할 수 있어야 한다. 비교 도구는 시나리오와 배포 제약에 따라 필터링을 지원해야 하며, 정확도, 희귀 사례 성능, 지연 시간, 에너지, 메모리 등 여러 기준을 함께 고려해야 한다.

후보 모델을 다음 단계로 승격(Promotion)하기 전에 명확한 승격 기준(Promotion Criteria)을 정의해야 한다. 최소 정확도, 중요 클래스 성능 저하 없음, 허용 가능한 지연 시간, 안정적인 학습, 문서화 완료, 데이터셋 승인, 기준 모델과의 비교 결과 등을 포함할 수 있다. 일부 모델은 반복 실험이나 특정 시나리오 기준도 만족해야 한다. 승격 결정은 검토자, 근거, 조건, 알려진 제한 사항과 함께 기록되어야 한다.

실패한 실험(Failed Experiment)도 충분한 정보를 포함하여 보존해야 한다. 수렴 실패(Poor Convergence), 불안정한 손실(Unstable Loss), 잘못된 라벨, 입력 형상 오류(Input Shape Error), 메모리 부족, 전처리 오류, 인프라 장애 등 다양한 원인이 존재한다. 추적 시스템은 기술적 실패와 잘못된 모델링 가설(Modeling Hypothesis)을 구분해야 한다. 실패 기록은 같은 실수를 반복하지 않도록 하는 중요한 자산이다.

비용 추적(Cost Tracking)은 실험 계획을 개선하는 데 도움이 된다. GPU 사용 시간(GPU Hour), 저장 공간, 네트워크 전송, 라벨링 비용, 엔지니어 작업 시간을 프로젝트와 실험별로 관리할 수 있다. 대규모 탐색은 막대한 자원을 사용할 수 있으므로 비용 대비 가치도 함께 고려해야 한다. 그러나 비용 절감을 위해 검증이나 안전을 희생해서는 안 된다.

접근 제어(Access Control)와 보안(Security)은 데이터셋, 코드, 모델, 실험 기록을 보호해야 한다. 프로젝트에는 고객 기밀 정보(Customer Confidential Data), 안전 사고, 독점 알고리즘(Proprietary Algorithm), 제한된 모델 가중치가 포함될 수 있다. 사용자 권한은 역할(Role)에 따라 부여되어야 하며 민감한 산출물은 암호화와 감사 로그(Audit Log)를 적용해야 한다. 학습 파이프라인(Service Account)도 최소 권한으로 운영되어야 한다.

개인정보 보호(Privacy)는 학습 데이터와 결과에도 그대로 적용되어야 한다. 데이터셋 메타데이터는 사용 목적, 지역 제한, 익명화 상태, 보존 기간, 고객 조건을 포함해야 한다. 학습 파이프라인은 제한된 데이터가 허가되지 않은 환경으로 복사되지 않도록 해야 한다. 시각화 자료도 개인정보 보호를 위해 마스킹(Masking)이 필요할 수 있으며, 모델 산출물도 민감한 정보를 포함할 가능성이 있으므로 적절히 관리되어야 한다.

문서화(Documentation)는 실험 기록을 기반으로 지속적으로 생성되어야 한다. 후보 모델 요약(Model Summary)은 목적, 데이터셋 계보(Dataset Lineage), 모델 구조, 학습 설정, 평가 결과, 시나리오별 성능, 자원 사용량, 제한 사항, 승인 상태를 포함할 수 있다. 자동 생성된 정보는 오류를 줄이고, 엔지니어는 해석과 운용 경고를 추가한다. 이러한 자료는 이후 모델 카드(Model Card), 검증 보고서, 릴리스 패키지 작성에도 활용될 수 있다.

실험 정보가 중앙화(Centralized)되면 협업(Collaboration)이 크게 향상된다. AI 엔지니어, 데이터 엔지니어, 로봇 엔지니어, 안전 검토자, 프로젝트 관리자는 동일한 실험 기록을 기준으로 논의할 수 있다. 댓글(Comment), 검토 상태(Review Status), 비교 결과, 결함 연결 정보는 중복 작업을 줄인다. 중요한 결론은 단순 토론이 아니라 공식 기록(Formal Note), 보고서, 승격 결정으로 남겨야 한다.

성숙한 모델 학습(Model Training) 및 실험 추적(Experiment Tracking) 시스템은 통제된 데이터셋, 재현 가능한 파이프라인(Reproducible Pipeline), 소스 코드, 실행 환경, 하드웨어, 성능 지표, 산출물, 평가, 승인 절차를 하나의 추적 가능한 프로세스로 연결한다. 이를 통해 어떤 모델이 가장 우수한지만이 아니라 왜 더 우수했는지, 어떤 조건에서 신뢰할 수 있는지, 어떤 자원이 필요한지, 결과를 다시 재현할 수 있는지를 명확하게 이해할 수 있다. 이러한 체계적인 접근은 자율이동로봇(AMR) 개발 팀이 안전성, 운용 적합성, 보안, 엔지니어링 책임성을 유지하면서 머신러닝 시스템을 지속적으로 발전시킬 수 있도록 지원한다.

## 15.03 Model Registry and Version Control

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

모델 레지스트리(Model Registry)와 버전 관리 시스템(Version Control System)은 모든 머신러닝 모델(Machine Learning Model)이 전체 운용 수명주기(Operational Lifetime) 동안 고유하게 식별되고, 추적되며, 검증되고, 배포되고, 모니터링되며, 재현될 수 있도록 보장하는 로봇 머신러닝 운영(Robot MLOps)의 핵심 거버넌스(Governance) 기반이다. 자율이동로봇(Autonomous Mobile Robot, AMR) 개발에서는 인지(Perception), 위치추정(Localization), 지도 작성(Mapping), 예측(Prediction), 내비게이션(Navigation), 이상 탐지(Anomaly Detection), 의사결정 지원(Decision Support)을 위한 수십 개에서 수백 개의 모델 변형(Model Variant)이 동시에 존재할 수 있다. 체계적인 레지스트리가 없으면 엔지니어는 어떤 모델이 어떤 데이터셋에서 학습되었고, 어떤 조건에서 검증되었으며, 어떤 로봇에 배포되었고, 어떤 운용 동작에 영향을 미쳤는지를 빠르게 파악할 수 없게 된다. 따라서 모델 레지스트리는 머신러닝 산출물(Machine Learning Artifact)에 대한 공식적인 단일 진실 공급원(Authoritative Source of Truth) 역할을 수행한다.

모델 레지스트리는 일반적인 파일 저장소(File Storage)와 근본적으로 다르다. 모델 가중치(Model Weight)를 단순히 폴더나 클라우드 저장소에 저장하면 이진 파일(Binary Artifact)은 보존될 수 있지만, 신뢰할 수 있는 수명주기 관리(Lifecycle Management)에 필요한 엔지니어링 맥락(Engineering Context)은 유지되지 않는다. 모델 레지스트리는 모델 식별자(Model Identifier), 버전(Version), 아키텍처(Architecture), 데이터셋 계보(Dataset Lineage), 학습 설정(Training Configuration), 실험 이력(Experiment History), 평가 보고서(Evaluation Report), 실행 환경 요구사항(Runtime Requirement), 배포 상태(Deployment Status), 승인 기록(Approval Record), 운용 제한사항(Operational Limitation) 등을 구조화된 메타데이터(Structured Metadata)와 함께 저장한다. 다시 말해 레지스트리는 단순한 파일이 아니라 모델 전체의 엔지니어링 지식(Engineering Knowledge)을 관리하는 시스템이다.

버전 관리(Version Control)는 시간에 따른 변경 사항을 체계적으로 관리하는 메커니즘(Mechanism)이다. 성능 향상, 오류 수정, 최적화, 재학습(Retraining), 아키텍처 변경, 보정(Calibration) 수정, 배포 패키지(Deployment Package) 변경이 발생할 때마다 기존 모델을 덮어쓰는 대신 새로운 버전을 생성해야 한다. 이전 버전은 항상 접근 가능해야 한다. 운영 중 발생한 사고, 고객 지원(Customer Support), 규제 조사(Regulatory Investigation), 과학적 검증(Scientific Validation) 과정에서는 과거 모델의 동작을 정확히 재현해야 할 수도 있기 때문이다. 변경 불가능한 버전(Immutable Version)은 승인된 모델과 실제 배포된 모델이 동일하다는 신뢰를 제공한다.

등록된 모든 모델은 수명주기 전체에서 유지되는 전역 고유 식별자(Globally Unique Identifier)를 가져야 한다. 버전 번호는 변경되더라도 논리적인 모델 식별(Logical Model Identity)은 변하지 않는다. 이를 통해 엔지니어는 하나의 인지 모델이나 내비게이션 예측기(Navigation Predictor)의 발전 과정을 추적하면서도 각각의 릴리스(Release)를 명확하게 구분할 수 있다. 사람이 읽기 쉬운 이름(Human-Readable Name)은 편리성을 제공하지만 내부 식별자는 프로젝트, 저장소, 조직, 배포 환경 전체에서 중복되지 않는 기계 친화적(Machine-Stable)인 식별자를 사용해야 한다.

모델 버전 번호(Model Version Number)는 조직 전체에서 일관된 정책에 따라 관리되어야 한다. 일부 조직은 메이저(Major), 마이너(Minor), 패치(Patch)로 구성된 시맨틱 버전(Semantic Versioning)을 사용하며, 다른 조직은 순차적인 빌드 번호(Build Identifier)나 릴리스 기반 명명 규칙을 사용할 수도 있다. 어떤 방식이든 각 버전 증가의 의미는 명확하게 정의되어야 한다. 메이저 버전은 아키텍처 재설계, 마이너 버전은 새로운 데이터셋을 이용한 재학습, 패치 버전은 모델 동작을 변경하지 않는 패키징이나 메타데이터 수정 등을 의미할 수 있다. 중요한 것은 특정 방식이 아니라 일관성을 유지하는 것이다.

모델 레지스트리는 논리적인 모델(Logical Model)과 실제 배포 패키지(Deployment Package)를 구분해야 한다. 하나의 학습된 모델은 여러 종류의 하드웨어 가속기(Hardware Accelerator), 운영체제(Operating System), 실행 엔진(Runtime Engine), 정밀도 모드(Precision Mode), 로봇 플랫폼(Robot Platform)에 맞게 여러 개의 배포 산출물로 변환될 수 있다. 예를 들어 하나의 인지 모델은 PyTorch 체크포인트(Checkpoint), ONNX 표현, 여러 GPU용 TensorRT 엔진, 임베디드 가속기용 최적화 패키지 등으로 존재할 수 있다. 이러한 배포 패키지는 동일한 논리 모델 버전을 참조하지만 각각의 패키징 메타데이터와 호환성 정보를 별도로 유지해야 한다.

모델 계보(Model Lineage)는 하나의 모델이 어떤 엔지니어링 산출물에서 생성되었는지를 설명한다. 등록된 모델은 학습 데이터셋 버전, 전처리 파이프라인(Preprocessing Pipeline), 소스 코드 수정 버전(Source Code Revision), 학습 설정, 실험 식별자(Experiment Identifier), 사전학습 가중치(Pretrained Weight), 미세조정(Fine-Tuning) 이력, 부모 모델(Parent Model)을 참조해야 한다. 이러한 계보는 단순한 파일 목록이 아니라 방향성을 가진 엔지니어링 그래프(Directed Engineering Graph)를 형성한다. 예상하지 못한 모델 동작이 발생하면 엔지니어는 문서를 뒤지는 대신 등록된 모델의 전체 계보를 즉시 추적할 수 있다.

데이터셋 계보(Dataset Lineage)도 동일하게 중요하다. 머신러닝 모델의 동작은 학습 데이터에 크게 의존하기 때문이다. 모델 레지스트리는 정확히 어떤 데이터셋 릴리스(Dataset Release), 온톨로지 버전(Ontology Version), 주석 정책(Annotation Policy), 전처리 설정, 데이터 증강 전략(Augmentation Strategy), 학습·검증·시험 데이터 분할을 사용했는지를 기록해야 한다. 여러 데이터셋 버전이 존재하는 경우 성능 향상이 새로운 데이터 때문인지, 수정된 라벨 때문인지, 향상된 전처리 때문인지, 알고리즘 개선 때문인지를 즉시 분석할 수 있어야 한다. 이러한 데이터 계보는 모델 간의 공정한 비교를 가능하게 한다.

학습 설정(Training Configuration)은 모델과 함께 반드시 보존되어야 한다. 학습률(Learning Rate), 최적화기(Optimizer), 스케줄러(Scheduler), 배치 크기(Batch Size), 손실 함수(Loss Function), 클래스 가중치(Class Weight), 데이터 증강 설정, 난수 시드(Random Seed), 분산 학습(Distributed Training) 설정, 조기 종료(Early Stopping) 조건, 하드웨어 정보는 모두 최종 모델 동작에 영향을 준다. 단순히 모델 가중치만 저장하는 레지스트리는 재현성(Reproducibility) 측면에서 큰 의미가 없다. 완전한 설정 기록은 동일한 실험을 다시 수행하거나 원인을 분석하는 데 필수적이다.

실험 추적(Experiment Tracking)과 모델 등록(Model Registration)은 밀접하게 연결되지만 서로 다른 목적을 가진다. 실험 추적은 실패한 실행(Failed Run), 탐색적 실험(Exploratory Experiment), 진단 실험(Diagnostic Experiment)을 포함한 모든 실행을 기록한다. 반면 모델 레지스트리는 실제 엔지니어링 자산(Engineering Asset)으로 인정되는 산출물만 저장한다. 모든 실험이 등록 모델이 되는 것은 아니다. 데이터 품질, 검증 결과, 문서화, 거버넌스 요구사항을 충족한 경우에만 실험 결과가 등록 모델로 승격(Promotion)되어야 한다. 이러한 구분은 레지스트리가 일시적인 실험으로 가득 차는 것을 방지한다.

메타데이터 품질(Metadata Quality)은 매우 중요하다. 엔지니어는 실제 모델 파일보다 메타데이터를 이용하여 모델을 검색하고 비교하기 때문이다. 등록된 모델은 작업(Task), 적용 분야(Application Domain), 지원 로봇 플랫폼, 센서 구성(Sensor Configuration), 운용 환경(Operating Environment), 사용 목적(Intended Use), 알려진 제한 사항, 안전 관련성(Safety Relevance), 자원 요구사항(Resource Requirement), 신뢰도 보정 상태(Confidence Calibration Status), 지원 실행 엔진(Supported Runtime Engine), 배포 제한(Deployment Restriction) 등을 포함해야 한다. 가능하면 메타데이터는 표준화된 용어(Control Vocabulary)를 사용해야 한다.

모델 문서(Model Documentation)는 가능하면 레지스트리 내부에서 직접 관리되어야 한다. 모델 카드(Model Card)는 목적(Purpose), 아키텍처, 데이터셋 계보, 평가 지표(Evaluation Metric), 벤치마크 결과(Benchmark Result), 운용 가정(Operational Assumption), 제한 사항, 윤리적 고려사항(Ethical Consideration), 배포 지침(Deployment Guidance), 모니터링 권장사항(Monitoring Recommendation)을 요약할 수 있다. 실험 추적 시스템은 기술적인 내용을 자동으로 채우고, 엔지니어는 해석과 운용 지침을 추가한다. 중앙 집중식 문서화는 지식 전달과 일관성을 크게 향상시킨다.

승인 워크플로(Approval Workflow)는 모델 등록을 단순 저장 기능에서 통제된 거버넌스로 발전시킨다. 후보 모델(Candidate Model)은 배포 대상이 되기 전에 정의된 검토 절차를 통과해야 한다. 검토자는 AI 엔지니어, 로봇 엔지니어, 안전 전문가(Safety Specialist), 보안 전문가(Security Expert), 품질 엔지니어(Quality Engineer), 제품 관리자(Product Manager), 도메인 전문가(Domain Expert)가 될 수 있다. 각 승인에는 검토자, 날짜, 근거 자료, 의견(Comment), 승인 사유(Decision Rationale), 운용 제한 사항이 기록되어야 하며, 이러한 정보는 모델 수명주기 전체에 함께 유지된다.

모델 수명주기 상태(Model Lifecycle State)는 엔지니어링 활동을 체계적으로 관리하는 데 사용된다. 일반적인 상태에는 실험(Experimental), 후보(Candidate), 검증 완료(Validated), 승인(Approved), 운영(Production), 사용 중단 권장(Deprecated), 보관(Archived), 폐기(Retired)가 포함된다. 실험 모델은 연구 단계이며, 후보 모델은 기술 요구사항을 만족했지만 추가 검토가 필요하다. 검증 모델은 공식 평가를 완료했고, 승인 모델은 배포가 가능하다. 운영 모델은 실제 플릿(Fleet)에서 사용된다. 사용 중단 모델은 유지보수는 가능하지만 신규 배포에는 사용되지 않는다. 보관 모델은 과거 기록을 유지하며, 폐기 모델은 더 이상 운용 대상이 아니다.

검증 근거(Validation Evidence)는 승인된 모든 모델과 함께 저장되어야 한다. 오프라인 벤치마크(Offline Benchmark), 시뮬레이션 보고서(Simulation Report), 재생 분석(Log Replay Analysis), 소프트웨어 인 더 루프 시험(Software-in-the-Loop Testing), 하드웨어 인 더 루프 검증(Hardware-in-the-Loop Validation), 현장 시험(Field Trial), 자원 프로파일링(Resource Profiling), 보정 결과(Calibration Measurement), 안전 평가(Safety Assessment), 강인성 분석(Robustness Analysis), 회귀 시험(Regression Report)은 모두 등록 모델과 연결되어야 한다. 이를 통해 배포 여부를 결정하는 엔지니어는 여러 시스템을 검색할 필요 없이 필요한 근거를 한곳에서 확인할 수 있다.

성능 지표(Performance Metric)는 단순한 숫자가 아니라 운용 맥락(Operational Context)과 함께 해석되어야 한다. 객체 검출 정확도, 위치추정 오차(Localization Error), 정밀도(Precision), 재현율(Recall), 추론 지연(Inference Latency), 메모리 사용량(Memory Consumption), 신뢰도 보정(Calibration Quality), 악천후 강인성, 저조도 성능, 희귀 객체 검출, 장애 복구 능력(Failure Recovery Capability)은 모두 서로 다른 의미를 가진다. 모델 레지스트리는 실험실 벤치마크와 실제 현장 검증 결과를 구분하여 저장해야 한다.

하드웨어 호환성(Hardware Compatibility)은 반드시 명시적으로 관리되어야 한다. 하나의 로봇 플릿은 서로 다른 GPU, 임베디드 가속기(Embedded Accelerator), 산업용 컴퓨터, 특수 추론 프로세서(Inference Processor)를 사용할 수 있다. 레지스트리는 지원 운영체제, CUDA 버전, 추론 엔진, 프로세서 구조(Processor Architecture), 메모리 요구사항, 저장 공간 요구사항, 전력 요구사항, 정밀도 모드, 알려진 하드웨어 제한 사항을 기록해야 한다. 자동 배포 시스템은 이러한 정보를 이용하여 호환되지 않는 모델이 잘못 설치되는 것을 방지한다.

실행 환경 의존성(Runtime Dependency)은 배포 실패를 방지하기 위해 관리되어야 한다. 등록된 모델은 프레임워크 버전(Framework Version), 실행 엔진, 컨테이너 이미지(Container Image), 공유 라이브러리(Shared Library), 설정 스키마(Configuration Schema), 전처리 모듈, 후처리 모듈(Postprocessing Module), 캘리브레이션 파일(Calibration File), 보조 자원(Auxiliary Resource)을 함께 기록해야 한다. 이러한 의존성도 모델과 함께 버전 관리되어야 하며, 하나의 배포 패키지는 독립적으로 실행 가능한 완전한 단위가 되어야 한다.

모델 패키징(Model Packaging)은 엔지니어링 산출물을 실제 배포 가능한 소프트웨어 구성요소로 변환한다. 패키지에는 모델 가중치, 실행 설정(Runtime Configuration), 전처리 로직, 추론 엔진, 캘리브레이션 파라미터, 메타데이터, 무결성 서명(Integrity Signature), 의존성 목록(Dependency Manifest), 모니터링 설정(Monitoring Configuration), 롤백 정보(Rollback Information)가 포함될 수 있다. 패키징 과정도 버전 관리되어야 하며, 최적화된 실행 형식(Runtime Format)으로 변환되는 과정에서 발생할 수 있는 수치적 차이도 추적해야 한다.

무결성 검증(Integrity Verification)은 모델 산출물이 손상되거나 무단으로 수정되는 것을 방지한다. 암호학적 해시(Cryptographic Hash), 디지털 서명(Digital Signature), 체크섬(Checksum), 패키지 검증 메커니즘을 사용하여 배포 전에 무결성을 확인해야 한다. 모든 배포 패키지는 저장, 전송, 설치 전 과정에서 무결성 정보를 유지해야 하며, 이를 통해 실제 설치된 모델이 승인된 모델과 동일함을 보장할 수 있다.

보안(Security)은 단순히 모델 파일을 보호하는 것을 넘어선다. 메타데이터 조회, 모델 다운로드, 문서 수정, 승인 수행, 새 버전 등록, 삭제 등 모든 작업은 서로 다른 권한을 가져야 한다. 인증(Authentication), 권한 관리(Authorization), 감사 로그(Audit Logging), 역할 기반 접근 제어(Role-Based Access Control)를 통해 레지스트리를 보호해야 한다. 국방, 산업 검사, 고객 전용 프로젝트의 모델은 별도의 접근 제한(Project-Specific Visibility Restriction)이 필요할 수도 있다.

역할 기반 접근 제어(Role-Based Access Control)는 협업을 지원하면서도 책임성을 유지한다. 데이터 과학자(Data Scientist), AI 엔지니어, 로봇 개발자, 시스템 아키텍트(System Architect), 검증 엔지니어, 제품 관리자, 배포 담당자, 운영팀, 고객 지원팀은 서로 다른 수준의 접근 권한을 가져야 한다. 일부 사용자는 메타데이터만 조회할 수 있으며, 다른 사용자는 새 버전을 등록하거나 운영 모델을 승인할 수 있다. 모든 변경은 사용자, 시간, 변경 대상, 변경 사유를 기록해야 한다.

감사 로그(Audit Logging)는 레지스트리에서 수행되는 모든 작업의 이력을 보존한다. 모델 생성, 메타데이터 수정, 릴리스 승인, 모델 다운로드, 수명주기 상태 변경, 문서 수정, 배포 대상 지정 등은 모두 변경 불가능한 로그로 남아야 한다. 운영 사고를 조사할 때는 누가 언제 어떤 모델을 승인했고 어떤 설정을 변경했는지가 중요한 근거가 된다. 완전한 감사 로그는 책임성과 규제 대응을 동시에 지원한다.

모델 재현성(Model Reproducibility)은 모델을 다시 생성하는 데 필요한 모든 엔지니어링 요소를 보존하는 것에 달려 있다. 소스 코드, 데이터셋, 전처리 파이프라인, 학습 설정, 실행 환경, 소프트웨어 의존성, 하드웨어 특성, 난수 시드, 실험 식별자, 평가 코드가 모두 포함되어야 한다. 따라서 모델 레지스트리는 실험 추적, 데이터셋 관리, 소스 코드 관리(Source Control), 컨테이너 저장소(Container Registry), 인프라 관리(Infrastructure Management)와 긴밀하게 통합되어야 한다.

여러 제품군(Product Line)이 동시에 발전하는 경우에는 브랜치 전략(Branching Strategy)이 필요하다. 산업 검사 로봇, 물류 로봇, 병원 배송 로봇, 실외 자율주행 로봇은 공통 인지 모델을 공유하면서도 각자의 최적화가 필요할 수 있다. 모델 레지스트리는 이러한 병렬 발전을 지원하면서도 서로 다른 제품 릴리스를 혼동하지 않도록 해야 한다. 브랜치 관계는 명확하게 기록되어야 하며, 한 제품에서 얻은 개선 사항을 다른 제품에 적용할 수 있는지 쉽게 분석할 수 있어야 한다.

모델 비교(Model Comparison)는 배포 결정을 지원하는 중요한 기능이다. 엔지니어는 모델 구조, 데이터셋 계보, 실험 설정, 벤치마크 성능, 자원 사용량, 배포 호환성, 안전 평가, 신뢰도 보정, 운용 제한 사항 등을 비교할 수 있어야 한다. 비교 도구는 많은 문서를 직접 읽지 않아도 주요 차이를 한눈에 보여주어야 한다. 이렇게 되면 모델 레지스트리는 단순 저장소가 아니라 의사결정 지원 시스템(Decision Support System) 역할도 수행한다.

입출력 인터페이스(Interface)가 변경될 때는 하위 호환성(Backward Compatibility)을 고려해야 한다. 입력 형식(Input Format), 출력 구조(Output Schema), 텐서 크기(Tensor Dimension), 좌표계(Coordinate Convention), 메타데이터 구조, 실행 인터페이스(Runtime Interface), 설정 파일은 시간이 지나면서 변경될 수 있다. 레지스트리는 호환성 정책과 마이그레이션(Migration) 방법을 문서화해야 하며, 자동 배포 시스템도 새로운 모델을 설치하기 전에 인터페이스 호환성을 확인해야 한다.

사용 중단 정책(Deprecation Policy)은 오래된 모델을 안전하게 퇴역시키기 위해 필요하다. 사용 중단 모델은 유지보수, 조사, 고객 지원, 호환성 시험에는 계속 사용할 수 있지만 새로운 배포에는 권장되지 않는다. 레지스트리는 사용 중단 사유, 권장 대체 모델, 알려진 제한 사항, 지원 종료 일정(Support Timeline)을 함께 제공해야 한다. 이를 통해 과거 모델은 유지하면서도 새로운 모델로 자연스럽게 전환할 수 있다.

보관(Archiving)은 삭제(Deletion)와 다르다. 연구 프로젝트, 종료된 제품, 규제 제출 자료, 고객 납품 모델은 수년간 보관해야 할 수도 있다. 이러한 모델을 삭제하면 중요한 엔지니어링 근거를 잃을 수 있다. 따라서 레지스트리는 장기 보관 기능을 제공하면서도 메타데이터, 문서, 감사 로그, 검증 자료, 배포 기록을 모두 유지해야 한다.

삭제 정책(Deletion Policy)은 매우 신중해야 한다. 임시 실험은 보존 정책에 따라 삭제할 수 있지만 운영 모델, 배포 패키지, 승인 기록, 감사 로그, 검증 자료는 일반적으로 보존되어야 한다. 삭제는 명시적인 승인과 함께 수행되어야 하며 삭제 기록도 감사 로그에 영구적으로 남아야 한다. 이러한 정책은 법적, 기술적, 운영상의 위험을 줄이는 동시에 저장 공간을 효율적으로 관리하도록 한다.

모델 레지스트리는 지속적 통합 및 지속적 배포(Continuous Integration / Continuous Deployment, CI/CD) 파이프라인과 통합되어 자동화된 수명주기 관리를 지원해야 한다. 성공적으로 학습된 모델은 자동으로 후보 등록(Candidate Registration), 검증 워크플로(Validation Workflow), 문서 생성, 보안 검사(Security Check), 배포 패키징을 수행하고 승인 요청을 생성할 수 있다. 그러나 최종 운영 등록은 조직의 승인 정책에 따라 이루어져야 하며, 사람의 검토는 여전히 필요하다.

플릿 관리 시스템(Fleet Management System)과의 통합은 개발과 운영 사이를 연결하는 중요한 역할을 한다. 모델 레지스트리는 어떤 로봇이 어떤 모델 버전을 사용하고 있는지, 어떤 패키지가 설치되었는지, 언제 업데이트되었는지, 롤백이 수행되었는지, 어떤 운용 지표가 해당 릴리스와 연결되는지를 기록해야 한다. 이를 통해 현장 문제는 등록된 모델과 직접 연결될 수 있으며, 사고 조사와 업데이트도 훨씬 빠르게 수행할 수 있다.

운영 모니터링 시스템(Operational Monitoring System)은 임의의 파일명이 아니라 공식 모델 식별자를 사용해야 한다. 성능 대시보드(Performance Dashboard), 텔레메트리(Telemetry), 이상 탐지 플랫폼, 사고 보고서, 유지보수 기록, 고객 지원 시스템은 모두 동일한 모델 식별자를 참조해야 한다. 이러한 표준화는 여러 지역과 여러 플릿에서 유사한 모델이 동시에 운용될 때 발생하는 혼란을 방지한다.

롤백 관리(Rollback Management)는 신뢰할 수 있는 버전 관리에 크게 의존한다. 운영 중 문제가 발생하면 엔지니어는 즉시 이전에 승인된 안정적인 버전을 찾아 복구해야 한다. 레지스트리는 이전 버전, 호환성 요구사항, 배포 이력, 롤백 절차, 운용 메모를 함께 관리해야 한다. 자동 배포 시스템은 수동 백업 폴더가 아니라 레지스트리에서 직접 롤백 대상을 선택해야 한다.

설정 관리(Configuration Management)는 모델 버전 관리와 항상 동기화되어야 한다. 머신러닝 모델은 임계값(Threshold), 캘리브레이션 파라미터, 전처리 옵션, 실행 플래그(Runtime Flag), 신뢰도 한계값, 안전 여유(Safety Margin), 로봇별 설정에 의존한다. 이러한 설정이 모델과 별도로 변경되면 검증 결과는 더 이상 유효하지 않을 수 있다. 따라서 레지스트리는 각 모델과 호환되는 설정 버전도 함께 관리하여 잘못된 조합이 운영 환경에 배포되지 않도록 해야 한다.

조직 규모가 커질수록 모델 레지스트리 거버넌스(Model Registry Governance)의 중요성도 커진다. 소규모 연구 그룹은 비공식적인 관리만으로도 충분할 수 있지만, 여러 제품과 고객, 개발 조직, 지역을 운영하는 산업용 로봇 기업은 표준화된 관리 체계를 필요로 한다. 레지스트리 정책은 명명 규칙(Naming Convention), 메타데이터 요구사항, 승인 절차, 보안 정책, 문서 표준, 수명주기 관리, 보존 정책을 조직 전체에서 일관되게 정의한다. 이러한 일관성은 협업을 향상시키고 엔지니어링 불확실성을 줄여준다.

최근 인공지능 규제(AI Regulation)는 추적성(Traceability), 책임성(Accountability), 투명성(Transparency), 문서화(Documentation)를 점점 더 강조하고 있다. 잘 설계된 모델 레지스트리는 이러한 요구사항을 자연스럽게 지원한다. 규제 기관, 감사 조직, 인증 기관(Certification Organization), 고객, 품질 조직은 학습 데이터, 검증 절차, 배포 이력, 운용 제한 사항, 변경 관리(Change Management)에 대한 정보를 요구할 수 있다. 모델 레지스트리는 이러한 정보를 신뢰성 있게 제공하는 핵심 시스템이 된다.

개방형 표준(Open Standard)은 장기적인 상호운용성(Interoperability)을 향상시킨다. 모델 레지스트리는 가능하면 특정 공급업체(Proprietary Format)에 의존하지 않는 메타데이터, 모델 형식(Model Format), 패키지 구조(Packaging Structure), 문서 구조(Document Structure), 프로그래밍 인터페이스(Programming Interface)를 사용하는 것이 바람직하다. 이는 향후 하드웨어, 소프트웨어 프레임워크, 조직 구조가 변경되더라도 시스템을 유연하게 발전시킬 수 있게 한다.

궁극적으로 모델 레지스트리(Model Registry)와 버전 관리(Version Control)는 머신러닝 산출물을 단순한 파일이 아니라 통제된 엔지니어링 자산(Governed Engineering Asset)으로 전환한다. 등록된 모든 모델은 기술 이력(Technical History), 검증 근거, 배포 기록, 운용 지식, 거버넌스 결정, 재현성 정보를 함께 가진다. 이러한 통합 수명주기 관리는 자율이동로봇(AMR) 조직이 머신러닝 모델을 안전하게 배포하고, 발전하는 플릿 전체에서 추적성을 유지하며, 운용 문제를 신속하게 분석하고, 규제 요구사항을 만족시키며, 엔지니어링 원칙과 운용 신뢰성을 유지한 채 지능형 로봇 시스템을 지속적으로 발전시키도록 지원한다.

## 15.04 Continuous Training and Deployment

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

지속적 학습 및 배포(Continuous Training and Deployment)는 로봇 머신러닝 운영(Robot MLOps)을 주기적인 모델 개발 단계에서 현장 증거(Field Evidence)를 지속적으로 활용하여 머신러닝 시스템을 개선하는 통제된 운영 순환 구조로 확장한다. 자율이동로봇(Autonomous Mobile Robot, AMR)은 일상적인 운용 과정에서 방대한 센서 데이터(Sensor Data), 미션 기록(Mission Record), 모델 출력(Model Output), 운영자 개입(Operator Intervention), 장애 이벤트(Failure Event), 환경 메타데이터(Environmental Metadata)를 생성한다. 지속적 파이프라인(Continuous Pipeline)은 이 가운데 선택된 증거를 갱신된 데이터셋, 후보 모델(Candidate Model), 검증된 배포 패키지(Validated Deployment Package), 모니터링되는 릴리스(Monitored Release)로 변환한다. 목표는 통제되지 않은 자동화가 아니라 추적성(Traceability), 안전(Safety), 보안(Security), 명확한 승인 경계(Approval Boundary)를 유지하는 반복 가능한 개선이다.

지속적 학습(Continuous Training)은 새로운 데이터가 생성될 때마다 무조건 모델을 재학습한다는 가정이 아니라 명확하게 정의된 트리거(Trigger)에서 시작되어야 한다. 트리거에는 정기적인 모델 갱신(Model Refresh), 중대한 데이터 드리프트(Data Drift), 반복되는 현장 장애(Field Failure), 신규 고객 환경(Customer Environment), 새로운 센서, 확장된 운용 영역(Operational Domain), 라벨 수정(Annotation Correction), 규제 요구사항(Regulatory Requirement), 주요 소프트웨어 릴리스(Software Release)가 포함될 수 있다. 각 트리거는 재학습을 통해 해결하려는 엔지니어링 문제(Engineering Problem)를 명확히 해야 한다. 이를 통해 실질적인 운용 가치 없이 자원만 소모하는 불필요한 학습 주기를 방지할 수 있다.

지속적 학습 루프(Continuous Learning Loop)는 데이터 수집(Data Collection)과 모델 승격(Model Promotion)을 구분해야 한다. 로봇은 지속적으로 관측 데이터를 수집하고 이벤트 요약(Event Summary)을 업로드할 수 있지만, 수집된 데이터는 먼저 적재(Ingestion), 개인정보 보호 통제(Privacy Control), 품질 검증(Quality Validation), 라벨링(Labeling), 데이터셋 구성(Dataset Assembly)을 거쳐야 한다. 이러한 절차를 통과한 이후에만 학습 데이터로 사용할 수 있어야 한다. 마찬가지로 자동으로 학습된 모델도 공식 검증 및 승인 요구사항을 충족하기 전까지는 후보 상태로 유지되어야 한다. 이러한 분리는 파이프라인을 자주 실행하면서도 검증되지 않은 데이터나 모델이 운영 로봇에 배포되는 것을 방지한다.

현장 데이터 선택(Field Data Selection)은 모든 센서 프레임을 업로드하고 라벨링하는 것이 현실적으로 어렵기 때문에 매우 중요하다. 이벤트 기반 수집(Event-Driven Collection)은 비상 정지(Emergency Stop), 원격 개입(Remote Intervention), 낮은 신뢰도 예측(Low-Confidence Prediction), 위치추정 초기화(Localization Reset), 도킹 실패(Docking Failure), 비정상 장애물(Unusual Obstacle), 안전 제어기 작동(Safety-Controller Activation), 경로 차단(Route Blockage), 분포 외 장면(Out-of-Distribution Scene)을 우선 수집할 수 있다. 동시에 어려운 사례만 데이터셋을 지배하지 않도록 대표적인 정상 운용 데이터도 보존해야 한다. 지속적 학습에는 일반 조건, 어려운 시나리오, 희귀하지만 운용상 중요한 이벤트가 균형 있게 포함되어야 한다.

데이터 적재 서비스(Data Ingestion Service)는 업로드된 세션(Session)이 완전하고, 신뢰할 수 있으며, 정확한 타임스탬프(Timestamp)를 가지고 있고, 올바른 로봇, 미션, 센서 구성(Sensor Configuration), 소프트웨어 빌드(Software Build), 모델 버전과 연결되어 있는지를 확인해야 한다. 파일 해시(File Hash), 세션 매니페스트(Session Manifest), 캘리브레이션 참조(Calibration Reference), 개인정보 분류(Privacy Classification), 전송 상태(Transfer Status)는 관리형 저장소(Managed Storage)에 데이터가 들어가기 전에 검증되어야 한다. 손상되거나 불완전한 기록은 검토를 위해 격리되어야 한다. 지속적 파이프라인은 작은 결함도 반복적으로 새로운 데이터셋에 포함시켜 확대할 수 있으므로 신뢰할 수 있는 적재 과정이 매우 중요하다.

메타데이터(Metadata)는 지속적 학습 시스템이 데이터가 생성된 맥락(Context)을 이해하도록 한다. 유용한 메타데이터에는 위치(Location), 날씨, 조명, 경로 유형(Route Type), 로봇 속도, 적재 중량(Payload), 센서 상태(Sensor Health), 미션 결과(Mission Outcome), 운영자 행동, 모델 신뢰도(Model Confidence), 실행 지연(Runtime Latency), 환경 범주(Environmental Category)가 포함될 수 있다. 메타데이터는 목표 지향적 데이터 선택(Targeted Data Selection)과 시나리오 기반 평가(Scenario-Based Evaluation)를 지원한다. 또한 성능 변화가 새로운 모델, 새로운 환경, 변경된 하드웨어, 고객 공정 변화(Customer Process Change), 수정된 로봇 설정 가운데 무엇 때문에 발생했는지 판단하는 데 도움을 준다.

현장 데이터가 학습에 사용되기 전에는 개인정보 보호 및 규정 준수 검사(Privacy and Compliance Check)가 수행되어야 한다. 카메라, 음성, 위치, 고객 공정, 운영자 데이터는 동의(Consent), 익명화(Anonymization), 보존 기간(Retention), 지역별 저장(Geographic Storage), 계약 조건(Contractual Restriction)의 적용을 받을 수 있다. 자동 비식별화(Automated Redaction)는 중앙 서버로 업로드하기 전에 얼굴, 차량 번호판, 화면, 음성 또는 기타 민감한 정보를 제거할 수 있다. 데이터셋 적격성 규칙(Dataset Eligibility Rule)은 제한된 데이터가 승인되지 않은 학습 환경에 유입되지 않도록 해야 한다. 지속적 개선은 개인정보 보호, 데이터 주권(Data Sovereignty), 보안, 고객 의무를 준수하는 경우에만 허용될 수 있다.

데이터셋 구성(Dataset Construction)은 계속 내용이 바뀌는 컬렉션이 아니라 변경 불가능하고 버전 관리된 릴리스(Immutable Versioned Release)를 생성해야 한다. 각 학습 주기는 매니페스트(Manifest), 온톨로지(Ontology), 전처리 설정(Preprocessing Configuration), 품질 보고서(Quality Report), 데이터 분할 정의(Split Definition), 변경 요약(Change Summary)을 포함하는 특정 데이터셋 버전을 참조해야 한다. 새로운 현장 증거는 새로운 데이터셋 릴리스를 생성할 수 있지만, 이전 데이터셋도 재현성을 위해 계속 보존되어야 한다. 시스템은 이전 버전과 비교하여 어떤 샘플이 추가되고, 제거되고, 재라벨링되고, 익명화되고, 재분류되었는지를 명확하게 설명해야 한다.

지속적 파이프라인에서는 학습(Training), 검증(Validation), 시험(Test) 데이터 분할을 특히 신중하게 관리해야 한다. 새로운 데이터는 같은 경로, 미션, 현장, 이벤트에서 수집된 기존 기록과 매우 유사할 수 있다. 관련 샘플이 학습과 검증 데이터에 동시에 포함되면 측정된 성능 향상은 실제보다 과장될 수 있다. 미션, 위치, 로봇, 기간, 시나리오 단위의 그룹 기반 분할(Group-Based Split)은 데이터 누출(Data Leakage)을 줄일 수 있다. 보호된 시험 데이터셋(Protected Test Dataset)은 주요 단계 평가를 위해 안정적으로 유지하고, 순환형 검증 데이터셋(Rotating Validation Dataset)은 새롭게 등장하는 운용 조건에서 성능을 측정하는 데 활용할 수 있다.

지속적 학습 파이프라인은 재현 가능한 워크플로(Reproducible Workflow)로 정의되어야 한다. 하나의 파이프라인은 승인된 데이터를 가져오고, 스키마(Schema)를 검증하며, 전처리를 수행하고, 데이터셋을 분할하고, 기준 모델(Baseline)을 초기화하고, 후보 모델을 학습하고, 체크포인트(Checkpoint)를 평가하고, 보고서를 생성하고, 산출물을 등록하고, 승격 요청을 생성할 수 있다. 파이프라인 정의는 버전 관리 시스템에 저장되고 관리형 인프라(Managed Infrastructure)에서 실행되어야 한다. 수동 탐색도 필요하지만, 운영 후보 모델은 코드, 설정, 환경, 하드웨어, 데이터 계보를 보존하는 반복 가능한 파이프라인을 통해 생성되어야 한다.

재학습(Retraining)은 엔지니어링 목표에 따라 다양한 전략을 사용할 수 있다. 전체 재학습(Full Retraining)은 초기 가중치나 사전학습 가중치에서 시작하여 갱신된 전체 데이터셋을 사용한다. 증분 학습(Incremental Training)은 기존 모델에서 시작하여 추가 데이터를 학습한다. 미세조정(Fine-Tuning)은 새로운 환경이나 작업에 맞게 선택된 계층을 조정한다. 도메인 적응(Domain Adaptation)은 목표 도메인(Target Domain)의 데이터를 활용하여 분포 차이를 줄인다. 각 접근 방식에는 장점과 위험이 있다. 증분 방식은 빠를 수 있지만 망각을 유발할 수 있고, 전체 재학습은 더 높은 계산 비용이 들지만 일관성을 확보할 수 있다.

파국적 망각(Catastrophic Forgetting)은 최근 데이터로 학습하면서 이전 운용 조건의 성능을 잃는 주요 위험이다. 특정 창고, 날씨, 고객 현장에 맞게 조정된 모델이 이전에 지원하던 환경에서는 성능이 저하될 수 있다. 따라서 지속적 학습은 이전 데이터셋의 재생 데이터(Replay Data), 균형 샘플링(Balanced Sampling), 정규화(Regularization), 지식 증류(Knowledge Distillation), 다중 도메인 평가(Multi-Domain Evaluation)를 포함해야 한다. 새로운 조건에서 개선되었다는 이유만으로 기존 시나리오에서 허용할 수 없는 성능 저하가 발생해서는 안 된다.

학습 설정(Training Configuration)은 각 학습 주기에서 통제되어야 한다. 학습률(Learning Rate), 최적화기(Optimizer), 배치 크기(Batch Size), 손실 함수(Loss Function), 데이터 증강(Data Augmentation), 클래스 가중치(Class Weight), 난수 시드(Random Seed), 사전학습 가중치(Pretrained Weight), 스케줄러(Scheduler), 조기 종료(Early Stopping) 규칙은 버전 관리되어야 한다. 변경 사항은 의도적이어야 하며 실험 비교에서 명확하게 보여야 한다. 데이터와 학습 전략을 동시에 바꾸면 성능 차이의 원인을 파악하기 어렵다. 통제된 실험을 통해 새로운 데이터, 수정된 라벨, 아키텍처 변경, 최적화 설정의 영향을 분리해야 한다.

자동 하이퍼파라미터 튜닝(Automatic Hyperparameter Tuning)은 후보 모델의 성능을 향상시킬 수 있지만, 승인된 파라미터 범위와 연산 예산(Compute Budget) 안에서 수행되어야 한다. 탐색 시스템은 학습률, 데이터 증강, 모델 크기, 임계값(Threshold), 압축 전략(Compression Strategy)을 평가할 수 있다. 모든 실행은 데이터셋 및 설정과 추적 가능하게 연결되어야 한다. 후보 모델은 하나의 평균 지표만으로 선택해서는 안 된다. 반복 실험, 시나리오별 성능, 추론 비용(Inference Cost), 신뢰도 보정(Calibration), 안전 관련 오류 패턴을 함께 고려해야 한다.

모든 지속적 학습 주기에서는 기준 모델 비교(Baseline Comparison)가 필수적이다. 새로운 후보 모델은 동일한 데이터셋과 평가 코드를 사용하여 현재 운영 모델(Current Production Model), 이전 승인 버전, 관련 참조 모델(Reference Model)과 비교되어야 한다. 비교 항목은 정확도, 재현율(Recall), 정밀도(Precision), 지연 시간(Latency), 메모리, 신뢰도 보정, 현장 시나리오, 희귀 사례, 운용 지표를 포함해야 한다. 후보 모델이 다른 실험 모델보다 우수하다는 이유만으로 승격되어서는 안 된다. 실제 배포 시스템과 비교하여 의미 있는 가치를 입증해야 한다.

회귀 시험(Regression Testing)은 이미 정상적으로 동작하는 기능을 보호한다. 회귀 시험 모음(Regression Suite)은 알려진 장애 사례, 안전에 중요한 장면, 어려운 조명, 악천후, 작은 객체, 도킹 시나리오, 위치추정 문제, 센서 성능 저하, 고객별 조건을 포함해야 한다. 기록된 로그와 시뮬레이션 시나리오는 반복 가능한 비교를 가능하게 한다. 모든 후보 모델은 동일한 회귀 시험 모음을 처리해야 하며, 중대한 성능 저하는 원인이 명확히 이해되고 정당화되며 명시적 운용 제한 아래 승인되지 않는 한 승격을 차단해야 한다.

시뮬레이션(Simulation)은 새로운 모델을 실제 로봇에 적용하기 전에 대규모 시험을 가능하게 한다. 후보 모델은 환경, 센서 노이즈, 객체 배치, 교통, 날씨, 사람 행동, 장애 조건의 통제된 변형에서 평가될 수 있다. 시뮬레이션은 실제 환경에서 재현하기 어렵거나 위험한 희귀 이벤트를 시험하는 데 특히 유용하다. 그러나 합성 장면(Synthetic Scene)은 실제 센서와 운용 효과를 완전히 반영하지 못할 수 있으므로 시뮬레이션 결과만으로 모든 검증을 대체해서는 안 된다. 시뮬레이션 검증은 로그 재생(Log Replay)과 현장 시험을 보완해야 한다.

로그 재생은 새로운 후보 모델을 이전에 기록된 로봇 세션에 적용하여 평가한다. 시스템은 센서 스트림(Sensor Stream), 미션 타이밍(Mission Timing), 모델 입력, 관련 시스템 상태를 재현하고 후보 모델의 출력을 수집한다. 로그 재생을 통해 비용이 많이 들거나 위험한 현장 이벤트를 다시 수행하지 않고도 모델을 비교할 수 있다. 이는 사고 재현(Incident Reproduction), 어려운 사례 평가(Hard-Case Evaluation), 회귀 시험에 특히 유용하다. 결과에는 사용된 세션, 전처리 경로, 실행 환경, 평가 버전, 후보 패키지가 정확히 기록되어야 한다.

소프트웨어 인 더 루프 시험(Software-in-the-Loop Testing)은 후보 모델이 로봇 미들웨어(Robot Middleware), 메시지 정의(Message Definition), 좌표계(Coordinate Frame), 경로 계획 인터페이스(Planning Interface), 설정 서비스(Configuration Service)와 올바르게 통합되는지를 확인한다. 하드웨어 인 더 루프 시험(Hardware-in-the-Loop Testing)은 실제 로봇 컴퓨터, 제어기, 네트워크, 가속기, 센서 인터페이스를 추가한다. 이를 통해 런타임 오류(Runtime Fault), 드라이버 비호환성(Driver Incompatibility), 메모리 압박(Memory Pressure), 메시지 손실(Message Loss), 동기화 문제, 열 스로틀링(Thermal Throttling), 시간 동작 문제를 발견할 수 있다. 지속적 배포 파이프라인은 후보 모델을 점진적으로 현실적인 검증 단계로 이동시켜야 한다.

광범위한 운영 배포 전에 실제 현장 시험(Physical Field Testing)은 여전히 필요하다. 실제 로봇은 진동, 휠 슬립(Wheel Slip), 센서 오염, 조명 변화, 예측하기 어려운 사람 행동, 네트워크 단절, 열 변화 등 완전히 시뮬레이션하기 어려운 조건을 경험한다. 통제된 현장 시험은 문서화된 시나리오, 승인 기준(Acceptance Criteria), 숙련된 운영자, 완전한 데이터 수집 조건에서 수행되어야 한다. 시험 결과는 모델, 소프트웨어, 하드웨어, 지도(Map), 캘리브레이션, 로봇 설정 버전과 연결되어야 한다.

승격 게이트(Promotion Gate)는 후보 모델이 학습 단계에서 배포 단계로 이동할 수 있는지를 결정한다. 게이트에는 데이터셋 승인, 최소 성능 기준, 중요 기능의 회귀 없음, 시뮬레이션 성공, 로그 재생 완료, 자원 호환성(Resource Compatibility), 현장 시험 근거, 보안 검사(Security Check), 개인정보 검토, 문서화, 전문가 승인이 포함될 수 있다. 모델의 안전 관련성에 따라 서로 다른 게이트가 적용될 수 있다. 낮은 위험의 분석 모델은 단순한 검토로 충분할 수 있지만, 움직임 판단에 영향을 주는 인지 모델은 더 강력한 다분야 검증(Multidisciplinary Validation)이 필요하다.

지속적 배포(Continuous Deployment)는 전체 플릿에 즉시 활성화한다는 의미가 아니다. 단계적 전략(Staged Strategy)은 운용 노출을 점진적으로 확대하여 위험을 줄인다. 후보 모델은 먼저 섀도 모드(Shadow Mode)에서 동작하고, 이후 내부 시험 로봇, 소규모 카나리 그룹(Canary Group), 제한된 고객 현장, 마지막으로 광범위한 플릿에 적용될 수 있다. 각 단계에는 적용 대상, 기간, 모니터링 지표, 성공 조건, 롤백 기준, 담당 검토자가 정의되어야 한다. 다음 단계로의 이동은 단순한 시간 경과가 아니라 검증 근거에 기반해야 한다.

섀도 배포(Shadow Deployment)는 후보 모델이 실제 데이터를 처리하지만 로봇을 직접 제어하지 않도록 한다. 후보 모델의 예측은 현재 운영 모델, 운영자 관찰, 미션 결과와 비교될 수 있다. 이 단계는 현장 데이터 분포, 실행 성능, 자원 소비, 신뢰도 동작, 모델 간 불일치 패턴을 파악하는 데 유용하다. 특히 안전 관련 인지나 예측 모델에 효과적이다. 다만 실제 로봇 동작은 다른 모델에 의해 결정되었으므로 섀도 결과는 이러한 조건을 고려하여 해석해야 한다.

카나리 배포(Canary Deployment)는 후보 모델을 제한된 수의 로봇이나 미션에 실제로 활성화한다. 선택된 그룹은 안전과 사업 위험을 제한하면서 의미 있는 운용 조건을 대표해야 한다. 카나리 로봇은 운용 지표와 모델 지표를 기준으로 기준 그룹(Baseline Group)과 비교되어야 한다. 비상 정지, 운영자 개입, 오검출, 지연 시간, 자원 사용량, 미션 실패 등 중요 지표가 승인된 한계를 초과하면 배포를 중단하거나 자동 롤백해야 한다.

환경 차이가 큰 경우에는 현장 기반 배포(Site-Based Deployment)가 적합할 수 있다. 특정 시설, 지역, 기후, 고객 공정에 맞게 조정된 모델은 먼저 해당 환경에서 운용되어야 한다. 모델 레지스트리(Model Registry)의 메타데이터와 배포 정책은 지원 환경과 제한사항을 명시해야 한다. 실내 물류창고에서 검증된 모델이 자동으로 실외 환경에서도 사용 가능하다고 판단해서는 안 된다. 지속적 배포 시스템은 각 승인 모델에 연결된 환경, 로봇, 센서, 속도 제한을 강제해야 한다.

무선 배포(Over-the-Air Delivery)는 로봇 플릿에 모델을 확장 가능하게 전달하는 방법이다. 패키지는 인증(Authentication)되고 암호화된 채널을 통해 전송되어야 하며, 서명(Signature)과 암호학적 해시(Cryptographic Hash)로 검증되어야 한다. 업데이트 관리자는 설치 전에 로봇 식별자, 하드웨어 프로파일(Hardware Profile), 운영체제, 실행 환경 버전, 배터리 수준, 사용 가능한 저장 공간, 네트워크 품질, 미션 상태를 확인해야 한다. 배포 이벤트는 중앙에 기록되어 어떤 패키지가 어떤 로봇에 전달되었고 활성화에 성공했는지를 확인할 수 있어야 한다.

원자적 설치(Atomic Installation)는 부분 업데이트로 인해 로봇이 불일치 상태에 빠지는 것을 방지한다. 전체 패키지는 활성화되기 전에 다운로드되고, 검증되고, 압축 해제되고, 시험되어야 한다. 함께 동작해야 하는 모델 가중치, 전처리, 후처리, 설정, 캘리브레이션, 실행 환경 의존성은 하나의 트랜잭션(Transaction)으로 활성화되어야 한다. 현재 정상 동작 버전은 새 버전이 시작 시험(Startup Check)을 통과할 때까지 유지되어야 한다. 활성화에 실패하면 로봇은 이전 승인 패키지를 계속 사용하거나 복원해야 한다.

호환성 검증(Compatibility Validation)은 설치 전과 설치 후에 모두 수행되어야 한다. 설치 전 검사는 패키지가 로봇의 프로세서, 가속기, 메모리, 센서, 드라이버, 실행 환경, 소프트웨어 인터페이스를 지원하는지 확인한다. 설치 후 검사는 모델이 정상적으로 로드되는지, 필요한 자원이 준비되어 있는지, 입출력 스키마(Input and Output Schema)가 일치하는지, 상태 모니터링(Health Monitoring)이 활성화되었는지를 확인한다. 호환성 정보는 임의의 파일명이나 운영자 판단이 아니라 모델 레지스트리와 로봇 자산 관리(Robot Inventory)에서 가져와야 한다.

실행 설정(Runtime Configuration)은 모델과 함께 버전 관리되어야 한다. 임계값, 클래스 매핑(Class Mapping), 캘리브레이션 파라미터, 전처리 옵션, 신뢰도 한계, 기능 플래그(Feature Flag), 안전 여유(Safety Margin), 현장별 설정은 모델 가중치가 동일하더라도 동작을 크게 바꿀 수 있다. 검증된 모델이라도 승인되지 않은 설정과 결합되면 검증되지 않은 시스템이 된다. 따라서 배포 패키지는 호환되는 설정 버전을 명시하고 지원되지 않는 조합이 활성화되지 않도록 해야 한다.

롤백(Rollback)은 지속적 배포의 핵심 기능이다. 시험 과정에서 발견되지 않은 비정상적인 지연, 불필요한 정지, 장애물 미탐, 메모리 증가, 특정 현장 장애, 안전 우려가 운영 모니터링에서 나타날 수 있다. 배포 플랫폼은 실패한 릴리스의 증거를 보존하면서 신속하게 검증된 정상 버전(Known-Good Version)으로 복귀할 수 있어야 한다. 통신이 가능한 경우 중앙에서, 연결이 끊긴 경우 로컬에서 롤백할 수 있어야 한다. 롤백 절차는 사고 발생 시 처음 시도하는 것이 아니라 사전에 시험되어야 한다.

로컬 안전 동작(Local Safety Behavior)은 클라우드 연결에 전적으로 의존해서는 안 된다. 로봇은 간헐적이거나 제한된 네트워크 환경에서 운용될 수 있으므로 엣지 시스템(Edge System)은 모델 상태, 실행 지연, 입력 누락, 유효하지 않은 출력, 가속기 장애, 자원 고갈을 자체적으로 모니터링해야 한다. 중요한 문제가 발생하면 로봇은 대체 모델(Fallback Model)을 활성화하고, 기능을 제한하고, 사람의 지원을 요청하거나, 안전 상태(Safe State)로 전환해야 한다. 이후 통신이 복원되면 로컬 판단과 이벤트를 중앙 플릿 기록과 동기화해야 한다.

모니터링(Monitoring)은 배포 직후부터 시작된다. 모델 지표에는 신뢰도 분포(Confidence Distribution), 예측 안정성(Prediction Stability), 클래스 빈도(Class Frequency), 분포 외 점수(Out-of-Distribution Score), 추론 지연, 입력 누락률, 신뢰도 보정 동작이 포함될 수 있다. 로봇 지표에는 미션 완료율, 비상 정지, 수동 개입, 도킹 성공, 경로 지연, 위치추정 초기화, 안전 제어기 작동, 에너지 소비, 고객 보고 문제가 포함될 수 있다. 두 수준의 지표를 결합하면 모델 변경이 실제 로봇 운용을 개선했는지 또는 악화시켰는지를 판단할 수 있다.

데이터 드리프트 모니터링(Data Drift Monitoring)은 현재 현장 입력과 학습 데이터 분포 사이의 변화를 탐지한다. 새로운 조명, 날씨, 장비, 시설 배치, 객체 유형, 카메라 설정, 센서 노화, 로봇 속도, 고객 공정은 데이터 특성을 바꿀 수 있다. 드리프트 신호는 통계 요약(Statistical Summary), 임베딩(Embedding), 모델 신뢰도, 클래스 빈도, 메타데이터 비교를 활용할 수 있다. 드리프트가 발생했다고 무조건 재학습해야 하는 것은 아니지만, 지속적이거나 성능과 관련된 변화는 조사와 목표 데이터 수집을 유발해야 한다.

개념 드리프트(Concept Drift)는 관측과 올바른 동작 사이의 관계가 변하는 경우에 발생한다. 시설이 새로운 교통 규칙을 도입하거나, 제한 구역을 재정의하거나, 객체 취급 방식이나 생산 공정을 변경할 수 있다. 입력의 외관은 비슷하게 유지되더라도 올바른 출력은 달라질 수 있다. 개념 드리프트를 탐지하려면 운영자 피드백, 갱신된 라벨, 미션 결과, 도메인 검토가 필요할 수 있다. 지속적 학습 시스템은 운용 공정의 변화와 데이터셋 및 모델 거버넌스를 연결해야 한다.

분포 외 이벤트(Out-of-Distribution Event)는 이후 분석을 위해 기록되어야 한다. 비정상 센서 패턴, 새로운 객체 유형, 예상하지 못한 지면, 희귀한 날씨, 익숙하지 않은 사람 행동, 손상된 센서는 낮은 신뢰도나 일관되지 않은 예측을 유발할 수 있다. 로봇은 보수적인 동작을 수행하면서 관련 데이터를 저장할 수 있다. 이러한 이벤트는 어려운 사례 마이닝(Hard-Case Mining)과 향후 데이터셋 확장의 후보가 된다. 다만 분포 외 탐지 자체도 오경보를 생성하거나 중요한 미지 상황을 놓칠 수 있으므로 검증되어야 한다.

운영자 피드백(Operator Feedback)은 자동 지표만으로 포착하기 어려운 중요한 기준 정답(Ground Truth)을 제공한다. 운영자는 불필요한 정지, 위험 요소 미탐, 부적절한 경로, 도킹 문제, 비정상 동작, 불필요한 개입을 구조화된 범주로 분류할 수 있다. 원격 지원과 수동 인계(Manual Takeover) 이벤트는 주변 데이터와 시스템 상태를 자동으로 보존해야 한다. 피드백은 로봇, 미션, 모델, 소프트웨어, 타임스탬프 식별자와 연결되어야 한다. 이를 통해 현장 관찰이 향후 학습 데이터로 이어지는 직접적인 경로가 형성된다.

사고 관리(Incident Management)는 배포 파이프라인과 통합되어야 한다. 안전 사고, 근접 사고(Near Miss), 개인정보 문제, 중대한 미션 실패, 비정상 모델 동작은 통제된 증거 보존과 조사를 요구한다. 사고 기록에는 센서 데이터, 로그, 활성 모델 패키지, 소프트웨어 버전, 설정, 로봇 상태, 운영자 행동, 환경 맥락이 포함되어야 한다. 관련 산출물은 제한된 접근이나 법적 보존(Legal Hold)이 필요할 수 있다. 근본 원인을 충분히 이해하기 전에는 단순히 재학습을 시작하여 문제를 숨기거나 반복해서는 안 된다.

지속적 개선(Continuous Improvement)은 우선순위 판단에 의존한다. 탐지된 모든 문제가 즉시 새로운 모델 릴리스를 요구하는 것은 아니다. 팀은 발생 빈도(Frequency), 심각도(Severity), 안전 영향, 고객 영향, 데이터 가용성, 예상 개선 효과를 평가해야 한다. 일부 문제는 모델 재학습이 아니라 센서 수리, 캘리브레이션, 소프트웨어 수정, 인터페이스 변경, 운영자 교육, 환경 수정으로 해결해야 할 수 있다. 지속적 파이프라인은 모든 운용 문제를 모델 문제로 가정하는 것이 아니라 엔지니어링 판단을 지원해야 한다.

빈번한 학습은 상당한 GPU 시간, 저장 공간, 네트워크 대역폭, 라벨링 작업, 시뮬레이션 자원, 엔지니어링 시간을 사용할 수 있으므로 비용 관리(Cost Management)가 중요하다. 파이프라인은 데이터셋, 실험, 후보 모델, 릴리스별 비용을 추적해야 한다. 캐싱(Caching), 선택적 업로드(Selective Upload), 이벤트 기반 수집, 계층형 저장소(Tiered Storage), 증분 처리(Incremental Processing), 예약 연산(Scheduled Compute)은 효율성을 높일 수 있다. 그러나 비용 절감을 위해 필수 안전 평가, 회귀 시험, 보안 검토, 운영 모니터링을 제거해서는 안 된다.

보안(Security)은 지속적 파이프라인 전체를 보호해야 한다. 공격자나 실수로 인해 데이터가 손상되고, 라벨이 변경되고, 학습 코드가 변조되고, 모델 패키지가 교체되고, 지식재산(Intellectual Property)이 유출되거나, 승인되지 않은 산출물이 배포될 수 있다. 최소 권한 접근(Least-Privilege Access), 서명된 코드(Signed Code), 안전한 빌드 환경(Secure Build Environment), 의존성 검사(Dependency Scanning), 산출물 서명(Artifact Signature), 감사 로그(Audit Logging), 보호된 서비스 계정(Service Account)을 적용해야 한다. 소프트웨어 공급망 기록(Software Supply-Chain Record)은 각 배포 모델에 관련된 외부 패키지, 컨테이너, 실행 엔진, 취약점을 식별해야 한다.

문서화(Documentation)는 전체 주기에서 자동으로 생성되어야 한다. 각 릴리스는 모델 식별자, 데이터셋 계보, 학습 설정, 평가 결과, 하드웨어 호환성, 배포 범위, 모니터링 계획, 제한 사항, 롤백 절차, 승인 기록, 변경 요약을 포함해야 한다. 자동 입력 항목은 누락을 줄이고, 엔지니어는 해석과 위험 설명을 추가한다. 체계적인 문서는 운영, 안전, 고객 지원, 향후 개발 조직이 무엇이 변경되었고 해당 릴리스를 어떻게 관리해야 하는지를 이해하도록 한다.

조직 역할(Organizational Role)은 명확하게 유지되어야 한다. 데이터 엔지니어(Data Engineer)는 데이터 적재와 데이터셋을 관리한다. AI 엔지니어(AI Engineer)는 학습 파이프라인과 모델을 개발한다. 로봇 엔지니어(Robotics Engineer)는 모델을 인지, 경로 계획, 제어, 하드웨어와 통합한다. 플랫폼 엔지니어(Platform Engineer)는 연산 자원, 모델 레지스트리, 배포, 모니터링을 운영한다. 검증, 안전, 보안, 개인정보 보호, 품질, 제품, 운영 조직은 근거와 승인을 제공한다. 명확한 책임은 중요한 활동이 누락되거나 중복되는 것을 방지한다.

성숙한 지속적 학습 및 배포 시스템(Continuous Training and Deployment System)은 폐쇄형이지만 통제된 학습 루프(Closed but Controlled Learning Loop)를 형성한다. 로봇은 운용 증거를 생성하고, 관리형 파이프라인은 선택된 증거를 검증된 데이터셋으로 변환하며, 학습은 추적 가능한 후보 모델을 생성하고, 계층화된 시험(Layered Testing)은 배포 준비 상태를 확인한다. 단계적 배포는 위험 노출을 제한하고, 플릿 모니터링(Fleet Monitoring)은 실제 현장 동작을 측정한다. 이후 피드백은 다음 개선 주기를 안내한다. 이러한 구조는 자율이동로봇 시스템이 재현성, 안전, 보안, 거버넌스, 운용 안정성을 희생하지 않고 현장에서 지속적으로 학습할 수 있도록 한다.

## 15.05 Edge AI Model Update Workflow

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

엣지 AI 모델 업데이트 워크플로(Edge AI Model Update Workflow)는 머신러닝 모델(Machine Learning Model)이 로봇의 엣지 컴퓨터(Edge Computer)에 준비되고, 검증되며, 배포되고, 설치되고, 활성화되고, 모니터링되며, 필요할 경우 롤백(Rollback)되는 전체 과정을 정의한다. 자율이동로봇(Autonomous Mobile Robot, AMR)은 프로세서 성능, 가속기 종류(Accelerator Type), 메모리, 저장 공간, 전력, 온도, 통신 품질, 미션 수행 가능 여부 등 엄격한 제약 조건에서 모델을 실행한다. 따라서 업데이트 워크플로는 일반적인 소프트웨어 업데이트 절차뿐 아니라 모델 전용 검증(Model-Specific Validation), 하드웨어 호환성(Hardware Compatibility), 실행 환경 모니터링(Runtime Monitoring), 안전 제어(Safety Control), 플릿 수준의 추적성(Fleet-Level Traceability)을 함께 포함해야 한다.

업데이트 워크플로는 후보 모델(Candidate Model)이 공식적인 개발과 검증을 모두 완료한 이후에만 시작되어야 한다. 후보 모델은 이미 고정된 데이터셋 버전(Dataset Version), 학습 설정(Training Configuration), 소스 코드 수정 버전(Source Code Revision), 실험 기록(Experiment Record), 모델 레지스트리(Model Registry) 항목, 평가 보고서(Evaluation Report), 승인 상태(Approval Status)와 연결되어 있어야 한다. 개발용 컴퓨터에서 식별되지 않은 가중치 파일(Weight File)을 수동으로 복사하여 엣지 배포를 시작해서는 안 된다. 모든 산출물은 고유 식별자(Unique Identifier), 버전, 계보(Lineage), 사용 목적(Intended Use), 알려진 제한 사항(Known Limitation), 지원 하드웨어 프로파일(Hardware Profile), 승인된 운용 영역(Operational Domain)을 가진 상태에서 패키징(Packaging)을 시작해야 한다.

모델 패키징(Model Packaging)은 검증된 모델을 완전한 엣지 배포 단위(Edge-Deployable Unit)로 변환하는 과정이다. 패키지에는 모델 가중치(Model Weight), 최적화된 실행 엔진(Optimized Runtime Engine), 전처리(Preprocessing) 및 후처리(Postprocessing) 코드, 클래스 정의(Class Definition), 캘리브레이션 파일(Calibration File), 실행 설정(Runtime Configuration), 의존성 목록(Dependency Manifest), 모니터링 파라미터(Monitoring Parameter), 시작 검사(Startup Check), 디지털 서명(Digital Signature), 롤백 정보가 포함될 수 있다. 이러한 구성 요소는 하나만 변경되어도 모델의 동작이 달라질 수 있으므로 함께 버전 관리되어야 한다. 하나의 배포 패키지는 독립적으로 관리되는 파일들의 집합이 아니라 하나의 통제된 소프트웨어 단위(Control Software Unit)로 동작해야 한다.

모델 변환(Model Conversion)은 학습에 사용된 형식이 로봇의 엣지 컴퓨터에서 직접 실행하기 적합하지 않은 경우 수행된다. PyTorch, TensorFlow 또는 다른 프레임워크(Framework)에서 학습된 모델은 ONNX로 변환된 후 TensorRT, OpenVINO, TensorFlow Lite 또는 제조사 전용 가속기(Runtime)용 형식으로 최적화될 수 있다. 이러한 변환 과정은 수치 정밀도(Numerical Precision), 지원 연산자(Supported Operator), 메모리 구조(Memory Layout), 출력 값을 변경할 수 있다. 따라서 변환된 모델은 원래 학습 체크포인트(Training Checkpoint)와 동일하게 동작한다고 가정해서는 안 되며 독립적으로 검증되어야 한다.

하드웨어별 최적화(Hardware-Specific Optimization)는 대상 엣지 플랫폼(Target Edge Platform)을 고려하여 수행되어야 한다. 하나의 플릿은 산업용 PC(Industrial PC), 독립형 GPU(Discrete GPU), NVIDIA Jetson, 신경망 처리 장치(Neural Processing Unit, NPU), 비전 처리 장치(Vision Processing Unit, VPU), CPU 또는 맞춤형 가속기(Custom Accelerator)를 함께 사용할 수 있다. 각각의 플랫폼은 서로 다른 정밀도 모드(Precision Mode), 텐서 형식(Tensor Format), 메모리 할당(Memory Allocation), 연산자 융합(Operator Fusion), 배치 설정(Batch Setting), 실행 라이브러리(Runtime Library)를 요구할 수 있다. 업데이트 워크플로는 하나의 논리 모델(Logical Model Version)에 연결된 여러 배포 변형(Deployment Variant)을 생성하면서 각 패키지의 호환성 메타데이터를 명확히 유지해야 한다.

양자화(Quantization), 가지치기(Pruning), 지식 증류(Knowledge Distillation), 그래프 최적화(Graph Optimization)는 지연 시간(Latency), 메모리 사용량, 전력 소비, 저장 공간 요구량을 줄이기 위해 적용될 수 있다. 이러한 기술은 엣지 배포에 매우 중요하지만 정확도 감소, 신뢰도 변화(Confidence Shift), 특정 클래스 성능 저하를 유발할 수도 있다. 따라서 압축된 모델도 새로운 모델과 동일한 수준의 검증 절차를 거쳐야 한다. 엔지니어는 오프라인 성능 지표(Offline Metric), 희귀 사례(Rare Case), 신뢰도 보정(Calibration), 실행 시간(Runtime Measurement), 로봇별 승인 기준을 이용하여 원본 모델과 최적화 모델을 비교해야 한다.

배포 승인 전에 대표적인 엣지 하드웨어에서 자원 프로파일링(Resource Profiling)을 수행해야 한다. 측정 항목에는 평균 및 최악의 추론 지연 시간(Inference Latency), 메모리 사용량(Memory Consumption), 가속기 사용률(Accelerator Utilization), 프로세서 사용률(Processor Utilization), 시작 시간(Startup Time), 온도, 소비 전력(Power Draw), 실제 시스템 부하에서의 지속 성능(Sustained Performance)이 포함되어야 한다. 단독 벤치마크에서는 우수한 성능을 보이는 모델도 위치추정(Localization), 지도 작성(Mapping), 경로 계획(Planning), 데이터 기록(Recording), 통신(Communication) 등이 동시에 실행되면 성능이 저하될 수 있다. 따라서 신경망 실행 시간보다 전체 시스템 프로파일링(End-to-End System Profiling)이 더 중요하다.

호환성 검증(Compatibility Validation)은 전체 실행 환경(Execution Environment)을 대상으로 수행되어야 한다. 패키지는 프로세서 구조(Processor Architecture), 운영체제(Operating System), 드라이버 버전(Driver Version), 가속기 실행 환경(Runtime), 미들웨어(Middleware), 센서 구성(Sensor Configuration), 메시지 구조(Message Schema), 캘리브레이션 버전(Calibration Version), 사용 가능한 저장 공간과 메모리 용량에 모두 적합해야 한다. 업데이트 서비스(Update Service)는 지원되지 않는 조합을 자동으로 거부해야 한다. 이러한 판단은 임의의 파일명이나 운영자의 기억이 아니라 구조화된 로봇 자산 관리(Robot Inventory)와 모델 레지스트리(Model Registry)의 메타데이터를 기반으로 이루어져야 한다.

보안 검사(Security Check)는 패키지가 빌드 환경(Build Environment)을 떠나기 전에 모델 공급망(Model Supply Chain)을 보호해야 한다. 소스 코드(Source Code), 의존성(Dependency), 컨테이너(Container), 실행 라이브러리(Runtime Library), 모델 가중치, 설정 파일(Configuration File)은 알려진 취약점(Known Vulnerability)과 무단 변경 여부를 검사해야 한다. 최종 패키지는 암호학적 해시(Cryptographic Hash)와 디지털 서명(Digital Signature)을 생성해야 하며, 로봇은 설치 전에 이를 반드시 검증해야 한다. 서명이 없거나, 손상되었거나, 만료되었거나, 신뢰할 수 없는 패키지는 올바른 모델 버전을 포함하고 있더라도 설치되어서는 안 된다.

업데이트 패키지는 모델 레지스트리와 연결된 관리형 산출물 저장소(Controlled Artifact Repository)에 저장되어야 한다. 저장소는 실제 이진 패키지(Binary Package)를 보관하고, 모델 레지스트리는 논리적 식별(Logical Identity), 계보(Lineage), 호환성(Compatibility), 승인 정보(Approval), 수명주기 상태(Lifecycle State), 배포 제한 사항을 관리한다. 업데이트 제어기(Update Controller)는 승인된 인터페이스를 통해 패키지를 가져오고 모든 다운로드 요청을 기록해야 한다. 이러한 구조는 개인 저장소, 메신저, 추적되지 않는 파일 서버를 통한 모델 배포를 방지한다.

플릿 대상 선정(Fleet Targeting)은 어떤 로봇이 업데이트를 받을 수 있는지를 결정한다. 선정 기준은 로봇 모델, 하드웨어 프로파일, 센서 구성, 고객 현장(Customer Site), 지역, 소프트웨어 릴리스, 미션 유형, 운용 속도, 안전 등급, 네트워크 상태 등이 될 수 있다. 하나의 창고나 특정 카메라 환경에서만 검증된 모델을 다른 환경에 자동으로 배포해서는 안 된다. 대상 선정 규칙은 명확하고 검토 가능해야 하며 버전 관리되어 모델 레지스트리에 기록된 승인 조건과 연결되어야 한다.

업데이트 스케줄러(Update Scheduler)는 실제 배포 전에 로봇의 운용 준비 상태(Operational Readiness)를 확인해야 한다. 로봇이 미션을 수행 중이거나, 화물을 운반 중이거나, 제한 구역에서 작업 중이거나, 고객 공정을 지원 중이거나, 배터리가 부족한 경우에는 업데이트를 수행해서는 안 된다. 일반적으로 업데이트는 충전 중, 유지보수 시간, 대기 상태 또는 계획된 서비스 시간(Service Window)에 수행되어야 한다. 스케줄러는 미션 상태, 배터리 수준, 네트워크 품질, 예상 전송 용량, 저장 공간, 현재 온도, 롤백 가능 여부를 모두 확인한 후 업데이트를 시작해야 한다.

패키지 전송(Package Transfer)은 인증(Authentication)되고 암호화된 통신(Encrypted Communication)을 사용해야 한다. 엣지 로봇은 공장 Wi-Fi, 전용 셀룰러 네트워크, 로컬 서버, 간헐적인 통신 환경을 사용할 수 있다. 전송 프로토콜은 중단 복구(Interruption Recovery), 청크 검증(Chunk Validation), 대역폭 제어(Bandwidth Control), 무결성 검사(Integrity Check)를 지원해야 한다. 대용량 패키지는 일시적인 통신 장애가 발생해도 처음부터 다시 다운로드해서는 안 된다. 로봇은 패키지를 임시 저장 영역(Staging Area)에 보관하고 전체 패키지가 완전히 수신되고 검증되기 전까지 현재 실행 중인 시스템을 변경해서는 안 된다.

설치 전 검사(Pre-Installation Check)는 전송이 완료된 이후에도 로봇이 여전히 설치 조건을 만족하는지 확인해야 한다. 하드웨어 상태, 저장 공간, 메모리, 운영체제, 실행 라이브러리, 현재 소프트웨어 버전, 센서 구성, 캘리브레이션, 미션 상태, 배터리 수준을 다시 확인해야 한다. 다운로드 과정이 길어지는 동안 시스템 상태가 바뀔 수 있기 때문이다. 또한 알려진 정상 롤백 패키지(Known-Good Rollback Package)가 로컬에 존재하거나 복구 가능해야 한다. 안전, 호환성, 복구 조건을 만족하지 못하면 설치를 중단해야 한다.

원자적 설치(Atomic Installation)는 부분 업데이트로 인해 시스템이 불일치 상태(Inconsistent State)가 되는 것을 방지한다. 모든 파일은 비활성 배포 영역(Inactive Deployment Slot) 또는 격리된 디렉터리에 먼저 설치되어야 한다. 모델 가중치, 실행 엔진(Runtime Engine), 전처리, 후처리, 설정(Configuration), 캘리브레이션, 모니터링 설정, 의존성은 하나의 버전 관리된 단위로 함께 설치되어야 한다. 모든 무결성 검사와 구조 검사가 완료된 이후에만 활성 버전으로 전환해야 하며, 이전 정상 버전은 새 버전의 활성화가 확인될 때까지 그대로 유지되어야 한다.

시작 검증(Startup Validation)은 새로운 모델이 실제 로봇 동작에 영향을 미치기 전에 수행되어야 한다. 엣지 컴퓨터는 모델이 정상적으로 로드되고, 필요한 메모리를 확보하며, 가속기를 인식하고, 예상 입력을 받아들이고, 올바른 출력을 생성하며, 초기 지연 시간 조건을 만족하는지를 확인해야 한다. 시험용 텐서(Test Tensor)나 기록된 참조 데이터(Reference Sample)를 이용하여 변환 오류, 의존성 오류, 스키마 오류를 탐지할 수 있다. 이 단계에서 문제가 발생하면 검증되지 않은 모델이 실제 운용에 사용되지 않도록 즉시 이전 활성 버전으로 복원해야 한다.

모델 활성화(Activation)는 통제된 로봇 상태에서 수행되어야 한다. 인지, 예측, 위치추정, 내비게이션, 주행 제어와 연결된 모델은 로봇이 정지 상태이거나 유지보수 모드(Maintenance Mode)에 있을 때 활성화하는 것이 바람직하다. 활성화 이벤트는 플릿 관리 시스템(Fleet Management System)과 동기화되어 운영팀이 로봇의 상태를 정확히 이해할 수 있어야 한다. 업데이트 시스템은 시작 시간, 완료 시간, 활성화된 모델 식별자, 패키지 버전, 설정 버전, 로봇 식별자, 서비스 재시작 여부를 모두 기록해야 한다.

활성화 직후에는 짧은 사후 상태 검사(Post-Activation Health Check)를 수행해야 한다. 라이브 센서 입력(Live Sensor Input)을 이용하여 입력 속도, 텐서 크기(Tensor Shape), 출력 빈도(Output Frequency), 신뢰도 분포(Confidence Distribution), 추론 지연, 메모리 사용량, 프로세서 및 가속기 부하, 오류 로그(Error Log)를 확인해야 한다. 또한 하위 모듈(Downstream Module)이 정상적인 메시지를 수신하는지, 인터페이스 불일치가 경로 계획이나 제어에 영향을 주지 않는지도 확인해야 한다. 이러한 검사가 완료될 때까지 로봇은 제한된 상태에서 운용되는 것이 바람직하다.

섀도 모드(Shadow Mode)는 주요 업데이트에서 추가적인 안전 단계를 제공할 수 있다. 새로운 모델은 실제 데이터를 처리하지만 현재 운영 모델이 계속 로봇을 제어한다. 두 모델의 출력은 클래스, 신뢰도, 위치, 거리, 지연 시간, 불일치 유형을 기준으로 비교된다. 섀도 실행은 실제 로봇 동작을 변경하지 않고도 현장 성능과 자원 사용량을 평가할 수 있다. 다만 두 개의 모델을 동시에 실행할 수 있는 충분한 연산 자원이 필요하며, 이로 인해 현재 시스템의 성능이 저하되어서는 안 된다.

카나리 활성화(Canary Activation)는 새로운 패키지를 제한된 수의 로봇에서만 실행하도록 하여 위험을 줄인다. 선택된 로봇은 하드웨어, 현장, 센서, 운용 조건을 대표해야 하며 동시에 안전 및 사업 위험은 최소화해야 한다. 카나리 그룹은 이전 버전을 사용하는 기준 그룹(Baseline Group)과 비교되어야 한다. 배포 확대 전에는 최소 관찰 기간(Minimum Observation Time), 수행 미션 수, 성공 기준(Success Criteria), 롤백 조건, 검토 책임자를 명확하게 정의해야 한다.

엣지 모니터링(Edge Monitoring)은 모델이 활성화되는 즉시 시작되어 배포 수명주기 전체에서 계속 수행된다. 모델 수준에서는 신뢰도 분포, 출력 안정성(Output Stability), 분포 외 점수(Out-of-Distribution Score), 예측 빈도, 클래스 분포, 추론 지연, 메모리 사용량, 입력 누락, 실행 오류(Runtime Error)를 모니터링할 수 있다. 로봇 수준에서는 비상 정지(Emergency Stop), 경로 실패(Route Failure), 도킹 성공(Docking Success), 위치추정 초기화(Localization Reset), 운영자 개입, 안전 제어기 작동, 미션 완료율, 지연 시간, 에너지 사용량, 고객 보고 문제를 함께 관찰해야 한다.

로컬 상태 모니터링(Local Health Monitoring)은 클라우드 연결이 불가능한 경우에도 반드시 동작해야 한다. 엣지 시스템은 모델 충돌(Model Crash), 잘못된 출력, 과도한 지연 시간, 메모리 부족, 가속기 장애, 센서 입력 누락, 비정상 신뢰도, 온도 또는 전력 문제를 스스로 감지해야 한다. 심각한 문제가 발생하면 로봇은 대체 모델(Fallback Model)로 전환하거나, 속도를 낮추거나, 일부 기능을 비활성화하거나, 원격 지원을 요청하거나, 안전한 위치로 이동하거나, 통제된 정지를 수행해야 한다. 이러한 로컬 안전 동작은 원격 서버의 연결 여부와 관계없이 수행되어야 한다.

롤백 조건(Rollback Condition)은 배포 전에 미리 정의되어야 한다. 시작 실패, 반복적인 추론 오류(Inference Error), 허용 범위를 초과한 지연 시간, 메모리 증가, 비정상 온도, 과도한 오정지(False Stop), 미션 완료율 감소, 안전 사고, 운영자 보고는 롤백의 원인이 될 수 있다. 명확한 기술적 오류는 자동 롤백을 수행할 수 있으며, 복잡한 운용 문제는 수동 승인을 통해 롤백을 결정할 수 있다. 이전 모델, 설정, 실행 환경 패키지는 항상 함께 복원되어야 하며 서로 다른 버전이 혼합되어서는 안 된다.

롤백은 신속하고, 원자적이며, 모든 과정이 기록되어야 한다. 업데이트 시스템은 문제가 있는 패키지를 비활성화하고, 정상 버전을 복원하며, 영향을 받은 서비스를 재시작하고, 상태 검사를 수행한 뒤 플릿 관리 시스템에 통보해야 한다. 실패한 버전의 로그, 성능 지표, 입력 샘플, 설정, 로봇 상태, 장애 발생 시각도 함께 보존되어야 한다. 롤백의 목적은 단순한 복구가 아니라 근본 원인 분석(Root Cause Analysis)을 지원하고 이후 릴리스에서 같은 문제가 반복되지 않도록 하는 것이다.

대체 모델(Fallback Model)은 롤백 버전과 다르다. 롤백은 이전 릴리스를 복원하는 것이지만, 대체 모델은 주 실행 환경(Primary Runtime)이 사용할 수 없거나 신뢰하기 어려울 때 제한된 기능만 제공한다. 기하학 기반 장애물 검출기(Geometric Obstacle Detector), 단순한 신경망(Simple Neural Network), 보수적인 주행 가능성 규칙(Conservative Traversability Rule), CPU 기반 모델이 제한된 운용을 유지하도록 도울 수 있다. 대체 모델의 활성화 규칙, 자원 요구사항, 지원 기능, 속도 제한, 종료 조건은 모두 검증되고 버전 관리되어야 한다.

설정 관리(Configuration Management)는 모델 업데이트와 항상 동기화되어야 한다. 신뢰도 임계값(Confidence Threshold), 클래스 매핑(Class Mapping), 센서 캘리브레이션, 이미지 크기 조정(Image Resizing), 정규화(Normalization), 안전 여유(Safety Margin), 실행 플래그(Runtime Flag), 현장별 설정은 모델 가중치가 동일하더라도 동작을 크게 바꿀 수 있다. 검증된 모델이라도 승인되지 않은 설정과 결합되면 검증되지 않은 시스템이 된다. 따라서 패키지 매니페스트(Package Manifest)는 호환 가능한 설정 버전을 명시해야 하며 로봇은 승인 범위를 벗어난 설정을 거부해야 한다.

플릿 가시성(Fleet Observability)은 모든 로봇의 배포 상태를 보여주어야 한다. 운영팀은 어떤 모델 버전이 활성 상태인지, 어떤 패키지가 준비되어 있는지, 설치 성공 여부, 활성화 시점, 롤백 발생 여부, 현재 상태를 확인할 수 있어야 한다. 대시보드는 현장, 로봇 종류, 하드웨어 프로파일, 고객, 소프트웨어 릴리스를 기준으로 필터링을 지원해야 한다. 동시에 개별 로봇의 정확한 업데이트 이력을 조사할 수 있는 기능도 제공되어야 한다.

오프라인 또는 독립형 로봇(Offline Robot)은 별도의 업데이트 절차가 필요하지만 동일한 수준의 검증을 받아야 한다. 패키지는 로컬 유지보수 서버(Local Maintenance Server), 이동식 저장장치(Removable Media), 보안 서비스 노트북(Service Laptop), 공장 내부 네트워크를 통해 전달될 수 있다. 이 경우에도 서명 검증(Signature Verification), 호환성 검사, 원자적 설치, 상태 검증, 감사 로그(Audit Logging), 롤백 요구사항은 동일하게 적용되어야 한다. 로봇이 중앙 시스템과 다시 연결되면 배포 기록은 로컬 증거를 유지한 채 중앙 시스템과 동기화되어야 한다.

감사 가능성(Auditability)은 모델 업데이트가 실제 로봇의 물리적 동작에 영향을 주기 때문에 매우 중요하다. 승인, 패키지 생성, 서명, 다운로드, 설치, 활성화, 장애, 롤백, 운영자 개입은 모두 타임스탬프(Timestamp)가 포함된 기록을 생성해야 한다. 감사 기록에는 사용자 또는 서비스 계정(Service Account), 로봇, 모델, 패키지, 설정, 변경 이유, 결과가 포함되어야 한다. 이러한 정보는 사고 조사, 고객 지원, 품질 관리, 사이버 보안 검토, 인증(Certification), 규제 대응을 지원한다.

개인정보 보호(Privacy)는 모델 업데이트 모니터링에도 적용되어야 한다. 진단 로그(Diagnostic Log)와 수집된 샘플에는 카메라 영상, 음성, 위치, 고객 공정 정보, 운영자 활동이 포함될 수 있다. 모니터링은 상태 분석과 조사에 필요한 최소한의 정보만 수집해야 한다. 민감한 데이터는 마스킹(Masking), 암호화(Encryption), 접근 제한(Restricted Access), 지역 저장(Regional Storage), 보존 기간 제한을 적용해야 한다. 업데이트 문제 해결 과정에서 고객 데이터나 개인정보의 무분별한 복사본이 생성되어서는 안 된다.

업데이트 워크플로는 기술적인 업데이트 성공(Technical Update Success)과 실제 운용 성공(Operational Model Success)을 구분해야 한다. 하나의 패키지는 다운로드, 설치, 활성화, 실행이 모두 정상적으로 완료되더라도 특정 환경에서는 잘못된 로봇 판단을 유발할 수 있다. 따라서 배포 평가는 기술적 상태뿐 아니라 미션 완료율, 운영자 개입, 안전 사고, 고객 피드백, 희귀 사례 동작, 드리프트 신호를 함께 고려해야 한다. 이러한 요소들이 실제 운용 가치를 결정한다.

점진적인 플릿 확장(Progressive Fleet Rollout)은 초기 단계에서 충분한 근거가 확보된 이후에만 수행되어야 한다. 배포는 개발용 로봇, 내부 시험 로봇, 카나리 그룹, 특정 고객 현장, 지역 그룹, 전체 대상 플릿 순서로 확대될 수 있다. 각 단계는 배포를 중단하거나 되돌릴 수 있는 능력을 유지해야 한다. 하드웨어, 환경, 고객 정책, 운용 위험에 따라 일부 로봇은 서로 다른 승인 버전을 계속 사용할 수도 있다.

업데이트 빈도(Update Frequency)는 개선 속도와 운용 안정성 사이의 균형을 유지해야 한다. 지나치게 빈번한 변경은 검증 부담을 증가시키고, 설정 조합을 복잡하게 만들며, 지원 조직을 혼란스럽게 하고, 현장 동작에 대한 신뢰를 떨어뜨릴 수 있다. 반대로 업데이트가 너무 드물면 알려진 문제가 오랫동안 해결되지 않고 중요한 개선이 지연될 수 있다. 조직은 단순히 빠른 업데이트를 목표로 하기보다 모델의 위험도, 운용 긴급성, 고객 영향, 검증 능력, 롤백 가능성을 종합적으로 고려한 릴리스 정책을 수립해야 한다.

모든 엣지 모델 릴리스에는 문서화(Documentation)가 함께 제공되어야 한다. 릴리스 패키지는 모델 식별자(Model Identity), 목적(Purpose), 계보(Lineage), 지원 로봇, 하드웨어 요구사항, 실행 환경 의존성(Runtime Dependency), 설정 호환성(Configuration Compatibility), 검증 근거(Validation Evidence), 자원 프로파일(Resource Profile), 배포 범위, 모니터링 계획, 알려진 제한 사항, 롤백 절차, 변경 요약(Change Summary)을 포함해야 한다. 자동 생성 기능은 기술 정보를 채우고, 엔지니어는 운용상의 해석과 주의사항을 추가해야 한다. 이러한 문서는 개발, 배포, 운영, 안전, 지원 조직 모두가 활용할 수 있어야 한다.

조직의 책임(Organizational Responsibility)은 명확하게 구분되어야 한다. AI 엔지니어는 모델을 준비하고 검증한다. 로봇 엔지니어는 모델이 인지, 경로 계획, 제어, 안전 계층과 올바르게 통합되는지를 확인한다. 플랫폼 엔지니어(Platform Engineer)는 모델 레지스트리, 빌드 시스템(Build System), 산출물 저장소(Artifact Repository), 배포 서비스, 가시성 시스템(Observability)을 운영한다. 플릿 운영팀(Fleet Operations)은 업데이트 일정을 관리하고 현장 준비 상태를 확인한다. 보안, 개인정보 보호, 안전, 품질, 제품 조직은 위험을 검토하고 배포 범위를 승인한다. 명확한 책임 분담은 업데이트 과정의 누락이나 충돌을 방지한다.

성숙한 엣지 AI 모델 업데이트 워크플로(Edge AI Model Update Workflow)는 모델 개발과 실제 물리적 운용을 하나의 통제된 흐름으로 연결한다. 패키징(Packaging), 최적화(Optimization), 호환성 검증, 안전한 전송(Secure Transfer), 원자적 설치(Atomic Installation), 단계적 활성화(Staged Activation), 로컬 상태 모니터링(Local Health Monitoring), 플릿 가시성(Fleet Observability), 롤백(Rollback)이 모두 체계적으로 연결된다. 모든 로봇은 자신이 사용하는 모델, 패키지, 설정, 승인 기록과 연결되어 있으며, 이러한 관리 체계를 통해 자율이동로봇(AMR) 플릿은 안전성(Safety), 사이버 보안(Cybersecurity), 추적성(Traceability), 유지보수성(Maintainability), 운용 연속성(Operational Continuity)을 유지하면서도 지속적으로 향상된 인공지능을 도입할 수 있다.

## 15.06 Runtime Model Monitoring

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

런타임 모델 모니터링(Runtime Model Monitoring)은 로봇이 실제 환경에서 운용되는 동안 머신러닝 모델(Machine Learning Model)의 동작을 지속적으로 관찰하는 과정이다. 자율이동로봇(Autonomous Mobile Robot, AMR) 시스템에서는 실시간 성능이 센서, 하드웨어, 소프트웨어 타이밍(Software Timing), 환경 조건, 운용 맥락(Operational Context), 하위 경로 계획 및 제어 모듈과의 상호작용에 따라 달라지므로 오프라인 검증(Offline Validation)만으로 모델 품질을 판단할 수 없다. 따라서 런타임 모니터링은 모델 수준 신호(Model-Level Signal)와 로봇 수준 결과(Robot-Level Outcome)를 연결하여 비정상 동작을 탐지하고, 조사하고, 제한하며, 향후 개선 활동으로 전환할 수 있도록 한다.

런타임 모니터링의 목적은 단순히 기술 통계(Technical Statistics)를 수집하는 것이 아니다. 주요 역할은 배포된 모델이 승인된 성능, 자원, 안전, 환경 경계 안에서 계속 동작하는지를 판단하는 것이다. 모델은 소프트웨어 오류 없이 실행되면서도 신뢰할 수 없는 예측, 과도한 지연 시간(Latency), 불안정한 신뢰도(Confidence), 익숙하지 않은 조건에서의 잘못된 판단을 생성할 수 있다. 따라서 모니터링은 모델이 실행되고 있는지뿐 아니라 그 동작이 운용상 허용 가능한 상태를 유지하는지도 함께 평가해야 한다.

모니터링은 기대 동작(Expected Behavior)을 명확하게 정의하는 것에서 시작된다. 각 배포 모델에는 지원 입력 형식, 정상 추론 주기(Inference Frequency), 예상 지연 시간, 메모리 범위, 신뢰도 동작, 클래스 분포(Class Distribution), 오류 허용 범위, 하드웨어 프로파일(Hardware Profile), 환경 도메인(Environmental Domain), 알려진 제한 사항을 정의한 모니터링 사양(Monitoring Specification)이 있어야 한다. 이러한 기대값은 검증 근거(Validation Evidence)와 배포 승인 기록(Deployment Approval Record)에서 도출되어야 한다. 문서화된 기준선(Baseline)이 없으면 정상 변동과 중대한 성능 저하를 구분하기 어렵다.

모든 모니터링 기록에는 모델 식별 정보(Model Identity)가 포함되어야 한다. 로그와 지표는 정확한 모델 버전, 배포 패키지, 실행 엔진(Runtime Engine), 전처리 설정(Preprocessing Configuration), 후처리 설정(Postprocessing Configuration), 캘리브레이션 데이터(Calibration Data), 로봇 소프트웨어 버전, 하드웨어 프로파일, 활성 기능 설정과 연결되어야 한다. 동일한 가중치 파일(Weight File)을 사용하는 두 로봇도 실행 환경이나 설정 구성 요소가 다르면 서로 다른 동작을 보일 수 있다. 완전한 식별 정보는 엔지니어가 문제를 재현할 수 있도록 하고, 호환되지 않는 배포 간의 잘못된 비교를 방지한다.

입력 모니터링(Input Monitoring)은 모델이 유효하고 예상된 데이터를 수신하는지를 확인한다. 카메라 모델의 경우 해상도, 프레임 속도(Frame Rate), 노출(Exposure), 밝기, 흐림(Blur), 영상 압축(Image Compression), 타임스탬프 연속성, 프레임 누락률을 포함할 수 있다. 라이다(LiDAR) 또는 레이더(Radar) 모델에서는 포인트 밀도(Point Density), 스캔 주파수, 거리 분포(Range Distribution), 반사도(Reflectivity), 패킷 손실(Packet Loss), 동기화 상태를 모니터링할 수 있다. 유효하지 않거나, 지연되거나, 손상되거나, 불완전한 센서 입력은 신경망 자체가 변경되지 않았더라도 모델 품질을 저하시킬 수 있다.

모델 출력은 센서 상태에 직접 의존하므로 센서 상태(Sensor Health)는 모델 모니터링과 연결되어야 한다. 먼지, 물, 진동, 렌즈 가림(Lens Obstruction), 캘리브레이션 변화(Calibration Shift), 케이블 고장, 온도, 기계적 손상은 입력 분포(Input Distribution)를 변화시킬 수 있다. 모니터링 시스템은 비정상적인 예측을 센서 진단 정보와 연관시켜야 하며, 즉시 모델 고장으로 결론 내려서는 안 된다. 이러한 구분은 올바른 대응이 모델 재학습인지, 센서 청소인지, 재캘리브레이션(Recalibration)인지, 하드웨어 수리인지, 설정 수정인지 판단하는 데 도움을 준다.

전처리 모니터링(Preprocessing Monitoring)은 원시 입력이 예상한 방식으로 정확히 변환되는지를 확인한다. 이미지 크기 조정(Image Resizing), 자르기(Cropping), 정규화(Normalization), 색상 변환(Color Conversion), 포인트 클라우드 필터링(Point-Cloud Filtering), 좌표 변환(Coordinate Transformation), 시간 정렬(Temporal Alignment)은 모델 동작을 변화시킬 수 있다. 소프트웨어 업데이트로 인해 모델 패키지는 동일한데 전처리 단계 하나가 우발적으로 변경될 수 있다. 런타임 검사는 추론 시작 전에 입력 크기, 값 범위, 정규화 통계, 변환 성공 여부, 스키마 호환성(Schema Compatibility)을 확인해야 한다.

추론 지연 시간(Inference Latency)은 로봇 시스템에서 가장 중요한 런타임 지표 중 하나이다. 정확한 출력을 생성하더라도 모델이 지나치게 느리게 동작하면 안전하지 않거나 운용상 사용할 수 없다. 모니터링은 평균 지연 시간, 백분위 지연 시간(Percentile Latency), 최악 지연 시간, 대기열 지연(Queue Delay), 전처리 시간, 추론 시간, 후처리 시간, 종단 간 응답 시간(End-to-End Response Time)을 측정해야 한다. 또한 로봇 속도가 높거나, 프로세서 부하가 크거나, 열 부하(Thermal Stress)가 높거나, 데이터 기록 및 네트워크 활동이 동시에 발생할 때 지연 시간이 증가하는지도 기록해야 한다.

평균 처리 시간만큼 시간 변동성(Timing Variation)도 중요하다. 모델이 일반적으로 30밀리초 안에 실행되더라도 메모리 압박(Memory Pressure), 가속기 자원 경쟁(Accelerator Contention), 가비지 컬렉션(Garbage Collection), 드라이버 동작, 열 스로틀링(Thermal Throttling)으로 인해 간헐적으로 수백 밀리초가 소요될 수 있다. 이러한 드문 지연은 제어 루프(Control Loop)를 방해하거나 오래된 인지 결과(Stale Perception)를 생성할 수 있다. 따라서 런타임 모니터링은 지터(Jitter), 마감시간 초과(Deadline Miss), 출력 데이터의 경과 시간(Output Age), 처리 주기 누락(Dropped Cycle), 다른 로봇 프로세스와의 시간 상관관계를 측정해야 한다.

처리량 모니터링(Throughput Monitoring)은 모델이 요구된 속도로 입력을 처리하는지를 확인한다. 카메라 인지(Camera Perception)는 안정적인 초당 프레임 수(Frames per Second)를 요구할 수 있으며, 지도 작성이나 검사 모델은 서로 다른 주기로 동작할 수 있다. 입력 데이터가 모델의 처리 속도보다 빠르게 도착하면 대기열이 증가하고 출력이 오래될 수 있다. 시스템은 입력 수신 속도, 처리 속도, 건너뛴 샘플(Skipped Sample), 대기열 깊이(Queue Depth), 적체 시간(Backlog Duration)을 추적해야 한다.

메모리 모니터링(Memory Monitoring)은 초기 할당량뿐 아니라 장기간의 변화를 포함해야 한다. 모델은 정상적으로 시작되더라도 메모리 누수(Memory Leak), 해제되지 않은 텐서(Retained Tensor), 무제한 대기열(Unbounded Queue), 로그 버퍼(Logging Buffer), 런타임 단편화(Runtime Fragmentation)로 인해 점진적으로 더 많은 메모리를 사용할 수 있다. 시스템은 CPU 메모리, 가속기 메모리, 스왑 사용량(Swap Use), 메모리 할당 실패(Allocation Failure), 시간에 따른 메모리 증가를 관찰해야 한다. 임계값은 일시적인 최대치와 장기적으로 프로세스 종료나 시스템 불안정을 유발할 수 있는 지속적인 증가를 구분해야 한다.

프로세서와 가속기 사용률(Processor and Accelerator Utilization)은 성능 변화의 원인을 이해하는 맥락을 제공한다. GPU, NPU, CPU 또는 메모리 대역폭 사용량이 높으면 추론 지연 증가나 처리량 감소를 설명할 수 있다. 반대로 사용률이 낮은데도 성능이 나쁘다면 동기화, 데이터 전송, 드라이버, 파이프라인 비효율 문제가 있을 수 있다. 모니터링은 하나의 자원 지표만 단독으로 해석하기보다 사용률을 클럭 주파수(Frequency), 온도, 전력 상태(Power State), 경쟁 작업(Competing Workload)과 함께 분석해야 한다.

모바일 로봇의 엣지 컴퓨터는 제한된 냉각 능력과 배터리 용량에서 동작하므로 온도와 전력 모니터링(Temperature and Power Monitoring)이 중요하다. 높은 온도는 프로세서 주파수를 낮추고 열 스로틀링을 유발할 수 있으며, 과도한 전력 소비는 미션 시간을 단축하거나 전기 시스템에 부담을 줄 수 있다. 런타임 모니터링은 모델 부하(Model Load)를 온도, 팬 동작(Fan Behavior), 소비 전력(Power Draw), 배터리 방전(Battery Discharge), 실제 운용 조건에서의 지속 추론 성능과 연관시켜야 한다.

출력 검증(Output Validation)은 모델 결과가 구조적·수치적으로 유효한 상태를 유지하는지를 확인한다. 시스템은 출력 누락, 숫자가 아님 값(NaN), 무한대 값(Infinite Value), 유효하지 않은 좌표, 음수 크기, 불가능한 거리, 잘못 형성된 텐서(Malformed Tensor), 지원되지 않는 클래스 식별자, 일관되지 않은 배열 크기를 탐지해야 한다. 구조적인 실패는 하위 모듈이 출력을 안전하게 사용할 수 없다는 의미이므로 즉시 로컬 복구(Local Recovery)를 실행할 수 있다.

신뢰도 모니터링(Confidence Monitoring)은 예측 점수(Prediction Score)의 통계적 동작을 관찰한다. 매우 낮은 신뢰도 값이 갑자기 증가하면 익숙하지 않은 데이터, 센서 성능 저하, 열악한 조명, 캘리브레이션 문제를 의미할 수 있다. 반대로 잘못된 조건에서 모델이 지나치게 확신하는 과신(Overconfidence)도 위험할 수 있다. 모니터링은 신뢰도 분포, 백분위수(Percentile), 엔트로피(Entropy), 상위 예측 간 점수 차이(Margin), 클래스별·현장별·미션별·환경별 신뢰도 추세를 추적해야 한다.

신뢰도 값은 신뢰도 보정(Calibration)과 관련하여 해석되어야 한다. 적절히 보정된 모델은 신뢰도 점수가 실제 정답률을 대략 반영해야 하지만, 모델 최적화, 양자화(Quantization), 도메인 변화(Domain Shift), 새로운 하드웨어 배포 이후 보정 상태가 바뀔 수 있다. 런타임 모니터링은 신뢰도 값을 이후에 확보되는 라벨(Label), 운영자 피드백, 미션 결과, 참조 센서(Reference Sensor)와 비교할 수 있다. 지속적인 불일치는 판단 임계값(Decision Threshold)이나 보정 방법을 갱신해야 함을 의미할 수 있다.

예측 안정성(Prediction Stability)은 시간에 따라 동작하는 로봇 시스템에서 중요하다. 인지 모델이 연속된 프레임 사이에서 객체 식별자, 위치, 클래스, 주행 가능성(Traversability)을 빠르게 변경하면 경로 계획이 불안정해질 수 있다. 모니터링은 라벨 깜박임(Label Flicker), 추적 중단(Track Interruption), 위치 점프(Position Jump), 신뢰도 진동(Confidence Oscillation), 경로 분류 변화, 동일 객체의 반복적인 출현과 소멸을 측정할 수 있다. 시간적 불안정성은 입력 노이즈, 약한 추적 성능, 낮은 모델 강건성(Model Robustness), 일관되지 않은 후처리를 나타낼 수 있다.

클래스 분포 모니터링(Class Distribution Monitoring)은 환경 변화나 모델 이상을 탐지하는 데 도움을 준다. 물류창고 로봇은 일반적으로 사람, 팔레트, 선반, 차량 등을 일정한 범위에서 관찰할 수 있다. 특정 클래스가 갑자기 사라지거나 다른 클래스가 과도하게 증가하면 새로운 환경 조건, 카메라 정렬 문제, 라벨 매핑 오류(Label Mapping Error), 모델 성능 저하를 의미할 수 있다. 그러나 자연스러운 미션 변화도 분포를 바꿀 수 있으므로 클래스 통계는 운용 맥락과 함께 분석되어야 한다.

분포 외 모니터링(Out-of-Distribution Monitoring)은 현재 입력이 학습 및 검증에 사용된 데이터와 크게 다른지를 추정한다. 방법에는 특징 임베딩(Feature Embedding), 재구성 오류(Reconstruction Error), 밀도 추정(Density Estimation), 거리 측정(Distance Measure), 신뢰도 패턴, 메타데이터 비교, 전용 탐지 모델이 사용될 수 있다. 목표는 특정 입력이 미지의 데이터임을 완전히 증명하는 것이 아니라 모델의 신뢰성이 낮아질 가능성이 있는 조건을 식별하는 것이다. 분포 외 신호는 이후 검토를 위해 주변 맥락과 함께 기록되어야 한다.

데이터 드리프트(Data Drift)는 시간에 따라 입력의 통계적 특성이 변하는 현상을 의미한다. 조명, 날씨, 카메라 노출, 시설 배치, 바닥 재질, 객체 외형, 로봇 속도, 센서 노화, 고객 운영 방식은 점진적으로 데이터 분포를 바꿀 수 있다. 런타임 모니터링은 현재 특징 통계를 학습 기준선이나 최근 참조 기간과 비교할 수 있다. 전체 평균만으로는 중요한 지역적 변화를 놓칠 수 있으므로 드리프트는 시나리오와 현장 단위로 평가되어야 한다.

개념 드리프트(Concept Drift)는 입력 외형이 유사하게 유지되더라도 올바른 해석이나 필요한 대응이 바뀌는 경우에 발생한다. 고객이 새로운 교통 규칙을 도입하거나, 검사 기준을 재정의하거나, 안전 구역을 변경하거나, 객체 처리 절차를 바꿀 수 있다. 모델 지표만으로는 이러한 변화를 탐지하지 못할 수 있다. 따라서 운영자 피드백, 갱신된 작업 절차, 미션 결과, 사고 기록, 비즈니스 규칙(Business Rule)을 런타임 모니터링에 통합해야 한다.

모델 불일치(Model Disagreement)는 유용한 모니터링 신호가 될 수 있다. 섀도 모드(Shadow Mode)에서 실행되는 새로운 모델은 현재 운영 모델, 대체 모델(Fallback Model), 규칙 기반 시스템(Rule-Based System), 다른 센서 모달리티(Sensor Modality)와 비교될 수 있다. 크거나 지속적인 불일치는 어려운 사례 또는 숨겨진 회귀(Regression)를 식별할 수 있다. 불일치가 반드시 새로운 모델의 오류를 의미하지는 않지만 검토 및 라벨링을 위한 목표 이벤트(Target Event)를 제공한다.

센서 간 일관성 모니터링(Cross-Sensor Consistency Monitoring)은 서로 다른 센서 시스템의 출력이 합리적인 범위에서 일치하는지를 확인한다. 카메라 검출 결과는 라이다 클러스터(LiDAR Cluster), 레이더 표적(Radar Target), 초음파 측정(Ultrasonic Measurement), 주행거리계(Odometry), 지도(Map), 디지털 트윈(Digital Twin) 데이터와 비교될 수 있다. 큰 불일치는 모델 오류, 캘리브레이션 변화, 동기화 문제, 센서 고장, 비정상 환경 조건을 의미할 수 있다. 이 방식은 운용 중 직접적인 기준 정답(Ground Truth)을 확보하기 어려울 때 특히 유용하다.

하위 영향 모니터링(Downstream Impact Monitoring)은 모델 출력을 실제 로봇 동작과 연결한다. 인지 모델이 통계적으로 안정적으로 보이더라도 비상 정지, 느린 경로, 반복적인 재계획(Replanning), 도킹 실패를 증가시킬 수 있다. 따라서 런타임 모니터링은 예측 결과를 경로 계획, 제어, 안전, 미션, 운영자 결과와 연결해야 한다. 이러한 연결은 모델 수준 변화가 전체 로봇 시스템에서 실질적인 의미를 가지는지를 판단하는 데 도움을 준다.

미션 완료율(Mission Completion Rate)은 주요 운용 지표이다. 인지, 위치추정, 예측, 검사 모델의 변화는 로봇이 지원 없이 할당된 작업을 완료할 수 있는지에 영향을 줄 수 있다. 모니터링은 성공적 완료, 부분 완료, 취소, 시간 초과(Timeout), 반복 시도, 복구 동작을 추적해야 한다. 이러한 결과는 모델 버전, 미션 유형, 현장, 로봇, 환경 조건, 실패 원인별로 분류되어야 한다.

운영자 개입(Operator Intervention)은 중요한 실제 품질 신호이다. 수동 제어 인계(Manual Takeover), 원격 지원(Remote Assistance), 경로 수정, 속도 저하, 비상 정지, 작업 취소는 모델 또는 연결된 자율주행 스택(Autonomy Stack)이 어려운 상황을 만났음을 나타낼 수 있다. 모니터링 시스템은 개입 전후의 센서 데이터, 모델 출력, 로봇 상태, 활성 소프트웨어, 운영자의 문제 분류를 보존해야 한다.

안전 제어기 작동(Safety-Controller Activation)은 일반적인 모델 지표와 별도로 모니터링되어야 한다. 독립 안전 시스템(Independent Safety System)은 AI 모델이 장애물을 놓치거나, 출력이 지연되거나, 안전하지 않은 궤적(Trajectory)을 생성할 때 로봇을 정지시킬 수 있다. 충돌이 발생하지 않더라도 보호 정지(Protective Stop)가 증가하면 모델 성능 저하를 의미할 수 있다. 모니터링은 작동 원인, 지속 시간, 위치, 로봇 속도, 감지된 위험, 모델 출력, 복구 동작을 기록해야 한다.

오정지(False Stop)와 불필요한 보수적 동작도 중요하다. 반사, 그림자, 바닥 표시, 먼지, 무해한 객체를 위험 요소로 반복 분류하면 지연과 운영자 불만이 증가할 수 있다. 모니터링은 실제 보호 동작과 불필요한 중단을 구분해야 한다. 생산성과 안전은 한쪽만 최적화하지 않고 함께 평가되어야 한다.

위치추정 및 내비게이션 모델(Localization and Navigation Model)은 특화된 런타임 지표를 요구한다. 여기에는 위치추정 공분산(Localization Covariance), 지도 정합 품질(Map Matching Quality), 위치 점프(Pose Jump), 재위치추정 빈도(Relocalization Frequency), 루프 폐쇄 동작(Loop-Closure Behavior), 위성항법 품질(GNSS Quality), 스캔 정합 점수(Scan Matching Score), 경로 이탈(Path Deviation), 계획 실패, 복구 횟수가 포함될 수 있다. 모니터링은 이러한 신호를 환경 조건과 활성 모델 버전에 연결하여 성능 저하의 원인이 인지, 지도, 위치추정, 계획, 센서 중 어디에 있는지 판단해야 한다.

검사 및 이상 탐지 모델(Inspection and Anomaly-Detection Model)은 다른 운용 지표가 필요하다. 모니터링 항목에는 검사 범위(Inspection Coverage), 영상 품질, 결함 탐지 빈도, 오경보율(False Alarm Rate), 누락된 결함 보고(Missed Defect Report), 운영자 확인, 관심영역 정렬(Region-of-Interest Alignment), 초점 품질(Focus Quality), 재검사 요청이 포함될 수 있다. 검증 라벨이 나중에 도착할 수 있으므로 시스템은 예측 결과, 검사 대상 자산, 사람 검토, 최종 품질 판단 간의 추적성을 보존해야 한다.

런타임 모니터링은 즉시 확인 가능한 상태 지표와 지연된 성능 지표를 구분해야 한다. 지연 시간, 메모리, 충돌, 입력 누락은 즉시 탐지할 수 있다. 반면 정확도, 오탐률(False-Positive Rate), 결함 재현율(Defect Recall), 미션 효과는 이후 라벨, 운영자 검토, 고객 결과가 필요할 수 있다. 모니터링 아키텍처는 서로 다른 시간 척도를 혼동하지 않으면서 실시간 경보(Real-Time Alert)와 지연 평가 파이프라인(Delayed Evaluation Pipeline)을 모두 지원해야 한다.

경보(Alerting)는 의미 있는 임계값과 맥락을 기반으로 해야 한다. 유효하지 않은 출력이나 메모리 고갈 같은 명확한 기술 오류에는 고정 임계값(Fixed Threshold)이 적합하다. 신뢰도, 클래스 분포, 드리프트에는 통계적 임계값이 더 적합할 수 있다. 동적 기준선(Dynamic Baseline)은 현장, 미션 유형, 날씨, 운용 시간대 차이를 반영할 수 있다. 경보 규칙은 과도한 오경보로 인해 운영자가 중요한 경고를 무시하게 되는 상황을 방지해야 한다.

경보 심각도(Alert Severity)는 운용 영향을 반영해야 한다. 정보성 이벤트(Informational Event)는 비정상적이지만 중요하지 않은 동작을 기록할 수 있다. 경고 이벤트(Warning Event)는 엔지니어 검토나 강화된 관찰이 필요할 수 있다. 중요 이벤트(Critical Event)는 자동 대체 모델 전환, 로봇 감속, 미션 중단, 롤백, 안전 정지를 요구할 수 있다. 심각도 정의는 대응 절차, 담당 조직, 에스컬레이션 경로(Escalation Path), 최대 대응 시간과 연결되어야 한다.

네트워크 연결이 제한될 수 있으므로 로컬 경보 처리(Local Alert Handling)가 필수적이다. 엣지 컴퓨터는 클라우드 확인을 기다리지 않고 중요 장애를 탐지하고 사전에 정의된 안전 대응을 적용해야 한다. 로컬 규칙은 모델 프로세스 재시작, 대체 모델 전환, 로봇 감속, 기능 비활성화, 미션 중단, 안전 정지를 수행할 수 있다. 로컬 시스템은 증거를 보존하고 통신이 복구되면 이벤트를 중앙 모니터링 시스템과 동기화해야 한다.

중앙 집중형 가시성(Centralized Observability)은 여러 로봇과 현장에 대한 플릿 수준의 가시성을 제공한다. 중앙 플랫폼은 지표, 로그, 배포 상태, 경보, 미션 결과, 드리프트 신호를 통합할 수 있다. 이를 통해 팀은 모델 버전을 비교하고, 현장별 패턴을 식별하고, 플릿 전체의 회귀를 탐지하고, 조사 우선순위를 정할 수 있다. 집계된 정보는 플릿 수준 추세에서 개별 로봇, 미션, 추론 이벤트까지 추적할 수 있는 상세도를 유지해야 한다.

대시보드(Dashboard)는 사용자 역할에 맞게 설계되어야 한다. AI 엔지니어는 신뢰도, 분포, 오류 분석을 필요로 할 수 있다. 로봇 엔지니어는 타이밍, 인터페이스, 하위 동작에 집중할 수 있다. 운영팀은 미션 상태, 개입, 로봇 가용성을 필요로 한다. 안전팀은 보호 정지, 근접 사고(Near Miss), 대체 모델 활성화를 검토할 수 있다. 경영진이나 제품 조직은 높은 수준의 신뢰성 및 고객 영향 지표를 필요로 할 수 있다.

로그(Log), 지표(Metric), 추적 정보(Trace), 이벤트 기록(Event Record)은 서로 다른 목적을 가진다. 지표는 압축된 수치 추세를 제공한다. 로그는 개별 메시지와 오류를 설명한다. 추적 정보는 처리 단계 간의 시간과 의존 관계를 보여준다. 이벤트 기록은 운영자 개입, 롤백, 안전 제어기 작동과 같은 운용 상황을 저장한다. 성숙한 모니터링 시스템은 공통 식별자(Common Identifier)를 통해 이러한 증거를 연결하여 엔지니어가 대시보드 경보에서 상세 근본 원인 정보로 이동할 수 있도록 한다.

로봇은 고주파 정보를 대량으로 생성할 수 있으므로 모니터링 데이터 용량을 통제해야 한다. 엣지 집계(Edge Aggregation), 샘플링(Sampling), 압축(Compression), 이벤트 기반 수집(Event-Triggered Capture), 계층형 보존(Tiered Retention)은 대역폭과 저장 비용을 줄일 수 있다. 일상적인 지표는 요약할 수 있지만, 중요 사고는 고해상도 맥락을 보존해야 한다. 데이터 축소 정책은 모든 센서 프레임을 지속적으로 업로드하지 않으면서도 진단에 충분한 정보를 유지해야 한다.

이벤트 기반 기록(Event-Triggered Recording)은 모델 문제 조사에 특히 유용하다. 로봇은 최근 센서 데이터, 예측 결과, 시스템 상태의 순환 버퍼(Rolling Buffer)를 유지할 수 있다. 비상 정지, 낮은 신뢰도 이벤트, 비정상적인 모델 불일치, 운영자 개입이 발생하면 해당 이벤트 이전의 버퍼와 이후 데이터가 함께 보존된다. 이를 통해 지속적인 저장 요구량을 제한하면서도 이벤트 전후의 맥락을 확보할 수 있다.

개인정보 보호 및 데이터 보호(Privacy and Data Protection)는 런타임 모니터링에 적용되어야 한다. 카메라 프레임, 음성, 위치, 고객 공정, 운영자 행동에는 민감한 정보가 포함될 수 있다. 모니터링은 필요한 데이터만 수집하고, 마스킹(Masking) 또는 익명화(Anonymization)를 적용하며, 저장 및 전송을 암호화하고, 접근을 제한하며, 보존 정책을 시행해야 한다. 국가나 현장에 따라 데이터 저장 위치와 승인 절차가 달라질 수 있다.

사이버 보안 모니터링(Cybersecurity Monitoring)은 모델과 모니터링 인프라를 모두 보호해야 한다. 예상하지 않은 모델 파일, 변경된 설정, 유효하지 않은 서명, 승인되지 않은 파라미터 변경, 의심스러운 접근, 비정상 통신은 시스템 침해(Compromise)를 의미할 수 있다. 악의적인 변경은 성능 저하처럼 보일 수 있으므로 보안 이벤트는 런타임 이상과 연관 분석되어야 한다. 감사 로그(Audit Log)는 누가 또는 어떤 서비스가 모델 관련 구성 요소를 변경했는지를 식별해야 한다.

잘못된 원격측정(Telemetry)은 문제를 숨기거나 과장할 수 있으므로 모니터링 무결성(Monitoring Integrity)이 중요하다. 지표에는 타임스탬프, 데이터 출처, 순서 정보(Sequence Information), 품질 상태가 포함되어야 한다. 센서, 엣지 컴퓨터, 중앙 서비스 간의 시계 동기화(Clock Synchronization)는 정확한 이벤트 재구성에 필요하다. 모니터링 데이터가 누락되거나 지연되는 현상 자체도 정상 동작으로 해석하지 말고 상태 이상 신호를 생성해야 한다.

임계값과 기준선은 버전 관리되어야 한다. 경보 규칙, 드리프트 탐지기, 신뢰도 한계, 집계 로직의 변경은 동일한 모델 동작에 대한 해석을 바꿀 수 있다. 따라서 모니터링 설정은 모델 및 배포 버전과 연결된 통제 산출물(Controlled Artifact)로 관리되어야 한다. 과거 분석에서는 각 시점에 어떤 모니터링 규칙이 활성화되어 있었는지를 보존해야 한다.

런타임 모니터링은 릴리스 간 모델 비교를 지원해야 한다. 엔지니어는 현재 버전과 이전 버전의 지연 시간, 신뢰도, 운영자 개입, 미션 완료율, 안전 이벤트, 에너지 사용량, 오류 패턴을 비교할 수 있어야 한다. 비교할 때는 현장, 로봇 유형, 미션 난이도, 운용 시간, 환경 조건을 통제해야 한다. 맥락 정규화(Contextual Normalization)가 없으면 더 어려운 환경에 배포된 모델이 실제로 더 우수하더라도 성능이 나빠 보일 수 있다.

카나리 모니터링(Canary Monitoring)은 소규모 업데이트 그룹과 기준 그룹을 직접 비교해야 한다. 시스템은 유사한 조건에서 기술적 지표와 운용 지표를 함께 측정해야 한다. 배포 확대는 사전에 정의된 성공 기준, 관찰 기간, 미션 수, 중요 회귀 부재에 따라 결정되어야 한다. 중요한 차이가 발견되면 더 많은 로봇에 모델을 배포하기 전에 조사해야 한다.

롤백 결정(Rollback Decision)은 모니터링 근거를 사용해야 한다. 반복적인 충돌, 잘못된 출력, 심각한 지연 같은 명확한 기술 장애는 자동 롤백을 정당화할 수 있다. 운용 성능 저하는 AI, 로봇, 안전, 운영 조직의 검토가 필요할 수 있다. 모니터링은 결정에 사용된 정확한 증거를 보존해야 하며, 여기에는 지표, 이벤트, 모델 버전, 설정, 환경 맥락, 승인 책임자가 포함되어야 한다.

모니터링이 주 모델(Primary Model)의 상태가 비정상적이거나 불확실하다고 판단하면 대체 모델(Fallback Model)이 활성화될 수 있다. 대체 모델은 정확도나 기능이 낮을 수 있지만 제한된 자원 조건에서도 예측 가능한 동작을 제공할 수 있다. 모니터링은 대체 모델이 활성화되었고, 정상이며, 호환되고, 자체 제한 조건 안에서 동작하는지를 확인해야 한다. 또한 주 모델로 복귀할 조건도 정의해야 한다.

사고 조사는 재현 가능한 이벤트 패키지(Reproducible Event Package)에서 시작되어야 한다. 패키지에는 선택된 센서 데이터, 모델 입력, 출력, 신뢰도 값, 런타임 지표, 로그, 추적 정보, 로봇 상태, 미션 상태, 운영자 행동, 활성 모델 식별자, 소프트웨어 버전, 캘리브레이션, 환경 메타데이터가 포함될 수 있다. 표준화된 패키지는 조사 시간을 줄이고 팀이 시뮬레이션이나 오프라인 분석에서 이벤트를 재생할 수 있도록 한다.

근본 원인 분석(Root-Cause Analysis)은 모든 이상이 모델 때문에 발생한다고 가정해서는 안 된다. 문제는 센서, 캘리브레이션, 타이밍, 하드웨어, 미들웨어, 설정, 지도, 네트워크, 하위 로직, 환경 변화, 운영자 절차에서 발생할 수 있다. 모니터링은 이러한 원인을 구분할 수 있도록 시스템 간 충분한 증거를 제공해야 한다. 실제 원인을 식별하지 않고 모델을 재학습하면 문제를 숨기거나 더 악화시킬 수 있다.

모니터링 결과는 지속적 학습 과정(Continuous Training Process)에 반영되어야 한다. 반복되는 낮은 신뢰도 이벤트, 분포 외 장면, 오정지, 미탐, 운영자 개입은 데이터 수집과 라벨링 후보가 될 수 있다. 시스템은 발생 빈도, 심각도, 새로움(Novelty), 안전 영향, 고객 영향, 예상 학습 가치(Expected Learning Value)에 따라 이벤트의 우선순위를 정해야 한다. 선택된 샘플은 현장 이벤트에서 향후 데이터셋 버전까지 완전한 계보를 유지해야 한다.

모든 모니터링 문제에 모델 재학습이 필요한 것은 아니다. 일부 문제는 임계값 조정, 신뢰도 보정, 센서 유지보수, 소프트웨어 최적화, 하드웨어 업그레이드, 지도 수정, 사용자 교육, 운용 정책 변경으로 더 적절하게 해결할 수 있다. 성숙한 조직은 머신러닝을 모든 장애의 기본 해결책으로 간주하지 않고 모니터링 증거를 사용하여 적절한 엔지니어링 대응을 선택한다.

서비스 수준 목표(Service-Level Objective)는 허용 가능한 런타임 동작을 공식화할 수 있다. 예를 들어 최대 추론 지연 시간, 최소 처리 속도, 허용 가능한 프레임 누락률, 모델 가용성(Model Availability), 최대 개입 빈도, 최소 미션 완료율을 정의할 수 있다. 이러한 목표는 모델 위험도와 운용 중요도를 반영해야 한다. 위반이 발생하면 사전에 정의된 정책에 따라 검토, 에스컬레이션, 자동 조치를 수행해야 한다.

신뢰성 분석(Reliability Analysis)은 개별 추론 이벤트뿐 아니라 장기간의 모델 가용성을 고려해야 한다. 모델이 정확하더라도 자주 재시작하거나, 장시간 동작 후 실패하거나, 온도 변화에서 성능이 저하될 수 있다. 모니터링은 가동 시간(Uptime), 충돌 빈도(Crash Frequency), 복구 시간(Recovery Time), 대체 모델 사용, 재시작 성공률, 기능 축소 상태의 지속 시간을 측정해야 한다. 이러한 지표는 모델이 실제 생산용 로봇에 충분히 신뢰할 수 있는지를 평가하는 데 도움을 준다.

연산은 배터리 기반 로봇의 운용 시간에 직접 영향을 주므로 에너지 효율(Energy Efficiency)도 런타임 모델 지표가 될 수 있다. 모니터링은 추론당 에너지, 미션당 에너지, 가속기 전력 상태, 열 부하, 모델 업데이트 전후의 배터리 소비를 비교할 수 있다. 작은 정확도 향상이 큰 운용 시간 감소를 정당화하지 못할 수 있다. 따라서 모델 평가는 미션 수준의 에너지 영향도 포함해야 한다.

플릿이 성장해도 모니터링 시스템은 확장 가능해야 한다. 수백 또는 수천 대 로봇에서 생성되는 고주파 지표는 네트워크와 중앙 저장소에 과도한 부하를 줄 수 있다. 계층형 집계(Hierarchical Aggregation)는 데이터를 로컬, 지역, 중앙 수준에서 요약할 수 있다. 현장 서버(Site Server)는 상세 분석을 처리하고 선택된 지표만 클라우드로 보낼 수 있다. 모니터링 아키텍처는 추적성을 잃지 않으면서 다양한 모델 버전, 로봇 유형, 고객, 배포 조건을 지원해야 한다.

연결이 끊기거나 보안 격리된 로봇(Air-Gapped Robot)도 모니터링을 지원해야 한다. 로컬 대시보드, 로그 저장, 경보, 이벤트 수집은 인터넷 연결 없이도 동작해야 한다. 데이터는 이후 승인된 유지보수 절차를 통해 전송할 수 있다. 연결형 플릿과 동일한 식별, 무결성, 보존, 감사 요구사항이 오프라인 모니터링에도 적용되어야 한다.

모든 모니터링 설계에는 문서화(Documentation)가 필요하다. 모델 릴리스는 필수 지표, 예상 범위, 경보 임계값, 드리프트 탐지 방식, 로컬 안전 동작, 에스컬레이션 규칙, 보존 정책, 개인정보 보호 통제, 담당 조직을 정의해야 한다. 알려진 사각지대(Known Blind Spot)도 문서화되어야 한다. 모니터링 시스템은 모든 장애를 반드시 탐지한다고 보장할 수 없으므로 배포 전에 한계를 이해해야 한다.

조직 책임(Organizational Responsibility)은 명확하게 구분되어야 한다. AI 엔지니어는 모델 동작 지표를 정의하고 예측을 분석한다. 로봇 엔지니어는 통합, 타이밍, 센서, 하위 동작을 모니터링한다. 플랫폼 엔지니어(Platform Engineer)는 원격측정, 저장소, 대시보드, 경보 시스템을 운영한다. 운영팀은 현장 이벤트를 분류하고 로봇 문제에 대응한다. 안전, 보안, 개인정보 보호, 품질, 제품 조직은 위험을 검토하고 대응 정책을 승인한다.

성숙한 런타임 모델 모니터링 시스템(Runtime Model Monitoring System)은 배포된 인공지능과 실제 운용 증거 사이에 지속적인 연결을 형성한다. 이 시스템은 입력, 전처리, 추론, 자원, 출력, 신뢰도, 드리프트, 하위 동작, 미션 결과, 안전 이벤트, 사람의 개입을 관찰한다. 중요 장애에는 로컬에서 대응하고, 플릿 전체의 가시성을 제공하며, 롤백과 대체 모델을 지원하고, 증거를 보존하며, 향후 엔지니어링 활동의 방향을 제시한다. 이러한 체계적인 구조를 통해 자율이동로봇 플릿은 변화하는 환경, 하드웨어 조건, 고객 운영, 모델 세대에서도 신뢰할 수 있는 AI 동작을 유지할 수 있다.

## 15.07 AI Governance and Approval Process

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

AI 거버넌스 및 승인(AI Governance and Approval)은 인공지능 시스템이 책임감 있게 개발되고, 검증되며, 배포되고, 모니터링되고, 폐기될 수 있도록 하기 위한 조직적, 기술적, 운영적 통제 체계를 의미한다. 자율이동로봇(Autonomous Mobile Robot, AMR) 환경에서 AI 모델은 인지(Perception), 위치추정(Localization), 내비게이션(Navigation), 검사(Inspection), 예측(Prediction), 미션 의사결정(Mission Decision)에 영향을 미치며, 이는 실제 물리적인 이동에 직접 연결된다. 따라서 거버넌스는 모델 성능을 안전(Safety), 사이버 보안(Cybersecurity), 개인정보 보호(Privacy), 품질(Quality), 법적 의무(Legal Obligation), 고객 요구사항(Customer Requirement), 운영 책임성(Operational Accountability)과 긴밀하게 연결해야 한다.

AI 거버넌스의 목적은 혁신을 늦추거나 엔지니어의 판단을 행정 절차로 대체하는 것이 아니다. 핵심 목적은 AI 기능이 실제 로봇, 작업자, 고객, 자산, 생산 공정에 영향을 미치기 전에 명확한 의사결정 권한(Decision Right), 필요한 증거(Evidence), 승인 범위(Approval Boundary), 에스컬레이션 절차(Escalation Path)를 확립하는 것이다. 성숙한 거버넌스 구조는 개발이 배포 단계에 도달하기 전에 책임, 문서 요구사항, 검토 기준, 릴리스 조건을 명확히 정의하여 오히려 조직이 더욱 효율적으로 움직일 수 있도록 한다.

거버넌스는 모델이 완성된 이후가 아니라 AI 활용 사례(Use Case)가 제안되는 시점부터 시작되어야 한다. 초기 제안서는 비즈니스 목표(Business Objective), 로봇 기능(Robotic Function), 예상 사용자, 운용 환경, 데이터 요구사항, 잠재적인 안전 영향, 목표 자율 수준(Level of Autonomy), 기존 소프트웨어 및 하드웨어와의 관계를 설명해야 한다. 이러한 초기 검토를 통해 머신러닝이 실제로 적합한 해결책인지, 보다 단순한 결정론적 방법(Deterministic Method)이 충분한지, 어떤 거버넌스 절차를 적용해야 하는지를 조기에 판단할 수 있다.

AI 시스템은 위험도(Risk)와 운영 중요도(Operational Importance)에 따라 분류되어야 한다. 유지보수 로그를 요약하는 모델은 장애물 회피에 영향을 주는 인지 모델보다 훨씬 가벼운 통제가 필요하다. 위험 분류는 물리적 안전, 자율 수준, 복구 가능성(Reversibility), 고객 영향, 개인정보 민감도, 사이버 보안 노출, 규제 관련성(Regulatory Relevance), 재무적 영향, 탐지되지 않은 실패 가능성을 종합적으로 고려해야 한다. 결정된 위험 등급은 요구되는 시험 수준, 문서화, 승인 절차, 모니터링 범위, 배포 제한을 결정한다.

모델이 사용될 운영 영역(Operational Domain)은 명확하게 정의되어야 한다. 실내 물류창고, 저속 주행, 특정 센서 구성, 일정한 조명 환경에서 승인된 모델을 실외 도로, 폭우, 고속 주행, 다른 카메라 환경에도 자동으로 사용할 수 있다고 가정해서는 안 된다. 거버넌스 기록에는 지원되는 환경, 로봇 종류, 하드웨어 프로파일, 운행 속도, 적재 조건, 사용자 그룹, 지역, 알려진 제외 사항이 명시되어야 한다. 이러한 범위는 이후 실제 배포를 제한하는 공식적인 기준이 된다.

책임(Accountability)은 명확한 조직 역할에 할당되어야 한다. 모델 소유자(Model Owner)는 AI 기능 전체와 사용 목적에 대한 책임을 가진다. 데이터 소유자(Data Owner)는 데이터셋의 적합성, 품질, 개인정보 보호, 접근 권한을 관리한다. AI 엔지니어는 모델 학습과 성능 근거를 책임지고, 로봇 엔지니어는 실제 시스템 통합과 동작을 검증한다. 안전, 보안, 개인정보 보호, 품질, 법무, 제품, 운영 조직은 각자의 전문 영역에서 위험을 검토하며, 최종 승인 권한(Final Approval Authority)은 명확하게 지정되어야 한다.

최종 책임은 AI 모델이 아니라 조직과 지정된 의사결정자에게 있어야 한다. AI 모델은 스스로 배포를 승인하거나 법적 책임을 질 수 없으며, 잔여 위험(Residual Risk)의 수용 여부를 판단할 수도 없다. 자동 평가 도구는 성능 지표를 계산하고 문제를 탐지할 수 있지만, 승인 여부는 반드시 책임 있는 사람이 증거를 해석하고 판단해야 한다. 모든 기록에는 누가, 언제, 어떤 근거를 바탕으로 결정을 내렸는지가 남아야 한다.

데이터 거버넌스(Data Governance)는 모델 승인 과정의 기초가 된다. 모든 데이터셋은 출처(Source), 수집 목적(Collection Purpose), 소유권, 접근 등급, 라이선스, 동의 근거(Consent Basis), 보존 기간, 필요한 경우 지역별 저장 제한을 명확히 가져야 한다. 기술적으로 접근 가능하다는 이유만으로 데이터가 학습 파이프라인에 포함되어서는 안 된다. 개인정보 보호, 고객 계약, 지식재산권(Intellectual Property), 수출 통제, 보안, 규제 요구사항을 충족하는지 먼저 평가해야 한다.

모델 학습 전에 데이터셋 품질(Dataset Quality)을 검토해야 한다. 검토 항목에는 데이터 완전성, 라벨 정확도(Label Accuracy), 클래스 균형(Class Balance), 시나리오 다양성, 타임스탬프 무결성, 캘리브레이션 기준, 센서 품질, 중복 데이터, 데이터 누수(Data Leakage), 중요한 운용 조건의 대표성이 포함될 수 있다. 또한 알려진 데이터 부족 영역, 희귀 사례(Rare Scenario), 성능 검증이 충분하지 않은 환경도 함께 식별해야 한다. 데이터셋이 승인되었다고 해서 완벽하다는 의미는 아니며, 제한 사항이 명확히 기록되어야 한다.

데이터셋 변경은 버전 관리(Version Control)와 재평가를 요구한다. 새로운 현장을 추가하거나, 라벨 정의를 변경하거나, 샘플을 삭제하거나, 주석을 수정하거나, 전처리를 변경하면 모델 구조가 동일하더라도 결과가 달라질 수 있다. 모든 데이터셋 릴리스에는 매니페스트(Manifest), 품질 보고서(Quality Report), 변경 요약(Change Summary), 데이터 분할(Split Definition), 승인 상태, 이전 버전과의 관계가 포함되어야 한다. 모델 학습은 항상 변경 불가능한 데이터셋 식별자(Immutable Dataset Identifier)를 참조해야 모델 계보(Lineage)를 재현할 수 있다.

모델 개발 거버넌스(Model Development Governance)는 통제된 소스 코드(Source Code), 문서화된 학습 설정(Training Configuration), 승인된 의존성(Dependency), 추적 가능한 실험(Traceable Experiment)을 요구해야 한다. 학습률(Learning Rate), 모델 구조(Architecture), 사전학습 가중치(Pretrained Weight), 데이터 증강(Augmentation), 난수 시드(Random Seed), 손실 함수(Loss Function), 압축 기법, 모델 선택 기준은 모두 기록되어야 한다. 운영 환경을 위한 후보 모델은 개인 컴퓨터에서 임의로 생성된 결과가 아니라 재현 가능한 파이프라인(Reproducible Pipeline)을 통해 생성되어야 한다.

외부 모델과 사전학습 구성 요소(Pretrained Component)는 별도의 검토가 필요하다. 오픈소스 모델(Open Source Model), 상용 API, 파운데이션 모델(Foundation Model), 합성 데이터 생성기(Synthetic Data Generator), 제3자 라이브러리는 라이선스 의무, 보안 취약점, 사용 제한, 데이터 이전 문제, 불명확한 학습 출처를 포함할 수 있다. 거버넌스는 이러한 의존성을 식별하고 해당 조건과 위험이 목표 로봇 제품에 적합한지 평가해야 한다. 외부 기술을 사용한다고 해서 내부 조직의 책임이 사라지는 것은 아니다.

모델 평가는 실제 로봇 기능에 적합한 사전 정의된 승인 기준(Acceptance Criteria)을 사용해야 한다. 단순한 전체 정확도(Aggregate Accuracy)는 대부분 충분하지 않다. 평가에는 클래스별 정밀도와 재현율(Precision and Recall), 신뢰도 보정(Calibration), 희귀 사례 성능, 강건성(Robustness), 추론 지연 시간, 메모리 사용량, 에너지 영향, 악조건 시험, 안전 관련 오류, 실제 운용 결과가 포함될 수 있다. 승인 기준은 최종 모델 선택 전에 정의되어야 결과에 따라 기준이 변경되는 상황을 방지할 수 있다.

기준 모델(Baseline)과의 비교는 반드시 수행되어야 한다. 후보 모델은 현재 운영 모델, 이전 승인 모델, 결정론적 대안, 기준 시스템과 동일한 평가 방법으로 비교되어야 한다. 비교 결과에는 개선 사항뿐 아니라 성능 저하(Regression)도 포함되어야 한다. 모델은 단독 성능만 우수하다고 승인되어서는 안 되며, 기존 기능을 허용 가능한 수준으로 유지하면서 실질적인 가치를 제공해야 한다.

시나리오 기반 검증(Scenario-Based Validation)은 로봇 AI에서 특히 중요하다. 시험은 정상 운용뿐 아니라 경계 조건(Boundary Condition), 센서 성능 저하, 특이 객체, 조명 변화, 악천후, 네트워크 단절, 높은 시스템 부하, 복구 동작, 고객별 작업 절차를 포함해야 한다. 안전과 관련된 시나리오는 평균 성능과 별도로 검토되어야 하며, 승인 여부는 선언된 운영 영역 전반에서 모델이 허용 가능한 성능을 보인다는 증거를 기반으로 결정되어야 한다.

시뮬레이션(Simulation), 기록 데이터 재생(Log Replay), 소프트웨어 기반 시험(SIL), 하드웨어 기반 시험(HIL), 실제 현장 시험(Field Trial)은 서로 다른 형태의 증거를 제공한다. 시뮬레이션은 대규모 변수 변경과 희귀 상황 시험을 가능하게 하고, 로그 재생은 실제 센서 데이터를 반복적으로 비교할 수 있도록 한다. SIL과 HIL은 인터페이스, 타이밍, 드라이버, 메모리, 가속기 문제를 드러낸다. 현장 시험은 실험실에서 재현하기 어려운 실제 환경의 영향을 확인할 수 있다. 최종 승인은 이들 모든 증거를 종합하여 이루어져야 한다.

독립적인 검토(Independent Review)는 승인 품질을 높인다. 모델을 개발한 엔지니어는 시스템을 가장 잘 이해하지만 일정 압박, 확증 편향(Confirmation Bias), 익숙한 시험 사례에 영향을 받을 수도 있다. 위험 수준에 따라 모델 학습에 직접 참여하지 않은 검토자가 필요할 수 있으며, 높은 물리적 위험이나 규제 관련 시스템의 경우 독립적인 안전, 품질, 보안 또는 외부 평가를 수행하는 것이 적절하다.

안전 검토(Safety Review)는 AI 모델이 결정론적 안전 메커니즘과 어떻게 상호작용하는지를 확인해야 한다. 비상 정지(Emergency Stop), 안전 제어기(Safety Controller), 속도 제한, 보호 구역, 충돌 방지(Collision Prevention), 대체 논리(Fallback Logic), 안전 상태(Safe State)가 불확실한 AI 출력에만 의존해서는 안 된다. 모델의 실패 형태(Failure Mode)는 문서화되어야 하며, 모델이 잘못 동작하거나 지연되거나 사용할 수 없는 경우에도 독립적인 보호 계층이 효과적으로 동작해야 한다.

사이버 보안 승인(Cybersecurity Approval)은 전체 모델 공급망(Model Supply Chain)을 대상으로 수행되어야 한다. 학습 환경, 소스 저장소, 의존성, 빌드 시스템, 모델 레지스트리, 산출물 저장소, 배포 서비스, 엣지 장치, 모니터링 채널은 모두 공격 대상이 될 수 있다. 검토 항목에는 접근 제어(Access Control), 취약점 분석(Vulnerability Scanning), 코드 서명(Code Signing), 패키지 서명, 비밀 정보 관리(Secrets Management), 무결성 검증, 감사 로그(Audit Log), 안전한 업데이트 메커니즘, 사고 대응이 포함되어야 한다. 기술적으로 우수한 모델이라도 공급망이 손상되면 안전하지 않다.

개인정보 보호 검토(Privacy Review)는 데이터 수집, 학습, 평가, 배포, 모니터링 전 과정을 포함해야 한다. 카메라, 오디오, 위치 정보, 작업자 정보, 고객 공정 데이터, 검사 데이터는 민감한 정보를 포함할 수 있다. 거버넌스는 데이터 최소화(Minimization), 동의(Consent), 마스킹(Masking), 익명화(Anonymization), 암호화(Encryption), 접근 제한, 보존 정책, 지역별 저장 요구사항을 적용해야 한다. 이러한 보호 조치는 초기 데이터 준비뿐 아니라 런타임 모니터링과 사고 조사 과정에서도 유지되어야 한다.

설명 가능성(Explainability)의 요구 수준은 모델의 기능과 위험도에 맞추어 결정되어야 한다. 모든 신경망의 판단을 사람이 이해할 수 있는 규칙으로 완전히 설명할 수는 없지만, 검토자는 모델의 목적, 주요 입력, 성능 한계, 알려진 실패 형태, 신뢰도 한계, 중요한 설계 선택 이유를 이해할 수 있어야 한다. 영향력이 큰 의사결정의 경우 중요도 분석(Saliency Analysis), 특징 분석(Feature Study), 제거 실험(Ablation Test), 사례와 반례, 구조화된 운영자 설명이 근거로 사용될 수 있다.

인간 감독(Human Oversight)은 추상적인 원칙이 아니라 실제 운영 메커니즘으로 정의되어야 한다. 거버넌스는 운영자가 언제 AI 동작을 검토하고, 무시하고, 일시 중지하고, 수정하거나 종료할 수 있는지를 명확히 정의해야 한다. 또한 사람의 개입이 항상 필요한지, 예외 상황에서만 필요한지, 실시간 개입이 불가능한지를 규정해야 한다. 감독 체계는 인터페이스, 교육, 대응 시간, 권한, 업무 부담까지 함께 평가되어야 한다.

승인 단계(Approval Gate)는 주요 생명주기 전환 시점에 맞추어 정의되어야 한다. 일반적으로 활용 사례 승인, 데이터 승인, 학습 승인, 후보 모델 등록, 기술 검증, 안전 검토, 보안 및 개인정보 승인, 현장 시험 승인, 제한적 배포, 전체 운영 릴리스 단계를 둘 수 있다. 각 단계는 필요한 증거, 의사결정자, 가능한 결과, 재진입 조건을 정의해야 한다. 해결되지 않은 고위험 문제가 다음 단계로 넘어가지 않도록 하는 것이 승인 단계의 목적이다.

승인 결과는 승인(Approval), 조건부 승인(Conditional Approval), 거부(Rejection), 추가 증거 요청(Request for Additional Evidence) 중 하나가 될 수 있다. 조건부 승인은 저속 운행, 특정 현장, 지정 센서, 감독 운용, 제한된 로봇 그룹과 같은 조건에서만 모델을 사용할 수 있을 때 유용하다. 가능하면 이러한 조건은 기계가 해석 가능한 형태로 정의하여 배포 시스템이 자동으로 적용할 수 있도록 해야 한다. 구두로 전달된 조건은 감사가 어렵고 쉽게 위반될 수 있다.

잔여 위험 수용(Residual Risk Acceptance)은 명시적으로 이루어져야 한다. 어떤 모델도 모든 불확실성과 실패 가능성을 제거할 수 없다. 거버넌스는 위험 완화 이후에도 남아 있는 위험, 예상 발생 가능성, 영향도, 보호 장치, 모니터링 계획, 위험 책임자를 문서화해야 한다. 승인이라는 것은 지정된 조건 아래에서 권한 있는 의사결정자가 이러한 잔여 위험을 이해하고 수용했다는 의미이며, 시스템이 절대 실패하지 않는다는 보증을 의미하지는 않는다.

모델 레지스트리(Model Registry)의 상태는 거버넌스 상태를 반영해야 한다. 후보 모델은 실험 단계(Experimental), 검토 중(Under Review), 검증 완료(Validated), 조건부 승인, 운영 승인(Production Approved), 사용 중지(Suspended), 폐기 예정(Deprecated), 종료(Retired)와 같은 상태를 거칠 수 있다. 레지스트리는 적절한 승인 상태가 없는 패키지가 운영 배포 경로로 이동하지 못하도록 해야 한다. 승인 기록, 검증 근거, 제한 사항, 만료일, 책임자는 모델 버전과 함께 유지되어야 한다.

운영 승인(Production Approval)은 단순한 가중치 파일이 아니라 전체 배포 단위(Deployment Unit)를 대상으로 해야 한다. 승인 대상에는 모델, 전처리, 후처리, 실행 엔진, 설정, 캘리브레이션, 임계값, 클래스 매핑, 의존성, 하드웨어 변형, 모니터링 규칙이 포함될 수 있다. 이 중 하나라도 변경되면 모델 동작이 달라질 수 있으므로, 어떤 변경이 전체 재승인을 요구하는지, 제한된 회귀 검토만 필요한지, 단순 행정 변경으로 처리할 수 있는지를 명확히 정의해야 한다.

승인 이후에도 변경 관리(Change Control)가 필요하다. 모델 재학습, 데이터셋 업데이트, 양자화, 실행 환경 변환(Runtime Conversion), 임계값 조정, 센서 교체, 소프트웨어 인터페이스 변경, 하드웨어 업그레이드, 현장 확대는 모두 검증된 동작에 영향을 줄 수 있다. 모든 변경은 영향도에 따라 분류되어야 하며, 위험이 낮은 변경은 간소화된 절차를 적용할 수 있지만 중요한 변경은 이전 승인 단계로 되돌아가야 한다. 이러한 분류 역시 문서화되고 검토 가능해야 한다.

단계적 배포(Staged Deployment)는 위험을 제한하면서 실제 운영 근거를 확보한다. 새롭게 승인된 모델은 먼저 섀도 모드(Shadow Mode), 내부 시험 로봇, 카나리 플릿(Canary Fleet), 특정 고객 현장, 제한된 지역에서 실행될 수 있다. 각 단계는 모니터링 지표, 성공 기준, 관찰 기간, 중단 조건, 롤백 권한을 정의해야 한다. 현재 확보된 증거를 넘어 배포를 확대하려면 별도의 명시적 승인이 필요하다.

런타임 모니터링(Runtime Monitoring)은 거버넌스의 일부이며 독립된 기술 활동이 아니다. 승인 과정에서는 모델 상태, 자원 사용량, 드리프트(Drift), 안전, 미션, 운영자, 보안 관련 지표를 사전에 정의해야 한다. 임계값, 경보 수준(Alert Severity), 에스컬레이션 절차, 로컬 안전 대응, 검토 책임 역시 배포 전에 결정되어야 한다. 적절한 모니터링이 불가능한 모델은 특히 정답(Ground Truth)이 늦게 확보되거나 실패를 즉시 발견하기 어려운 경우 운영 배포에 적합하지 않을 수 있다.

정기 검토(Periodic Review)는 승인된 모델이 시간이 지나도 계속 적합한지를 확인해야 한다. 환경, 고객 운영 방식, 규제, 하드웨어, 데이터셋, 공격 기법, 조직 목표는 모두 변화할 수 있다. 검토는 일정 주기로 수행하거나 사고, 드리프트, 신규 현장, 주요 소프트웨어 릴리스, 장기 운용, 큰 성능 변화가 발생했을 때 수행할 수 있다. 계속된 승인은 과거 결정이 아니라 현재의 증거를 기반으로 해야 한다.

승인에는 만료일(Expiration Date) 또는 재검토 시점(Review Date)이 포함될 수 있다. 이는 증거가 충분하지 않거나 환경이 빠르게 변화하는 경우 유용하다. 만료 전에 모델 소유자는 최신 모니터링 결과, 사고 이력, 드리프트 분석, 고객 피드백, 보안 상태, 검증 근거를 제출해야 한다. 이를 기반으로 승인 연장(Renewal), 제한 강화, 모델 교체, 사용 중지, 폐기를 결정할 수 있다.

사고 거버넌스(Incident Governance)는 안전 사고, 근접 사고(Near Miss), 개인정보 침해, 보안 문제, 예기치 않은 모델 동작, 주요 운영 장애를 어떻게 보고하고 조사할지를 정의해야 한다. 즉각적인 대응에는 배포 중단, 로봇 격리, 증거 보존, 대체 시스템 활성화, 모델 롤백이 포함될 수 있다. 사고 조사는 모델뿐 아니라 센서, 데이터, 소프트웨어, 하드웨어, 설정, 운영자, 환경, 조직 절차까지 함께 검토해야 한다.

조사 이후에는 시정 조치(Corrective Action)와 예방 조치(Preventive Action)가 수행되어야 한다. 시정 조치는 현재 문제를 해결하고, 예방 조치는 유사한 문제가 다른 곳에서 반복될 가능성을 줄인다. 조치에는 모델 재학습, 데이터셋 확장, 캘리브레이션 수정, 소프트웨어 수정, 추가 시험, 강화된 모니터링, 절차 개선, 운영자 교육, 하드웨어 변경, 거버넌스 절차 개선이 포함될 수 있다. 완료 여부는 단순 기록이 아니라 실제 검증을 통해 확인되어야 한다.

사용 중지 권한(Suspension Authority)은 명확해야 한다. 신뢰할 수 있는 위험이 발생하면 안전, 보안, 품질, 운영 책임자는 전체 승인위원회를 기다리지 않고 모델 릴리스를 즉시 중단할 권한을 가져야 한다. 절차에는 누가 중지할 수 있는지, 어떤 로봇이 영향을 받는지, 운영은 어떻게 계속되는지, 어떤 증거를 보존하는지, 어떤 조건에서 복귀할 수 있는지가 정의되어야 한다. 물리 시스템에서는 신속한 사용 중지가 매우 중요하다.

롤백 승인(Rollback Approval)은 배포 이전에 준비되어야 한다. 일부 기술 장애는 자동 롤백이 가능하지만 복잡한 운영 문제는 사람의 승인이 필요할 수 있다. 거버넌스는 정상 버전(Known-Good Version), 대체 기능(Fallback Capability), 롤백 조건, 통신 절차, 롤백 이후 검토를 정의해야 한다. 조직이 안전하게 복구할 수 없는 릴리스는 승인되어서는 안 된다.

문서화(Documentation)는 엔지니어링, 운영, 감사, 향후 검토를 지원할 수 있을 만큼 충분해야 한다. 필요한 산출물에는 활용 사례 정의, 위험 분류, 데이터셋 카드(Dataset Card), 모델 카드(Model Card), 실험 계보(Experiment Lineage), 평가 보고서, 안전 평가, 보안 검토, 개인정보 보호 검토, 현장 시험 결과, 승인 기록, 배포 제한 사항, 모니터링 계획, 롤백 절차, 사고 이력, 변경 기록이 포함될 수 있다. 문서 품질은 조직이 AI를 효과적으로 관리할 수 있는 능력에 직접적인 영향을 준다.

기록은 모델 위험도, 제품 생명주기, 고객 계약, 법적 요구사항에 따라 보존되어야 한다. 감사 추적(Audit Trail)은 누가 모델을 생성하고, 검토하고, 승인하고, 배포하고, 중지하고, 변경하고, 폐기했는지를 기록해야 한다. 또한 시각, 사유, 근거, 조건, 결과도 포함해야 한다. AI가 안전, 품질, 고객 자산, 규제에 영향을 미치는 경우 변경 불가능한 기록(Immutable Record)이 특히 중요하다.

의사결정 회의는 이미 문서화된 내용을 반복하는 것이 아니라 해결되지 않은 위험과 근거를 중심으로 이루어져야 한다. 검토 자료에는 목적, 위험 등급, 성능, 제한 사항, 검증 결과, 미해결 문제, 배포 범위, 모니터링 계획, 롤백 준비 상태가 요약되어야 한다. 검토자는 충분한 분석 시간을 확보할 수 있도록 사전에 자료를 받아야 하며, 승인 회의가 이미 배포가 결정된 이후의 형식적인 절차가 되어서는 안 된다.

거버넌스 지표(Governance Metric)는 프로세스 자체의 효과를 측정할 수 있다. 검토 기간, 문서 완성률, 조건부 승인 비율, 미해결 문제 수, 배포 사고, 롤백 빈도, 만료된 승인, 모니터링 범위, 감사 예외, 시정 조치 완료 시간 등이 유용한 지표가 될 수 있다. 목적은 모든 문제를 없애는 것이 아니라 중요한 위험이 지속적으로 발견되고 해결되는지를 확인하는 것이다.

프로세스 효율성(Process Efficiency)은 가능한 부분에서 자동화를 통해 향상되어야 한다. 템플릿, 모델 카드, 데이터셋 매니페스트, 자동 시험 보고서, 레지스트리 워크플로, 정책 검사, 서명 검증, 배포 자격 규칙, 승인 대시보드는 반복적인 업무를 줄일 수 있다. 자동화는 반복 가능한 통제를 수행하되 최종 판단은 책임 있는 사람이 해야 한다. 체크리스트 통과만으로 안전이 보장된다고 생각하게 만드는 자동화는 오히려 위험할 수 있다.

거버넌스는 다양한 개발 속도를 지원해야 한다. 연구 단계에서는 높은 유연성이 필요하지만 운영 배포는 강력한 통제가 필요하다. 격리된 개발 환경(Sandbox Environment)은 운영 로봇이나 민감한 데이터를 위험에 노출하지 않고 빠른 실험을 가능하게 한다. 연구 결과가 실제 현장 적용 단계에 가까워질수록 점진적으로 더 엄격한 거버넌스 절차를 적용해야 한다.

고객별 거버넌스(Customer-Specific Governance)가 필요한 경우도 있다. 전 세계적으로 승인된 모델이라도 특정 고객은 현장 승인(Site Acceptance), 보안 검토, 개인정보 계약, 현장 검증(Local Validation), 설정 승인을 요구할 수 있다. 거버넌스 기록은 공통 모델 승인과 고객별 승인을 구분하여 관리해야 한다. 이렇게 하면 공통 검증 결과를 재사용하면서도 각 현장의 책임을 유지할 수 있다.

규제 의무(Regulatory Obligation)는 거버넌스의 일부로 관리되어야 한다. 적용 대상에는 기계 안전(Machinery Safety), 기능 안전(Functional Safety), 사이버 보안, 개인정보 보호, 제조물 책임(Product Liability), 작업장 규정, 데이터 이전, 산업별 검사 기준, 새로운 AI 규제가 포함될 수 있다. 어떤 규제가 적용되는지는 법무 및 규정 준수 조직이 판단해야 하며, 엔지니어링 문서는 근거를 제공할 수 있지만 독자적으로 규제 준수를 선언해서는 안 된다.

윤리적 고려(Ethical Consideration)는 규제보다 더 넓은 범위를 포함할 수 있다. 로봇 AI는 작업자의 자율성, 감시(Surveillance), 접근성(Accessibility), 공정성(Fairness), 업무 설계(Job Design), 고객 신뢰(Customer Trust)에 영향을 줄 수 있다. 거버넌스는 데이터 수집이 적절한지, 사용자가 시스템의 한계를 이해하는지, 인간의 존엄성이 존중되는지, 기술이 불필요한 피해를 초래하지 않는지를 검토해야 한다. 이러한 윤리 검토는 추상적인 선언이 아니라 실제 설계와 운영 결정에 연결되어야 한다.

외부 공급업체(Supplier)로부터 중요한 AI 구성 요소를 제공받는 경우 공급업체 거버넌스(Supplier Governance)가 필요하다. 계약에는 모델 버전, 업데이트 정책, 보안 취약점, 데이터 처리, 지원 기간, 사고 통보, 성능 주장, 지식재산권, 검증 근거 접근 권한이 포함되어야 한다. 로봇을 실제 배포하는 조직은 공급업체가 관리하는 위험과 스스로 책임져야 하는 위험을 명확히 이해해야 한다.

검토자와 운영자의 교육 및 역량(Training and Competence)은 매우 중요하다. 승인 참여자는 모델의 역할, 주요 성능 지표, 실패 형태, 자신의 전문성 한계를 이해해야 한다. 운영자는 비정상 동작을 식별하고, 이벤트를 보고하고, 안전 대응을 수행하며, 자동화에 과도하게 의존하지 않도록 교육받아야 한다. 시간과 권한, 기술적 이해가 부족한 사람에게 형식적인 책임만 부여하면 거버넌스는 효과를 잃게 된다.

이해 상충(Conflict of Interest)과 일정 압박(Schedule Pressure)은 적절히 관리되어야 한다. 프로젝트 팀은 상업적 일정이나 고객 요구 때문에 충분한 검증 없이 배포를 서두를 수 있다. 독립 검토자는 조직 내 불이익 없이 문제를 제기할 수 있어야 한다. 승인 기준은 일정 때문에 비공식적으로 완화되어서는 안 되며, 예외가 필요한 경우에는 문서화되고, 기간이 제한되며, 위험 평가와 적절한 승인 절차를 거쳐야 한다.

AI 거버넌스는 위험 수준에 비례해야 한다. 저위험 모델에 지나친 절차를 적용하면 자원이 낭비되고 조직은 절차를 우회하려고 할 수 있다. 반대로 고위험 로봇 기능에 충분한 통제를 적용하지 않으면 사람과 조직은 허용할 수 없는 위험에 노출된다. 위험 기반 접근(Risk-Based Approach)은 가장 큰 영향을 미치는 영역에 거버넌스 자원을 집중하도록 한다. 위험 분류 기준과 임계값은 주기적으로 검토되어 현실성과 신뢰성을 유지해야 한다.

폐기(Retirement)는 거버넌스 생명주기의 일부이다. 모델은 새로운 모델로 교체되거나, 하드웨어 변경, 지원 종료, 성능 저하, 보안 위험, 규제 변화, 운영 필요성 감소로 인해 폐기될 수 있다. 폐기 절차에서는 배포 자격을 제거하고, 필요한 기록을 보존하며, 영향을 받는 로봇을 식별하고, 정책에 따라 산출물을 보관 또는 삭제하며, 더 이상 지원되지 않는 모델이 운영 중이지 않음을 확인해야 한다. 고객과 운영팀에는 사전 통보가 필요할 수도 있다.

성숙한 AI 거버넌스 및 승인 프로세스(AI Governance and Approval Process)는 아이디어에서 실제 운영까지 이어지는 통제된 경로를 제공한다. 운영 영역을 정의하고, 위험을 분류하며, 데이터를 관리하고, 재현 가능한 개발을 요구하고, 기술 및 시스템 성능을 평가하며, 안전·보안·개인정보·법적 요구사항을 검토하고, 책임 있는 승인자를 지정하며, 단계적 배포를 수행하고, 현장 동작을 모니터링하며, 사고·변경·폐기를 관리한다. 이러한 구조는 자율이동로봇 조직이 혁신과 신뢰를 동시에 유지할 수 있도록 한다.

가장 강력한 거버넌스 시스템은 문서나 위원회만으로 구성되지 않는다. 거버넌스는 엔지니어링 도구, 모델 레지스트리, 데이터 플랫폼, 배포 서비스, 모니터링 시스템, 접근 제어, 운영 절차에 내재되어야 한다. 승인되지 않은 데이터셋은 운영 학습에 사용할 수 없고, 승인되지 않은 모델은 배포할 수 없으며, 호환되지 않는 로봇은 패키지를 설치할 수 없고, 중요한 모니터링 이벤트는 자동으로 정의된 대응 절차를 시작해야 한다. 이때 거버넌스는 단순한 정책이 아니라 기술 아키텍처의 일부가 된다.

궁극적으로 AI 승인(AI Approval)은 일회성 결정이 아니라 지속적인 책임이다. 모델은 가정(Assumption), 운영 영역, 보호 장치, 모니터링, 근거가 유효한 동안에만 승인 상태를 유지할 수 있다. 새로운 데이터셋, 새로운 현장, 새로운 하드웨어 플랫폼, 새로운 소프트웨어 릴리스, 사고, 환경 변화는 모두 승인 판단에 영향을 줄 수 있다. 지속적인 거버넌스는 배포된 로봇 AI가 조직의 목표, 고객의 기대, 인간의 안전, 사이버 보안, 개인정보 보호, 품질, 운영 신뢰성과 지속적으로 일치하도록 보장한다.

## 15.08 MLOps Checklists and Templates

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

MLOps 체크리스트 및 템플릿(MLOps Checklists and Templates)은 로봇 시스템에 사용되는 머신러닝 모델(Machine Learning Model)을 개발하고, 검증하고, 승인하고, 배포하고, 모니터링하고, 유지관리하기 위한 반복 가능한 구조를 제공한다. 자율이동로봇(Autonomous Mobile Robot, AMR) 환경에서 이러한 도구는 비공식적인 지식에 대한 의존도를 줄이고, 중요한 기술적, 운영적, 안전, 보안, 문서화 요구사항이 적절히 검토되었는지를 팀이 확인할 수 있도록 한다. 체크리스트는 엔지니어링 판단을 대체하지 않지만, 이러한 판단을 프로젝트, 팀, 로봇 플랫폼, 배포 현장 전반에서 더욱 일관되고 감사 가능하며 전수 가능한 형태로 만든다.

MLOps 체크리스트의 주요 목적은 복잡한 모델 생명주기(Model Lifecycle)에서 핵심 활동이 누락되는 것을 방지하는 데 있다. AI 개발은 데이터 수집, 라벨링(Labeling), 학습, 평가, 통합, 엣지 최적화(Edge Optimization), 릴리스, 모니터링, 롤백(Rollback), 사고 대응을 포함한다. 각 단계에는 서로 다른 사람과 도구가 참여하며, 장애는 이들 단계 사이의 경계에서 자주 발생한다. 구조화된 체크리스트는 명확한 인계 지점(Handoff Point)을 만들고, 모델이 다음 단계로 이동하기 전에 가정, 의존성, 위험, 미해결 문제가 검토되도록 한다.

템플릿(Template)은 증거가 어떤 방식으로 문서화되어야 하는지를 정의함으로써 체크리스트를 보완한다. 체크리스트가 데이터셋 품질 검토 여부를 묻는다면, 데이터셋 보고서 템플릿(Dataset Report Template)은 출처, 소유권, 클래스 범위, 라벨링 방법, 알려진 부족 영역, 개인정보 보호 상태, 버전 식별자와 같이 반드시 기록해야 할 정보를 구체적으로 정의한다. 템플릿은 각 모델 릴리스가 유사한 정보를 예측 가능한 형식으로 제공하도록 하여 보고서 비교와 검토를 쉽게 만든다. 또한 문서를 반복적으로 새로 설계하는 데 소요되는 시간을 줄인다.

체크리스트 설계는 일반적인 소프트웨어 절차를 그대로 복사하는 것이 아니라 조직의 실제 생명주기와 일치해야 한다. 연구팀은 가벼운 실험 통제가 필요할 수 있지만, 운영용 로봇 팀은 안전 검증, 하드웨어 호환성, 운영 모니터링, 롤백 준비에 대해 더 강력한 요구사항이 필요하다. 체크리스트는 실제 승인 게이트(Approval Gate), 도구 체계, 담당 역할, 배포 환경과 연결되어야 한다. 실제 의사결정이나 위험과 관계없는 항목은 제거하거나 간소화해야 한다.

각 체크리스트 항목은 검증할 수 있을 정도로 구체적이어야 한다. "모델이 좋은가?" 또는 "안전을 고려했는가?"와 같은 질문은 신뢰할 수 있는 증거를 만들기에는 지나치게 모호하다. 더 나은 항목은 모델이 사전에 정의된 클래스별 재현율 목표를 충족했는지, 성능이 저하된 센서 시나리오를 시험했는지, 대체 동작(Fallback Behavior)을 검증했는지, 배포 패키지가 서명 검증(Signature Validation)을 통과했는지를 묻는다. 각 항목에는 기대되는 증거, 담당 검토자, 완료 상태, 남아 있는 조건이나 예외가 정의되어야 한다.

체크리스트가 단순히 항목을 체크하는 절차(Box-Ticking Exercise)가 되어서는 안 된다. 완료되었다는 것은 단순히 확인란을 선택했다는 의미가 아니라, 증거가 존재하고 실제로 검토되었다는 의미여야 한다. 고위험 항목은 보고서, 시험 로그, 대시보드, 승인 기록, 서명된 결정 문서와 연결되어야 할 수 있다. 적용되지 않음(Not Applicable)으로 표시할 수 있는 기능도 필요하지만, 그 이유를 기록해야 한다. 이는 팀이 설명 없이 어려운 요구사항을 우회하는 것을 방지한다.

활용 사례 정의 템플릿(Use-Case Definition Template)은 일반적으로 MLOps 워크플로의 첫 번째 산출물이다. 이 템플릿은 운영 목표, 대상 사용자, 로봇 기능, 환경, 지원 하드웨어, 자율 수준, 예상 출력, 하위 소비 모듈(Downstream Consumer), 비즈니스 가치를 설명해야 한다. 또한 알려진 제외 사항, 가정, 성공 기준, 모델 실패 시 잠재적인 영향도 식별해야 한다. 명확한 활용 사례 정의는 이후 팀이 불분명하거나 지속적으로 변경되는 기대사항을 기준으로 모델을 평가하는 문제를 방지한다.

위험 분류 템플릿(Risk-Classification Template)은 필요한 검증 및 승인 수준을 결정하는 데 도움을 준다. 이 템플릿은 물리적 안전, 운영 영향, 개인정보 민감도, 사이버 보안 노출, 고객 영향, 복구 가능성(Reversibility), 법적 관련성, 탐지되지 않은 실패 가능성을 평가할 수 있다. 결과는 단순히 위험 등급만 부여하는 것이 아니라 그 판단 근거도 설명해야 한다. 이후 위험 등급은 적절한 체크리스트 경로, 필수 검토자, 시험 범위, 모니터링 수준, 배포 제한을 선택하는 기준이 된다.

데이터 출처 접수 체크리스트(Data-Source Intake Checklist)는 새로 수집되거나 외부에서 획득한 데이터가 사용 가능한지를 확인한다. 이 체크리스트는 출처 식별, 수집 목적, 소유권, 라이선스, 고객 허가, 동의, 접근 제한, 지역적 제약, 수출 제한, 보존 규칙을 검증해야 한다. 로봇 데이터의 경우 센서 유형, 캘리브레이션 상태, 로봇 구성, 현장, 미션, 환경 조건, 수집 소프트웨어 버전도 기록할 수 있다. 이러한 정보는 이후 재현성과 분석을 위해 필수적이다.

데이터셋 카드 템플릿(Dataset Card Template)은 특정 데이터셋 릴리스의 구성과 한계를 요약한다. 여기에는 데이터셋 식별자, 버전, 생성일, 출처 구성, 샘플 수, 클래스 분포, 시나리오 범위, 라벨링 절차, 품질관리 방법, 학습·검증·시험 데이터 분할, 알려진 편향, 누락된 조건, 개인정보 보호 조치, 의도된 사용 목적이 포함되어야 한다. 또한 부적절한 사용 사례도 문서화하여 데이터셋이 설계되지 않은 환경이나 의사결정에 적용되는 것을 방지해야 한다.

라벨링 체크리스트(Labeling Checklist)는 주석(Annotation)이 일관된 기준에 따라 정의되고 생성되는지를 검증한다. 라벨 정의, 예시, 경계 사례(Edge Case), 품질 기준, 검토자 책임, 의견 불일치 해결 절차가 문서화되었는지를 확인해야 한다. 인지 및 검사 모델의 경우 가림(Occlusion) 규칙, 객체 경계, 결함 유형, 신뢰도 태그, 무시 영역(Ignored Region), 시간적 일관성이 포함될 수 있다. 라벨 정의가 변경되면 데이터셋 버전 업데이트와 영향 분석을 수행해야 한다.

데이터 품질 템플릿(Data-Quality Template)은 자동 및 수동 검토 결과를 모두 기록해야 한다. 일반적인 정보에는 누락 파일, 손상된 샘플, 타임스탬프 공백, 중복 데이터, 클래스 불균형, 센서 누락, 캘리브레이션 오류, 주석 불일치, 데이터 분할 간 분포 차이가 포함된다. 보고서는 무엇이 탐지되었고, 무엇이 수정되었으며, 무엇이 아직 해결되지 않았고, 이러한 한계가 모델 평가에 어떤 영향을 주는지를 설명해야 한다. 품질 증거는 학습에 사용된 정확한 데이터셋 버전과 연결되어야 한다.

데이터 분할 체크리스트(Data-Split Checklist)는 데이터 누수(Data Leakage)와 오해를 일으키는 평가를 방지하기 위해 필요하다. 학습, 검증, 시험 데이터가 실제 운영 문제에 적합한 기준으로 분리되었는지를 검증해야 한다. 인접 프레임이 거의 동일한 경우 무작위 프레임 단위 분할은 부적절할 수 있다. 로봇 데이터셋은 미션, 경로, 날짜, 현장, 자산, 날씨, 로봇 개체별로 분리해야 할 수 있다. 체크리스트는 분할 논리를 설명하고 시험 데이터가 모델 선택에 사용되지 않았음을 확인해야 한다.

실험 계획 템플릿(Experiment-Plan Template)은 대규모 학습을 시작하기 전에 모델 개발 방법을 정의한다. 이 템플릿은 가설, 기준 모델, 후보 아키텍처, 데이터셋, 평가 지표, 자원 예산, 예상 위험, 의사결정 기준을 기록해야 한다. 제거 실험(Ablation Study), 최적화 전략, 강건성 시험, 목표 하드웨어도 포함할 수 있다. 이러한 항목을 사전에 정의하면 비구조적인 실험을 줄이고 특정 모델이나 학습 방법이 선택된 이유를 팀이 이해할 수 있다.

실험 추적 체크리스트(Experiment-Tracking Checklist)는 학습 실행이 재현 가능하고 상호 비교 가능한지를 확인한다. 소스 코드 커밋, 데이터셋 버전, 설정 파일, 난수 시드(Random Seed), 의존성 버전, 사전학습 가중치, 실행 환경, 하드웨어, 출력 산출물, 평가 결과를 확인해야 한다. 각 실험에는 고유 식별자가 부여되어야 한다. 실패한 실행도 유용한 증거를 제공할 수 있으므로 기록되어야 하며, 실패 사례를 제외하면 중요한 한계나 낭비된 시도를 숨길 수 있다.

학습 설정 템플릿(Training Configuration Template)은 모델 동작에 실질적으로 영향을 주는 모든 파라미터를 설명해야 한다. 여기에는 아키텍처, 최적화 알고리즘(Optimizer), 학습률, 학습률 스케줄, 배치 크기, 손실 함수, 데이터 증강, 샘플링 정책, 종료 기준, 체크포인트 정책, 혼합 정밀도 설정(Mixed-Precision Setting)이 포함된다. 연속 학습 또는 전이 학습(Transfer Learning)의 경우 고정된 계층, 유지 데이터, 이전 모델 출처, 파국적 망각(Catastrophic Forgetting)을 줄이기 위한 방법도 기록해야 한다. 설정 파일은 통제 산출물로 저장되어야 한다.

기준 평가 체크리스트(Baseline Evaluation Checklist)는 후보 모델이 적절한 대안과 비교되었는지를 확인한다. 비교 대상에는 운영 모델, 이전 승인 버전, 결정론적 방법, 더 단순한 신경망, 공급업체 모델, 사람 기반 절차가 포함될 수 있다. 모든 후보는 동일한 데이터셋과 시나리오에서 평가되어야 한다. 체크리스트는 개선뿐 아니라 성능 저하도 함께 보고하도록 요구해야 한다. 새로운 모델은 단 하나의 대표 지표가 개선되었다는 이유만으로 선택되어서는 안 된다.

모델 평가 보고서 템플릿(Model Evaluation Report Template)은 엔지니어링 의사결정을 지원하는 형태로 성능을 제시해야 한다. 전체 지표, 클래스별 지표, 신뢰도 보정, 신뢰도 분포, 오류 사례, 희귀 상황 결과, 지연 시간, 처리량, 메모리 사용량, 하드웨어 프로파일을 포함해야 한다. 개발 단계 결과와 최종 시험 결과는 구분되어야 하며, 필요한 경우 통계적 불확실성도 설명해야 한다. 알려진 약점과 지원되지 않는 조건은 부록에 숨기지 말고 명확하게 보여야 한다.

강건성 시험 체크리스트(Robustness-Testing Checklist)는 이상적인 조건 밖에서의 성능을 검증한다. 조명 변화, 흐림, 진동, 비, 안개, 먼지, 부분 가림, 센서 노이즈, 입력 누락, 타임스탬프 지연, 특이 객체, 지도 변경, 고속 주행, 프로세서 과부하가 포함될 수 있다. 체크리스트는 시뮬레이션으로 생성한 손상과 실제 현장 근거를 구분해야 한다. 또한 신뢰도가 낮거나 입력이 승인된 운영 영역 밖에 있을 때 기대되는 동작을 정의해야 한다.

시나리오 검증 템플릿(Scenario-Validation Template)은 개별 모델 출력이 아니라 실제 로봇 상황을 중심으로 시험을 구성한다. 각 시나리오는 초기 조건, 환경, 로봇 구성, 모델 버전, 기대 동작, 통과 기준, 안전 예방조치, 수집된 증거를 설명해야 한다. 보행자 횡단, 팔레트 장애물, 좁은 통로 주행, 도킹 접근, 위치추정 성능 저하, 어려운 표면 검사, 센서 중단 후 복구 등이 예시가 될 수 있다. 결과는 재현 가능해야 하며 관련 로그와 연결되어야 한다.

소프트웨어 인더루프 체크리스트(Software-in-the-Loop Checklist)는 완전한 실제 로봇 없이도 목표 소프트웨어 아키텍처 안에서 모델을 검증한다. 인터페이스, 메시지 스키마, 타임스탬프, 전처리, 후처리, 설정 로딩, 예외 처리, 출력 유효성, 경로 계획 또는 검사 모듈과의 호환성을 확인해야 한다. 기록 데이터를 재생하여 버전 간 비교도 수행할 수 있다. 반복성이 요구되는 경우 결정론적 동작을 검증하고 허용 가능한 수치 차이를 문서화해야 한다.

하드웨어 인더루프 체크리스트(Hardware-in-the-Loop Checklist)는 배포 패키지가 실제 엣지 하드웨어, 드라이버, 가속기, 센서, 통신 인터페이스와 함께 정상 동작하는지를 확인한다. 시작 시간, 지속 지연 시간, 메모리 안정성, 온도, 전력 소비, 처리량, 동시 작업 부하에서의 동작을 측정해야 한다. 장시간 운용과 재시작 복구 시험도 포함해야 한다. 하드웨어별 문제는 워크스테이션 개발 환경에서 드러나지 않는 경우가 많으므로 이 체크리스트는 필수적이다.

모델 최적화 체크리스트(Model-Optimization Checklist)는 ONNX 변환, TensorRT 컴파일, 양자화(Quantization), 가지치기(Pruning), 지식 증류(Distillation)와 같은 변환 및 가속 작업을 다룬다. 수치적 호환성, 지원되지 않는 연산, 캘리브레이션 데이터셋 품질, 정확도 변화, 지연 시간 개선, 메모리 감소, 하드웨어 의존성, 대체 동작을 검증해야 한다. 변환 과정에서 원래 모델이 동일하더라도 출력이 달라질 수 있으므로 최적화된 산출물은 별도의 배포 단위로 관리해야 한다.

모델 카드 템플릿(Model Card Template)은 승인된 AI 모델의 운영 정보를 간결하게 요약한다. 모델 식별 정보, 목적, 지원 운영 영역, 아키텍처, 학습 데이터 참조, 평가 결과, 알려진 한계, 예상 입력 및 출력, 하드웨어 요구사항, 신뢰도 해석, 안전 역할, 모니터링 요구사항, 금지된 사용을 포함해야 한다. 모델 카드는 모든 개발 세부정보에 접근하지 않아도 엔지니어링, 운영, 품질, 승인 조직이 이해할 수 있어야 한다.

배포 준비 체크리스트(Deployment-Readiness Checklist)는 후보 모델이 통제된 현장 사용을 시작할 준비가 되었는지를 판단한다. 기술 검증, 안전 검토, 보안 검토, 개인정보 승인, 패키지 무결성, 레지스트리 상태, 목표 장치 호환성, 모니터링 설정, 롤백 준비, 운영자 문서, 지원 책임을 확인해야 한다. 미해결 문제는 심각도에 따라 평가해야 한다. 단순히 학습이 완료되었거나 평가 지표가 좋아 보인다는 이유만으로 모델을 배포해서는 안 된다.

릴리스 패키지 템플릿(Release Package Template)은 로봇에 배포되는 모든 구성 요소를 설명해야 한다. 모델 가중치, 실행 엔진, 전처리 코드, 후처리 코드, 설정, 클래스 매핑, 캘리브레이션 파일, 의존성 버전, 서명, 체크섬(Checksum), 호환성 규칙, 모니터링 설정이 포함될 수 있다. 패키지 매니페스트는 실제 설치된 항목을 정확히 검증할 수 있도록 해야 한다. 전체 실행 맥락이 없는 가중치 파일만으로는 통제된 운영 릴리스에 충분하지 않다.

보안 체크리스트(Security Checklist)는 모델 배포 전에 적용되어야 한다. 산출물 서명, 무결성 검사, 의존성 취약점 분석, 접근 권한, 비밀정보 관리, 안전한 전송, 신뢰할 수 있는 저장소, 장치 인증, 업데이트 권한, 감사 로그를 확인해야 한다. 로봇이 서명되지 않았거나 호환되지 않는 패키지를 거부하는지도 검증해야 한다. 보안 통제는 학습 및 빌드 환경에서 엣지 설치와 롤백에 이르는 전체 파이프라인을 보호해야 한다.

개인정보 체크리스트(Privacy Checklist)는 배포 및 모니터링이 승인된 데이터 처리 규칙을 준수하는지 확인한다. 어떤 센서 데이터가 처리되고, 저장되고, 업로드되고, 보존되고, 공유되는지를 식별해야 한다. 마스킹, 익명화, 암호화, 지역별 저장, 접근 제한, 삭제 일정이 요구될 수 있다. 이벤트 기반 기록(Event-Triggered Recording)과 사고 패키지도 동일한 요구사항을 따라야 한다. 현장, 센서, 보존 기간, 데이터 흐름이 변경되면 개인정보 승인을 갱신해야 한다.

현장 시험 계획 템플릿(Field-Trial Plan Template)은 제한된 실제 환경 평가를 어떻게 수행할지를 정의한다. 시험 목표, 로봇 개체, 현장, 운영자, 기간, 미션 유형, 모델 버전, 비교 그룹, 성공 기준, 중단 조건, 안전 통제, 데이터 수집, 의사소통 절차를 명시해야 한다. 시험 관찰과 운영 승인을 구분해야 하며, 성공적인 현장 시험은 소수의 시연에 대한 비공식적인 인상보다 구조화된 증거를 생성해야 한다.

운영자 준비 체크리스트(Operator-Readiness Checklist)는 현장 사용을 담당하는 사람이 모델과 대응 절차를 이해하는지를 확인한다. 운영자는 의도된 동작, 한계, 경고 신호, 개입 방법, 대체 모드, 사고 보고 절차, 비상 대응을 알고 있어야 한다. 교육 완료는 문서화되어야 한다. 또한 인터페이스가 활성 모델 상태, 기능 축소 상태, 업데이트 대기 상태, 롤백 상태를 명확하게 표시하는지도 확인해야 한다.

단계적 배포 체크리스트(Staged-Deployment Checklist)는 섀도 모드에서 카나리, 파일럿, 전체 배포로의 진행을 지원한다. 각 단계는 적용 가능한 로봇, 현장, 미션 제한, 관찰 기간, 지표, 경보 임계값, 성공 기준, 확대 승인 권한을 정의해야 한다. 비교를 위한 기준 그룹이 유지되는지도 확인해야 한다. 중요한 조건이 발생하면 배포를 자동 또는 수동으로 중단해야 하며, 확대는 수집된 증거에 대한 명시적 검토를 거쳐야 한다.

카나리 릴리스 템플릿(Canary-Release Template)은 새 모델을 가장 먼저 받는 소규모 그룹을 기록한다. 로봇 식별자, 현장, 패키지 버전, 시작 시점, 비교 기준, 예상 미션 수, 모니터링 지표, 사고 연락처, 롤백 절차를 포함해야 한다. 결과는 지연 시간과 메모리 같은 기술 지표뿐 아니라 미션 완료, 운영자 개입, 안전 정지, 생산성, 에너지 사용과 같은 운영 지표도 비교해야 한다. 결론은 확대, 수정, 롤백 중 하나를 지원해야 한다.

런타임 모니터링 체크리스트(Runtime-Monitoring Checklist)는 운영 릴리스 전에 관찰 가능성(Observability)이 활성화되어 있는지를 검증한다. 모델 식별, 입력 품질, 센서 상태, 추론 지연 시간, 처리량, 메모리, 온도, 출력 유효성, 신뢰도, 드리프트, 모델 불일치, 미션 결과, 운영자 개입, 안전 장치 작동, 보안 이벤트를 포함해야 한다. 대시보드 접근, 로컬 경보 처리, 데이터 보존, 타임스탬프 동기화, 에스컬레이션 경로도 확인해야 한다. 모니터링 자체의 장애도 경보를 발생시켜야 한다.

모니터링 계획 템플릿(Monitoring-Plan Template)은 어떤 지표를 수집하고, 어디에서 처리하며, 어떻게 집계하고, 비정상 상황에서 어떤 조치를 수행할지를 정의한다. 각 지표에 대해 예상 범위, 경고 임계값, 중요 임계값, 평가 시간 범위, 담당 팀, 대응 방법을 기록해야 한다. 즉시 확인 가능한 기술 상태와 지연된 정확도 또는 품질 측정을 구분해야 한다. 환경 차이가 큰 경우 현장별 기준선이 필요할 수 있다.

경보 대응 체크리스트(Alert-Response Checklist)는 모니터링이 문제를 탐지했을 때 운영자와 엔지니어가 일관되게 대응할 수 있도록 한다. 심각도, 초기 격리, 증거 보존, 통보 경로, 대체 동작, 롤백 권한, 조사 책임자, 복구 기준을 정의해야 한다. 로컬 조치에는 프로세스 재시작, 모델 전환, 감속, 미션 중단, 안전 상태 진입이 포함될 수 있다. 이 체크리스트는 압박이 큰 사고 상황에서 대응 지연을 줄여야 한다.

롤백 준비 체크리스트(Rollback-Readiness Checklist)는 조직이 실패한 릴리스에서 복구할 수 있는지를 확인한다. 검증된 정상 모델, 보존된 패키지, 호환성, 롤백 명령, 로컬 저장 공간, 활성화 절차, 검증 시험, 담당 권한자, 의사소통 계획을 확인해야 한다. 연결이 제한된 로봇도 안전한 버전으로 되돌아갈 수 있어야 한다. 롤백은 실제 사고 중에 작동할 것이라고 가정하지 말고 배포 전에 시험해야 한다.

사고 보고서 템플릿(Incident-Report Template)은 조사와 향후 학습에 충분한 정보를 기록해야 한다. 시간, 로봇, 현장, 미션, 모델 버전, 소프트웨어 버전, 센서 상태, 환경 조건, 관찰된 동작, 안전 영향, 운영자 조치, 로그, 지표, 보존 데이터가 포함될 수 있다. 보고서는 확인된 사실과 가정을 구분해야 한다. 초기 보고서가 불완전할 수 있지만, 이후 업데이트에는 근본 원인, 시정 조치, 예방 조치, 종료 근거가 기록되어야 한다.

근본 원인 분석 템플릿(Root-Cause-Analysis Template)은 모델, 데이터, 센서, 소프트웨어, 하드웨어, 설정, 네트워크, 환경, 인간 요인을 포함하여 조사를 구성할 수 있다. 사건의 시간 순서를 재구성하고, 기여 조건을 식별하고, 예상 동작과 실제 동작을 비교하며, 가설을 시험해야 한다. 이 템플릿은 증거 없이 모델을 원인으로 단정하는 것을 방지해야 한다. 많은 AI 사고는 학습 결함보다 통합 또는 운영상의 문제에서 발생한다.

시정 및 예방 조치 템플릿(Corrective-and-Preventive-Action Template)은 사고, 감사 지적, 반복적인 모니터링 경보 이후 생성된 조치를 기록한다. 각 조치에는 담당자, 우선순위, 목표 일자, 검증 방법, 종료 근거가 있어야 한다. 조치에는 모델 변경, 데이터 수집, 라벨링, 캘리브레이션, 소프트웨어 수정, 하드웨어 유지보수, 모니터링 개선, 절차 변경, 운영자 교육이 포함될 수 있다. 종료는 단순히 수행되었다는 기록이 아니라 조치가 실제로 효과가 있었음을 보여주는 증거를 요구해야 한다.

지속적 학습 체크리스트(Continuous-Training Checklist)는 향후 모델 개선을 위해 현장 데이터를 사용하는 과정을 관리한다. 이벤트 선택 기준, 데이터 사용 가능성, 개인정보 검토, 라벨링 상태, 데이터셋 버전 관리, 드리프트 분석, 기준 모델 유지, 재학습 전략, 회귀 시험, 승인 요구사항을 확인해야 한다. 현장 데이터가 자동으로 다음 학습 주기에 포함되어서는 안 된다. 선택은 학습 가치, 심각도, 발생 빈도, 새로움, 운영 관련성을 기준으로 이루어져야 한다.

변경 요청 템플릿(Change-Request Template)은 데이터, 모델, 임계값, 하드웨어, 실행 환경, 센서, 인터페이스, 배포 범위에 대한 변경을 문서화한다. 변경 이유, 영향을 받는 구성 요소, 예상 이점, 위험, 필요한 시험, 롤백 계획, 승인 경로를 설명해야 한다. 변경은 잠재적 영향에 따라 경미, 중간, 주요로 분류해야 한다. 이 분류에 따라 간소화된 검토 또는 전체 재승인 여부가 결정된다.

모델 비교 템플릿(Model-Comparison Template)은 여러 후보 모델이나 버전을 검토할 때 유용하다. 핵심 지표, 자원 요구사항, 지원 시나리오, 알려진 약점, 배포 복잡성, 모니터링 요구사항, 운영 영향을 나란히 비교해야 한다. 모든 판단을 하나의 점수로 강제해서는 안 된다. 안전, 지연 시간, 정확도, 에너지, 유지보수성, 고객 요구사항은 명시적인 판단이 필요한 상충 관계를 포함할 수 있다.

승인 기록 템플릿(Approval-Record Template)은 최종 의사결정을 간결하게 제공해야 한다. 모델, 데이터셋, 패키지, 운영 영역, 검토된 증거, 승인자, 결정 일자, 결정 결과, 잔여 위험, 조건, 배포 범위, 모니터링 요구사항, 만료일, 롤백 버전을 식별해야 한다. 결과는 승인, 조건부 승인, 거부, 추가 증거 요청이 될 수 있다. 조건은 실제로 적용하고 감사할 수 있을 만큼 구체적이어야 한다.

정기 검토 체크리스트(Periodic-Review Checklist)는 운영 중인 모델이 배포 후에도 계속 적합한지를 확인한다. 모니터링 추세, 드리프트, 사고, 고객 피드백, 운영자 개입, 보안 상태, 하드웨어 변경, 신규 규제, 현장 확대, 미해결 시정 조치를 검토해야 한다. 검토 결과에 따라 승인 갱신, 제한 변경, 추가 검증 요청, 모델 사용 중지, 폐기를 결정할 수 있다. 기존 가정이 변경된 경우 과거 승인이 자동으로 계속 유효해서는 안 된다.

폐기 체크리스트(Retirement Checklist)는 오래된 모델을 안전하게 제거하도록 한다. 대체 계획, 영향을 받는 로봇, 배포 자격 제거, 패키지 보관 또는 삭제, 고객 통보, 기록 보존, 모니터링 종료, 지원되지 않는 인스턴스가 남아 있지 않다는 검증을 확인해야 한다. 폐기된 모델을 참조하는 종속 소프트웨어나 보고서도 식별해야 한다. 폐기는 단순히 새로운 배포를 중단하는 것이 아니라 통제된 생명주기 단계이다.

MLOps 절차 자체도 시간이 지나면서 변경되므로 템플릿 소유권과 버전 관리가 중요하다. 각 체크리스트와 템플릿에는 소유자, 버전, 승인일, 개정 이력, 검토 일정이 있어야 한다. 용어, 시험 기준, 승인 역할, 증거 요구사항이 변경되면 사용자에게 전달되어야 한다. 과거 프로젝트는 당시 사용한 템플릿 버전을 보존해야 과거 의사결정을 정확히 해석할 수 있다.

디지털 워크플로(Digital Workflow)는 체크리스트의 효과를 높일 수 있다. 데이터 카탈로그, 실험 추적기, 모델 레지스트리, 이슈 관리 시스템, 배포 플랫폼, 모니터링 대시보드와 통합하면 증거를 자동으로 연결할 수 있다. 필수 정보가 누락되면 다음 단계 진행을 차단할 수 있으며, 승인 상태는 배포 자격을 제어할 수 있다. 자동화는 수동 입력을 줄이지만, 의사결정의 근거를 가리거나 불완전한 증거가 유효해 보이도록 해서는 안 된다.

체크리스트 지표(Checklist Metric)는 MLOps 절차의 약점을 드러낼 수 있다. 조직은 불완전한 문서, 반복되는 예외, 검토 기간, 배포 게이트 실패, 모니터링 누락, 롤백 사건, 미해결 위험, 기한이 지난 시정 조치를 추적할 수 있다. 이러한 지표는 문제를 보고한 팀을 처벌하기보다는 절차를 개선하는 데 사용되어야 한다. 건강한 거버넌스 문화는 숨겨진 장애보다 조기에 발견된 문제를 더 가치 있게 평가한다.

체크리스트를 효과적으로 사용하려면 교육이 필요하다. 엔지니어, 검토자, 운영자, 관리자는 각 산출물이 왜 필요한지, 어떤 증거가 적절한지, 언제 에스컬레이션이 필요한지를 이해해야 한다. 신규 구성원은 잘 작성된 템플릿 예시와 일반적인 오류를 교육받아야 한다. 공통 이해가 없으면 팀마다 같은 양식을 서로 다르게 작성하여 비교, 감사, 의사결정에서의 가치가 감소한다.

MLOps 체크리스트는 위험도에 비례해야 한다. 영향이 낮은 실험 모델은 더 짧은 절차를 사용할 수 있지만, 안전 관련 인지 또는 내비게이션 모델은 포괄적인 증거가 필요하다. 모든 프로젝트에 동일한 절차를 강제해서는 안 된다. 위험 기반 템플릿(Risk-Based Template)은 연구 속도를 유지하면서 사람, 자산, 고객 운영, 규제 의무에 영향을 미치는 운영 시스템에 강력한 통제를 제공한다.

성숙한 MLOps 체크리스트 및 템플릿 라이브러리(MLOps Checklists and Templates Library)는 조직의 경험을 재사용 가능한 엔지니어링 실무로 전환한다. 이 라이브러리는 모델 생명주기 전반에서 무엇을 정의하고, 시험하고, 검토하고, 승인하고, 모니터링하고, 보존해야 하는지를 체계적으로 기록한다. 각 항목을 증거, 소유권, 위험, 의사결정 권한과 연결함으로써 일관된 릴리스, 더 빠른 검토, 명확한 책임, 안전한 배포, 자율이동로봇 플릿 전반의 지속적인 개선을 지원한다.
