
--------------------------------
# 스프링 입문 - 코드로 배우는 스프링부트, 웹MVC, DB 접근기술 - 김영한


--------------------------------
# 코코아톡 클론코딩 / HTML, CSS, Github


--------------------------------
# 바닐라 JS로 크롬앱 만들기 / Javascript


--------------------------------
# 실전! 스프링부트와 JPA활용1 - 웹 애플리케이션 개발 - 김영한


--------------------------------
# 진짜 입문자를 위한 클라우드와 AWS

O 클라우드의 장점은 유연성(필요할때 원하는 조건으로 사용), 내구성(오류시점에도 데이터가 안전하게 저장), 안전성(유지보수기간 최소화)임

O IaaS: 컴퓨팅, 스토리지, 네트워크 등의 리소스를 인터넷으로 연결된 서비스의 형태로 제공함
 - EC2 : 컴퓨팅 .CPU + 메모리로 구성 .GPU가 포함된 경우도 있음(EC2->인스턴스 생성)
 - EBS : 스토리지 .EC2에 연결해서 사용하는 SSD .OS 및 필요한 프로그램과 데이터의 일부를 저장
 - VPC : 네트워크 .EC2를 연결하기 위한 네트워크 망. VPC와 인터넷을 연결해야 서비스 사용 가능

O Amazon S3
 - simple storage service
 - 객체 저장소로서 파일단위로 저장(드롭박스처럼 파일업로드와 다운로드가 가능한 저장소)
 - 버킷만들기(그 후 폴더만들기, 업로드/다운로드 모두 가능, 퍼블릭으로 설정하면 해당 url로 접근가능함)
 - 정적페이지파일(html)에 대해서도 웹서버인것처럼 제공함. 

O AWS Route 53
 - 100% 가용성을 보장하는, DNS 서비스
 - 레코드 세트를 생성해서 원하는 url 주소로 설정할 수 있음

O AWS Virtual Private Cloud.
 - 각 서버를 연결하기 위한 사설 네트워크망. 용도에 따라 subnet으로 나눔(Public subnet/Private subnet)
 - 3-Tier Web Application Architecrue.(Route 53 -> Web서버인 public subnet->앱서버인 private subnet)

--------------------------------
# 초보를 위한 도커 안내서

O 도커의 장점
 - 오픈소스라 어느 회사에도 종속적이지 않고 간편함.
 - 표준성: 컨테이너라는 표준으로 서버를 배포하므로 모든 서비스들의 배포과정이 동일해짐
 - 독립적이고 간편함. 성능저하 거의 없음 (vs 가상머신)

O 쿠버네티스
 - 도커 여러개를 관리
 - 스케줄링 : 컨테이너를 적당한 서버에 배표
 - 클러스터링 : 여러개의 서버를 하나의 서버처럼 사용
 - 서비스 디스커버리 : 서비스를 찾아주는 기능
 
O 도커 컴포즈
 - docker-compose.yml 파일로 도커 컴포즈를 관리함.
 - docker-compose up <-> docker-copose down

O 도커 이미지
 - 새로운 상태를 이미지로 저장함(ubuntu -> ubuntu + git 을 이미지로 만듦)
 - 도커이미지 만드는 명령어 : docker build -t 이름공간/이미지이름:태그 .
 - .dockerignore 도 있음
 - 그런데 이러한 서버에서 작업하는 것들을 Dockerfile로도 관리할 수 있음.


O 이미지 저장소
 - push 를 하면 docker hub 에 띄우고 pull을 하면 불러오게 됨

--------------------------------
# TDC

O 딥러닝 Basic
-Layer : 레이어 중 데이터 들어오는 첫 번째 레이어 input layer, 결과 출력하는 마지막 레이어를 output layer, 이 두 레이어 사이에 있는 레이어는 모두 hidden layer 임. 
CF. Softmax함수: output 레이어에 적용되는 함수. 스코어에 대한 총합을 1로 맞추어서, 클래스간 상대적인 비교가 가능하게 가는 것

- Activation function(활성화 함수): 인공신경망의 각 뉴런이 데이터를 가중합하고 난 뒤 취하는 함수 ex.sigmoid, relu
. Sigmoid : 0~1사이의 실수로 결과출력, 가중치가 너무 크거나 작으면 의미없게 됨(곡선)
. Relu : 계산간편, 0 또는 1로만 결과를 출력함(직선)

- Loss함수: 모범답안(데이터로 주어짐)과 예측값(모델이 입력 데이터로 추론함)의 차이를 정량화하는 함수. 목적은 Loss가 가능한 한 작아지도록 하는 파라미터를 찾는 것임. Ex.MSE, NLL
. MSE : 전통적, sigmoid 랑 같이쓰면 너무 느림
. NLL : =Cross Entropy loss, 분류할때 유용, softmax랑 같이쓰면 특히 효과
1.	sparse_categorical_crossentropy: 라벨이 정수형태일 때
2.	CategoricalCrossentropy: Loss 정보가 one-hot encoding([0, 1] 혹은 [1, 0] 형태)

- Optimizer : 파라미터를 더 좋은 최적 값으로 업데이트해주는 역할을 수행
. Momentum 계열의 optimizer : 과거의 파라미터 업데이트 내역을 누적, 진행하던 방향성을 반영하여 빠르게 최적점으로 업데이트 ex.SGD
. Adaptive 계열의 optimizer: learning rate를 학습진행에 따라 유연하게 설정 ex.ADAM

-오버피팅이 발생했을 때 해결방안 : 
 1. early stopping(조기종료) 2.Dropout(드롭 아웃). Dense 아래에 놓어야함.


O CNN
- CNN =  Feature Extractor(Convolution+ Pooling) + Classifier(실제로 분류, hidden과 output)
. Convolution은 이미지의 특징을 추출하는 역할, Pooling은 파라미터 자체를 줄여주는 역할
. Feature Extractor= Conv2D(계층이 쌓일수록 좋음) + Maxpooling(2x2 filter 사이즈를 유지좋음.) 레이어로 구성. 이 둘을 번갈아 총 3~4 계층이 좋음
- activation은 softmax, relu 를 사용해야함.

- convolution 예시
Sequential([
         #### ANSWER #### 
         Conv2D(30, kernel_size=10, activation='relu', input_shape=(100, 100, 1))
         ################
])
->Output_shape(91, 91, 30)

- pooling 예시
model_mp2 = Sequential([
      MaxPool2D(pool_size=(3, 3), input_shape=(30, 30, 3))
])
->Output_shape(10, 10, 3) 
/ 여기에는 input_shape 안 넣어도 됨. 첫번째 conv에만 넣으면 됨

