# hongik_challenge
## 프로젝트 주제
이미지 학습을 통해 컨베이어 벨트위의 물건을 자동으로 분류하는 모형 및 시스템 제작

## 프로젝트 수행 기간
2023.03 - 2023.06 (4학년 1학기 홍익챌린지 프로젝트)

## 프로젝트 참여 인원
2명

## 프로젝트 수행 과정
1) 라즈베리파이와 센서 학습 및 실습 후 모형 제작
   
   ![image](https://github.com/Kim-yerin0904/hongik_challenge/assets/77713307/1cb021d3-162e-4d04-9d08-ea3d3c9cad35)
   + 완성된 모형 사진

  - 모형 제작 재료 : 라즈베리파이, GPIO 확장핀, 브레드보드, LED, 컨베이어 벨트, 서보 모터, USB 웹캠, 라즈베리파이 카메라, 적외선 센서, DC 모터, 모터 드라이브, 터미널 변환기
  - 라즈베리파이, GPIO 확장핀, 브레드 보드 : 센서 연결 및 조작
  - 서보모터 3개 : 물건 분류 시 이동시켜주는 역할
  - USB 웹캠 : 실시간 스트리밍을 위한 카메라
  - 라즈베라파이 카메라 : 이미지 분류를 위한 사진을 찍는 역할
  - 적외선 센서 : 컨베이어 벨트 위의 물건을 인식하기 위한 센서
  - DC 모터 : 컨베이어 벨트를 돌아가게 하는 모터
  - 모터 드라이버 : DC 모터의 속도, 방향 조정 역할
  - 터미널 변환기 : 모터 드라이버에 안정된 전원 공급 역할
    
2) 이미지 분류 모델 제작
  - kaggle에서 패스트 푸드 데이터 셋 다운 받아 사용.
  - roboflow에서 핫도그, 도넛, 피자 데이터를 각각 120장씩 라벨링
  - train data : test data = 8 : 2
  - 높은 정확도를 위해 train 데이터 증식
  - yolov5s 모델 이용 : img_size=426, batch=8, epoch=50
    ![image](https://github.com/Kim-yerin0904/hongik_challenge/assets/77713307/9cc90501-45ec-4f5a-b0c7-85caad902f0f)
    + 모델 정확도 confusion matrix
  
3) 서버, DB 구축 및 연동 웹페이지 제작
  - 네이버 클라우드 플랫폼에서 서버 대여, 공인 ip 주소 할당 및 연결
  - Django를 이용하여 웹페이지 제작, DB는 MySQL
  - 재고 파악 기능을 위한 stock app 생성
  - MySQL work bench 사용, stock 테이블 생성 product_name과 product_count로 구성
    
4) MQTT 통신
  - MQTT 통신을 위해 브로커는 mosquitto 사용
  - 센서의 정보를 서버에서 알 수 있도록 각 토픽을 만들어 구독하도록 함
    + camera 토픽 : 라즈베리파이 카메라가 물건의 사진을 찍을 때
    + aimodel 토픽 : yolov5 모델의 이미지를 통한 예측이 끝나 결과가 나올 때
    + dcmotor : dc모터 제어. 컨베이어벨트 멈추거나 다시 돌릴 때
    + infra : 적외선 센서에 물건이 감지 될 때
    + servo : 서보 모터 제어
      
5) 실시간 스트리밍 기능
  - 라즈베리파이의 motion 사용하여 구현
  - 라즈베리파이의 8081번 포트에서 확인 할 수 있음
![image](https://github.com/Kim-yerin0904/hongik_challenge/assets/77713307/8d439599-b82a-4057-982c-45f1f73dc15d)
+ 라즈베리파이 8081번 포트
  - ncloud 서버에서 만든 웹사이트 html의 img 태그에 라즈베라파이 8081번 포트 연결

6) 센서 제어를 위한 python 코드
  - 

## 프로젝트 수행 중 발생된 문제와 해결 방안
1) 
## 프로젝트 결과

