---
title: "WS-AtomicTransaction 구성 MMC 스냅인 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# WS-AtomicTransaction 구성 MMC 스냅인
WS\-AtomicTransaction 구성 MMC 스냅인은 로컬 및 원격 시스템에서 WS\-AtomicTransaction 설정의 일부분을 구성하는 데 사용됩니다.  
  
## 설명  
 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 또는 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]을 실행하는 경우 **제어판\/관리 도구\/구성 요소 서비스\/**로 이동하여 **내 컴퓨터**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택하여 MMC 스냅인을 찾을 수 있습니다.이 위치는 MSDTC를 구성할 수 있는 위치와 동일합니다.구성에 사용 가능한 옵션은 **WS\-AT** 탭에 그룹화되어 있습니다.  
  
 Windows Vista 또는 [!INCLUDE[lserver](../../../includes/lserver-md.md)]을 실행하는 경우 **시작** 단추를 클릭하고 **검색** 상자에 `dcomcnfg.exe`를 입력하여 MMC 스냅인을 사용할 수 있습니다.MMC가 열리면 **내 컴퓨터\\Distributed Transaction Coordinator\\로컬 DTC** 노드로 이동하여 마우스 오른쪽 단추를 클릭하고 **속성**을 선택합니다.구성에 사용 가능한 옵션은 **WS\-AT** 탭에 그룹화되어 있습니다.  
  
 앞의 단계는 로컬 컴퓨터를 구성하기 위한 스냅인을 시작하는 데 사용됩니다.원격 컴퓨터를 구성하려면 **제어판\/관리 도구\/구성 요소 서비스\/**에서 원격 컴퓨터의 이름을 찾고, [!INCLUDE[wxp](../../../includes/wxp-md.md)] 또는 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]을 실행하는 경우 비슷한 단계를 수행해야 합니다.Windows Vista 또는 [!INCLUDE[lserver](../../../includes/lserver-md.md)]을 실행하는 경우 Vista 및 [!INCLUDE[lserver](../../../includes/lserver-md.md)]에 대해 앞의 단계를 수행하고, 원격 컴퓨터의 노드 아래에 있는 **Distributed Transaction Coordinator\\로컬 DTC** 노드를 사용합니다.  
  
 도구의 사용자 인터페이스를 사용하려면 다음 경로에 있는 WsatUI.dll 파일을 등록해야 합니다.  
  
 **%PROGRAMFILES%\\Microsoft SDKs\\Windows\\v6.0\\Bin\\WsatUI.dll**  
  
 다음 명령을 사용하여 등록을 수행할 수 있습니다.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 이 도구를 사용하여 기본 WS\-AtomicTransaction 설정을 수정할 수 있습니다.예를 들어, WS\-AtomicTransaction 프로토콜 지원을 활성화 및 비활성화하고, WS\-AT에 대해 HTTP 포트를 구성하고, SSL 인증서를 HTTP 포트에 바인딩하고, 인증서 주체 이름을 지정하여 인증서를 구성하고, 추적 모드를 선택하고, 기본 및 최대 시간 제한을 설정할 수 있습니다.  
  
 로컬 컴퓨터에서만 WS\-AtomicTransaction 지원을 구성해야 하는 경우 이 도구의 명령줄 버전을 사용할 수 있습니다.명령줄 도구에 대한 [!INCLUDE[crabout](../../../includes/crabout-md.md)]는 [WS\-AtomicTransaction 구성 유틸리티\(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) 항목을 참조하십시오.  
  
 MMC 스냅인과 명령줄 도구 모두 일부 WS\-AT 설정 구성을 지원하지 않습니다.이러한 설정은 레지스트리를 직접 수정해야지만 편집할 수 있습니다.등록 설정에 대한 [!INCLUDE[crabout](../../../includes/crabout-md.md)]는 [WS\-Atomic Transaction 지원 구성](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)을 참조하십시오.  
  
### 사용자 인터페이스 설명  
 **WS\-Atomic Transaction 네트워크 지원 사용**:  
  
 이 확인란을 선택하거나 선택 취소하여 이 스냅인의 모든 GUI 구성 요소를 사용하거나 사용하지 않습니다.  
  
 이 확인란을 선택하기 전에 인바운드 통신이나 아웃바운드 통신 또는 두 통신 모두에서 네트워크 DTC 액세스를 사용할 수 있어야 합니다.MSDTC 스냅인의 **보안** 탭에서 이 값을 확인할 수 있습니다.  
  
#### 네트워크 그룹 상자  
 네트워크 그룹에서 SSL 암호화와 같은 HTTPS 포트 및 추가 보안 설정을 지정할 수 있습니다.DTC 네트워크 트랜잭션이 활성화되어 있지 않은 경우 이 그룹은 비활성화되어 회색으로 표시됩니다.  
  
 **HTTPS 포트**  
  
 WS\-AT에 사용되는 HTTPS 포트의 값입니다.값은 유효한 포트를 나타내는 1\-65535 범위의 숫자여야 합니다.HTTP 포트를 변경하면 HTTP 서비스 구성이 수정됩니다. 즉, 이전에 사용한 WS\-AT 서비스 주소가 해제되고 새 WS\-AT 서비스 주소가 새 포트에 따라 등록됩니다.또한 새로 선택한 포트는 SSL 암호화를 위해 현재 선택한 인증서를 사용하여 암호화됩니다.  
  
> [!NOTE]
>  이 도구를 실행하기 전에 방화벽을 이미 활성화한 경우 예외 목록에 포트가 자동으로 등록됩니다.이 도구를 실행하기 전에 방화벽을 비활성화한 경우 방화벽에 대해 추가로 구성되는 사항은 없습니다.  
  
 WS\-AT를 구성한 후에 방화벽을 활성화하는 경우 이 도구를 다시 실행하고 이 매개 변수를 사용하여 포트 번호를 제공해야 합니다.구성한 후에 방화벽을 비활성화하는 경우 WS\-AT는 추가 입력 없이 계속 작동합니다.  
  
 **끝점 인증서**  
  
 **선택** 단추를 클릭하면 로컬 컴퓨터에 현재 사용할 수 있는 인증서 목록이 표시되어 SSL 암호화에 사용할 수 있는 인증서를 선택할 수 있습니다.인증서에는 개인 키가 있어야 합니다.그렇지 않으면 오류 메시지가 표시됩니다.  
  
> [!NOTE]
>  선택한 포트에 대한 SSL 인증서를 설정하는 경우 인증서가 있으면 해당 포트와 연결된 원래 SSL 인증서를 덮어씁니다.  
  
 **허가된 계정**  
  
 **선택** 단추를 클릭하면 Windows 액세스 제어 목록 편집기가 호출됩니다. 이 편집기를 사용하면 **참여** 권한 그룹에서 **허용** 또는 **거부** 확인란을 선택하여 WS\-Atomic Transaction에 참여할 수 있는 사용자 또는 그룹을 지정할 수 있습니다.  
  
 **허가된 인증서**  
  
 **선택** 단추를 클릭하면 로컬 컴퓨터에 현재 사용할 수 있는 인증서 목록이 표시됩니다.그런 다음 WS\-Atomic Transaction에 참여시할 수 있는 인증서 ID를 선택할 수 있습니다.  
  
#### 시간 제한 그룹 상자  
 **시간 제한** 그룹 상자에서는 WS\-Atomic Transaction의 기본 및 최대 시간 제한을 지정할 수 있습니다.보내기 시간 제한의 유효한 값은 1부터 3600까지입니다.받기 시간 제한의 유효한 값은 0에서 3600까지입니다.  
  
#### 추적 및 로깅 그룹 상자  
 **추적 및 로깅** 그룹 상자에서 원하는 추적 및 로깅 수준을 구성할 수 있습니다.  
  
 **옵션** 단추를 클릭하면 추가 설정을 지정할 수 있는 페이지가 호출됩니다.  
  
 **추적 수준** 조합 상자에서 <xref:System.Diagnostics.TraceLevel> 열거형의 유효한 값을 선택할 수 있습니다.또한 동작 추적 및 동작 전파를 수행할지 또는 개인적으로 식별할 수 있는 정보를 수집할지를 지정하는 확인란을 사용할 수 있습니다.  
  
 **로깅 세션** 그룹 상자에서 로깅 세션도 지정할 수 있습니다.  
  
> [!NOTE]
>  다른 추적 소비자가 WS\-AT 추적 공급자를 사용 중인 경우 추적 이벤트에 새 로깅 세션을 만들 수 없습니다.이 시간 동안 로깅을 구성하려고 시도하면 "공급자를 사용하지 못했습니다. 오류 코드: 1" 오류 메시지가표시됩니다.  
  
 추적 및 로깅[!INCLUDE[crabout](../../../includes/crabout-md.md)][관리 및 진단](../../../docs/framework/wcf/diagnostics/index.md)을 참조하십시오.  
  
## 참고 항목  
 [WS\-Atomic Transaction 지원 구성](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)   
 [WS\-AtomicTransaction 구성 유틸리티\(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)   
 [관리 및 진단](../../../docs/framework/wcf/diagnostics/index.md)