---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a900a1f3fc2e07cffe04833cc3c7d3ccd063e24a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltpeerauthenticationgt"></a>&lt;peerAuthentication&gt;
Určuje nastavení ověřování pro certifikát sdílené používá sdílené uzel.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<sdílené >  
\<peerAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`certificateValidationMode`|Volitelné výčtu. Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů. Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také.|  
|`customCertificateValidatorType`|Volitelný řetězec. Určuje typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`. Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]poskytuje sdílené výchozí validátor certifikátu, který ověřuje certifikátu partnerského proti úložiště důvěryhodných osob. Také ověřuje, že certifikát řetězí platný kořenový. Můžete implementovat vlastní validátor zadejte odlišné chování a používat tento atribut tak, aby odkazovalo na vlastní validátor.|  
|`revocationMode`|Volitelné výčtu. Určuje režim odvolání certifikátu. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Systém ověří, že sdílené certifikát nebyl odvolaný podle vyhledá v seznamu odvolaných certifikátů. Tato kontrola může provést kontrolou online nebo seznam odvolaných certifikátů uložené v mezipaměti. Kontrola odvolání může být vypnuto nastavením tohoto atributu na hodnotu NoCheck.|  
|`trustedStoreLocation`|Volitelné výčtu. Určuje umístění důvěryhodného úložiště, kde je ověřen certifikátu partnerského [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zabezpečení systému. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Určuje, že aktuální přihlašovací údaje pro uzel sdílené.|  
  
## <a name="remarks"></a>Poznámky  
 `<authentication>` Element odpovídá <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy. Tento element určuje validátor, která se vyvolá při ověřování sousedním sousedním v mřížce. Když se nové sdílené pokusí navázat připojení sousedním, předá vlastní pověření na odpovídá partnera. Validátor odpovídající partner je vyvolána k ověření pověření vzdálené strany. Při každém navázání připojení sdílené v mřížce, oba partneři jsou vzájemně ověřeni, jsou vyvolány význam validátory na obou koncích.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Ověřování zpráv rovnocenného kanálu](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování rovnocenného kanálu](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
