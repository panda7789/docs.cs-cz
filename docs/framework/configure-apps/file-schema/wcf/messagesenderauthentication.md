---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c6183a8d27d56c7199b815ccb31b06f983a51b33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398392"
---
# \<messageSenderAuthentication>
Určuje nastavení ověřování pro certifikát partnerských vztahů používaných odesílatelem zprávy.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`certificateValidationMode`|Volitelný výčet. Určuje jeden z pěti režimů, který se používá k ověření přihlašovacích údajů. Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode> . Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.|  
|`customCertificateValidatorType`|Volitelný řetězec. Určuje typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` . Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Windows Communication Foundation (WCF) poskytuje výchozí validátor certifikátu peere, který ověřuje partnerský certifikát pro úložiště důvěryhodných osob. Také ověří, že certifikát řetězí až k platnému kořenu. Můžete implementovat vlastní validátor pro určení jiného chování a použít tento atribut k odkazování na vlastní validátor.|  
|`revocationMode`|Volitelný výčet. Určuje režim odvolaných certifikátů. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . Systém ověří, že se partnerský certifikát neodvolává tím, že ho vyhledá v seznamu odvolaných certifikátů. Tuto kontrolu můžete provést buď kontrolou online, nebo se seznamem odvolaných certifikátů v mezipaměti. Kontrolu odvolání lze zapnout nastavením tohoto atributu na hodnotu Nekontrolovat.|  
|`trustedStoreLocation`|Volitelný výčet. Určuje umístění důvěryhodného úložiště, ve kterém je certifikát partnerského vztahu ověřen systémem zabezpečení WCF. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|Určuje aktuální pověření pro partnerský uzel.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv. U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [\<certificate>](certificate-element.md) . Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku. Validátor může buď přijmout nebo odmítnout přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Síť rovnocenných počítačů](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpečení aplikací rovnocenného kanálu](../../../wcf/feature-details/securing-peer-channel-applications.md)
