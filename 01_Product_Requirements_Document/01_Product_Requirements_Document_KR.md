**Volume 10. AMR Engineering Process and Development Manual**

# Chapter01. Product Requirements Document

## 01.01 PRD Overview and Objectives

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

제품 요구사항 문서(Product Requirements Document, PRD)는 자율이동로봇(Autonomous Mobile Robot, AMR) 제품이 무엇을 달성해야 하는지, 왜 개발되어야 하는지, 그리고 개발 전 과정에서 성공 여부를 어떻게 평가할 것인지를 정의하는 가장 핵심적인 기준 문서이다. PRD는 단순한 기능 목록이 아니라, 사업 이해관계자(Business Stakeholder), 고객(Customer), 시스템 아키텍트(System Architect), 소프트웨어 엔지니어(Software Engineer), 기계 설계 엔지니어(Mechanical Engineer), 전기 설계 엔지니어(Electrical Engineer), 인공지능(AI) 연구원, 생산(Manufacturing) 조직, 품질보증(Quality Assurance, QA) 조직, 현장 운영(Operation) 조직이 동일한 목표를 공유하도록 만드는 공통 기준이다. 구현이 시작되기 전에 목표와 요구사항을 명확하게 문서화함으로써 모호성을 줄이고 의사소통의 차이를 최소화하며, 이후의 모든 엔지니어링 활동이 일관된 방향에서 진행될 수 있는 기반을 마련한다. 본 내용은 첨부된 엔지니어링 매뉴얼에서 제품 요구사항 문서(Product Requirements Document) 장의 첫 번째 항목으로 구성되어 있다.

현대의 AMR 개발은 서로 다른 우선순위와 기술적 제약을 가진 다양한 공학 분야가 동시에 참여하는 복합적인 개발 과정이다. 기계 엔지니어(Mechanical Engineer)는 구조 강성, 적재 용량(Payload Capacity), 내구성(Durability), 생산성(Manufacturability), 환경 보호(Environmental Protection)를 고려하며, 전기 엔지니어(Electrical Engineer)는 전력 분배(Power Distribution), 배터리 시스템(Battery System), 안전 회로(Safety Circuit), 센서(Sensor), 통신 인터페이스(Communication Interface)를 설계한다. 소프트웨어 개발자는 분산 소프트웨어, 미들웨어(Middleware), 실시간 제어(Real-Time Control), 클라우드 연동(Cloud Connectivity)을 담당하고, AI 엔지니어는 인지(Perception), 위치추정(Localization), 자율주행(Navigation), 의사결정(Decision Making) 알고리즘을 개발한다. 포괄적인 PRD가 없다면 각 조직은 고객 요구를 서로 다르게 해석하게 되고, 결국 프로젝트 후반부에 통합 문제와 일정 지연, 기술 부채(Technical Debt)가 발생할 가능성이 크게 증가한다.

PRD의 가장 중요한 목적은 고객의 기대(Customer Expectation)를 측정 가능한 엔지니어링 요구사항(Engineering Requirement)으로 변환하는 것이다. 고객은 대부분 기술 용어가 아니라 운영 목표(Operational Goal)의 형태로 요구사항을 제시한다. 예를 들어 물류 운반 효율 향상, 인건비 절감, 작업 안전성 향상, 반복적인 검사 업무 자동화, 장시간 무인 운용 등의 형태로 요구를 표현한다. PRD는 이러한 비즈니스 언어(Business Language)를 모든 엔지니어링 조직이 이해하고 분석하며 구현하고 검증할 수 있는 정량적인 기술 요구사항으로 변환하는 역할을 수행한다.

잘 작성된 PRD는 프로젝트의 사업적 목적(Business Motivation) 또한 명확하게 정의한다. 모든 엔지니어링 투자는 생산성 향상(Productivity Improvement), 운영 효율(Operation Efficiency), 유지보수 비용 절감(Maintenance Cost Reduction), 적용 분야 확대(Application Expansion), 시장 차별화(Competitive Differentiation)와 같은 구체적인 사업 목표와 연결되어야 한다. 엔지니어가 각각의 요구사항이 왜 필요한지를 이해하고 있다면 개발 과정에서 예상하지 못한 제약이 발생하더라도 보다 합리적인 기술적 의사결정을 내릴 수 있다. 따라서 PRD는 단순한 기술 명세서가 아니라 엔지니어링 우선순위와 사업 전략을 연결하는 전략 문서(Strategic Document)의 역할도 수행한다.

PRD의 또 다른 중요한 목적은 실제 개발이 시작되기 전에 제품 범위(Product Scope)를 명확하게 정의하는 것이다. 로봇 개발 프로젝트에서는 개발이 진행되는 동안 새로운 아이디어가 지속적으로 추가되기 때문에 범위 확장(Scope Expansion)은 일정 지연과 비용 증가의 가장 큰 원인 가운데 하나이다. 혁신은 중요하지만 통제되지 않은 기능 추가는 시스템 통합 복잡도를 증가시키고 제품 안정성을 저하시킬 수 있다. 잘 작성된 PRD는 반드시 구현해야 하는 핵심 기능과 향후 확장 가능한 선택 기능을 명확하게 구분하고, 프로젝트 범위를 벗어나는 요구사항을 정의함으로써 안정적인 제품 개발을 가능하게 한다.

PRD는 여러 조직이 동일한 용어를 사용할 수 있도록 공통 용어(Common Vocabulary)를 정의하는 역할도 수행한다. 임무 수행(Mission Execution), 위치추정 정확도(Localization Accuracy), 적재 용량(Payload Capacity), 장애물 회피(Obstacle Avoidance), 운영 가용성(Operational Availability), 도킹 정밀도(Docking Precision), 기능 안전(Functional Safety), 인지 신뢰도(Perception Confidence), 플릿 관리(Fleet Coordination), 자율 복구(Autonomous Recovery)와 같은 용어들은 프로젝트 초기에 명확하게 정의되어야 한다. 소프트웨어 개발자, 기계 설계자, AI 연구원, 고객이 동일한 용어를 서로 다르게 해석하는 경우 이러한 문제는 시스템 통합 단계에서야 드러나는 경우가 많다. PRD는 이러한 용어를 표준화(Standardization)함으로써 의사소통 오류를 줄이고 개발 효율을 향상시킨다.

요구사항 추적성(Requirement Traceability)은 PRD의 또 다른 핵심 목적이다. PRD에 정의된 모든 요구사항은 반드시 실제 고객 요구에서 출발해야 하며, 시스템 아키텍처(System Architecture), 세부 설계(Sub-System Design), 구현(Implementation), 시험 계획(Test Planning), 검증(Verification), 생산(Manufacturing), 현장 운영(Field Operation), 유지보수(Maintenance)에 이르기까지 지속적으로 연결되어야 한다. 이러한 추적성은 특정 기능이 왜 존재하는지, 어떤 고객 가치를 제공하는지, 어느 시스템이 이를 구현하는지, 그리고 최종적으로 어떻게 검증할 것인지를 명확하게 설명할 수 있도록 해준다. 특히 수백에서 수천 개의 요구사항을 포함하는 대규모 AMR 시스템에서는 이러한 추적성이 프로젝트 관리의 핵심 요소가 된다.

PRD는 시스템 아키텍처(System Architecture) 설계의 출발점이기도 하다. 시스템 아키텍트는 제품의 운영 목표, 사용 환경, 성능 요구사항, 안전 요구사항, 규제(Regulation), 향후 제품 확장 계획을 이해하지 못하면 최적의 하드웨어(Hardware) 및 소프트웨어(Software) 구조를 설계할 수 없다. 컴퓨팅 플랫폼(Computing Platform), 센서 구성(Sensor Configuration), 통신 네트워크(Communication Network), 배터리 용량(Battery Capacity), AI 가속기(AI Accelerator), 기계 구조(Mechanical Structure), 소프트웨어 모듈화(Modularization)에 대한 모든 결정은 명확한 제품 요구사항을 기반으로 이루어진다. 따라서 시스템 아키텍처는 PRD를 기반으로 도출되어야 하며, PRD보다 먼저 설계되어서는 안 된다.

성공적인 AMR 제품은 매우 다양한 운영 환경(Operational Environment)에서 동작해야 하기 때문에 PRD에는 운영 환경에 대한 명확한 정의가 반드시 포함되어야 한다. 실내 물류 로봇(Indoor Logistics Robot)은 정형화된 창고 환경에서 운행하지만, 병원 서비스 로봇(Hospital Service Robot)은 의료진과 환자 주변에서 동작하며, 실외 검사 로봇(Outdoor Inspection Robot)은 기후 변화와 다양한 지형을 견뎌야 하고, 건설 로봇(Construction Robot)은 지속적으로 변화하는 작업 환경에서 운용된다. 이러한 환경의 차이는 센서 선택(Sensor Selection), 위치추정(Localization), 환경 보호 등급(IP Rating), 이동 플랫폼(Mobility Platform), 안전 전략(Safety Strategy), AI 강건성(Robustness)에 직접적인 영향을 미친다. 따라서 PRD는 운영 환경에 대한 가정을 명확하게 문서화하여 잘못된 설계 판단을 방지한다.

PRD에 정의되는 성능 목표(Performance Objective)는 반드시 측정 가능(Measurable)하고 현실적(Realistic)이며 검증 가능(Verifiable)해야 한다. 예를 들어 "로봇은 효율적으로 주행해야 한다"와 같은 문장은 엔지니어링 측면에서 거의 의미가 없다. 대신 최고 주행 속도(Maximum Speed), 위치추정 정확도(Localization Accuracy), 장애물 탐지 거리(Obstacle Detection Range), 적재 중량(Payload Capacity), 배터리 지속시간(Battery Endurance), 도킹 반복 정밀도(Docking Repeatability), 시스템 기동 시간(System Startup Time), 인지 지연시간(Perception Latency), 임무 성공률(Mission Completion Rate), 네트워크 가용성(Network Availability), 시스템 가동률(System Uptime)과 같이 정량적인 목표를 정의해야 한다. 이러한 수치는 엔지니어가 설계 대안을 비교할 수 있도록 하며, 시험 조직이 객관적으로 요구사항 충족 여부를 검증할 수 있도록 한다.

안전 목표(Safety Objective)는 모든 AMR 제품 요구사항 문서에서 가장 중요한 요소 가운데 하나이다. 자율 로봇은 사람, 설비, 인프라, 고가의 자산과 직접 상호작용하기 때문에 기능 안전(Functional Safety)은 비상정지(Emergency Stop) 기능만으로 충분하지 않다. 위험 분석(Hazard Analysis), 충돌 회피(Collision Avoidance), 센서 이중화(Sensor Redundancy), 고장 감지(Fault Detection), 성능 저하 운전(Degraded Operation), 비상 복구(Emergency Recovery), 안전 정지(Safe Shutdown)와 같은 다양한 안전 기능이 초기 요구사항 단계에서부터 정의되어야 한다. PRD는 이러한 안전 요구사항을 프로젝트 초기에 반영함으로써 안전이 사후 기능이 아니라 시스템의 기본 설계 원칙이 되도록 만든다.

인공지능(AI)은 현대 AMR 플랫폼의 핵심 구성 요소가 되었으며, 이에 따라 AI 관련 요구사항도 PRD에서 중요한 비중을 차지한다. 인지 정확도(Perception Accuracy), 객체 인식(Object Recognition), 의미 이해(Semantic Understanding), 위치추정 신뢰도(Localization Confidence), 적응형 경로 계획(Adaptive Planning), 자율 의사결정(Autonomous Decision Making)은 모두 고객이 기대하는 핵심 기능이다. 그러나 PRD는 특정 알고리즘이나 구현 기술을 요구하기보다는 실제 운영 성능을 중심으로 요구사항을 정의해야 한다. 이러한 접근 방식은 개발 과정에서 더욱 우수한 AI 모델이 등장하더라도 고객 요구사항을 변경하지 않고 기술을 발전시킬 수 있도록 해준다.

PRD는 프로젝트 계획(Project Planning)을 수립하는 기준이 되기도 한다. 모든 AMR 프로젝트는 예산(Budget), 일정(Schedule), 컴퓨팅 자원(Computing Resource), 생산 복잡도(Manufacturing Complexity), 기술적 실현 가능성(Technical Feasibility)이라는 다양한 제약 조건을 가진다. 어떤 요구사항은 제품 성공을 결정하는 핵심 요소인 반면, 다른 요구사항은 사용자 경험(User Experience)을 향상시키는 부가 기능일 수도 있다. PRD는 이러한 요구사항의 우선순위(Priority)를 명확하게 정의하여 프로젝트 관리자(Project Manager)와 기술 리더(Technical Leader)가 제한된 자원을 가장 중요한 목표에 집중할 수 있도록 지원한다.

궁극적으로 제품 요구사항 문서(Product Requirements Document, PRD)는 고객의 기대와 엔지니어링 실행 사이를 연결하는 공식적인 계약 문서(Contractual Reference)의 역할을 수행한다. PRD는 시스템 아키텍처 설계(System Architecture Design), 세부 시스템 개발(Sub-System Development), 시스템 통합(System Integration), 시험 전략(Test Strategy), 생산 준비(Manufacturing Preparation), 현장 배치(Deployment), 향후 제품 진화(Product Evolution)에 이르기까지 모든 개발 활동의 기준이 된다. 앞으로 AMR 플랫폼은 더욱 고도화된 AI, 클라우드 서비스(Cloud Service), 엣지 컴퓨팅(Edge Computing), 자율 의사결정 기술을 지속적으로 통합하게 될 것이며, 이에 따라 체계적이고 측정 가능하며 추적 가능한 PRD의 중요성은 더욱 커질 것이다. 우수하게 작성된 PRD는 단순히 제품의 요구사항을 기록하는 문서가 아니라 혁신적인 아이디어를 신뢰성(Reliability), 확장성(Scalability), 안전성(Safety), 그리고 상업적 성공(Commercial Success)을 갖춘 자율 로봇 시스템으로 실현하기 위한 핵심적인 엔지니어링 기반을 제공한다.

## 01.02 Customer and Use Case Analysis

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

고객 및 사용 사례 분석(Customer and Use Case Analysis)은 자율이동로봇(Autonomous Mobile Robot, AMR)을 누가 사용할 것인지, 어떤 운영상의 문제를 해결해야 하는지, 로봇이 어떤 환경에서 운용될 것인지, 그리고 실제 현장에서 성공 여부를 어떤 기준으로 평가할 것인지를 이해하는 과정이다. 제품 요구사항 문서(Product Requirements Document, PRD)에서는 이러한 분석이 광범위한 비즈니스 요구를 구체적인 제품 요구사항으로 변환하는 근거를 제공한다. 이를 통해 기술적으로 뛰어난 로봇을 개발했음에도 고객의 실제 업무 흐름(Workflow), 제약 조건(Constraint), 위험(Risk), 경제적 우선순위(Economic Priority)를 충족하지 못하는 상황을 방지할 수 있다. 본 내용은 첨부된 엔지니어링 매뉴얼의 제품 요구사항 문서(Product Requirements Document) 장에 포함된 "01_02_Customer_and_Use_Case_Analysis" 항목을 기반으로 한다.

고객 분석(Customer Analysis)의 첫 번째 단계는 구매 조직 전체를 하나의 고객으로 간주하지 않고, 모든 이해관계자(Stakeholder)를 식별하는 것이다. 구매 결정권자(Economic Buyer)는 투자 비용(Capital Cost), 투자 대비 수익(Return on Investment, ROI), 구축 일정(Deployment Schedule)에 관심을 가지는 반면, 실제 운영자(Operator)는 사용 편의성(Ease of Use), 예측 가능한 동작(Predictable Behavior), 작업 부담 감소(Reduced Workload)를 중요하게 생각한다. 유지보수 엔지니어(Maintenance Technician)는 부품 접근성, 진단 기능, 신속한 수리 절차를 요구하며, 안전 관리자(Safety Manager)는 위험 요소와 규정 준수(Compliance)를 평가한다. 정보기술(IT) 조직은 네트워크 통합(Network Integration), 사이버보안(Cybersecurity), 데이터 소유권(Data Ownership), 유지보수 지원 체계를 검토한다.

따라서 고객 분석은 구매자(Buyer), 사용자(User), 유지보수 담당자(Maintainer), 시스템 관리자(Administrator), 감독자(Supervisor), 그리고 로봇과 동일한 공간을 공유하는 사람들까지 구분하여 분석해야 한다. 이러한 집단은 서로 다른 우선순위를 가지며, 때로는 성공 기준조차 상충될 수 있다. 예를 들어 생산 관리자는 최대 속도와 생산성을 요구할 수 있지만, 안전 관리자는 보다 보수적인 주행과 충분한 정지 거리를 선호할 수 있다. PRD는 이러한 차이를 명확하게 기록하여 상세 설계 이전에 필요한 기술적 절충안(Trade-off)을 검토할 수 있도록 해야 한다.

고객이 제시하는 요구사항을 그대로 최종 요구사항으로 받아들여서는 안 된다. 고객은 종종 실제 문제보다 자신이 생각하는 해결 방법을 제안하는 경우가 많기 때문이다. 예를 들어 더 큰 배터리를 요구하는 것은 실제로는 운행 시간이 부족한 것이 아니라 충전 환경이 불편하거나 임무 스케줄링(Mission Scheduling)이 비효율적이기 때문일 수 있다. 추가 센서를 요구하는 경우도 실제 원인은 사각지대(Blind Spot)나 과거 충돌 경험일 수 있다. 따라서 엔지니어는 고객이 요청한 기술이 아니라 그 요청의 근본 원인(Root Cause)을 파악하여 요구사항을 정의해야 한다.

사용 사례 분석(Use Case Analysis)은 고객의 요구를 정상 운용(Normal Operation), 비정상 운용(Abnormal Operation), 성능 저하 운용(Degraded Operation), 비상 상황(Emergency Condition)에서 로봇이 어떻게 동작해야 하는지에 대한 구조적인 시나리오로 변환하는 과정이다. 일반적인 사용 사례는 작업을 시작하는 주체(Actor), 운영 목적(Objective), 환경(Context), 예상되는 작업 순서(Sequence), 교환되는 정보(Information Exchange), 최종 결과(Outcome)를 포함한다. AMR의 경우 임무를 수신하고, 출발 위치로 이동하며, 적재 준비를 확인하고, 사람과 차량이 함께 있는 환경을 통과하여 목적지에 도킹(Docking)한 후 작업 완료를 보고하고 충전소로 복귀하는 과정 전체가 하나의 사용 사례가 될 수 있다.

사용 사례는 단순히 자율주행 부분만을 설명해서는 안 되며 전체 운영 프로세스(End-to-End Workflow)를 포함해야 한다. AMR은 창고관리시스템(Warehouse Management System, WMS), 엘리베이터(Elevator), 자동문(Automatic Door), 컨베이어(Conveyor), 로봇팔(Robot Arm), 검사 장비(Inspection Equipment), 플릿 관리 시스템(Fleet Management System), 충전기(Charging Station), 작업자와 함께 동작하는 복합 시스템이다. 이러한 상호작용이 사용 사례에서 제외되면 인터페이스 요구사항이 프로젝트 후반에 발견될 수 있다. 결과적으로 로봇은 성공적으로 주행하더라도 작업 정보를 주고받거나 적재 완료를 확인하지 못하고, 외부 시스템의 지연 상황을 처리하지 못하는 문제가 발생할 수 있다.

