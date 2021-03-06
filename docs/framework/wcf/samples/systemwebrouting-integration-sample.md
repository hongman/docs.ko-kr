---
title: "SystemWebRouting Integration 샘플 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# SystemWebRouting Integration 샘플
이 샘플에서는 호스팅 계층과 <xref:System.Web.Routing> 네임스페이스에 있는 클래스의 통합을 보여 줍니다.  <xref:System.Web.Routing> 네임스페이스의 클래스를 사용하면 응용 프로그램에서 실제 리소스에 직접적으로 해당하지 않는 URL을 사용할 수 있습니다.  개발자는 웹 라우팅을 사용하여 실제 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 서비스에 다시 매핑되는 HTTP용 가상 주소를 만들 수 있습니다.  이렇게 하면 실제 파일 또는 리소스 없이 WCF 서비스를 호스트해야 하거나 .html 또는 .aspx와 같은 파일 확장명이 포함되지 않은 URL을 사용하여 서비스에 액세스해야 하는 경우에 유용합니다.  이 샘플에서는 <xref:System.Web.Routing.RouteTable> 클래스를 사용하여 global.asax에 정의된 실행 중인 서비스에 매핑되는 가상 URI를 만드는 방법을 보여 줍니다.  이 예제의 경우 WCF를 사용하여 만든 `movies` 피드와 `channels` 피드라는 두 개의 RSS 피드가 있습니다.  서비스를 활성화하는 URL에는 파일 확장명이 포함되어 있지 않으며 이 URL은 <xref:System.Web.HttpApplication.Application_Start%2A> 메서드에서 등록됩니다.  
  
> [!NOTE]
>  <xref:System.Web.Routing> 네임스페이스의 클래스는 HTTP를 통해 호스트되는 서비스에 대해서만 작동합니다.  
  
> [!NOTE]
>  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]에서는 확장명이 없는 URL을 지원하는 데 다른 메서드를 사용하므로 이 샘플은 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]에서만 작동합니다.  
  
> [!IMPORTANT]
>  컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.  계속하기 전에 다음\(기본\) 디렉터리를 확인하세요.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  이 디렉터리가 없으면 [.NET Framework 4용 WCF\(Windows Communication Foundation\) 및 Windows WF\(Workflow Foundation\) 샘플](http://go.microsoft.com/fwlink/?LinkId=150780)\(영문\)로 이동하여 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 및 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 샘플을 모두 다운로드하세요.  이 샘플은 다음 디렉터리에 있습니다.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### 이 샘플을 사용하려면  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]에서 WebRoutingIntegration.sln 파일을 엽니다.  
  
2.  F5 키를 눌러 솔루션을 실행하고 웹 개발 서버를 시작합니다.  
  
     샘플의 디렉터리 목록이 나타납니다.  파일 확장명이 .svc인 파일은 없습니다.  
  
3.  주소 표시줄에서 URL에 `movies`를 추가하여 http:\/\/localhost:\[port\]\/movies가 되도록 하고 Enter 키를 누릅니다.  
  
     movies 피드가 브라우저에 나타납니다.  
  
4.  주소 표시줄에서 URL에 `channels`를 추가하여 http:\/\/localhost:\[port\]\/channels가 되도록 하고 Enter 키를 누릅니다.  
  
     channels 피드가 브라우저에 나타납니다.  
  
5.  Alt\+F4를 눌러 웹 브라우저를 닫습니다.  
  
     개발 서버가 종료되지 않은 경우 알림 영역 아이콘을 마우스 오른쪽 단추로 클릭하고 **중지**를 선택합니다.  
  
#### IIS에서 호스트될 때 이 샘플을 사용하려면  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]에서 WebRoutingIntegration.sln 파일을 엽니다.  
  
2.  Ctrl\+Shift\+B를 눌러 프로젝트를 빌드합니다.  
  
3.  IIS\(인터넷 정보 서비스\) 관리자에서 웹 응용 프로그램을 만듭니다.  
  
    1.  IIS 관리자에서 **기본 웹 사이트**를 마우스 오른쪽 단추로 클릭하고 **응용 프로그램 추가**를 선택합니다.  
  
    2.  **별칭**에 `WebRoutingIntegration`을 입력합니다.  
  
    3.  **실제 경로**에서 프로젝트 내의 Service 폴더를 선택합니다.  
  
    4.  **확인**을 누릅니다.  
  
4.  웹 응용 프로그램을 마우스 오른쪽 단추로 클릭하고 **응용 프로그램 관리**, **찾아보기**를 차례로 선택하여 응용 프로그램을 시작합니다.  
  
5.  주소 표시줄에서 URL에 `movies`를 추가하여 http:\/\/localhost:\[port\]\/movies가 되도록 하고 Enter 키를 누릅니다.  
  
     movies 피드가 브라우저에 나타납니다.  
  
6.  주소 표시줄에서 URL에 `channels`를 추가하여 http:\/\/localhost:\[port\]\/channels가 되도록 하고 Enter 키를 누릅니다.  
  
     channels 피드가 브라우저에 나타납니다.  
  
7.  Alt\+F4를 눌러 웹 브라우저를 닫습니다.  
  
 이 샘플에서는 HTTP를 통해 호스트되는 서비스의 요청을 라우트하기 위해 <xref:System.Web.Routing> 네임스페이스의 클래스를 사용하여 호스팅 계층을 작성할 수 있음을 보여 줍니다.  
  
> [!NOTE]
>  기본 응용 프로그램 풀 버전이 버전 2로 설정되어 있으면 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]로 업데이트하세요.  
  
## 참고 항목  
 [AppFabric 호스팅 및 지속성 샘플](http://go.microsoft.com/fwlink/?LinkId=193961)