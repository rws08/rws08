# 어플리케이션 프로젝트 구성과 인원운영에 관하여

## 프로젝트 구성 컨셉
- 직관적이며 단순하게 파악이 가능하도록 함
- In(Data) -> Function(Manager/ViewModel 등) -> Out(View) 에 맞춰서 구성
- 처음 접하는 개발자도 빠르게 구성요소를 파악할 수 있게 함
- 개발 진행시 구성 인원간의 충돌을 최대한 회피함
  
## 프로젝트 구성
> Data - 어플리케이션에서 사용되는 데이터의 클래스들
> - Data 기준으로 화면/API 등의 유지보수 처리의 용이성 확보
> - ex) API를 통한 Data, 내부에서 관리하는 Data(SharedPreferance/NSUserDefaults 등)
>
> Manager - 어플리케이션의 제어를 위한 Singleton 클래스들
> - 어플리케이션 Life cycle에 맞춰서 관리
> - 공용 Data 제어, 각종 하드웨어 처리 제어, 통계용 정보 처리, 로그성 데이터 처리, Notification 연동 처리, 외부 라이브러리 연동 등
>
> View - 어플리케이션을 구성하는 화면들
>> - Page(ViewController/Activity)
>>   - 주요 화면들
>> - Widget(UIView/Layout)
>>   - 화면 구성을 위한 UI 화면들
>> - Default functions - CRUD를 차용
>>   - initData/UI(C) 
>>     - Data 의 초기값을 결정하며 UI의 초기상태 처리를 진행
>>     - 되도록 어떤 데이터도 없는 경우를 가정하여 처리(null 또는 loading data 상태)
>>   - setData/UI(R)
>>     - 기본 Data 가 갖춰지고 사용자의 컨트롤을 보장하는 UI 상태가 되도록 처리
>>     - Init 다음 바로 사용됨
>>   - updateData/UI(U)
>>     - 사용자 컨트롤 등에 의하여 Set된 데이터가 변경되는 경우의 처리(ex: 리스트의 필터값 변경, 비밀번호 검증에 대한 UX 등)
>>     - Init/Set 이후에 처리 되도록 구성하지만 반드시 사용되지는 않음
>>   - deleteData/UI(D)
>>     - 화면이 메모리상 제거되는 경우 사용
>>     - 특별한 경우를 제외하고 사용 불필요
>
> Library
> - 독립적인 라이브러리들
> - SNS SDK, Github ...

## 인원 운영
### Manager 담당 - 총 1명 또는 플랫폼당 1명
- 프로젝트 구성 관리
- View 개발자를 지원함

### View 담당 - 플랫폼당 Page 규모 기준으로 n명
- UI 개발
- Page별 비즈니스 로직 처리
- Page/Widget 별로 개별 Data를 구성

### 인원의 배정
- 신규 인원은 1Page의 신규 화면 개발 또는 구화면의 재개발을 진행함
- 프로젝트 진행시에는 Page 단위로 인원을 배정하여 충돌 회피
- Page내의 개발 방식의 독립성을 최대한 보장하고 서로 공유하도록 함