운영 시나리오(Operational Scenario)는 반드시 고객의 실제 현장 환경을 기반으로 작성되어야 한다. 바닥 상태(Floor Quality), 통로 폭(Corridor Width), 경사(Slope), 문턱(Threshold), 조명(Lighting), 먼지(Dust), 온도(Temperature), 무선 통신 환경(Wireless Coverage), 사람과 차량의 이동량(Traffic), 반사체(Reflective Surface), 이동 장애물(Dynamic Obstacle)은 모두 시스템 설계에 직접적인 영향을 준다. 실내 물류 환경은 비교적 구조화되어 있지만 작업 혼잡도와 임시 적치물이 존재하며, 실외 환경은 기상 변화, 노면 상태, GNSS 제한, 환경 오염 등의 요소를 포함한다. PRD는 이러한 환경 조건을 설계 입력값(Design Input)으로 명확하게 기록해야 한다.

임무 수행 빈도(Mission Frequency)와 작업 부하(Workload Pattern) 역시 중요한 분석 대상이다. 평균 운행량만을 기준으로 설계하면 실제 피크 시간대(Peak Condition)의 요구사항을 놓칠 수 있다. 예를 들어 평상시에는 시간당 10회의 작업만 수행하지만 교대 시간이나 생산 피크 시간에는 두 배 이상의 작업이 발생할 수도 있다. 따라서 배터리 지속시간(Battery Endurance), 충전 전략(Charging Strategy), 플릿 규모(Fleet Size), 열 관리(Thermal Behavior), 통신 용량(Communication Capacity), 교통 관리(Traffic Management)는 현실적인 운영 패턴을 기준으로 분석되어야 한다. 고객 분석에는 임무 시간, 이동 거리, 대기 시간, 적재 중량 분포, 충전 가능 시간, 운영 교대, 계절 및 시간대별 부하 변화가 포함되어야 한다.

운반하거나 검사하는 대상의 물리적 특성(Physical Characteristics) 역시 사용 사례에 포함되어야 한다. 단순한 적재 중량(Payload Mass)만으로는 충분하지 않으며, 크기(Size), 무게 중심(Center of Gravity), 형상(Shape), 안정성(Stability), 표면 상태(Surface Condition), 적재 방식(Loading Method)은 모두 섀시(Chassis), 제동(Braking), 서스펜션(Suspension), 도킹(Docking), 주행 제어(Motion Control)에 영향을 준다. 견고한 컨테이너와 액체 탱크, 견인 카트(Towing Cart), 의료 캐비닛(Medical Cabinet), 검사 장비는 서로 다른 설계 요구사항을 가진다. PRD는 대표적인 적재 형태와 함께 안정성 문제를 일으킬 수 있는 특수 사례도 함께 정의해야 한다.

사람과의 상호작용(Human Interaction)은 로봇 사용자뿐 아니라 주변 사람들의 관점에서도 분석되어야 한다. 숙련된 작업자는 로봇의 상태 표시와 복구 절차를 이해할 수 있지만, 방문객이나 환자, 외부 작업자, 보행자는 로봇의 의도를 이해하지 못할 수 있다. 따라서 사용 사례에는 로봇이 진행 방향, 주행 상태, 경고, 고장 상태, 지원 요청 등을 어떻게 전달할 것인지가 포함되어야 한다. 디스플레이(Display), 조명(Light), 음향(Sound), 모바일 애플리케이션(Mobile Application), 원격 관제(Dashboard), 물리 버튼(Button), 자연어 명령(Natural Language Command) 등 다양한 인터페이스를 사용할 수 있지만, 반드시 실제 작업 환경과 사용자의 수준에 적합해야 한다.

예외 상황(Exception Scenario)은 정상적인 작업 흐름보다 더욱 중요한 경우가 많다. 실제 현장에서 발생하는 대부분의 장애는 정상 조건이 아니라 예외 상황에서 발생하기 때문이다. 예를 들어 통로가 막힌 경우, 적재물이 불완전한 경우, 엘리베이터를 사용할 수 없는 경우, 충전기가 이동된 경우, 위치추정 성능이 저하된 경우, 네트워크가 끊어진 경우, 배터리가 부족한 경우, 센서가 오염된 경우, 예기치 못한 사람의 행동, 손상된 바닥, 외부 장비 고장 등이 모두 고려되어야 한다. 사용 사례는 이러한 상황을 어떻게 감지하고, 대기할 것인지, 재시도할 것인지, 우회할 것인지, 지원을 요청할 것인지, 안전 상태(Safe State)로 전환할 것인지 등을 정의해야 한다.

복구 전략(Recovery Strategy)은 안전성을 유지하면서도 운영 중단을 최소화하도록 설계되어야 한다. 불확실성이 발생할 때마다 단순히 정지하는 로봇은 안전 측면에서는 적절할 수 있지만, 운영 효율성은 크게 저하될 수 있다. 반대로 모든 상황을 자동으로 복구하려는 접근은 시스템이 상황을 정확히 이해하지 못할 경우 더 큰 위험을 초래할 수도 있다. 고객 분석은 어떤 장애는 즉시 정지해야 하는지, 어떤 장애는 성능 저하 상태에서 계속 운행 가능한지, 어떤 장애는 자동 복구할 수 있는지, 어떤 경우에는 유지보수 담당자나 원격 운영자에게 이관해야 하는지를 명확하게 정의해야 한다.

정량적인 수용 기준(Acceptance Criteria)은 개별 부품의 성능이 아니라 사용 사례를 기반으로 정의되어야 한다. 최고 속도는 임무 수행량과 보행자 안전을 고려해야 하며, 위치추정 정확도는 도킹과 적재 작업을 만족해야 한다. 배터리 용량은 실제 운행 주기와 충전 환경을 기준으로 결정되어야 하며, 장애물 탐지 거리는 차량의 제동 거리와 동역학(Dynamics)을 고려하여 정의되어야 한다. 이러한 사용 사례 중심 접근 방식은 개별 기술 사양이 아니라 제품 전체의 성능 목표를 설정할 수 있도록 해준다.

경제성 분석(Economic Analysis)은 주요 사용 사례가 고객에게 어떤 가치를 제공하는지를 함께 평가해야 한다. AMR은 작업 시간을 단축하고, 산업재해를 줄이며, 작업 품질의 일관성을 높이고, 운영 시간을 확대하며, 검사 데이터를 축적하고, 숙련 작업자가 더 높은 부가가치 업무에 집중할 수 있도록 하는 등의 효과를 제공할 수 있다. 이러한 이점은 장비 구매 비용, 시스템 통합 비용, 인프라 구축 비용, 교육 비용, 유지보수 비용, 에너지 소비, 예상 다운타임(Total Cost of Ownership, TCO)과 비교되어야 한다. 기술적으로 성공한 사용 사례라도 고객의 경제적 효과가 충분하지 않다면 상업적으로 성공하기 어렵다.

사용 사례 분석은 구축을 위해 고객이 제공해야 하는 환경과 책임(Customer Responsibility)도 함께 정의해야 한다. 일부 AMR은 정확한 디지털 지도(Digital Map), 안정적인 무선 네트워크, 도킹 마커(Docking Marker), 충전 공간, 바닥 유지관리, 교통 규칙, 기업 시스템과의 연동을 요구한다. 이러한 조건은 일정, 비용, 성능, 책임 범위에 직접적인 영향을 미친다. 만약 고객이 별도의 환경 구축 없이 즉시 운영을 기대한다면 제품은 더욱 높은 수준의 자율성(Onboard Autonomy), 강건한 인지(Perception), 대체 통신 및 위치추정 기능을 제공해야 할 수도 있다.

사용 사례는 비즈니스 중요도(Business Importance), 안전성(Safety Significance), 기술적 위험(Technical Risk), 발생 빈도(Frequency), 고객 가치(Customer Value)를 기준으로 우선순위를 설정해야 한다. 가장 중요한 사용 사례는 제품이 시장에서 성공하기 위해 반드시 수행되어야 하는 핵심 임무를 의미한다. 부가적인 사용 사례는 운영 효율 향상이나 적용 범위 확대를 지원하며, 미래 사용 사례(Future Use Case)는 초기 개발 범위를 확장하지 않으면서 향후 시스템 확장성(Scalability)을 고려하는 데 활용될 수 있다. 이러한 우선순위 설정은 불필요한 기능 증가를 방지하고 개발 자원을 가장 중요한 기능에 집중할 수 있도록 해준다.

고객 및 사용 사례 분석은 PRD가 승인된 이후에도 계속 유지되어야 한다. 시제품 평가(Prototype Test), 시뮬레이션(Simulation), 현장 조사(Site Survey), 운영자 인터뷰(Operator Interview), 현장 시험(Field Trial), 초기 구축(Early Deployment) 과정에서는 초기 요구사항 단계에서 확인하지 못했던 새로운 문제들이 발견되는 경우가 많다. 이러한 결과는 원래의 사용 사례와 비교하여 검토하고, 요구사항 변경 절차를 통해 관리되어야 한다. 지속적인 피드백(Continuous Feedback)은 제품이 실제 운영 경험을 반영하면서도 요구사항의 추적성(Traceability)과 개발 범위의 일관성을 유지할 수 있도록 한다.

성숙한 고객 및 사용 사례 분석(Customer and Use Case Analysis)은 단순히 고객 인터뷰를 정리한 문서가 아니다. 이는 이해관계자, 비즈니스 목표, 운영 환경, 작업 흐름, 시스템 인터페이스, 위험 요소, 성능 목표, 예외 상황 처리, 수용 기준(Acceptance Criteria)을 하나의 일관된 운영 모델(Operational Model)로 통합하는 과정이다. 이러한 운영 모델은 기능 요구사항(Functional Requirement), 안전 요구사항(Safety Requirement), 시스템 아키텍처(System Architecture), 검증 계획(Verification Plan), 구축 준비(Deployment Preparation), 제품 전 생애주기(Lifecycle Support)의 기반이 된다. 고객 요구와 사용 사례가 정확하게 이해될 때, AMR 개발은 단순한 기술 중심의 실험을 넘어 신뢰성(Reliability), 확장성(Scalability), 그리고 경제성(Economic Value)을 갖춘 실질적인 자동화 시스템으로 발전할 수 있다.

## 01.03 Functional Requirements

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

기능 요구사항(Functional Requirements)은 자율이동로봇(Autonomous Mobile Robot, AMR)이 고객의 요구를 만족시키고 의도된 운영 임무를 수행하기 위해 반드시 수행해야 하는 기능을 정의한다. 기능 요구사항은 시스템이 제공해야 하는 동작(Behavior), 서비스(Service), 반응(Response), 의사결정(Decision), 정보 교환(Information Exchange), 상호작용(Interaction)을 기술하며, 구현 방법이나 기술적인 세부 설계를 미리 제한하지 않는다. 제품 요구사항 문서(Product Requirements Document, PRD)에서 기능 요구사항은 고객 및 사용 사례 분석(Customer and Use Case Analysis)과 시스템 아키텍처(System Architecture), 하위 시스템 명세(Sub-System Specification), 소프트웨어 기능(Software Function), 하드웨어 인터페이스(Hardware Interface), 검증 절차(Verification Procedure), 운영 수용 기준(Operational Acceptance Criteria)을 연결하는 핵심 역할을 수행한다.

기능 요구사항은 반드시 식별된 이해관계자 요구(Stakeholder Need), 사용 사례(Use Case), 운영 시나리오(Operational Scenario), 규제 요구(Regulatory Requirement), 또는 제품 목표(Product Objective)에서 출발해야 한다. 각각의 요구사항은 특정 조건에서 AMR이 어떤 동작을 수행해야 하는지와 시스템이 최종적으로 어떤 결과를 제공해야 하는지를 명확하게 설명해야 한다. 또한 설계와 시험이 가능할 정도로 충분히 구체적이어야 하지만, 특정 공급업체(Supplier), 알고리즘(Algorithm), 센서 모델(Sensor Model), 소프트웨어 라이브러리(Software Library), 기계 구조(Mechanical Solution)에 불필요하게 의존해서는 안 된다. 단, 특정 기술 자체가 고객 또는 인터페이스 요구사항인 경우에는 예외가 될 수 있다.

효과적인 기능 요구사항은 일반적으로 시스템이 반드시 수행해야 하는 동작을 명확하게 기술하는 문장으로 작성된다. 영어에서는 의무적인 요구사항을 표현하기 위해 "shall"이라는 표현을 사용하며, 이를 통해 권장사항(Recommendation), 설명(Explanation), 가정(Assumption), 향후 계획(Future Possibility)과 구분한다. 좋은 요구사항은 어떤 시스템이(Responsible System), 어떤 동작을(Required Action), 어떤 조건에서(Triggering Condition), 어떤 결과(Expected Output)를 생성해야 하는지를 포함한다. 반면 "빠르다(Fast)", "지능적이다(Intelligent)", "사용하기 쉽다(User-Friendly)", "매우 신뢰성이 높다(Highly Reliable)"와 같은 모호한 표현은 별도의 정량적 기준이 정의되지 않는 한 사용해서는 안 된다.

AMR 기능 요구사항의 첫 번째 핵심 영역은 임무 수신(Mission Reception)과 작업 관리(Task Management)이다. 로봇은 운영자(Operator), 플릿 관리 시스템(Fleet Management System), 창고관리시스템(Warehouse Management System, WMS), 제조실행시스템(Manufacturing Execution System, MES), 또는 승인된 외부 시스템으로부터 전달되는 임무를 수신하고, 해석하며, 검증하고, 수락하거나 거부하고, 대기열(Queue)에 저장하며, 일시 중지(Suspend), 재개(Resume), 완료(Complete)할 수 있어야 한다. 각 임무에는 목적(Objective), 우선순위(Priority), 목적지(Destination), 적재 상태(Payload Condition), 필요한 장비(Required Equipment), 시간 제약(Timing Constraint), 완료 조건(Completion Criteria)이 포함되어야 한다.

임무를 수신한 후 AMR은 현재의 시스템 상태와 구성으로 해당 작업을 안전하고 정상적으로 수행할 수 있는지를 판단해야 한다. 이를 위해 지도(Map) 사용 가능 여부, 위치추정(Localization) 신뢰도, 배터리 상태(Battery Condition), 센서 상태(Sensor Status), 적재 적합성(Payload Compatibility), 통신 가능 여부(Communication Availability), 이동 경로(Route Accessibility), 외부 인터페이스(External Interface)의 준비 상태 등을 확인해야 한다. 만약 임무를 수행할 수 없다면 단순히 실패하는 것이 아니라 그 이유를 명확하게 제시하며 거부하거나 연기(Postpone)해야 한다.

자율주행(Autonomous Navigation)은 기능 요구사항 가운데 가장 중요한 영역이다. AMR은 자신의 위치를 결정하고, 이동 경로를 계산하며, 주행 명령(Motion Command)을 생성하고, 계획된 경로를 따라 이동하며, 주변 환경 변화에 따라 행동을 지속적으로 수정해야 한다. 이러한 기능에는 목적지 기반 이동(Mission Destination), 허용 구역(Allowed Zone), 금지 구역(Prohibited Area), 교통 방향(Traffic Direction), 속도 제한 구역(Speed Region), 도킹 접근(Docking Approach), 임시 제한 구역(Temporary Restriction) 등이 포함된다. 기능 요구사항은 이러한 주행 행동을 정의하지만, 실제 알고리즘이나 구현 방식은 시스템 아키텍처와 상세 설계 단계에서 결정되어야 한다.

장애물 처리(Obstacle Handling)는 사람, 차량, 장비, 임시 장애물, 막힌 통로 등 이동을 방해하는 다양한 상황에 대한 시스템의 대응을 정의한다. AMR은 장애물을 감지(Detect)하고, 필요한 경우 중요도를 판단(Classify)하며, 속도를 줄이거나, 정지하거나, 대기하거나, 경로를 재계획(Replan)하거나, 운영자의 지원을 요청해야 한다. 또한 일시적인 통행 방해와 장기간의 경로 차단을 구분하여, 사람의 일시적인 이동 때문에 임무를 불필요하게 취소하지 않으면서도 안전하지 않은 통과는 방지해야 한다.

위치추정(Localization) 및 지도 관리(Map Management) 기능은 운영 환경 전반에서 안정적인 자율주행을 지원해야 한다. AMR은 초기 위치를 설정하고, 이동 중 자신의 위치를 지속적으로 추정하며, 위치추정 성능 저하를 감지하고, 가능한 경우에는 자동 복구를 수행하며, 신뢰성 있는 위치추정이 불가능한 경우에는 적절한 안전 상태(Safe State)로 전환해야 한다. 지도 관리 기능에는 승인된 지도 로딩(Map Loading), 운영 구역 선택, 지도 업데이트 수신, 제한 구역 인식, 지도 버전과 소프트웨어 버전 간의 호환성 유지 등이 포함될 수 있다.

적재물 처리(Payload Handling) 기능은 AMR의 제품 유형에 따라 들어 올리기(Lifting), 내리기(Lowering), 견인(Towing), 자동 연결(Coupling), 분리(Releasing), 컨베이어 이송(Conveying), 고정(Securing), 계량(Weighing), 적재 감지(Detection), 적재 확인(Verification) 등을 포함할 수 있다. 로봇은 적재 인터페이스가 준비되었는지 확인한 후 작업을 시작해야 하며, 적재 및 하역이 성공적으로 완료되었는지도 판단해야 한다. 또한 적재물이 없거나, 잘못 배치되었거나, 불안정하거나, 호환되지 않거나, 외부 장비에서 정상적으로 분리되지 않은 경우의 동작도 정의되어야 한다.

도킹(Docking) 기능은 충전기(Charging Station), 컨베이어(Conveyor), 엘리베이터(Elevator), 검사 장비(Inspection System), 로봇팔(Robot Arm), 작업 스테이션(Workstation), 자재 이송 장비(Material Transfer Device)와의 정밀한 연동을 지원한다. AMR은 올바른 도킹 대상을 식별하고, 지정된 경로를 통해 접근하며, 위치와 자세(Position and Orientation)를 정렬하고, 연결 성공 여부를 확인하며, 상대 시스템에 작업 준비 완료를 통보해야 한다. 도킹에 실패한 경우에는 제한된 횟수만큼 재시도하거나, 대체 절차를 수행하거나, 반복적인 위험 동작을 발생시키지 않으면서 운영자 지원을 요청해야 한다.

에너지 관리(Energy Management)는 로봇이 임무를 완료하면서도 배터리 수명과 운영 가용성을 유지하도록 지원한다. AMR은 배터리 상태를 지속적으로 모니터링하고, 현재 임무를 수행할 수 있는 충분한 에너지가 있는지를 판단하며, 필요 시 충전을 예약하거나 요청하고, 충전기로 이동하여 충전을 시작하고, 충전 진행 상태를 확인해야 한다. 또한 에너지가 부족한 경우에는 새로운 임무를 수락하지 않아야 하며, 운영 정책(Operation Policy)에 따라 충전 후 중단된 작업을 자동으로 재개할 수 있어야 한다.

사람-기계 인터페이스(Human-Machine Interface, HMI)는 사용자에게 이해하기 쉬운 정보와 적절한 제어 기능을 제공해야 한다. 운영자는 로봇의 식별 정보(Robot Identity), 임무 상태(Mission Status), 운영 모드(Operating Mode), 배터리 상태(Battery Level), 경고(Warning), 고장(Fault), 지원 요청(Request for Assistance)을 확인할 수 있어야 한다. 권한이 있는 사용자는 작업 시작(Start), 일시 정지(Pause), 취소(Cancel), 경로 변경(Redirect), 복구(Recovery), 수동 제어(Manual Control)를 수행할 수 있어야 한다. 또한 시스템은 권한이 없는 사용자의 접근이나 상충되는 명령을 방지하고, 자율 모드(Autonomous Mode), 원격 제어(Remote Operation), 수동 운전(Manual Mode), 유지보수 모드(Maintenance Mode)를 명확하게 표시해야 한다.

