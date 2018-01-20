---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 734deddc2924814b081ce80b8504fb77e78c095c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagesenderauthenticationgt"></a>&lt;messageSenderAuthentication&gt;
Určuje nastavení ověřování pro sdílené certifikát používaný službou odesílatele zprávy.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<sdílené >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication  
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
|`certificateValidationMode`|Volitelné výčtu. Určuje jeden z pěti režimů slouží k ověření přihlašovacích údajů. Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také.|  
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
 Tento element musí být nakonfigurován, pokud je zvoleno ověřování zpráv. Pro výstup kanály, je každá zpráva podepsaná pomocí certifikátu poskytované [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Všechny zprávy před doručí aplikaci, je zkontrolován pověřením zpráv pomocí validátor určeného `customCertificateValidatorType` atribut tohoto elementu. Validátor můžete buď přijmout nebo odmítnout přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Ověřování zpráv rovnocenného kanálu](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování rovnocenného kanálu](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
