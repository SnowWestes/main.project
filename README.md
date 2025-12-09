# main.project

# 🏠 IoT 실내 환경 모니터링 시스템 (Indoor Environment Monitoring System)

아두이노, 프로세싱, 앱인벤터를 활용한 **Wi-Fi 기반 실내 환경 모니터링 및 제어 시스템**입니다.
PC를 중계 서버(Web Server)로 활용하여, 외부 하드웨어(Wi-Fi 모듈) 추가 없이 기존 아두이노 우노 보드로 IoT 기능을 구현하였습니다.

## 📌 주요 기능
1.  **실시간 모니터링:** 온도(NTC)와 밝기(CDS) 데이터를 1초 단위로 앱에서 확인
2.  **원격 제어:** 앱을 통해 LED 조명과 부저(경보)를 원격으로 ON/OFF
3.  **자동 경고 시스템:**
    * 설정 온도(30°C) 초과 시 부저 자동 작동
    * 설정 밝기(300) 미만 시 LED 자동 점등
4.  **브릿지(Bridge) 통신:** 프로세싱이 아두이노(시리얼)와 앱(Wi-Fi) 간의 통신을 중계

## 🛠️ 시스템 구성도
`[Arduino Uno] <--(USB Serial)--> [PC / Processing Server] <--(Wi-Fi HTTP)--> [Smartphone / App Inventor]`

## ⚙️ 하드웨어 및 소프트웨어
### Hardware
* Arduino Uno R3
* Temperature Sensor (NTC Thermistor 10k)
* Light Sensor (CDS / LDR)
* LED (Red/Yellow)
* Piezo Buzzer (Passive)
* Resistors (10kΩ for sensors, 220Ω for LED)

### Software
* **Arduino IDE:** 센서 데이터 수집 및 액추에이터 제어
* **Processing 4:** PC 웹 서버 구축 (Port 8888), 데이터 파싱 및 중계
* **MIT App Inventor 2:** 안드로이드 앱 GUI 구성 및 HTTP 통신

## 🚀 설치 및 실행 방법 (How to Run)

### 1. Arduino
1.  `Arduino/Sensor_Device/Sensor_Device.ino` 파일을 아두이노에 업로드합니다.
2.  회로 연결:
    * NTC: A0
    * CDS: A1
    * LED: Pin 3
    * Buzzer: Pin 4

### 2. Processing (Server)
1.  `Processing/IoT_Bridge_Server/IoT_Bridge_Server.pde` 파일을 실행합니다.
2.  코드 상단의 `portName`을 아두이노가 연결된 포트(예: COM4)로 수정합니다.
3.  실행 버튼을 누르고 콘솔창에 뜨는 **IP 주소**를 확인합니다. (예: `192.168.0.15`)
    * *주의: 방화벽 경고가 뜨면 '허용'을 눌러야 합니다.*

### 3. App Inventor (Client)
1.  스마트폰을 PC와 **동일한 Wi-Fi** (또는 핫스팟)에 연결합니다.
2.  앱을 실행하고 상단 입력창에 프로세싱에서 확인한 **IP 주소와 포트(8888)**를 입력합니다.
    * 입력 예시: `192.168.0.15:8888`
3.  **[서버설정]** 버튼을 누르면 연결됩니다.

## ⚠️ 트러블 슈팅 (Troubleshooting)
* **Error 1101 발생 시:** PC의 방화벽을 끄거나 스마트폰 핫스팟을 사용하여 연결하세요.
* **데이터가 안 뜰 때:** 아두이노 시리얼 모니터가 켜져 있다면 끄고 프로세싱을 다시 실행하세요.

---
### 👨‍💻 Developer
* 이름: 이준완
* 소속: 국립경국대학교 1학년 컴퓨터공학과