AMR은 숙련된 운영자가 아닌 주변 사람들에게도 자신의 상태와 의도를 전달해야 한다. 이를 위해 이동 방향 표시(Direction Indicator), 조명(Lighting), 경고음(Audible Warning), 바닥 투사(Projected Symbol), 디스플레이(Display Message), 예측 가능한 움직임(Motion Pattern) 등을 활용할 수 있다. 기능 요구사항은 이러한 신호가 언제 활성화되고, 어떤 의미를 가지며, 직진, 회전, 후진, 도킹, 대기, 장애 대응, 비상 상황에서 어떻게 변화해야 하는지를 정의해야 한다.

외부 시스템 연동(External System Integration)은 AMR이 플릿 관리 시스템(Fleet Management System), 기업 시스템(Enterprise System), 엘리베이터, 자동문, 컨베이어, 충전기, 출입통제시스템(Access Control System), 검사 장비, 클라우드 서비스(Cloud Service)와 명령(Command), 상태(Status), 지도(Map), 작업 정보(Task Data), 경보(Alarm), 운영 기록(Log)을 교환하는 기능을 정의한다. 기능 요구사항에는 교환되는 정보, 통신 방향(Direction), 인증(Authorization), 응답(Acknowledgement), 타임아웃(Timeout), 외부 시스템 장애 시의 동작이 포함되어야 한다.

플릿 운영(Fleet Operation)은 단일 로봇의 기능을 넘어서는 추가적인 기능을 요구한다. 플릿에 속한 AMR은 자신의 위치(Position), 가용성(Availability), 임무 상태(Mission Status), 시스템 상태(Health Condition), 자원 요구(Resource Need)를 플릿 관리 시스템에 보고해야 한다. 또한 교통 제어(Traffic Coordination), 작업 할당(Task Assignment), 지도 업데이트(Map Update), 충전 예약(Charging Reservation), 우선순위 변경(Priority Change)을 수신할 수 있어야 한다. 전체 시스템은 경로 충돌을 방지하고, 공유 자원을 효율적으로 관리하며, 일부 로봇이 고장 나더라도 전체 운영이 지속될 수 있도록 해야 한다.

진단(Diagnostics) 및 장애 관리(Fault Management)는 시스템이 이상 상태를 감지하고 적절하게 대응할 수 있도록 한다. AMR은 하드웨어(Hardware), 소프트웨어 프로세스(Software Process), 센서(Sensor), 구동기(Actuator), 네트워크(Network), 전원 모듈(Power Module), 저장 장치(Storage Device), 외부 인터페이스를 지속적으로 모니터링해야 한다. 발견된 장애는 심각도(Severity)와 운영 영향(Operational Effect)에 따라 분류되어야 하며, 관련 정보를 기록하고, 승인된 시스템에 통보하며, 가능한 경우 영향을 받는 기능만 격리하고, 정상(Normal), 성능 저하(Degraded), 일시 정지(Paused), 복구(Recovery), 유지보수(Maintenance), 안전 정지(Safe Shutdown) 상태로 전환해야 한다.

운영 기록(Operational Logging)은 디버깅(Debugging), 검증(Validation), 유지보수(Maintenance), 고객 지원(Customer Support), 제품 개선(Product Improvement)을 위한 핵심 정보를 제공한다. AMR은 임무 이벤트(Mission Event), 상태 전이(State Transition), 사용자 명령(User Command), 경고, 장애, 자율주행 의사결정(Navigation Decision), 인터페이스 통신, 충전 이벤트, 주요 센서 데이터를 기록해야 한다. 모든 로그에는 동기화된 시간 정보(Timestamp)와 로봇 식별 정보가 포함되어야 하며, 네트워크 장애나 시스템 재시작이 발생하더라도 중요한 진단 정보가 손실되지 않도록 해야 한다.

소프트웨어 및 구성 관리(Software and Configuration Management)는 현장에서 운용되는 로봇이 승인된 버전으로 유지되도록 보장한다. AMR은 설치된 소프트웨어, 펌웨어(Firmware), AI 모델, 보정 데이터(Calibration Data), 지도(Map), 파라미터(Parameter)를 보고할 수 있어야 한다. 승인된 업데이트는 수신, 검증, 설치, 활성화, 롤백(Rollback), 거부가 가능한 절차를 따라야 하며, 서로 호환되지 않는 구성 요소가 함께 설치되지 않도록 해야 한다. 또한 유지보수와 부품 교체, 원격 업데이트 이후에도 중요한 구성 정보가 유지되어야 한다.

기능 요구사항은 운영 모드(Operating Mode)와 상태 전이(State Transition)도 정의해야 한다. 일반적으로 전원 꺼짐(Power-Off), 시작(Startup), 초기화(Initialization), 대기(Standby), 자율 운행(Autonomous Operation), 수동 운전(Manual Operation), 원격 지원(Remote Assistance), 충전(Charging), 유지보수(Maintenance), 성능 저하 운전(Degraded Operation), 장애 대응(Fault Response), 비상 정지(Emergency Stop)와 같은 모드가 존재한다. PRD는 각 모드에서 어떤 기능이 활성화되는지, 어떤 이벤트가 상태 전이를 발생시키는지, 이동을 시작하기 위한 조건은 무엇인지, 예상하지 못한 상태 전이가 어떻게 방지되는지를 정의해야 한다.

시작(Startup)과 종료(Shutdown)는 단순한 기술적 세부사항이 아니라 중요한 제품 기능으로 정의되어야 한다. 시작 과정에서는 필수 하드웨어 점검, 소프트웨어 초기화, 구성 검증, 통신 연결, 안전 기능 확인, 자율 운행 가능 여부를 확인해야 한다. 종료 과정에서는 이동을 멈추고, 구동기를 안전한 상태로 전환하며, 필요한 데이터를 저장하고, 통신을 종료한 후, 제어된 순서에 따라 전원을 차단해야 한다. 또한 예기치 않은 전원 차단 이후의 복구 동작도 함께 정의되어야 한다.

기능 요구사항에는 성능 저하 운전(Degraded Operation)도 반드시 포함되어야 한다. 모든 장애가 시스템 전체의 정지를 의미하는 것은 아니다. 제품과 사용 사례에 따라 AMR은 속도를 줄인 상태로 계속 운행하거나, 일부 기능만 비활성화하거나, 대체 센서를 사용하거나, 서비스 구역으로 복귀하거나, 안전하게 하역을 완료할 수도 있다. 이러한 성능 저하 운전은 명확한 조건과 범위 내에서만 허용되어야 하며, 운영자와 외부 시스템은 현재 시스템의 기능이 변경되었음을 반드시 인지할 수 있어야 한다.

모든 기능 요구사항은 원래의 고객 요구와 연결되어야 하며, 시스템 아키텍처(System Architecture), 구현 모듈(Implementation Component), 검증 항목(Verification Case)과도 추적 가능해야 한다. 이러한 추적성(Traceability)은 고객 요구가 모두 반영되었는지 확인할 수 있을 뿐 아니라, 근거 없는 기능이 설계에 포함되는 것을 방지한다. 또한 요구사항이 변경될 경우 영향을 받는 하드웨어, 소프트웨어, 인터페이스, 시험, 문서, 생산 절차, 현장 설정을 사전에 분석할 수 있도록 지원한다.

기능 요구사항은 완전성(Completeness), 일관성(Consistency), 실현 가능성(Feasibility), 필요성(Necessity), 시험 가능성(Testability)의 관점에서 검토되어야 한다. 중복되는 요구사항은 통합하고, 상충되는 내용은 이해관계자의 검토를 통해 해결해야 한다. 가능하면 하나의 요구사항은 하나의 핵심 기능만을 설명하도록 작성해야 하며, 의존성(Dependency)이나 가정(Assumption)은 복잡한 문장 속에 포함하지 말고 별도로 문서화해야 한다. 이러한 원칙은 여러 개발 조직이 동일한 기능을 서로 다르게 구현하는 문제를 예방한다.

PRD의 기능 요구사항은 제품 수준(Product Level)의 기능 정의에 집중해야 하며, 상세 설계 문서가 되어서는 안 된다. 기능 요구사항은 고객과 운영 환경이 제품에 요구하는 기능을 정의하고, 기계(Mechanical), 전기(Electrical), 임베디드(Embedded), 소프트웨어(Software), 인지(Perception), 위치추정(Localization), 자율주행(Navigation), 인공지능(AI), 클라우드(Cloud), 플릿 관리(Fleet Management) 등의 하위 시스템 문서는 그 기능을 어떻게 구현할 것인지를 설명해야 한다. 이러한 역할 분리는 기술 발전에 따라 구현 방식이 변경되더라도 제품 요구사항을 안정적으로 유지할 수 있도록 한다.

잘 작성된 기능 요구사항은 시스템 아키텍처 설계(System Architecture Design), 개발 계획(Development Planning), 인터페이스 정의(Interface Definition), 위험 분석(Risk Assessment), 시험(Test), 생산 준비(Manufacturing Preparation), 구축(Deployment), 전 생애주기 지원(Lifecycle Support)의 안정적인 기반을 제공한다. 기능 요구사항은 AMR이 독립적으로 개발된 기술들의 단순한 집합이 아니라 하나의 완전한 제품(Product)으로 동작하도록 만든다. 임무 수행(Mission Execution), 자율주행(Navigation), 사람과의 상호작용(Human Interaction), 적재물 처리(Payload Handling), 에너지 관리(Energy Management), 통신(Communication), 진단(Diagnostics), 복구(Recovery), 운영 제어(Operational Control)를 명확하고 추적 가능한 형태로 정의함으로써 PRD는 고객의 요구를 실제 구현 가능한 제품 기능으로 전환하는 핵심 역할을 수행한다.

## 01.04 Performance and Safety Requirements

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

성능 및 안전 요구사항(Performance and Safety Requirements)은 자율이동로봇(Autonomous Mobile Robot, AMR)이 할당된 임무를 얼마나 효과적으로 수행해야 하는지와, 그 과정에서 얼마나 안전하게 동작해야 하는지를 정의한다. 기능 요구사항(Functional Requirements)이 로봇이 무엇을 수행해야 하는지를 설명한다면, 성능 요구사항(Performance Requirements)은 해당 기능이 어느 정도의 수준으로 제공되어야 하는지를 정량적으로 규정한다. 안전 요구사항(Safety Requirements)은 사람, 장비, 인프라, 적재물, 로봇 자체에 허용할 수 없는 피해가 발생하지 않도록 필요한 조건, 제어, 제한, 보호 동작을 정의한다. 이 두 요구사항은 일반적인 기대를 객관적인 엔지니어링 목표로 변환하여 아키텍처, 설계, 시험, 구축, 운영 승인을 지원한다.

성능 요구사항은 부품 사양이나 경쟁사의 마케팅 수치만을 기준으로 선택해서는 안 되며, 실제 고객 업무 흐름(Customer Workflow)에서 도출되어야 한다. 로봇이 높은 속도로 주행할 수 있더라도 대기, 도킹(Docking), 복구(Recovery), 충전, 외부 시스템 연동에 과도한 시간이 소요된다면 실제 생산성을 향상시키지 못할 수 있다. 따라서 제품 수준의 성능은 임무 완료 시간(Mission Completion Time), 운반 처리량(Transport Throughput), 가용성(Availability), 도킹 성공률(Docking Success Rate), 복구 시간(Recovery Time), 에너지 소비(Energy Consumption), 운영 일관성(Operational Consistency)을 중심으로 평가해야 한다. 모든 성능 지표는 고객 가치와 사용 사례에 명확하게 연결되어야 한다.

잘 작성된 성능 요구사항은 운용 조건(Operating Condition), 측정 대상(Measured Quantity), 요구 임계값(Required Threshold), 허용 편차(Allowable Variation), 검증 방법(Verification Method)을 포함해야 한다. "로봇은 빠르게 이동해야 한다" 또는 "시스템은 매우 정확해야 한다"와 같은 문장은 객관적인 설계 판단이나 수용 시험(Acceptance Test)을 지원할 수 없기 때문에 충분하지 않다. 적절한 요구사항은 특정 적재량과 바닥 조건에서의 최고 속도(Maximum Speed), 승인된 운영 구역 내 위치추정 정확도(Localization Accuracy), 지정된 속도에서의 정지 거리(Stopping Distance), 대표 시나리오에 대한 임무 성공률 등을 명확하게 정의해야 한다.

주행 속도(Vehicle Speed)는 가장 눈에 띄는 AMR 성능 특성 가운데 하나이지만, 신중하게 정의되어야 한다. 최고 속도(Maximum Speed), 일반 운행 속도(Normal Operating Speed), 감속 운행 속도(Reduced Speed), 도킹 속도(Docking Speed), 후진 속도(Reversing Speed), 안전 제한 속도(Safety-Limited Speed)는 서로 다른 값으로 정의될 수 있다. 속도 제한은 적재물 안정성(Payload Stability), 제동 성능(Braking Capability), 센서 감지 거리(Sensor Range), 바닥 상태(Floor Condition), 보행자 밀도(Pedestrian Density), 회전 반경(Turning Radius), 현장 운용 규칙을 반영해야 한다. 또한 최고 속도를 생산성의 유일한 지표로 간주해서는 안 된다.

가속도(Acceleration), 감속도(Deceleration), 저크(Jerk)는 안전성과 적재물 안정성에 직접적인 영향을 준다. 급격한 움직임은 적재물 이동, 액체 흔들림, 취약 제품 손상, 주변 사람의 불안감을 유발할 수 있다. 따라서 이동, 비상 대응, 회전, 도킹, 적재물 이송 상황별로 허용 가능한 가속도와 감속도 범위를 정의해야 한다. 민감한 장비, 의료 자재, 높은 적재물, 현수 적재물(Suspended Load), 정밀 위치 안정성이 필요한 검사 시스템을 운반하는 경우에는 저크 제한도 요구될 수 있다.

정지 성능(Stopping Performance)은 실제 운용 조건을 반영하여 정의해야 한다. 필요한 정지 거리는 차량 속도, 적재량, 바닥 마찰(Floor Friction), 경사, 타이어 상태, 제어 지연(Control Latency), 브레이크 반응(Brake Response), 환경 오염 등에 따라 달라진다. 성능 요구사항은 일반 제어 정지(Normal Controlled Stop), 보호 정지(Protective Stop), 비상 정지(Emergency Stop)를 구분해야 한다. 시험은 무부하 상태의 이상적인 실험실 조건이 아니라 대표 적재물과 실제 바닥 조건을 기반으로 수행해야 하며, 제품 정의상 허용되는 가장 불리한 조합도 검증해야 한다.

위치추정 성능(Localization Performance)은 AMR이 허용 구역 내에서 안정적으로 이동하고, 좁은 통로에 접근하며, 외부 장비와 정확하게 상호작용할 수 있는지를 결정한다. 위치추정 요구사항은 절대 위치 정확도(Absolute Position Accuracy), 상대 정확도(Relative Accuracy), 반복 정밀도(Repeatability), 방향각 정확도(Heading Accuracy), 초기화 시간(Initialization Time), 복구 시간(Recovery Time), 신뢰도 모니터링(Confidence Monitoring)을 포함할 수 있다. 일반 통로 주행은 비교적 큰 오차를 허용할 수 있지만, 정밀 도킹, 자동 적재, 로봇 검사, 고정 생산 장비와의 연동은 더 높은 정확도를 요구한다.

자율주행 성능(Navigation Performance)은 단순한 경로 정확도(Path Accuracy) 이상으로 평가해야 한다. 중요한 지표에는 경로 완료율(Route Completion Rate), 이동 효율(Travel Efficiency), 재계획 지연시간(Replanning Latency), 장애물 대응 시간(Obstacle Response Time), 교착 발생 빈도(Deadlock Frequency), 복구 성공률(Recovery Success Rate), 교통 규칙 준수(Traffic Compliance), 동적 환경에서의 부드러운 주행 능력이 포함된다. 수학적으로 가장 짧은 경로라도 잦은 정지나 다른 로봇과의 충돌 가능성을 증가시키면 운영적으로는 비효율적일 수 있다.

장애물 감지 성능(Obstacle Detection Performance)은 운영 환경에 존재하는 위험 요소를 기준으로 정의해야 한다. 감지 거리(Detection Range), 시야각(Field of View), 최소 감지 물체 크기(Minimum Detectable Object Size), 응답 지연(Response Latency), 분류 신뢰도(Classification Confidence), 조명 및 기상 조건별 성능이 요구사항에 포함될 수 있다. 시스템은 허용 가능한 정지 거리 내에서 필요한 안전 대응을 수행할 수 있도록 충분히 이른 시점에 장애물을 감지해야 한다. 사람, 차량, 낮은 물체, 돌출 구조물, 반사체, 어두운 물체 등 위험 분석에서 식별된 대상에 대한 평가가 필요하다.

적재 성능(Payload Capability)은 최대 적재 중량만으로 정의할 수 없다. 허용 적재 크기, 무게 중심(Center of Gravity), 하중 분포(Load Distribution), 고정 방식(Attachment Method), 이송 높이(Transfer Height), 견인 저항(Towing Resistance), 가속·제동·회전·경사 주행 중 안정성이 함께 고려되어야 한다. 로봇은 승인된 적재 범위(Loading Envelope) 내에서만 정격 적재량을 안전하게 운반할 수 있다. 사용자가 이 범위를 초과하는 경우 시스템은 가능한 범위에서 이를 감지하고, 주행을 제한하거나, 경고를 발생시키거나, 운영자 확인을 요구해야 한다.

도킹 성능(Docking Performance)은 일반적으로 위치 정확도(Position Accuracy), 자세 정확도(Orientation Accuracy), 반복 정밀도(Repeatability), 접근 시간(Approach Time), 체결 성공률(Engagement Success Rate), 실패 후 복구 동작으로 정의된다. 요구사항은 최초 시도 기준인지, 제한된 재시도를 포함한 기준인지, 적재 및 환경 변화가 있는 반복 운용 기준인지 명확히 해야 한다. 도킹 성공은 목표물 구조, 바닥 편차, 센서 가시성, 기계 공차(Mechanical Tolerance), 외부 장비와의 통신에 영향을 받으므로 이러한 조건도 검증 범위에 포함되어야 한다.

배터리 및 에너지 성능(Battery and Energy Performance)은 AMR의 작업 지속시간과 운영 가용성을 결정한다. 주요 지표에는 운용 시간(Operating Duration), 충전당 임무 횟수(Missions per Charge), 거리 또는 임무당 에너지 소비, 최소 예비 전력(Minimum Reserve Level), 충전 시간(Charging Time), 충전 효율(Charging Efficiency), 수명 주기 동안의 배터리 열화(Battery Degradation)가 포함된다. 연속 무부하 주행으로 측정한 지속시간은 대기, 리프팅, 컴퓨팅, 통신, 반복 가감속이 포함된 실제 운영을 대표하지 못하므로 대표 운용 주기(Duty Cycle)를 정의해야 한다.

운영 가용성(Operational Availability)은 예정된 운영 시간 가운데 로봇이 실제로 임무를 수행할 수 있는 시간의 비율을 의미한다. 가용성은 신뢰성(Reliability), 충전, 유지보수, 소프트웨어 재시작 시간, 장애 복구, 환경적 중단, 외부 인프라 상태에 영향을 받는다. 요구사항에는 가동률(Uptime), 평균 고장 간격(Mean Time Between Failures, MTBF), 평균 수리 시간(Mean Time to Repair, MTTR), 예방정비 주기(Preventive Maintenance Interval), 최대 허용 다운타임(Maximum Permitted Downtime)이 포함될 수 있다.

응답 시간(Response Time)은 분산형 AMR 시스템에서 중요한 성능 요구사항이다. 임무 승인 응답, 운영자 명령 반응, 장애물 대응, 비상 입력 처리, 인터페이스 타임아웃(Interface Timeout), 지도 로딩, 소프트웨어 시작, 원격 상태 보고 등은 각각 다른 시간 제한을 가질 수 있다. 개별 알고리즘이 정확하더라도 전체 응답 지연이 크면 생산성이 저하되거나 위험한 동작이 발생할 수 있다. 따라서 이벤트 감지부터 실제 물리적 또는 정보적 반응까지의 종단간 지연시간(End-to-End Latency)을 정의해야 한다.

