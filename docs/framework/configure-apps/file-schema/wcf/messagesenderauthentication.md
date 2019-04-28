---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: b8643a5321bbab692ebb704101c664105b4ab55c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763942"
---
# <a name="messagesenderauthentication"></a>\<messageSenderAuthentication>
Určuje nastavení ověřování pro sdílené certifikát používaný službou odesílatele zprávy.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<peer>  
\<messageSenderAuthentication>  
  
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
|`certificateValidationMode`|Volitelný výčet. Určuje jeden z pěti režimů pro ověření pověření. Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.|  
|`customCertificateValidatorType`|Volitelný řetězec. Určuje typ a sestavení používané pro ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`. Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF) poskytuje sdílené výchozí validátor certifikátu, který ověřuje certifikát peer proti úložišti důvěryhodných osob. Také ověřuje, že certifikát zřetězený platného kořenového. Můžete implementovat vlastní validátor určit různá chování a používání tohoto atributu na vlastní validátor.|  
|`revocationMode`|Volitelný výčet. Určuje režim odvolání certifikátu. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Systém ověří, že peer certifikát nebyl odvolaný ve vyhledávání v seznamu odvolaných certifikátů. Tato kontrola lze provést tak, že zkontrolujete online nebo seznam odvolaných certifikátů uložené v mezipaměti. Kontrola odvolání můžete vypnout pomocí nastavení tohoto atributu na NoCheck.|  
|`trustedStoreLocation`|Volitelný výčet. Určuje umístění úložiště pro důvěryhodného kde ověření certifikátu druhé strany systém zabezpečení WCF. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Určuje aktuální pověření pro partnerský uzel.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element musí být nakonfigurované, pokud je zvoleno ověřování zpráv. Pro výstup kanály, každá zpráva je podepsaná pomocí certifikátu poskytnutého [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Všechny zprávy, předtím, než se doručí do aplikace, jsou porovnávána s přihlašovacími údaji zprávy pomocí validátor určené `customCertificateValidatorType` atribut tohoto elementu. Validátor můžete přijmout nebo odmítnout přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
