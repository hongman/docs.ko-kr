---
title: "&lt;defaultCertificate&gt; 요소 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;defaultCertificate&gt; 요소
서비스 또는 STS가 협상 프로토콜을 통해 인증서를 제공하지 않을 때 사용할 X.509 인증서를 지정합니다.  
  
## 구문  
  
```  
  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## 특성 및 요소  
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### 특성  
  
|특성|설명|  
|--------|--------|  
|findValue|문자열.  검색할 값입니다.|  
|x509FindType|열거형입니다.  검색할 인증서 필드 중 하나입니다.|  
|storeLocation|열거형입니다.  검색할 두 시스템 저장소 위치 중 하나입니다.|  
|storeName|열거형입니다.  검색할 시스템 저장소 중 하나입니다.|  
  
## findValue 특성  
  
|값|설명|  
|-------|--------|  
|문자열|이 값은 검색 중인 필드\(X509FindType 특성으로 지정\)에 따라 다릅니다.  예를 들어, 지문을 검색할 경우 이 값은 16진수 문자열이어야 합니다.|  
  
## x509FindType 특성  
  
|값|설명|  
|-------|--------|  
|열거형|값에는 FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier가 있습니다.|  
  
## storeLocation 특성  
  
|값|설명|  
|-------|--------|  
|열거형|CurrentUser 또는 LocalMachine입니다.|  
  
## storeName 특성  
  
|값|설명|  
|-------|--------|  
|열거형|값에는 AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople 및 TrustedPublisher가 포함됩니다.|  
  
### 자식 요소  
 없음  
  
### 부모 요소  
  
|요소|설명|  
|--------|--------|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|클라이언트에 대해 서비스를 인증할 때 사용할 인증서를 지정합니다.|  
  
## 설명  
 인증서 기반 메시지 보안을 사용하는 바인딩의 경우 서비스에 보내는 메시지를 암호화하는 데 이 구성 요소에 지정된 인증서를 사용하며, 서비스에서는 클라이언트로 보내는 회신에 서명하는 데 이 인증서를 사용해야 합니다.  이 구성 요소는 서비스가 인증서를 지정하지 않을 때 사용되는 단일 인증서를 저장합니다.  
  
## 예제  
 다음 예제에서는 해당 URI가 http:\/\/www.contoso.com으로 시작하는 끝점에 사용할 인증서와 인증서 협상을 수행하지 않는 다른 모든 끝점에 대한 인증서를 지정합니다.  
  
```  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## 참고 항목  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>   
 [인증서 작업](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [\<authentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)   
 [클라이언트에 보안 설정](../../../../../docs/framework/wcf/securing-clients.md)   
 [서비스 및 클라이언트에 보안 설정](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)