환경 성능 요구사항(Environmental Performance Requirements)은 온도, 습도, 먼지, 수분 노출, 진동, 충격, 조명 변화, 전자기 간섭(Electromagnetic Interference), 바닥 상태에서 로봇이 어떻게 동작해야 하는지를 정의한다. 실내와 실외 AMR은 서로 다른 환경 문제를 가지지만, 구조화된 실내 환경에서도 금속 분진, 세척수, 열원, 반사 유리, 단차 등이 존재할 수 있다. 요구사항은 정상 운용 범위(Normal Operating Range), 성능 저하 범위(Reduced-Performance Range), 보관 한계(Storage Limit), 운행 중지 또는 지원 요청 조건을 구분해야 한다.

안전 요구사항은 체계적인 위험 식별(Hazard Identification)과 위험 평가(Risk Assessment)에서 시작된다. 개발팀은 로봇이 사람에게 상해를 입히거나, 충돌, 끼임, 압착, 낙하물, 감전, 화재, 제어 불능 이동, 재산 피해를 유발할 수 있는 합리적으로 예측 가능한 상황을 분석해야 한다. 위험 분석은 정상 사용, 유지보수, 충전, 운송, 소프트웨어 업데이트, 수동 복구, 부품 고장, 예측 가능한 오사용(Foreseeable Misuse)을 모두 포함해야 한다.

위험 감소(Risk Reduction)는 체계적인 우선순위에 따라 수행되어야 한다. 가장 우선적인 방법은 에너지 제한, 끼임 지점 감소, 안정성 향상, 위험 부품 접근 방지와 같은 본질적으로 안전한 설계(Inherently Safe Design)를 통해 위험을 제거하는 것이다. 위험을 제거할 수 없는 경우에는 안전 등급 센서(Safety-Rated Sensor), 제동, 가드(Guard), 인터록(Interlock), 비상 정지 등의 보호 조치를 적용한다. 경고, 교육, 운용 절차는 추가 보호 수단이지만 실현 가능한 공학적 제어를 대신해서는 안 된다.

보호 정지 요구사항(Protective Stop Requirements)은 사람이나 장애물이 안전 구역(Safety Zone)에 진입하거나 안전한 운용을 보장할 수 없을 때 AMR이 어떻게 반응해야 하는지를 정의한다. 로봇은 안정성을 유지하고 2차 위험을 방지하면서 위험한 움직임을 제어된 방식으로 감소시키거나 제거해야 한다. 요구사항에는 정지 트리거 조건, 정지 범주(Stopping Category), 브레이크 동작, 재시작 조건, 사용자 표시, 임무 상태와의 연동이 포함되어야 한다. 자동 재시작은 환경이 재평가되고 승인된 안전 로직이 허용하는 경우에만 가능해야 한다.

비상 정지 요구사항(Emergency Stop Requirements)은 사람이 위험한 로봇 동작을 신속하게 중단할 수 있도록 해야 한다. 비상 정지 장치는 접근 가능하고 명확하게 식별되며, 관련된 모든 운용 모드에서 효과적으로 작동해야 한다. 비상 정지가 활성화되면 일반 임무 명령보다 우선하여 시스템을 정의된 안전 상태로 전환해야 한다. 비상 정지 해제만으로 자동 재시작되어서는 안 되며, 명시적인 리셋(Reset)과 상태 확인 절차가 필요하다.

안전 등급 인지(Safety-Rated Perception)는 정의된 보호 영역 내에서 사람이나 장애물을 감지하기 위해 필요할 수 있다. PRD는 인증된 안전 기능(Certified Safety Function)과 일반 자율주행 또는 운영 지능을 위한 인지 기능을 명확하게 구분해야 한다. 성능이 높은 AI 모델이라도 자동으로 안전 등급 보호 장치로 간주할 수 없다. 안전 요구사항은 어떤 감지 채널이 인증된 보호 기능을 제공하는지, 진단 범위(Diagnostic Coverage)를 어떻게 확보하는지, 센서가 가려지거나 오염되거나 정렬 불량 또는 고장 상태일 때 로봇이 어떻게 대응하는지를 정의해야 한다.

제동 및 모션 제어 안전 요구사항(Braking and Motion Control Safety Requirements)은 단일 고장(Single Fault)과 제어 권한 상실(Loss of Control Authority)을 고려해야 한다. AMR은 시작, 종료, 충전, 적재, 유지보수, 모드 전환 중 예기치 않은 움직임을 방지해야 한다. 위험 수준에 따라 이중 제동(Redundant Braking), 토크 모니터링(Monitored Torque Control), 안전 속도 제한(Safe Speed Limitation), 안전 방향 제어(Safe Direction), 예기치 않은 재시작 방지가 필요할 수 있다.

안정성 요구사항(Stability Requirements)은 고중량 적재, 견인, 실외 운용, 높은 무게 중심을 가진 로봇에서 특히 중요하다. 제품은 승인된 운용 범위 내에서 가속, 제동, 회전, 경사 주행, 문턱 통과, 적재물 이송 중 안정성을 유지해야 한다. 요구사항은 적재량, 조향각(Steering Angle), 경사, 표면 상태에 따라 속도를 제한할 수 있다. 전적으로 수동 구조만으로 전복 위험을 통제할 수 없는 경우에는 하중 감지(Load Detection), 안정성 추정(Stability Estimation), 모션 제한(Motion Restriction), 운영자 경고가 필요할 수 있다.

전기 안전 요구사항(Electrical Safety Requirements)은 배터리 에너지, 충전 인터페이스, 전력 분배, 절연(Insulation), 접지(Grounding), 단락(Short Circuit), 과전류(Overcurrent), 과열(Overheating), 유지보수 접근을 다룬다. 로봇은 주요 전기 상태를 모니터링하고 필요 시 위험 에너지를 차단해야 한다. 충전은 올바른 연결과 호환성이 확인된 이후에만 시작되어야 한다. 손상된 케이블, 커넥터 고장, 수분 노출, 배터리 열 이상, 정비 및 운송 중 안전한 취급도 요구사항에 포함되어야 한다.

화재 및 열 안전(Fire and Thermal Safety)은 AMR이 고에너지 배터리, 모터, 전력 전자장치, 컴퓨터, 충전 시스템을 제한된 공간에 통합하기 때문에 반드시 고려해야 한다. 시스템은 주요 온도를 모니터링하고, 냉각 장애를 감지하며, 한계값에 접근하면 출력을 감소시키고, 계속 운용할 경우 손상 또는 위험이 발생할 수 있다면 정지해야 한다. 열 보호 기능은 높은 주변 온도, 막힌 통풍구, 지속적인 고부하 운전, 부품 열화 상태에서도 유효해야 한다.

기능 안전 요구사항(Functional Safety Requirements)은 고장 발생 시 모니터링, 진단, 안전 상태 전환을 포함해야 한다. 안전 관련 부품은 요구되는 진단 전략에 따라 시작 시점과 운용 중에 점검되어야 한다. 감지된 고장은 제어 정지, 재시작 금지, 감속 운행, 유지보수 잠금(Maintenance Lockout)과 같은 예측 가능한 반응을 유발해야 한다. 로봇은 고장 상태를 명확하게 전달하고 문제 분석 및 규제 증빙을 위한 충분한 기록을 보존해야 한다.

사이버보안(Cybersecurity)은 물리적 안전에도 영향을 줄 수 있다. 비인가 명령, 손상된 업데이트, 허위 센서 데이터, 네트워크 공격은 로봇의 동작을 변경할 수 있기 때문이다. 안전 관련 요구사항은 명령 채널 보호(Command Channel Protection), 소프트웨어 진위성(Software Authenticity), 접근 제어(Access Control), 구성 무결성(Configuration Integrity)을 위해 사이버보안 요구사항과 연계되어야 한다. 통신 장애나 인증 문제로 인해 제어되지 않은 움직임이 발생해서는 안 되며, 신뢰할 수 있는 제어 정보가 없을 경우에는 안전 또는 제한 상태로 전환해야 한다.

인적 요소(Human Factors)는 사용자가 로봇의 상태를 이해하고 올바르게 대응할 수 있도록 안전 요구사항에 반영되어야 한다. 시각 표시, 경고음, 디스플레이, 조작 장치는 일관되고 명확해야 한다. 로봇은 준비 상태, 이동 중, 대기, 충전, 고장, 원격 제어, 유지보수 상태를 명확하게 전달해야 한다. 과도한 경고는 사용자가 이를 무시하게 만들 수 있으므로 피해야 하며, 안전 정보는 긴급성에 따라 우선순위를 부여하고 운용 환경에 적합한 방식으로 제공해야 한다.

성능 및 안전 요구사항 모두에 대해 검증 방법(Verification Method)을 정의해야 한다. 분석(Analysis), 검사(Inspection), 시뮬레이션(Simulation), 부품 시험(Component Test), 하드웨어 인 더 루프 시험(Hardware-in-the-Loop Test), 통제된 현장 시험(Controlled Field Test), 공식 안전 검증(Formal Safety Validation)을 사용할 수 있다. 각 시험은 초기 조건, 적재물, 환경, 소프트웨어 버전, 측정 장비, 수용 임계값, 반복 횟수를 명확하게 정의해야 한다. 안전 시험에는 고장 주입(Fault Injection), 센서 차단, 통신 손실, 전원 차단, 비상 정지, 복구 절차도 포함되어야 한다.

요구사항은 단일 최적화 시제품뿐 아니라 생산 편차(Production Variation)와 수명 주기 열화(Lifecycle Degradation)를 고려해야 한다. 브레이크 마모, 타이어 마모, 배터리 노화, 센서 오염, 보정 편차(Calibration Drift), 기계 공차, 소프트웨어 업데이트는 시간이 지남에 따라 성능에 영향을 줄 수 있다. 따라서 수용 한계에는 현실적인 여유도(Margin)와 주기적인 검사 또는 재보정 요구가 포함되어야 한다. 새롭게 조정된 하나의 시제품에서만 만족할 수 있는 요구사항은 양산 제품에 충분하지 않다.

성능 및 안전 요구사항은 고객 요구, 사용 사례, 위험 요소, 아키텍처 구성 요소, 검증 결과와 추적 가능해야 한다. 하나의 요구사항이 변경될 경우 기계 설계, 전기 시스템, 소프트웨어 동작, AI 모델, 시험 절차, 운영 매뉴얼, 구축 조건에 미치는 영향을 파악할 수 있어야 한다. 이러한 추적성(Traceability)은 국부적인 성능 최적화가 시스템 수준의 안전성과 고객 가치를 약화시키는 것을 방지하고, 설계 검토 및 규제 평가를 위한 근거를 제공한다.

성능과 안전의 관계는 세심한 절충 관리(Trade-Off Management)를 필요로 한다. 더 높은 속도는 처리량을 향상시킬 수 있지만 정지 거리와 충돌 에너지를 증가시킨다. 더 큰 적재 용량은 사업 가치를 높일 수 있지만 안정성, 제동, 배터리 지속시간에 영향을 준다. 적극적인 자동 복구는 다운타임을 줄일 수 있지만 비정상 상황에서 불확실성을 증가시킬 수 있다. 따라서 PRD는 이러한 절충 관계를 명확하게 드러내고, 단일 최대 성능 수치보다 안전하고 예측 가능하며 반복 가능한 운용을 우선해야 한다.

잘 정의된 성능 및 안전 요구사항은 실제 환경에서 생산적이고 신뢰할 수 있으며 운용에 적합한 AMR을 개발하기 위한 측정 가능한 기준을 제공한다. 이러한 요구사항은 제품이 얼마나 빠르고 정확하며, 가용성이 높고, 효율적이며, 강건하고, 신속하게 반응해야 하는지를 규정하는 동시에 위험을 어떻게 예방하고, 감지하고, 통제하고, 검증할 것인지를 정의한다. 고객 가치, 운영 환경, 엔지니어링 역량, 위험 감소를 통합함으로써 PRD는 성능 향상이 사람과 시스템을 보호해야 하는 책임과 분리되지 않도록 보장한다.

## 01.05 AI and Data Requirements

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

인공지능 및 데이터 요구사항(AI and Data Requirements)은 자율이동로봇(Autonomous Mobile Robot, AMR)이 인공지능(Artificial Intelligence, AI)을 어떻게 활용해야 하는지, 운영 데이터를 어떻게 수집하고 관리해야 하는지, 그리고 개발 및 운영 전 과정에서 허용 가능한 성능을 어떻게 유지해야 하는지를 정의한다. 이러한 요구사항은 어떤 AI 기반 기능이 필요한지, 이를 지원하기 위해 어떤 데이터가 필요한지, 모델(Model)의 품질을 어떻게 평가할 것인지, 그리고 데이터를 어떻게 보호하고 업데이트하며 관리(Governance)할 것인지를 규정한다. 제품 요구사항 문서(Product Requirements Document, PRD)에서는 고객의 기대를 인지(Perception), 예측(Prediction), 의사결정(Decision Making), 모델 개발(Model Development), 검증(Validation), 엣지 배포(Edge Deployment), 운영 모니터링(Monitoring), 지속적인 개선(Continuous Improvement)과 연결하는 역할을 수행한다.

AI 요구사항은 특정 모델 구조(Model Architecture)나 알고리즘을 먼저 선택하는 것이 아니라, 로봇이 실제로 제공해야 하는 운영 기능(Operational Capability)에서 출발해야 한다. 고객은 일반적으로 어떤 AI 모델을 사용하는지보다 AMR이 사람을 감지하고, 장애물을 인식하며, 주변 환경을 이해하고, 주행 가능한 공간을 추정하며, 적재 상태를 판단하고, 움직임을 예측하며, 신뢰성 있는 의사결정을 수행할 수 있는지에 관심을 가진다. 따라서 PRD는 기술의 발전에 따라 모델을 교체하거나 개선할 수 있도록 구현 방식이 아닌 제품 수준의 동작과 측정 가능한 결과를 정의해야 한다.

AI와 기존 소프트웨어(Conventional Software)의 역할은 명확하게 구분되어야 한다. 일부 기능은 결정론적 로직(Deterministic Logic), 기하학적 방법(Geometric Method), 안전 제어기(Safety-Rated Controller), 규칙 기반 상태 기계(Rule-Based State Machine)로 구현하는 것이 적합하며, 다른 기능은 기계학습(Machine Learning)을 활용하는 것이 효과적이다. PRD는 어떤 기능에 AI가 반드시 필요한지, 선택적으로 사용할 수 있는지, 그리고 안전과 직결되는 기능에서는 AI가 유일한 판단 근거가 되어서는 안 되는지를 명확하게 정의해야 한다. 이러한 구분은 확률적 모델(Probabilistic Model)에 대한 불필요한 의존을 방지하고 더욱 견고한 시스템 아키텍처(System Architecture)를 지원한다.

인지 요구사항(Perception Requirements)은 일반적으로 AI 관련 요구사항 가운데 가장 큰 비중을 차지한다. AMR은 사람, 차량, 팔레트(Pallet), 랙(Rack), 문(Door), 바닥 경계(Floor Boundary), 잔해(Debris), 낮은 장애물(Low Obstacle), 돌출 구조물(Overhanging Structure), 환경 위험 요소(Environmental Hazard)를 감지해야 할 수 있다. 요구사항에는 인식 대상(Target Class), 감지 거리(Operating Range), 시야각(Field of View), 운용 환경, 최소 물체 크기(Minimum Object Size), 요구 신뢰도(Expected Confidence), 처리 지연(Latency), 실패 시 대응(Failure Response)이 포함되어야 한다. 또한 자율주행을 위한 일반 인지와 인증된 안전 기능(Certified Safety Function)은 명확하게 구분되어야 한다.

AI 성능은 학습 과정에서 사용하는 정확도 지표만으로 평가해서는 안 되며 제품 수준(Product Level)의 성능으로 평가해야 한다. 정밀도(Precision), 재현율(Recall), IoU(Intersection over Union), 분류 정확도(Classification Accuracy), 추적 성능(Tracking Quality)은 중요한 지표이지만, 임무 성공률(Mission Success), 불필요한 정지(False Stop Frequency), 위험 요소 미검출률(Missed Hazard Rate), 자율주행 효율(Navigation Efficiency), 도킹 신뢰성(Docking Reliability), 운영자 작업 부담(Operator Workload)과 직접 연결되어야 한다. 벤치마크(Benchmark) 점수가 우수한 모델이라도 현장에서 불안정한 동작이나 과도한 경고를 발생시키면 실제 제품으로는 적합하지 않을 수 있다.

데이터 요구사항(Data Requirements)은 각 AI 기능을 개발하고 운영하기 위해 필요한 정보를 명확하게 정의하는 것에서 시작된다. 필요한 데이터에는 카메라 영상(Camera Image), 라이다 포인트 클라우드(LiDAR Point Cloud), 레이더(Radar), 초음파(Ultrasonic), 위성항법(GNSS), 관성측정장치(IMU), 휠 오도메트리(Wheel Odometry), 로봇 상태(Robot State), 구동 명령(Actuator Command), 지도(Map Information), 임무 이벤트(Mission Event), 환경 정보(Environmental Context), 사람의 주석(Human Annotation) 등이 포함될 수 있다. PRD는 필요한 데이터 종류(Modality), 샘플링 주기(Sampling Rate), 시간 동기화 정확도(Synchronization Accuracy), 해상도(Resolution), 저장 기간(Storage Duration), 센서 간 관계를 정의해야 한다.

데이터셋 커버리지(Dataset Coverage)는 AI 모델이 학습 데이터에 포함된 조건만을 학습할 수 있기 때문에 매우 중요하다. 데이터 계획(Data Plan)은 다양한 환경, 조명 조건, 기상 조건, 바닥 재질, 적재물 종류, 사람의 행동, 차량 이동, 장애물 종류, 센서 오염, 드문 운영 상황(Rare Operational Event)을 포함해야 한다. 데이터는 개발이 쉬운 특정 환경이 아니라 실제 배치 환경의 다양성을 반영해야 하며, 부족한 조건은 알려진 한계(Known Limitation) 또는 향후 데이터 수집 우선순위(Future Collection Priority)로 기록되어야 한다.

데이터 품질(Data Quality) 요구사항은 손상된 데이터, 불완전한 데이터, 중복 데이터, 시간 정렬 오류(Misalignment), 잘못된 라벨(Label)을 어떻게 탐지하고 처리할 것인지를 정의해야 한다. 센서 보정(Sensor Calibration), 시간 동기화(Timestamp Synchronization), 좌표계 일관성(Coordinate Consistency), 파일 무결성(File Integrity), 메타데이터 완전성(Metadata Completeness), 라벨 정확도(Label Accuracy)는 모델 신뢰성에 직접적인 영향을 미친다. PRD는 데이터를 학습이나 평가에 사용하기 전에 최소 품질 기준과 승인 절차를 정의해야 하며, 품질이 낮은 데이터를 승인된 데이터와 혼합해서는 안 된다.

라벨링(Labeling) 요구사항은 주석 클래스(Annotation Class), 정의(Definition), 형식(Format), 품질 수준(Quality Level), 검토 절차(Review Procedure), 모호한 사례 처리 방법을 정의해야 한다. 명확한 정책이 없으면 동일한 객체를 여러 작업자가 서로 다르게 라벨링할 수 있다. 따라서 PRD는 클래스 정의, 경계 기준(Boundary Rule), 가림(Occlusion) 처리, 불확실성 표시(Uncertainty Marking), 품질 감사(Quality Audit)를 포함해야 하며, 복잡한 작업에서는 전문가 검증(Expert Validation)이 필요할 수도 있다.

학습 데이터(Training Dataset), 검증 데이터(Validation Dataset), 시험 데이터(Test Dataset)는 명확하게 분리되어야 한다. 검증 데이터는 모델 선택과 튜닝(Tuning)에 사용되며, 시험 데이터는 최종 성능을 독립적으로 평가하기 위한 것이다. 시험 데이터를 반복적으로 튜닝에 사용하면 실제 성능을 과대평가하게 될 수 있다. PRD는 데이터 분리 원칙, 버전 관리(Version Control), 접근 권한(Access Restriction), 평가 데이터셋 업데이트 조건을 정의해야 한다.

엣지 케이스(Edge Case)와 어려운 사례(Hard Case)는 실제 현장의 신뢰성을 결정하는 중요한 요소이다. 부분적으로 가려진 사람, 특이한 복장, 반사 물질, 투명 물체, 낮은 장애물, 강한 햇빛, 야간, 비, 먼지, 움직이는 그림자, 혼잡한 교차로, 훼손된 바닥 표시, 예기치 않은 적재물 형상 등이 이에 해당한다. 데이터 요구사항은 이러한 사례를 시뮬레이션(Simulation), 현장 시험(Field Test), 사고(Incident), 고객 피드백(Customer Feedback)을 통해 수집하고 우선순위를 관리하는 절차를 포함해야 한다.

합성 데이터(Synthetic Data)와 시뮬레이션은 실제 데이터 수집이 어렵거나 위험하거나 비용이 높은 상황을 보완하는 수단이 될 수 있다. 시뮬레이션 센서는 조명, 기상, 물체 위치, 움직임, 고장 상황을 다양하게 생성할 수 있다. 그러나 합성 데이터는 실제 센서 노이즈(Sensor Noise), 재질 특성(Material Property), 환경 복잡성, 사람의 행동을 완전히 재현하지 못할 수 있다. 따라서 PRD는 합성 데이터 사용 범위와 검증 방법, 그리고 시뮬레이션과 실제 환경 간 차이(Sim-to-Real Gap)를 평가하는 절차를 정의해야 한다.

모델 강건성(Model Robustness) 요구사항은 배포 이후 발생하는 환경 변화까지 고려해야 한다. 센서 노화(Sensor Aging), 카메라 오염(Camera Contamination), 지도 변경(Map Change), 계절에 따른 조명 변화, 새로운 차량 종류, 작업복 변화, 설비 구조 변경, 지역 차이 등은 AI 성능을 저하시킬 수 있다. 시스템은 이러한 성능 저하를 가능한 범위에서 감지하고, 초기 검증 결과가 영구적으로 유지된다고 가정해서는 안 된다. 요구사항에는 신뢰도 모니터링(Confidence Monitoring), 분포 변화 감지(Distribution Shift Detection), 대체 동작(Fallback Behavior), 정기 재평가(Scheduled Reevaluation)가 포함될 수 있다.

불확실성 처리(Uncertainty Handling)는 확률 기반 AI 모델의 특성상 매우 중요한 요구사항이다. AMR은 모든 AI 출력 결과를 동일하게 신뢰해서는 안 된다. PRD는 신뢰도 임계값(Confidence Threshold), 결과 거부 규칙(Rejection Rule), 상위 제어(Escalation), 결정론적 안전 로직과의 연계를 정의해야 한다. 신뢰도가 부족한 경우에는 감속, 정지, 운영자 지원 요청, 대체 센서 활용, 제한 운전 모드(Limited Operating Mode)로 전환하는 등의 절차가 필요하다.

실시간 성능(Real-Time Performance) 요구사항에는 추론 지연(Inference Latency), 업데이트 주기(Update Frequency), 계산 부하(Computational Load), 메모리 사용량(Memory Usage), 자원 경쟁(Resource Contention) 시의 동작이 포함되어야 한다. 아무리 정확한 모델이라도 응답 속도가 느리거나 위치추정(Localization), 경로 계획(Planning), 제어(Control), 안전 모니터링(Safety Monitoring)의 자원을 과도하게 사용한다면 적합하지 않다. PRD는 센서 입력부터 AI 출력까지의 전체 지연시간(End-to-End Delay)을 정의해야 한다.

AI 배포(AI Deployment) 요구사항은 지원되는 프로세서(Processor), AI 가속기(Accelerator), 모델 형식(Model Format), 실행 환경(Runtime Environment), 업데이트 절차(Update Mechanism)를 정의해야 한다. 양자화(Quantization), 가지치기(Pruning), 컴파일(Compilation), 배치 처리(Batching), 하드웨어 최적화(Hardware-Specific Acceleration)가 필요할 수 있다. 시스템은 모델 활성화 전에 메모리, 시간, 발열(Thermal), 전력 제한을 만족하는지를 확인해야 하며, 문제가 발생하면 롤백(Rollback)을 수행할 수 있어야 한다.

버전 관리 및 추적성(Version Control and Traceability)은 데이터셋, 라벨, 학습 코드, 파라미터(Parameter), 모델 가중치(Model Weight), 보정 파일(Calibration File), 평가 보고서(Evaluation Report), 배포 패키지(Deployment Package)를 모두 포함해야 한다. 배포된 모델은 어떤 데이터와 설정으로 생성되었는지 명확하게 연결되어야 하며, 이를 통해 결과를 재현하고, 버전을 비교하며, 문제 발생 시 영향을 받는 로봇을 식별할 수 있다.

AI 검증(AI Validation)은 실험실 시험(Laboratory Testing), 시뮬레이션, 기록 데이터 재생(Recorded Data Replay), 폐쇄 환경 시험(Closed-Course Testing), 실제 현장 시험(Field Trial)을 포함해야 한다. 평가는 정상 시나리오뿐 아니라 다양한 환경 변화, 알려진 엣지 케이스, 예상 가능한 실패 조건까지 포함해야 한다. PRD는 수용 기준(Acceptance Criteria), 반복 횟수, 통계적 신뢰도(Statistical Confidence), 최소 시나리오 범위를 정의해야 하며, 오프라인 모델 정확도와 실제 로봇 시스템 성능을 구분해야 한다.

AI가 사람과 다양한 환경을 대상으로 동작하는 경우 편향성(Bias)과 대표성(Representativeness)도 고려해야 한다. 특정 작업장, 복장, 체형, 차량 종류, 조명 조건에 치우친 데이터는 다른 환경에서 성능 저하를 일으킬 수 있다. 데이터 계획은 중요한 사용자 집단과 환경이 충분히 포함되어 있는지를 평가해야 하며, 성능 차이가 발견되면 제품 배포 전에 이를 개선해야 한다.

데이터 개인정보 보호(Data Privacy) 요구사항은 AMR이 영상, 음성, 위치 정보, 작업자 활동, 고객 자산, 운영 정보를 기록하는 경우 반드시 필요하다. PRD는 어떤 데이터를 수집할 수 있는지, 수집 목적, 보관 기간, 접근 권한, 익명화(Anonymization) 또는 삭제(Delete) 조건을 정의해야 한다. 데이터 수집은 정당한 제품 및 운영 목적에 한정되어야 하며, 저장 공간이 충분하다는 이유만으로 민감한 데이터를 보관해서는 안 된다.

데이터 보안(Data Security) 요구사항은 기록, 저장, 전송, 학습, 분석 과정 전반에서 정보를 보호해야 한다. 접근 제어(Access Control), 암호화(Encryption), 인증(Authentication), 무결성 검증(Integrity Check), 감사 로그(Audit Log), 안전한 삭제(Secure Deletion)가 필요할 수 있다. 로봇은 고객 데이터, 지도, 모델 파일, 운영 기록이 무단으로 유출되지 않도록 해야 하며, 클라우드 전송과 원격 진단(Remote Diagnostics)도 승인된 보안 정책을 따라야 한다.

데이터 소유권(Data Ownership)과 사용 권한(Usage Rights)은 현장 데이터 수집 이전에 명확하게 정의되어야 한다. 고객(Customer), 로봇 제조사(Robot Manufacturer), 시스템 통합 업체(System Integrator), AI 개발 조직은 원시 데이터(Raw Data), 가공 데이터(Derived Data), 라벨, 학습 모델, 성능 보고서의 소유권에 대해 서로 다른 기대를 가질 수 있다. PRD 또는 관련 계약서는 활용 범위, 데이터 재사용, 모델 학습 권한, 보관 기간, 공유 제한을 명확하게 규정해야 한다.

운영 데이터 수집(Operational Data Collection)은 유지보수와 지속적인 성능 향상을 지원하면서도 로봇과 네트워크에 과도한 부담을 주지 않아야 한다. 시스템은 이벤트 기반 센서 데이터(Event-Triggered Sensor Data), 임무 요약(Mission Summary), 모델 신뢰도(Model Confidence), 엣지 케이스, 장애(Fault), 사고 직전 상황(Near Miss), 환경 정보를 기록할 수 있다. 요구사항은 기록 조건, 이벤트 전후 저장 구간, 로컬 버퍼(Local Buffer), 업로드 우선순위, 압축(Compression), 네트워크 장애 시 동작을 정의해야 한다.

지속적인 학습(Continuous Learning)은 현장 로봇이 스스로 운영 모델을 변경하는 방식이 아니라 통제된 절차를 따라야 한다. 현장 데이터는 새로운 모델 학습에 사용할 수 있지만, 새로운 모델은 검토(Review), 검증(Validation), 승인(Approval), 단계적 배포(Staged Deployment)를 거쳐야 한다. 온라인 적응(Online Adaptation)은 명확하게 제한된 범위에서만 허용되어야 하며 롤백 기능을 제공해야 한다. 이러한 관리 체계는 통제되지 않은 모델 드리프트(Model Drift)를 방지한다.

운영 중 모니터링(Runtime Monitoring)은 AI 출력이 실제 환경에서도 계속 신뢰할 수 있는지를 감시해야 한다. 주요 지표에는 신뢰도 분포(Confidence Distribution), 감지 빈도(Detection Frequency), 오경보(False Alarm), 운영자 개입률(Intervention Rate), 처리 지연, 프레임 손실(Dropped Frame), 센서 상태(Sensor Health), 시나리오 커버리지(Scenario Coverage)가 포함된다. 모니터링은 비정상적인 변화를 식별해야 하지만, 모든 통계적 변화를 곧바로 결함으로 간주해서는 안 된다. 성능 저하가 확인되면 조사, 롤백, 운용 제한, 추가 데이터 수집을 수행해야 한다.

사람의 감독(Human Oversight) 요구사항은 언제 운영자, 원격 감독자(Remote Supervisor), 전문가가 AI의 판단을 검토해야 하는지를 정의한다. 일부 상황에서는 로봇이 행동하기 전에 사람의 승인이 필요하며, 다른 상황에서는 완전 자율 운행 후 사후 검토만 수행할 수도 있다. 인터페이스는 AI 모델의 내부 출력이 아니라 의사결정에 필요한 정보를 이해하기 쉬운 형태로 제공해야 하며, 운영자는 신뢰도 값의 의미와 한계를 이해하고 잘못된 탐지나 위험한 동작을 보고할 수 있어야 한다.

AI 안전(AI Safety) 요구사항은 모델 실패(Model Failure), 센서 장애, 손상된 입력(Corrupted Input), 불일치한 출력(Inconsistent Output)에 대한 대체 전략(Fallback Strategy)을 포함해야 한다. AI 구성 요소의 실패가 제어되지 않은 움직임이나 필수 기능 상실로 이어져서는 안 된다. 기능에 따라 결정론적 규칙, 이중 센서(Redundant Sensor), 감속 운행, 원격 지원(Remote Assistance), 안전 정지(Safe Stop)를 사용할 수 있으며, PRD는 각 기능에 허용되는 대체 절차와 정상 운행 복귀 조건을 정의해야 한다.

데이터 및 AI 요구사항은 고객 요구(Customer Needs), 기능 요구사항(Functional Requirements), 위험 요소(Hazard), 시스템 아키텍처(System Architecture), 데이터셋(Dataset), 모델(Model), 검증 항목(Verification Case)과 모두 추적 가능해야 한다. 요구사항이 변경되면 데이터 수집 계획, 라벨링 규칙, 학습 파이프라인(Training Pipeline), 엣지 하드웨어(Edge Hardware), 소프트웨어 인터페이스, 검증 보고서, 배포된 로봇에 미치는 영향을 분석할 수 있어야 한다. 이러한 추적성은 모델 개선이 시스템 호환성이나 안전성을 저해하지 않도록 보장한다.

성숙한 AI 및 데이터 요구사항 관리(AI and Data Requirements Process)는 학습 기반 AMR의 안정적인 기반을 제공한다. 이를 통해 AI 모델은 신뢰할 수 있는 데이터로 학습되고, 실제 운영 성능을 기준으로 평가되며, 컴퓨팅 제약을 고려하여 배포되고, 운영 중 지속적으로 모니터링되며, 통제된 절차를 통해 업데이트된다. 성능(Performance), 강건성(Robustness), 개인정보 보호(Privacy), 보안(Security), 추적성(Traceability), 전 생애주기 관리(Lifecycle Management)를 통합함으로써 PRD는 AI가 통제되지 않는 요소가 아니라 실제 고객 가치를 창출하는 핵심 기술로 활용될 수 있도록 지원한다.

## 01.06 System Interface Requirements

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

시스템 인터페이스 요구사항(System Interface Requirements)은 자율이동로봇(Autonomous Mobile Robot, AMR)이 내부 하위 시스템(Internal Subsystem) 및 외부 장비(External Equipment)와 전력(Power), 신호(Signal), 명령(Command), 데이터(Data), 기계적 힘(Mechanical Force), 운영 상태(Operational State)를 어떻게 교환해야 하는지를 정의한다. 이러한 요구사항은 기계(Mechanical), 전기(Electrical), 임베디드(Embedded), 소프트웨어(Software), 인공지능(Artificial Intelligence, AI), 클라우드(Cloud), 플릿(Fleet), 고객 시스템(Customer System)이 하나의 통합된 제품으로 동작하기 위한 경계를 설명한다. 명확한 인터페이스 정의는 무엇이, 언제, 어떤 방향으로 교환되며, 각 기능의 소유 주체가 누구인지와 예상하지 못한 상황에서 시스템이 어떻게 대응해야 하는지를 규정하여 통합 위험을 줄인다.

인터페이스 요구사항은 상호작용에 참여하는 시스템(Participating System), 상호작용 방향(Direction of Interaction), 전달되는 정보 또는 자원(Transferred Information or Resource), 동작을 시작하는 조건(Triggering Condition), 요구되는 응답(Required Response), 실패 시 동작(Failure Behavior)을 명확하게 식별해야 한다. 또한 설계, 구매, 구현, 검증을 지원할 만큼 충분히 구체적이어야 하지만 특정 공급업체나 일시적인 기술에 불필요하게 종속되어서는 안 된다. "로봇은 고객 시스템과 통신해야 한다"와 같은 표현은 메시지 내용, 타이밍, 프로토콜, 권한, 응답 확인, 호환성, 예외 처리를 정의하지 않기 때문에 충분하지 않다.

상세 인터페이스 요구사항을 작성하기 전에 시스템 경계(System Boundary)를 먼저 설정해야 한다. AMR 제품은 이동 플랫폼(Mobile Platform), 온보드 컴퓨터(Onboard Computer), 안전 제어기(Safety Controller), 센서(Sensor), 구동기(Actuator), 배터리 시스템(Battery System), 사람-기계 인터페이스(Human-Machine Interface, HMI), 무선 통신(Wireless Communication), 일부 클라우드 또는 플릿 서비스를 포함할 수 있다. 반면 엘리베이터, 컨베이어, 자동문, 창고 시스템, 검사 장비, 충전기, 고객 네트워크는 외부 시스템으로 분류될 수 있다. PRD는 제품 책임의 종료 지점과 고객, 공급업체, 시스템 통합 파트너의 책임 시작 지점을 명확하게 정의해야 한다.

내부 인터페이스(Internal Interface)는 로봇 내부의 주요 하위 시스템을 연결한다. 기계 구조는 모터, 배터리, 센서, 컴퓨터, 안전 장치, 적재 모듈(Payload Module), 보호 커버를 지지하면서 정렬, 냉각, 접근성, 진동 한계를 유지해야 한다. 전기 시스템은 각 장치에 제어된 전력과 보호 기능을 제공한다. 임베디드 제어기는 구동기와 명령 및 피드백을 교환하고, 상위 컴퓨터는 시간 동기화된 센서 데이터를 수신하여 자율주행 또는 임무 결정을 생성한다. 각 인터페이스에는 명확한 소유 주체와 승인된 명세가 있어야 한다.

기계 인터페이스 요구사항(Mechanical Interface Requirements)은 장착 형상(Mounting Geometry), 치수(Dimension), 공차(Tolerance), 하중 전달 경로(Load Path), 체결 방식(Fastener), 재질 호환성(Material Compatibility), 정렬 기준(Alignment Feature), 정비 접근성(Service Access), 환경 밀봉(Environmental Sealing)을 정의한다. 센서 마운트, 적재 플랫폼, 견인 장치, 도킹 장치, 로봇팔 인터페이스는 예상되는 진동, 충격, 가속, 제동, 적재 조건에서도 기계적으로 안정적이어야 한다. 또한 허용 힘(Allowable Force), 모멘트(Moment), 변형(Deflection), 무게 중심 한계(Center-of-Gravity Limit), 설치 방향(Installation Orientation), 교체 절차를 정의해야 한다.

전기 전력 인터페이스(Electrical Power Interface)는 전압 범위(Voltage Range), 전류 용량(Current Capacity), 접지(Grounding), 절연(Isolation), 보호 기능(Protection), 커넥터 유형(Connector Type), 극성(Polarity), 시작 순서(Startup Sequence), 종료 순서(Shutdown Sequence), 비정상 상태 대응(Abnormal-Condition Behavior)을 정의한다. AMR은 구동 시스템에 배터리 전압을 직접 공급하고, 센서, 컴퓨터, 통신 장치, 제어 전자장치에는 안정화된 저전압을 공급할 수 있다. 요구사항은 돌입 전류(Inrush Current), 회생 에너지(Regenerative Energy), 과도 전압(Transient Voltage), 단락(Short Circuit), 전자기 노이즈(Electromagnetic Noise), 열 한계(Thermal Limit), 안전 정비를 고려해야 한다.

로봇 내부의 통신 인터페이스(Communication Interface)는 CAN, CAN FD, EtherCAT, Ethernet, 직렬 통신(Serial Link), 디지털 입력 및 출력(Digital Input and Output) 등을 사용할 수 있다. PRD는 필요한 데이터 범주(Data Category), 메시지 소유권(Message Ownership), 갱신 주기(Update Rate), 지연 한계(Latency Limit), 동기화 요구(Synchronization Need), 오류 검출(Error Detection), 버스 부하 가정(Bus-Load Assumption)을 정의해야 한다. 상세 프레임 정의는 별도의 인터페이스 제어 문서(Interface Control Document, ICD)에 포함될 수 있지만, 제품 요구사항에서는 각 연결이 제공해야 하는 성능과 동작을 규정해야 한다.

센서 인터페이스(Sensor Interface)는 단순한 물리 커넥터와 데이터 형식 이상의 정보를 필요로 한다. 시스템은 센서의 위치(Position), 방향(Orientation), 보정 정보(Calibration), 시간 정보(Timestamp), 좌표계(Coordinate Frame), 동작 상태(Operating Status), 신뢰도(Confidence)를 알아야 한다. 카메라, 라이다(LiDAR), 레이더(Radar), 초음파(Ultrasonic), 위성항법(GNSS), 관성측정장치(IMU), 엔코더(Encoder), 안전 센서 데이터는 인지와 위치추정에서 결합될 수 있으므로 시간 동기화가 필수적이다. 요구사항은 허용 시간 오차, 보정 정확도, 시작 시 가용성, 데이터 손실 처리, 진단 보고를 정의해야 한다.

구동기 인터페이스(Actuator Interface)는 주행, 제동, 조향, 리프팅, 결합, 보조 기구가 명령을 수신하고 상태를 보고하는 방법을 정의한다. 명령에는 속도(Velocity), 위치(Position), 토크(Torque), 방향(Direction), 활성화 상태(Enable State), 운용 모드(Operating Mode)가 포함될 수 있으며, 피드백에는 실제 움직임, 전류(Current), 온도(Temperature), 리미트 스위치 상태(Limit-Switch State), 고장 코드(Fault Code), 준비 상태(Readiness)가 포함될 수 있다. 인터페이스는 상충되거나 위험한 명령을 방지해야 하며, 타임아웃(Timeout) 시 동작도 정의해야 한다.

소프트웨어 인터페이스(Software Interface)는 메시지(Message), 서비스(Service), 액션(Action), 공유 데이터 모델(Shared Data Model), 파일(File), 이벤트(Event), 응용 프로그래밍 인터페이스(Application Programming Interface, API)를 통해 모듈을 연결한다. 요구사항은 단순한 필드명보다 의미론적 해석(Semantic Meaning)을 정의해야 한다. 임무 식별자(Mission Identifier), 로봇 자세(Robot Pose), 지도 버전(Map Version), 적재 상태(Payload State), 고장 코드(Fault Code), 도킹 상태(Docking Status)는 모든 구성 요소에서 동일하게 해석되어야 한다. 단위(Unit), 좌표계 규칙, 타임스탬프, 열거형(Enumeration), 유효 범위, 값 없음 처리 방식도 표준화되어야 한다.

임무 및 플릿 인터페이스(Mission and Fleet Interface)는 AMR이 작업을 수신하고 실행 상태를 보고할 수 있도록 한다. 임무 요청에는 출발지, 목적지, 우선순위, 적재 정보, 경로 제약, 필요 장비, 시간 조건, 완료 기준이 포함될 수 있다. 로봇은 수신 확인(Acknowledgement), 수행 가능성 검증(Feasibility Validation), 수락 또는 거부, 진행 상태 보고, 완료 또는 실패 결과를 제공해야 한다. 요구사항은 중복 메시지 처리, 취소, 일시 정지 및 재개, 임무 소유권, 타임아웃, 플릿 연결 복구 이후 동작을 정의해야 한다.

기업 시스템 인터페이스(Enterprise Interface)는 AMR을 창고관리시스템(Warehouse Management System, WMS), 제조실행시스템(Manufacturing Execution System, MES), 병원 정보 시스템(Hospital Information System), 자산 관리 플랫폼(Asset Management Platform), 고객 애플리케이션과 연결한다. 이러한 시스템은 로봇 소프트웨어와 다른 데이터 구조와 거래 규칙(Transaction Rule), 가용성 기대치를 가진다. PRD는 운반 요청, 자재 식별자, 생산 상태, 재고 확인, 작업 완료와 같은 비즈니스 이벤트(Business Event)를 정의해야 한다. 거래 실패 또는 순서 오류 발생 시 검증, 재시도, 정합성 복구, 감사 기록 책임도 규정해야 한다.

인프라 인터페이스(Infrastructure Interface)는 엘리베이터, 자동문, 컨베이어, 게이트, 신호등, 충전기, 도킹 스테이션, 검사 장비와의 연동을 지원한다. 로봇은 대상 장치의 가용성을 확인하고, 접근 또는 동작을 요청하며, 허가를 수신하고, 물리적 준비 상태를 확인한 뒤 상호작용을 수행하고 완료를 보고해야 한다. 외부 시스템이 준비되지 않은 상태에서 로봇이 움직이지 않도록 인터록(Interlock)을 정의해야 한다. 응답 지연, 장치 사용 불가, 요청 충돌, 통신 장애, 불완전한 상호작용에서의 안전 이탈도 포함되어야 한다.

충전 인터페이스(Charging Interface)는 기계적 정렬, 전기적 연결, 통신, 에너지 관리 동작을 결합한다. AMR은 올바른 충전기를 식별하고, 허용된 정렬 공차 내에서 접근하고, 접촉을 형성하며, 전기적 호환성을 확인한 후 안전 검사가 완료된 경우에만 충전을 시작해야 한다. 필요에 따라 충전기와 로봇은 준비 상태, 전압, 전류, 온도, 고장, 충전 상태를 교환해야 한다. 인터페이스는 분리 동작, 비상 중단, 이물질, 접촉부 오염, 충전 실패 후 복구 절차를 정의해야 한다.

사람-기계 인터페이스(Human-Machine Interface, HMI)는 운영자, 정비 담당자, 감독자, 주변 사람이 로봇의 상태를 이해하고 제어할 수 있도록 한다. 시스템은 물리 버튼, 터치스크린, 조명, 경고음, 모바일 애플리케이션, 원격 대시보드, 정비 도구를 사용할 수 있다. 인터페이스 요구사항은 표시 정보, 명령 권한(Command Authority), 사용자 역할(User Role), 경보 우선순위(Alarm Priority), 언어 요구(Language Requirement), 접근성(Accessibility), 안전 관련 동작에 대한 확인 절차를 정의해야 한다. 동일한 운영 상태는 로컬 및 원격 화면에서 일관되게 표현되어야 한다.

클라우드 및 원격 서비스 인터페이스(Cloud and Remote-Service Interface)는 모니터링, 분석, 진단, 소프트웨어 업데이트, 모델 배포, 지도 관리, 장기 데이터 저장을 지원할 수 있다. 요구사항은 클라우드 연결이 끊어진 경우에도 유지되어야 하는 기능과 온라인 인증이 필요한 기능을 구분해야 한다. AMR은 불필요한 클라우드 의존 없이 핵심 로컬 기능을 계속 수행할 수 있어야 한다. 데이터 업로드 우선순위, 대역폭 제한, 버퍼링(Buffering), 압축(Compression), 재시도, 재연결 후 동기화도 정의해야 한다.

사이버보안 요구사항(Cybersecurity Requirements)은 모든 디지털 인터페이스에 적용된다. 장치와 서비스는 승인된 참여자를 인증하고, 데이터 무결성(Data Integrity)을 보호하며, 명령 권한을 제한하고, 로봇 제어, 지도, 소프트웨어, 모델, 고객 정보에 대한 비인가 접근을 방지해야 한다. 인터페이스 요구사항에는 암호화(Encryption), 인증서 관리(Certificate Management), 보안 세션(Secure Session), 접근 로그(Access Log), 네트워크 분리(Network Segmentation), 요청 빈도 제한(Rate Limiting)이 포함될 수 있다. 비정상, 재전송, 손상, 미인증 메시지는 안전 기능을 방해하지 않으면서 거부되어야 한다.

타이밍 요구사항(Timing Requirements)은 실시간 제어, 인지, 안전 모니터링, 임무 조정을 지원하는 인터페이스에서 매우 중요하다. PRD는 운용 중요도에 따라 갱신 주기, 최대 지연(Maximum Latency), 지터(Jitter), 타임아웃, 동기화 정확도, 응답 기한(Response Deadline)을 정의해야 한다. 상태 대시보드는 수초 지연을 허용할 수 있지만, 구동 제어와 장애물 대응 데이터는 밀리초 수준의 응답을 요구할 수 있다. 타이밍은 센싱, 처리, 네트워크 전송, 수신 소프트웨어, 실제 물리적 반응을 포함한 종단간 기준으로 측정해야 한다.

인터페이스 가용성(Interface Availability)과 성능 저하 동작(Degradation Behavior)은 실제 배치 환경에서 통신 장애가 불가피하므로 명확하게 정의되어야 한다. AMR은 짧은 패킷 손실(Packet Loss), 일시적 서비스 중단, 지속적인 인터페이스 실패를 구분할 수 있어야 한다. 영향을 받는 기능에 따라 로컬 운행 지속, 감속, 임무 일시 중지, 통신 재시도, 캐시 정보 사용, 지원 요청, 안전 정지를 수행할 수 있다. 요구사항은 무한 대기와 반복적인 위험 재시도를 방지해야 한다.

호환성 및 버전 관리(Compatibility and Version Management)는 소프트웨어, 펌웨어, 지도, AI 모델, 외부 서비스, 하드웨어 모듈이 독립적으로 발전하는 환경에서 필수적이다. 각 인터페이스는 지원 버전을 식별하고, 운용 시작 전에 호환되지 않는 조합을 탐지할 수 있어야 한다. 일부 릴리스에는 하위 호환성(Backward Compatibility)이 요구될 수 있고, 주요 변경은 연계된 업그레이드를 필요로 할 수 있다. 시스템은 지원하지 않는 구성을 명확하게 거부하고, 실패한 업데이트에 대비한 롤백(Rollback) 기능을 유지해야 한다.

인터페이스 제어 문서(Interface Control Document, ICD)는 구현 조직과 공급업체가 필요로 하는 상세 기술 정의를 제공한다. 여기에는 커넥터 도면, 핀 배열(Pin Assignment), 신호 레벨(Signal Level), 메시지 스키마(Message Schema), 프로토콜 순서(Protocol Sequence), 상태 기계(State Machine), API 정의, 타이밍 다이어그램, 오류 코드, 소유권 정보가 포함될 수 있다. PRD는 어떤 인터페이스에 통제된 문서가 필요한지와 승인 책임자를 정의해야 한다. 작은 필드나 커넥터 변경도 여러 하위 시스템에 영향을 줄 수 있으므로 공식 검토 절차를 따라야 한다.

인터페이스 검증(Interface Verification)은 검사(Inspection), 분석(Analysis), 시뮬레이션(Simulation), 프로토콜 시험(Protocol Testing), 전기 시험(Electrical Testing), 기계 조립성 확인(Mechanical Fit Check), 소프트웨어 통합(Software Integration), 하드웨어 인 더 루프 시험(Hardware-in-the-Loop Testing), 대표 현장 시나리오를 포함해야 한다. 시험은 정상 통신뿐 아니라 잘못된 입력, 지연 메시지, 중복 요청, 연결 해제, 데이터 손상, 버전 불일치, 전원 중단, 부분 체결 상황까지 검증해야 한다.

추적성(Traceability)은 모든 인터페이스 요구사항을 고객 요구, 사용 사례, 기능 요구사항, 아키텍처 구성 요소, 구현 부품, 검증 항목과 연결해야 한다. 인터페이스가 변경되면 관련 하드웨어 도면, 케이블 조립체(Cable Assembly), 소프트웨어 모듈, API, 시험 절차, 매뉴얼, 공급업체 계약, 현장 구성에 미치는 영향을 식별할 수 있어야 한다. AMR의 인터페이스 결함은 기계, 전기, 소프트웨어, AI, 안전, 플릿, 고객 시스템 전반으로 전파될 수 있기 때문에 이러한 영향 분석은 특히 중요하다.

잘 정의된 시스템 인터페이스 요구사항은 독립적으로 개발된 구성 요소들이 하나의 통합된 AMR 제품으로 동작할 수 있도록 한다. 이러한 요구사항은 물리적 연결, 전력 공급, 통신, 명령 권한, 데이터 해석, 타이밍, 보안, 진단, 장애 복구를 위한 신뢰성 있는 경계를 설정한다. 정상 상호작용뿐 아니라 비정상 상황의 동작까지 정의함으로써 PRD는 후반 통합 문제를 줄이고, 조직 간 책임을 명확하게 하며, 모듈화 개발을 지원하고, 로봇이 더 큰 자동화 환경 안에서 안전하고 효과적으로 운용될 수 있도록 한다.

## 01.07 PRD Review and Approval Process

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

제품 요구사항 문서(Product Requirements Document, PRD)의 검토 및 승인 프로세스(PRD Review and Approval Process)는 제품의 전체 생애주기(Product Lifecycle) 동안 제품 정의(Product Definition)를 체계적으로 평가(Evaluation), 검증(Validation), 승인(Approval), 유지관리(Maintenance)하기 위한 프레임워크를 제공한다. PRD는 단순한 기술 명세서가 아니라 제품이 무엇을 수행해야 하는지, 어떤 고객 가치를 제공해야 하는지, 어떤 제약 조건을 준수해야 하는지, 그리고 개발 조직들이 어떻게 협력해야 하는지를 정의하는 공식적인 합의 문서이다. 체계적인 검토 및 승인 절차는 실제 개발이 시작되기 전에 PRD가 기술적으로 정확하고, 사업적으로 가치가 있으며, 내부적으로 일관성을 유지하고, 고객의 기대와 완전히 일치하도록 보장한다.

검토 프로세스의 가장 중요한 목적은 변경 비용이 가장 낮은 초기 단계에서 문제를 발견하는 것이다. 기획 단계에서 발견된 오류는 대부분 문서 수정만으로 해결할 수 있지만, 동일한 문제가 하드웨어 구매, 소프트웨어 구현, 생산 준비, 고객 배치 이후에 발견되면 설계 변경, 일정 지연, 비용 증가, 계약 변경으로 이어질 수 있다. 따라서 PRD 검토는 개발이 시작되기 전에 체계적인 평가를 수행하여 후속 기술 위험을 줄이는 가장 효과적인 품질보증(Quality Assurance) 활동 중 하나이다.

검토 프로세스에는 관련된 모든 이해관계자(Stakeholder)가 참여해야 한다. 하나의 분야만으로는 제품 전체를 이해할 수 없기 때문이다. 제품 관리(Product Management)는 고객 가치와 시장 적합성을 검토하고, 시스템 엔지니어링(Systems Engineering)은 기술적 일관성을 검증하며, 기계 엔지니어링(Mechanical Engineering)은 구조적 실현 가능성을 검토한다. 전기 엔지니어링(Electrical Engineering)은 전원 및 하드웨어 인터페이스를 검토하고, 소프트웨어 엔지니어링(Software Engineering)은 구현 복잡성을 평가하며, AI 엔지니어링(AI Engineering)은 데이터와 모델 요구사항을 검토한다. 또한 생산(Manufacturing), 품질(Quality), 서비스(Service), 사업(Business) 부서도 참여하며, 계약이 필요한 경우 고객 대표(Customer Representative)도 검토에 참여할 수 있다.

검토 프로세스는 문서 작성(Document Preparation)과 문서 작성자의 자체 검증(Self-Verification)에서 시작된다. 공식 검토를 요청하기 전에 작성자는 PRD가 승인된 템플릿을 따르고 있는지, 필수 항목을 모두 포함하는지, 용어가 일관성 있게 사용되는지, 최신 참조 문서를 사용하고 있는지, 버전 관리(Version Control)가 이루어지고 있는지, 조직의 문서 작성 기준을 만족하는지를 확인해야 한다. 기본적인 편집 오류는 다분야 검토 전에 해결되어야 하며, 검토자는 문서 형식이 아니라 제품 품질에 집중할 수 있어야 한다.

범위 검증(Scope Verification)은 가장 먼저 수행되어야 하는 검토 항목 중 하나이다. 검토자는 PRD가 제품의 경계(Product Boundary), 목표 고객(Intended Customer), 운영 환경(Operational Environment), 사용 사례(Use Case), 지원 구성(Supported Configuration), 제외 범위(Exclusion), 가정(Assumption), 의존성(Dependency), 사업 목표(Business Objective)를 명확하게 정의하고 있는지를 확인해야 한다. 범위가 명확하지 않으면 기능 확장(Feature Expansion), 고객 기대 충돌, 중복 개발, 일정 불안정과 같은 문제가 발생하기 쉽다.

요구사항의 완전성(Requirement Completeness)은 제품의 모든 영역에서 체계적으로 평가되어야 한다. 기능 요구사항(Functional Requirements), 성능 요구사항(Performance Requirements), 안전 요구사항(Safety Requirements), AI 요구사항(AI Requirements), 인터페이스 요구사항(Interface Requirements), 환경 요구사항(Environmental Requirements), 운영 요구사항(Operational Requirements), 유지보수 요구사항(Maintenance Requirements), 규제 요구사항(Regulatory Requirements), 검증 요구사항(Verification Requirements), 전 생애주기 요구사항(Lifecycle Requirements)이 모두 검토 대상이 되어야 한다. 잘못된 요구사항보다 누락된 요구사항이 더 큰 위험을 초래하는 경우가 많으며, 이러한 누락은 통합 단계나 고객 인수시험(Customer Acceptance Test)에서 뒤늦게 발견되는 경우가 많다.

일관성 검토(Consistency Checking)는 요구사항들이 서로 충돌하거나 실현 불가능한 기대를 만들지 않는지를 확인한다. 성능 요구사항은 안전 제한과 충돌해서는 안 되며, 인터페이스 정의는 시스템 아키텍처와 호환되어야 하고, AI 기능은 사용 가능한 컴퓨팅 자원과 일치해야 하며, 운영 절차는 고객의 실제 업무 흐름과 부합해야 한다. 검토자는 용어, 수치, 운용 모드, 시간 가정, 측정 단위, 참조 표준을 검토하여 문서 전체의 모호성과 불일치를 제거해야 한다.

요구사항의 품질(Requirement Quality)은 시스템 엔지니어링(Systems Engineering)의 원칙에 따라 평가되어야 한다. 모든 요구사항은 필요성(Necessity), 고유 식별성(Unique Identification), 명확성(Clarity), 기술적 실현 가능성(Technical Feasibility), 시험 가능성(Testability), 측정 가능성(Measurability), 추적성(Traceability), 구현 독립성(Implementation Independence)을 만족해야 하며, 주관적인 표현을 포함해서는 안 된다. "빠르다(Fast)", "지능적이다(Intelligent)", "사용하기 쉽다(User Friendly)", "고품질(High Quality)", "효율적이다(Efficient)"와 같은 표현은 반드시 측정 가능한 수용 기준(Acceptance Criteria)과 함께 사용되어야 한다.

고객 가치(Customer Value)는 검토 과정 전체에서 가장 중요한 평가 기준이 되어야 한다. 모든 주요 요구사항은 고객의 문제를 해결하거나, 운영 효율을 향상시키거나, 안전을 높이거나, 총소유비용(Total Cost of Ownership)을 줄이거나, 유지보수를 단순화하거나, 제품 경쟁력을 향상시키는 목적을 가져야 한다. 명확한 고객 가치나 사업적 가치가 없는 요구사항은 반드시 재검토되어야 한다. 불필요한 기능은 개발 비용, 구현 복잡도, 검증 비용, 장기 유지보수 비용만 증가시키고 시장 경쟁력에는 기여하지 않을 가능성이 높다.

기술적 실현 가능성 검토(Technical Feasibility Review)는 제안된 요구사항이 현재의 기술 수준, 예산, 일정, 인력, 생산 능력, 공급망 제약 내에서 실제로 달성 가능한지를 평가한다. 성능 목표는 낙관적인 가정이 아니라 실제 엔지니어링 근거에 기반해야 한다. 요구사항이 현재 기술 수준을 초과하는 경우에는 목표 수정, 단계별 구현(Phased Implementation), 위험 완화(Risk Mitigation), 추가 연구 개발을 권고해야 한다.

위험 평가(Risk Assessment)는 모든 주요 PRD 검토와 함께 수행되어야 한다. 기술 위험(Technical Risk), 일정 위험(Schedule Risk), 생산 위험(Manufacturing Risk), 공급망 위험(Supply-Chain Risk), 사이버보안 위험(Cybersecurity Risk), AI 관련 위험(AI-Related Risk), 안전 위험(Safety Risk), 인증 위험(Certification Risk), 사업 위험(Commercial Risk)을 식별하고 문서화해야 한다. 높은 위험을 가진 요구사항은 최종 승인 전에 시제품(Prototype), 개념 검증(Proof of Concept), 시뮬레이션(Simulation), 실험실 시험(Laboratory Experiment), 공급업체 평가(Supplier Evaluation), 고객 검증(Customer Validation)이 필요할 수 있다.

검증 계획(Verification Planning)은 구현 이후가 아니라 요구사항 검토 단계에서 함께 검토되어야 한다. 모든 요구사항은 검사(Inspection), 분석(Analysis), 시뮬레이션(Simulation), 시연(Demonstration), 실험실 시험(Laboratory Testing), 현장 시험(Field Testing), 공식 검증(Formal Validation)과 같은 하나 이상의 검증 방법을 가져야 한다. 또한 수용 기준이 측정 가능하며, 필요한 시험 환경, 장비, 데이터셋, 계측 장비, 평가 절차가 실제로 준비 가능한지를 확인해야 한다.

추적성 검토(Traceability Review)는 모든 요구사항이 원래의 출처(Source)와 구현 결과(Implementation)를 연결할 수 있는지를 확인한다. 고객 요구(Customer Needs)는 제품 목표(Product Objectives), 기능 요구사항(Functional Requirements), 하위 시스템 명세(Sub-System Specifications), 구현 작업(Implementation Tasks), 검증 항목(Verification Cases), 수용 기준(Acceptance Criteria)으로 연결되어야 한다. 이러한 추적성은 변경 영향 분석을 쉽게 하고, 승인되지 않은 기능이 제품에 포함되는 것을 방지하며, 인증, 품질 감사, 규제 대응, 고객과의 의사소통에도 도움이 된다.

분야 간 설계 정합성(Cross-Functional Design Alignment)은 검토 회의에서 반드시 확인되어야 한다. 기계 구조는 전기 아키텍처를 지원해야 하고, 전기 인터페이스는 임베디드 소프트웨어를 지원해야 하며, 소프트웨어 아키텍처는 AI 처리 요구사항을 만족해야 하고, AI 모델은 사용 가능한 컴퓨팅 자원 내에서 동작해야 한다. 또한 모든 하위 시스템은 시스템 수준의 안전 목표(System-Level Safety Objectives)를 만족해야 한다. 많은 통합 문제는 독립적으로 최적화된 하위 시스템들이 전체 시스템 관점에서 검토되지 않았기 때문에 발생한다.

구성 관리(Configuration Management)는 PRD 승인 과정에서 매우 중요한 역할을 수행한다. 모든 검토 문서는 고유 식별자(Document Identifier), 개정 번호(Revision Number), 발행일(Publication Date), 작성자(Author), 검토자 목록(Reviewer List), 승인 상태(Approval Status), 변경 이력(Change History)을 가져야 한다. 이전 버전은 보관되어야 하지만, 개발 과정에서 실수로 사용되지 않도록 관리되어야 한다. 체계적인 구성 관리는 모든 개발 조직이 동일한 승인 문서를 기준으로 작업하도록 보장한다.

공식 검토 회의(Formal Review Meeting)는 비공식 토론이 아니라 구조화된 절차를 따라야 한다. 참가자는 회의 전에 문서를 검토하고, 문제를 독립적으로 식별하며, 중요도에 따라 분류하고, 해결 방안을 논의하며, 실행 항목(Action Item)을 지정하고, 의사결정을 기록해야 한다. 검토 회의는 조직 간 책임을 따지는 자리가 아니라 제품 품질을 향상시키기 위한 자리이며, 개인의 의견보다 객관적인 기술 근거(Objective Technical Evidence)가 의사결정의 기준이 되어야 한다.

검토 결과(Review Findings)는 제품 품질과 프로젝트 수행에 미치는 영향에 따라 분류되어야 한다. 치명적 문제(Critical Finding)는 안전, 규제 준수, 고객 계약, 핵심 기능에 영향을 주므로 승인 전에 반드시 해결되어야 한다. 주요 문제(Major Finding)는 구현 가능성, 시스템 통합, 검증, 운영 성능에 큰 영향을 준다. 경미한 문제(Minor Finding)는 문서 명확성, 일관성, 용어, 형식과 관련된 사항이다. 이러한 우선순위는 가장 중요한 문제 해결에 집중할 수 있도록 한다.

실행 항목 관리(Action-Item Management)는 모든 검토 이후 반드시 수행되어야 한다. 발견된 모든 문제는 담당자(Owner), 완료 예정일(Expected Completion Date), 해결 상태(Resolution Status), 검증 방법(Verification Method), 종료 승인(Closure Approval)을 가져야 한다. 검토 의견은 회의가 끝난 후 사라져서는 안 되며, 만족스럽게 해결될 때까지 추적 가능해야 한다. 체계적인 실행 항목 관리는 동일한 문제가 반복되는 것을 방지한다.

승인 권한(Approval Authority)은 검토 프로세스가 시작되기 전에 정의되어야 한다. 조직에 따라 제품 관리자(Product Management), 수석 시스템 엔지니어(Chief Systems Engineer), 소프트웨어 책임자, 하드웨어 책임자, 안전 엔지니어(Safety Engineer), 품질보증(Quality Assurance), 생산(Manufacturing), 규제 전문가(Regulatory Specialist), 경영진(Executive Management), 고객 대표(Customer Representative)의 승인이 필요할 수 있다. 승인 절차는 필수 승인자(Mandatory Approver), 선택 검토자(Optional Reviewer), 승인 순서(Approval Sequence), 조건부 승인 기준(Conditional Approval Criteria), 필요한 증빙 자료를 명확하게 정의해야 한다.

조건부 승인(Conditional Approval)은 일부 미해결 문제가 남아 있지만 개발 진행에 큰 영향을 주지 않는 경우 적용될 수 있다. 이러한 승인에는 미해결 항목, 담당자, 완료 기한, 관련 위험, 적용 제한 사항이 명확하게 기록되어야 한다. 그러나 안전 문제, 주요 고객 요구사항, 핵심 아키텍처 결정과 같은 근본적인 사항을 미루기 위한 수단으로 사용되어서는 안 된다.

공식 승인 이후 PRD는 제품 개발의 기준선(Baseline)이 된다. 개발 조직은 승인된 요구사항을 구현해야 하며, 개인적인 해석이나 비공식 논의를 기준으로 개발해서는 안 된다. 설계 변경은 승인 문서를 직접 수정하는 것이 아니라 변경 관리(Change Management) 절차를 통해 수행되어야 한다. 안정적인 기준선은 일정 계획, 구성 관리, 검증 관리, 공급업체 협력, 계약 관리를 가능하게 한다.

복잡한 제품 개발에서는 고객 요구, 기술, 규제, 공급업체, 시장 환경이 변화하기 때문에 요구사항 변경은 불가피하다. 모든 변경 제안(Change Request)은 기술적 근거(Technical Justification), 사업적 이유(Business Rationale), 영향을 받는 요구사항, 구현 영향, 검증 영향, 일정 영향, 비용 영향, 위험 분석, 우선순위를 포함해야 한다. 변경 요청은 승인된 PRD에 반영되기 전에 반드시 체계적인 검토를 거쳐야 한다.

영향 분석(Impact Analysis)은 변경 관리에서 가장 중요한 활동 가운데 하나이다. 단순해 보이는 요구사항 변경도 기계 설계, 전자 시스템, 소프트웨어 아키텍처, AI 모델, 통신 인터페이스, 안전 분석, 생산 공정, 문서, 공급업체 계약, 규제 승인, 시험 절차, 교육 자료, 유지보수 문서에 영향을 줄 수 있다. 체계적인 영향 분석은 예상하지 못한 부작용을 예방하고 전체적인 엔지니어링 품질을 향상시킨다.

정기적인 PRD 검토(Periodic PRD Review)는 최초 승인 이후에도 제품 생애주기 전체에서 계속 수행되어야 한다. 시스템 아키텍처 완료, 시제품 제작, 하위 시스템 통합, 검증 완료, 생산 준비, 고객 파일럿 운영, 상용 출시와 같은 주요 개발 단계는 승인된 요구사항이 여전히 유효한지를 확인할 수 있는 중요한 시점이다. 개발 과정에서 얻어진 교훈(Lessons Learned)은 현재 제품의 기준선을 유지하면서 차세대 제품 개선에도 활용될 수 있다.

검토 프로세스 자체도 지속적으로 개선되어야 한다. 조직은 검토 참여율, 결함 발견률(Defect Discovery Rate), 요구사항 품질 지표(Requirement Quality Metrics), 검토 기간, 변경 빈도, 승인 소요 시간, 출시 후 결함 원인, 고객 피드백, 시정 조치 효과(Corrective Action Effectiveness)를 측정할 수 있다. 이러한 지표는 검토 프로세스가 충분히 초기 단계에서 문제를 발견하는지와 조직의 엔지니어링 역량이 향상되고 있는지를 평가하는 데 활용된다.

디지털 협업 플랫폼(Digital Collaboration Platform)은 중앙 집중식 문서 저장(Document Storage), 버전 관리, 의견 추적(Comment Tracking), 워크플로 자동화(Workflow Automation), 전자 승인(Electronic Approval), 요구사항 추적성, 이슈 관리(Issue Management), 감사 이력(Audit History)을 제공함으로써 PRD 검토 효율을 크게 향상시킬 수 있다. 이러한 도구는 문서 중복을 줄이고, 분산된 개발 조직 간 협업을 지원하며, 품질관리시스템(Quality Management System)을 위한 객관적인 증빙 자료를 제공한다.

조직은 프로젝트마다 동일한 수준의 평가가 이루어질 수 있도록 표준 검토 체크리스트(Standard Review Checklist)를 운영해야 한다. 체크리스트에는 요구사항 명확성, 일관성, 완전성, 실현 가능성, 시험 가능성, 안전성, 사이버보안, AI 준비도, 인터페이스 호환성, 규제 준수, 생산성(Manufacturability), 유지보수성(Maintainability), 서비스성(Serviceability), 문서 품질, 고객 정렬(Customer Alignment)이 포함될 수 있다. 표준화된 체크리스트는 개인의 경험에 대한 의존도를 줄이고 여러 제품군에서 일관된 검토 품질을 확보하는 데 도움이 된다.

효과적인 PRD 검토 문화(PRD Review Culture)는 문서를 비판하는 것이 아니라 건설적인 기술 토론을 장려해야 한다. 검토 참여자는 위험을 발견하고, 제품 품질을 향상시키며, 고객 가치를 높이고, 성공적인 구현을 지원하는 데 집중해야 한다. 개방적인 의사소통(Open Communication), 객관적인 근거(Evidence-Based Reasoning), 상호 존중(Mutual Respect), 다분야 협업(Interdisciplinary Collaboration)은 권위 중심의 승인보다 훨씬 더 우수한 엔지니어링 의사결정을 가능하게 한다. 검토의 목적은 가능한 빨리 문서를 승인하는 것이 아니라 성공적인 제품 개발 가능성을 최대화하는 것이다.

체계적인 PRD 검토 및 승인 프로세스(PRD Review and Approval Process)는 제품 요구사항 문서를 단순한 계획 문서가 아니라 제품 전 생애주기를 지원하는 공식적인 엔지니어링 기준선(Engineering Baseline)으로 전환한다. 체계적인 기술 검토, 다분야 협업, 구조화된 위험 평가, 엄격한 구성 관리, 공식 승인 체계, 지속적인 추적성, 전 생애주기 변경 관리를 결합함으로써 조직은 안정적인 제품 개발 기반을 구축할 수 있다. 이러한 프로세스는 엔지니어링 품질을 향상시키고, 프로젝트의 불확실성을 줄이며, 고객 신뢰를 높이고, 승인된 모든 요구사항이 안전하고 경쟁력 있으며 유지보수가 용이하고 상업적으로 성공적인 자율이동로봇 개발에 직접 기여하도록 보장한다.

## 01.08 PRD Template and Examples

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

제품 요구사항 문서 템플릿(Product Requirements Document Template)은 자율이동로봇(Autonomous Mobile Robot, AMR) 제품을 명확하고 완전하며 검토 가능한 형태로 정의하기 위한 반복 가능한 구조를 제공한다. 템플릿은 엔지니어링 판단(Engineering Judgment)을 대체하지 않지만, 중요한 항목이 누락되지 않도록 하고 서로 다른 조직이 공통된 방식으로 요구사항을 설명하도록 지원한다. 섹션 순서, 용어, 요구사항 형식, 추적성 필드(Traceability Field), 승인 정보를 표준화함으로써 제품 관리, 시스템 엔지니어링, 소프트웨어, 하드웨어, AI, 안전, 생산, 품질, 서비스, 공급업체, 고객 간 의사소통을 향상시킨다.

PRD 템플릿의 목적은 제품에 대한 초기 의도를 체계적인 엔지니어링 기준선(Engineering Baseline)으로 전환하는 것이다. 초기 제품 아이디어는 일반적으로 비공식 회의, 프레젠테이션, 고객 요청, 시장 보고서, 시제품 시연 등을 통해 표현된다. 이러한 자료는 유용한 정보를 포함할 수 있지만 세부 수준, 정확성, 권한이 서로 다르다. 템플릿은 제품 범위, 고객 가치, 시스템 동작, 측정 가능한 목표, 제약 조건, 가정, 인터페이스, 검증 방법, 승인 결정을 하나의 공식 문서에 통합할 수 있는 관리된 공간을 제공한다.

실용적인 PRD 템플릿은 문서 관리 정보(Document Control Information)로 시작해야 한다. 이 섹션에는 문서 제목, 제품명, 문서 번호, 개정 번호, 상태, 작성자, 소유자, 작성일, 검토일, 승인일, 보안 등급, 적용 조직이 포함된다. 개정 이력(Revision History)은 주요 변경 내용을 요약하고 각 변경을 담당한 사람을 식별해야 한다. 이러한 항목은 행정적으로 보일 수 있지만, 개발 조직이 오래된 문서를 사용하는 것을 방지하고 제품 생애주기 전반에서 통제된 의사결정이 이루어졌다는 증거를 제공한다.

문서의 목적(Document Purpose)과 대상 독자(Intended Audience)는 템플릿의 앞부분에서 설명되어야 한다. 목적 설명은 PRD가 왜 존재하며 아키텍처, 설계, 구현, 검증, 생산, 배치, 유지보수 과정에서 어떻게 사용되는지를 명확하게 한다. 대상 독자에는 내부 엔지니어링 조직, 경영진, 외부 개발 파트너, 공급업체, 인증 기관, 생산 인력, 서비스 조직, 고객 대표가 포함될 수 있다. 독자를 정의하면 작성자가 적절한 기술 수준을 선택하고 설명되지 않은 가정을 줄일 수 있다.

제품 개요(Product Overview) 섹션은 기술 전문가와 비기술 이해관계자가 모두 이해할 수 있는 수준에서 제품을 설명해야 한다. 어떤 종류의 AMR을 개발하는지, 어떤 운영 문제를 해결하는지, 누가 사용하는지, 더 큰 자동화 환경에서 어떤 역할을 수행하는지를 설명해야 한다. 유용한 제품 개요는 요구사항을 이해할 수 있는 충분한 배경을 제공하면서도 마케팅 설명으로 변질되어서는 안 된다. 또한 제안 제품과 기존 솔루션의 차이를 설명하고 핵심 운영 개념(Operational Concept)을 명확하게 해야 한다.

사업 목표(Business Objectives)는 제품 요구사항이 측정 가능한 조직 및 고객 성과를 달성하기 위해 만들어지므로 반드시 포함되어야 한다. 템플릿은 목표 시장, 예상 고객, 경쟁 위치, 매출 기회, 배치 규모, 총소유비용(Total Cost of Ownership), 생산성 향상, 인력 절감, 안전 개선, 서비스 전략, 출시 일정에 관한 정보를 요구할 수 있다. 이러한 목표는 검토자가 각 주요 기술 요구사항이 불필요한 복잡성을 추가하는 것이 아니라 유효한 사업 목적에 기여하는지를 판단하는 데 도움을 준다.

고객 및 이해관계자(Customer and Stakeholder) 섹션은 제품 요구사항에 영향을 미치거나 제품 운용의 영향을 받는 조직과 개인을 식별한다. 여기에는 로봇 운영자, 감독자, 시설 관리자, 정비 기술자, 정보기술 조직, 안전 관리자, 생산 엔지니어, 물류 계획 담당자, 시스템 통합업체, 규제기관, 구매 조직이 포함될 수 있다. 각 이해관계자에 대해 역할, 기대, 우려사항, 권한, 수용 기준을 설명할 수 있다. 이는 개발 조직 내부의 가정이 아니라 실제 운영 요구가 요구사항에 반영되도록 지원한다.

문제 정의(Problem Statement)는 제품이 해결하려는 현재의 운영상 한계를 설명해야 한다. 강력한 문제 정의는 기술적 해결책을 즉시 제시하기보다 현재 업무 흐름, 지연, 위험, 비용, 품질 문제, 용량 제약, 안전 문제를 설명한다. 예를 들어 반복적인 수작업 자재 운반, 예측하기 어려운 운송 대기시간, 중량물과의 위험한 상호작용, 완료 작업의 추적성 부족 등이 문제일 수 있다. 문제와 해결책을 분리하면 다양한 설계 대안을 객관적으로 검토할 수 있다.

제품 비전(Product Vision)은 제품이 성공적으로 배치된 이후의 바람직한 미래 상태를 설명한다. AMR이 고객 운영을 어떻게 변화시킬지, 어느 수준의 자율성을 기대하는지, 사람의 역할이 어떻게 변화할지, 어떤 사업적 또는 운영적 개선이 이루어질지를 전달해야 한다. 비전은 설계 결정을 안내할 만큼 도전적이어야 하지만 관련 없는 기능이 프로젝트에 포함되지 않도록 충분히 구체적이어야 한다. 상세 요구사항을 해석하거나 우선순위를 결정할 때 공통 방향을 제공한다.

범위(Scope) 섹션은 제품과 개발 프로젝트에 포함되는 내용을 정의한다. 지원 기능, 하드웨어 구성, 소프트웨어 서비스, AI 기능, 운영 사이트, 적재물 유형, 통신 시스템, 액세서리, 고객 통합 활동을 식별해야 한다. 최초 출시와 향후 출시의 범위를 별도로 정의할 수도 있다. 이러한 구분은 장기 아이디어가 즉시 이행해야 하는 계약상 약속으로 오해되는 것을 방지하고, 모든 기능을 동시에 제공할 수 없는 경우 단계적 개발을 지원한다.

범위 제외(Out-of-Scope) 섹션도 동일하게 중요하다. 이 섹션은 프로젝트가 제공하지 않을 기능과 책임을 기록한다. 예를 들어 시설 재건축, 고객 네트워크 소유권, 모든 고객 업무 흐름의 자동 생성, 공공도로 운행, 위험물 처리, 지원하지 않는 로봇팔, 현재 출시 범위에 포함되지 않은 환경 인증 등이 해당될 수 있다. 명확한 제외 범위는 오해를 줄이고 이후 변경 요청을 평가할 수 있는 기준을 제공한다.

가정(Assumptions)과 의존성(Dependencies)은 전용 섹션에 기록해야 한다. 가정에는 바닥 상태, 무선 통신 범위, 운영자 교육, 적재물 제시 방식, 조명, 온도, 고객 인프라, 예상 임무량이 포함될 수 있다. 의존성에는 공급업체 부품, 외부 API, 충전 스테이션, 엘리베이터 제어기, 지도 데이터, 규제 승인, 클라우드 서비스, 고객 측 소프트웨어가 포함될 수 있다. 불확실한 가정에 기반한 요구사항은 해당 가정 변경 시 비용, 일정, 아키텍처, 검증에 큰 영향을 줄 수 있으므로 별도로 식별해야 한다.

운영 환경(Operational Environment) 섹션은 AMR이 어디에서 어떤 조건으로 작동해야 하는지를 정의한다. 실내 또는 실외 사용, 바닥 종류, 경사, 출입문 폭, 통로 형상, 조명, 먼지, 습기, 온도, 진동, 전자기 환경, 보행자 밀도, 차량 통행, GNSS 가용성, 네트워크 범위 등이 포함될 수 있다. 운영 환경은 가능한 한 정량적으로 설명되어야 하며, 이를 통해 엔지니어링 조직은 현실적인 배치 조건을 반영한 부품 선택과 검증 시험을 수행할 수 있다.

사용 사례(Use Cases)는 이해관계자와 외부 시스템이 제품과 상호작용하여 운영 목표를 달성하는 방법을 설명한다. 사용 사례에는 임무 할당, 자율주행, 적재물 픽업, 운송, 도킹, 충전, 검사, 원격 지원, 지도 갱신, 유지보수, 비상 복구 등이 포함될 수 있다. 템플릿은 시작 조건, 참여자, 정상 흐름, 대체 흐름, 완료 상태, 예외 동작을 기록해야 한다. 이러한 시나리오는 누락된 요구사항을 찾고 시스템 검증의 실질적인 기반을 제공한다.

운영 시나리오(Operational Scenarios)는 정상 상황과 예외 상황을 모두 포함해야 한다. 정상 운용은 시작, 임무 수행, 장애물 회피, 도킹, 종료를 설명할 수 있다. 예외 시나리오는 경로 차단, 통신 단절, 배터리 부족, 센서 성능 저하, 적재물 불일치, 도킹 실패, 비상 정지, 위치추정 불확실성, 외부 장비 사용 불가, 예상하지 못한 사람의 개입 등을 다룰 수 있다. 비정상 상황을 포함하면 PRD가 이상적인 동작만 설명하는 것을 방지하고 현실적인 신뢰성과 안전 계획을 지원한다.

기능 요구사항(Functional Requirements)은 제품이 무엇을 수행해야 하는지를 정의한다. 템플릿은 고유 식별자, 요구사항 문장, 근거, 출처, 우선순위, 검증 방법, 담당자, 추적성 참조를 포함하는 일관된 요구사항 형식을 제공해야 한다. 기능 요구사항에는 임무 관리, 자율주행, 위치추정, 장애물 대응, 적재물 처리, 도킹, 충전, 사용자 상호작용, 플릿 통신, 진단, 로그, 소프트웨어 업데이트, 운용 모드, 복구 기능이 포함될 수 있다. 각 요구사항은 명확하고 시험 가능한 문장으로 하나의 동작만 설명해야 한다.

성능 요구사항(Performance Requirements)은 필요한 기능을 어느 수준으로 수행해야 하는지를 정의한다. 템플릿에는 속도, 가속도, 정지거리, 위치 정확도, 도킹 반복정밀도, 임무 완료율, 장애물 검출거리, 배터리 운용시간, 충전시간, 응답 지연, 무선 가용성, 적재 용량, 경사로 주행 능력, 가동시간, 복구시간과 같은 목표값이 포함될 수 있다. 모든 값은 운영 조건, 단위, 허용오차, 검증 기준을 함께 포함해야 한다. 조건 없는 수치는 조직 간에 서로 다른 해석을 초래할 수 있다.

안전 요구사항(Safety Requirements)은 부수적인 항목이 아니라 통합된 제품 영역으로 제시되어야 한다. 템플릿은 위험요인(Hazard), 안전 목표, 위험 저감 조치, 운용 한계, 보호 정지, 비상 정지, 속도 제한, 제동 동작, 안정성 요구사항, 전기 보호, 열 보호, 사람 감지, 경고 장치, 안전 상태 동작을 식별해야 한다. 적용 가능한 표준, 규정, 위험 평가에 대한 참조도 포함되어야 한다. 안전 요구사항은 식별된 위험과 계획된 검증 증거에 추적 가능해야 한다.

AI 및 데이터 요구사항(AI and Data Requirements)은 제품 내에서 기계학습 또는 지능형 인지 기능이 수행할 역할을 정의해야 한다. 템플릿은 목표 AI 기능, 입력 센서, 출력 결정, 성능 지표, 신뢰도 처리, 데이터셋 범위, 라벨 품질, 엣지 케이스(Edge Case), 컴퓨팅 제약, 모델 버전 관리, 런타임 모니터링, 대체 동작, 재학습 통제, 개인정보 보호, 데이터 소유권, 사이버보안을 설명할 수 있다. 또한 불확실성과 실패 동작을 적절히 관리할 수 있도록 AI 기능과 결정론적 제어(Deterministic Control)를 구분해야 한다.

시스템 인터페이스 요구사항(System Interface Requirements)은 제품이 내부 하위 시스템과 외부 시스템과 어떻게 상호작용하는지를 정의한다. 템플릿은 기계, 전기, 통신, 소프트웨어, 센서, 구동기, 사람-기계, 플릿, 클라우드, 인프라, 충전, 기업 시스템 인터페이스를 식별해야 한다. 각 인터페이스 설명에는 참여 시스템, 정보 방향, 프로토콜, 데이터 모델, 타이밍, 권한, 보안, 응답 확인, 실패 동작, 호환성, 검증 방법이 포함될 수 있다. 상세한 커넥터나 메시지 명세는 관리된 인터페이스 제어 문서(Interface Control Document)를 통해 참조할 수 있다.

시스템 아키텍처(System Architecture) 섹션은 주요 제품 구성 요소와 그 관계에 대한 논리적 개요를 제공해야 한다. PRD가 상세 설계 명세서가 되어서는 안 되지만, 역할을 할당하고 제품 경계를 설명할 수 있는 수준의 아키텍처 배경은 제공해야 한다. 일반적인 구성 요소에는 이동 플랫폼, 전력 시스템, 안전 제어기, 모션 제어기, 인지 센서, 자율주행 컴퓨터, AI 컴퓨터, 무선 네트워크, 플릿 플랫폼, 사람-기계 인터페이스, 적재 모듈, 충전기, 외부 고객 시스템이 포함된다.

구성 및 변형 관리(Configuration and Variant Management)는 제품이 여러 적재물, 배터리 용량, 센서 패키지, 컴퓨팅 옵션, 구동 시스템, 지역별 버전, 고객별 액세서리를 지원할 때 포함되어야 한다. 템플릿은 표준 구성, 선택 구성, 시제품 구성, 미래 개념을 구분해야 한다. 각 변형은 명확한 호환성 규칙을 가져야 하며 핵심 제품 요구사항을 암묵적으로 변경해서는 안 된다. 구성 매트릭스(Configuration Matrix)는 설계, 시험, 승인되지 않은 조합이 사용되는 것을 방지할 수 있다.

규제 및 표준 요구사항(Regulatory and Standards Requirements)은 제품 개발에 영향을 주는 외부 의무를 식별한다. 적용 가능한 표준에는 기계 안전, 산업용 차량, 전기 장비, 배터리, 전자파 적합성(Electromagnetic Compatibility), 무선 통신, 사이버보안, 환경 보호, 기능 안전(Functional Safety), 데이터 개인정보 보호, 지역 인증이 포함될 수 있다. 템플릿은 관련 문서, 개정판, 적용 여부, 담당자, 요구 증거를 식별해야 한다. 표준과 규정은 장기 개발 과정에서 변경될 수 있으므로 정기적으로 검토해야 한다.

신뢰성, 가용성, 유지보수성, 서비스성(Reliability, Availability, Maintainability, and Serviceability) 요구사항은 장기간 운용에서 제품이 어떻게 성능을 유지해야 하는지를 정의한다. 템플릿은 예상 운용시간, 고장률, 임무 가용성, 진단 범위, 수리시간, 예방정비 주기, 교체 가능 모듈, 예비부품 전략, 정비 접근성, 원격 지원, 유지보수 데이터를 요구할 수 있다. 이러한 요구사항은 아키텍처와 부품 선택에 영향을 주므로 기능 설계가 완료된 이후로 미루어서는 안 된다.

생산 요구사항(Manufacturing Requirements)은 반복 가능한 생산과 조립을 위해 필요한 제품 특성을 설명해야 한다. 여기에는 생산 수량, 표준 부품, 조립 제약, 케이블 배선, 체결 방식, 보정 절차, 출하 전 시험(End-of-Line Testing), 추적성 라벨, 공급업체 관리, 품질 검사 지점, 생산 데이터 수집이 포함될 수 있다. PRD는 불필요한 생산 세부사항을 피해야 하지만, 비용, 품질 일관성, 확장성, 생산 준비도에 큰 영향을 주는 제품 수준의 기대사항은 정의해야 한다.

배치 및 시운전 요구사항(Deployment and Commissioning Requirements)은 AMR을 고객 현장에 어떻게 도입할지를 정의한다. 템플릿에는 현장 조사, 지도 생성, 네트워크 설정, 충전기 설치, 외부 시스템 통합, 인수시험, 운영자 교육, 안전 검증, 문서 전달, 생산 운영 인계가 포함될 수 있다. 어떤 작업을 제품 공급업체, 시스템 통합업체, 고객, 제3자가 수행하는지 명확히 해야 한다. 이러한 구분은 현실적인 프로젝트 일정과 상업 계약을 위해 필수적이다.

검증 및 유효성 확인 요구사항(Verification and Validation Requirements)은 템플릿 전체에 포함되어야 하며, 별도의 통합 섹션에서도 정리되어야 한다. 검증(Verification)은 각 요구사항이 정확하게 구현되었는지를 확인하고, 유효성 확인(Validation)은 완성된 제품이 의도된 환경에서 사용자의 요구를 만족하는지를 확인한다. 템플릿은 검사, 분석, 시뮬레이션, 시연, 실험실 시험, 현장 시험, 고객 인수시험을 검증 방법으로 지정할 수 있다. 각 요구사항은 측정 가능한 증거, 담당 조직, 완료 기준과 연결되어야 한다.

수용 기준(Acceptance Criteria)은 고객 또는 내부 승인 권한자가 제품을 수용하거나 출시하는 조건을 설명해야 한다. 필수 시험 완료, 성능 목표 달성, 치명적 결함 종료, 문서 제공, 현장 운용 성공, 교육 완료, 규제 증거 확보, 승인된 예외 상태 등이 포함될 수 있다. 수용 기준은 최종 시험이 시작되기 전에 정의되어야 하며, 승인 결정은 주관적 판단이 아니라 사전에 합의된 증거를 기반으로 이루어져야 한다.

요구사항 우선순위(Requirement Priority)는 예산, 일정, 기술적 제약으로 모든 기능을 동시에 제공할 수 없을 때 개발 조직의 의사결정을 지원한다. 템플릿은 필수, 높음, 중간, 낮음, 미래, 선택 등의 범주를 사용할 수 있다. 우선순위는 고객 가치, 안전 중요도, 계약 의무, 기술적 의존성, 출시 일정을 반영해야 한다. 낮은 우선순위로 표시된 요구사항이 제품 수용에 필수적이어서는 안 되며, 필수 요구사항에는 명확한 구현 및 검증 계획이 있어야 한다.

요구사항 근거(Requirement Rationale)는 특정 요구사항이 존재하는 이유를 설명하며, 향후 조직이 목적을 이해하지 못한 채 이를 삭제하거나 수정하는 것을 방지할 수 있다. 근거에는 고객 조사, 위험 분석, 시장 분석, 현장 데이터, 아키텍처 결정, 공급업체 제약, 규제 의무, 교훈(Lessons Learned)이 포함될 수 있다. 근거는 요구사항 자체를 대체하지 않지만, 설계 의사결정, 검토 회의, 변경 영향 분석에 중요한 배경을 제공한다.

템플릿의 요구사항 예시(Requirement Example) 섹션은 적절한 표현과 부적절한 표현을 모두 보여주어야 한다. "AMR은 오랫동안 운용되어야 한다"와 같은 모호한 문장은 측정 가능한 목표를 제공하지 않는다. 보다 강력한 예시는 AMR이 외부 충전 없이 정의된 임무 주기에서 최소 8시간의 대표 운용을 완료해야 한다고 규정할 수 있다. 개선된 문장은 기대 동작, 측정 조건, 수용 기준을 설정하면서 불필요한 구현 세부사항은 피한다.

두 번째 예시는 주관적인 자율주행 요구사항과 측정 가능한 요구사항을 비교할 수 있다. "로봇은 정확하게 주행해야 한다"는 표현은 정확도가 위치추정, 경로 추종, 정지, 도킹 중 무엇을 의미하는지 알 수 없어 해석이 불명확하다. 보다 명확한 요구사항은 지정된 바닥, 적재물, 속도, 위치추정 조건에서 AMR이 명령된 목적지 대비 정의된 위치 허용오차 내에 정지해야 한다고 규정할 수 있다. 이 요구사항은 합의된 측정 장비와 반복 시험을 통해 검증할 수 있다.

인터페이스 예시는 실패 동작을 정의하는 것의 중요성을 보여주어야 한다. 약한 표현은 AMR이 플릿 시스템으로부터 임무를 수신해야 한다고만 요구할 수 있다. 완전한 요구사항은 로봇이 각 유효한 임무 요청을 지정된 시간 안에 확인하고, 지원하지 않는 요청을 이유 코드와 함께 거부하며, 통신 타임아웃을 검출하고, 플릿 연결이 끊어졌을 때 정의된 운영 상태로 전환해야 한다고 규정해야 한다. 이러한 표현은 정상 운용, 예외 처리, 객관적 검증을 모두 지원한다.

안전 요구사항 예시는 "로봇은 안전해야 한다"와 같은 일반적인 문장에만 의존해서는 안 된다. 유용한 요구사항은 비상 정지 장치가 활성화되면 위험한 모션 명령을 제거하고, 요구되는 정지 기능을 수행하며, 자동 재시작을 방지하고, 승인된 안전 개념에 따라 의도적인 리셋을 요구하도록 정의할 수 있다. 구체적인 정지 성능과 안전 무결성(Safety Integrity)은 지원 안전 명세에서 정의하되 제품 요구사항과 추적성을 유지할 수 있다.

AI 요구사항 예시는 불확실성과 런타임 제약을 고려해야 한다. AI 모델이 항상 장애물을 정확히 인식해야 한다고 요구하는 대신, PRD는 인지 시스템이 지정된 환경 조건에서 정의된 객체 유형을 검출하고 신뢰도 또는 유효성 상태를 보고하도록 요구할 수 있다. 신뢰도가 승인된 임계값보다 낮을 경우 시스템은 감속하거나, 다른 센서 확인을 요청하거나, 안전하게 정지하거나, 시스템 안전 전략에 따라 정의된 다른 동작으로 전환해야 한다.

완전한 PRD 예시는 서로 다른 섹션의 요구사항들이 어떻게 연결되는지를 보여주어야 한다. 예측 가능한 자재 운송이라는 고객 요구는 임무 관리 기능, 임무 완료 성능 목표, 플릿 인터페이스 요구사항, 운영 가용성 기준, 충전 요구사항, 진단 기능, 검증 시나리오로 이어질 수 있다. 이러한 관계를 보여주면 작성자는 좋은 PRD가 서로 독립된 문장의 목록이 아니라 고객 가치, 제품 동작, 기술 제약, 수용 증거를 통합한 모델이라는 점을 이해할 수 있다.

템플릿에는 요구사항 추적성 매트릭스(Requirements Traceability Matrix)가 포함되거나 추적성을 관리하는 시스템을 참조해야 한다. 매트릭스는 이해관계자 요구, 사용 사례, 제품 요구사항, 하위 시스템 요구사항, 아키텍처 구성 요소, 위험요인, 검증 항목, 시험 결과를 연결할 수 있다. 이를 통해 고립된 요구사항(Orphan Requirement), 미구현 요구, 누락 시험, 제안된 변경의 영향을 식별할 수 있다. 추적성은 안전 평가, 인증, 고객 검토, 제품 업데이트에서 특히 중요하다.

검토 및 승인(Review and Approval) 섹션은 필수 검토자, 승인자, 검토 단계, 지적사항 분류, 실행 항목 담당자, 종료 증거, 승인 상태를 식별해야 한다. 템플릿에는 필요에 따라 제품 관리, 시스템 엔지니어링, 하드웨어, 소프트웨어, AI, 안전, 품질, 생산, 서비스, 사업 책임자, 고객의 서명 또는 전자 승인 기록이 포함될 수 있다. 승인 구조는 실제 의사결정 권한을 반영해야 하며 의미 있는 기술 검토 없이 형식적인 서명만 수집해서는 안 된다.

변경 관리(Change Management) 섹션은 승인된 요구사항을 어떻게 수정할 수 있는지를 설명해야 한다. 변경 요청은 제안된 개정, 근거, 영향을 받는 이해관계자, 기술 영향, 비용, 일정, 위험, 검증 영향, 필요한 승인 수준을 식별해야 한다. PRD 템플릿은 이전 기준선을 보존해야 하며, 감사 추적(Audit Trail) 없이 주요 결정이 대체되지 않도록 해야 한다. 통제된 변경 관리는 엔지니어링 일관성을 보호하면서 정당한 이유가 있을 경우 제품이 발전할 수 있도록 한다.

부록(Appendices)은 본문의 가독성을 방해하지 않으면서 상세한 지원 정보를 제공하는 데 사용할 수 있다. 일반적인 부록에는 용어, 약어, 참조 문서, 아키텍처 다이어그램, 규제 매트릭스, 고객 업무 흐름, 구성 표, 요구사항 예시, 위험 요약, 데이터 사전(Data Dictionary), 시험 환경 설명, 승인 기록이 포함된다. 각 부록은 본문에서 참조되어야 하며 동일한 구성 관리(Configuration Management) 규율을 따라야 한다.

최적의 PRD 템플릿은 지나치게 짧지도, 불필요하게 방대하지도 않아야 한다. 지나치게 단순한 템플릿은 안전, 인터페이스, 데이터, 유지보수, 배치, 검증 항목을 누락할 수 있다. 반대로 지나치게 경직된 템플릿은 의미 있는 분석 없이 형식적으로 섹션을 채우게 하거나 관련 없는 내용을 포함하게 만들 수 있다. 따라서 템플릿은 구조, 지침, 예시, 필수 필드를 제공하면서도 다양한 AMR 제품, 개발 단계, 고객 환경, 조직 프로세스에 맞게 통제된 조정을 허용해야 한다.

템플릿 안에 예시를 포함하면 작성자가 기대되는 상세 수준과 요구사항 작성 방식을 이해할 수 있으므로 일관성이 향상된다. 그러나 예시는 적용 가능성을 확인하지 않고 그대로 복사해서는 안 된다. 경량 실내 운송 로봇을 위해 작성된 요구사항은 실외 중량급 AMR, 검사 로봇, 로봇팔 플랫폼에 적합하지 않을 수 있다. 모든 예시는 지침으로 사용되어야 하며 실제 고객 요구, 시스템 아키텍처, 위험요인, 기술, 검증 조건에 따라 다시 작성되어야 한다.

잘 설계된 PRD 템플릿과 신중하게 선정된 예시는 제품 개발을 위한 공통 엔지니어링 언어(Shared Engineering Language)를 형성한다. 이는 고객 기대를 완전하고, 측정 가능하며, 추적 가능하고, 승인된 요구사항으로 전환하는 동시에 프로젝트와 제품 세대 간 일관성을 유지하도록 돕는다. 체계적인 검토, 구성 관리, 변경 통제, 생애주기 검증과 함께 사용될 때 템플릿은 단순한 문서 형식을 넘어선다. 안전하고 경쟁력 있으며 유지보수가 용이하고 확장 가능하며 상업적으로 성공적인 자율이동로봇 제품을 개발하기 위한 실질적인 프레임워크가 된다.
