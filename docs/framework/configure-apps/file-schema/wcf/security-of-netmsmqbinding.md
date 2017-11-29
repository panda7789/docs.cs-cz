---
title: "&lt;security&gt; – &lt;netMsmqBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 15ebbd1f0f139ef0d66ed802b990876735074485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a>&lt;security&gt; – &lt;netMsmqBinding&gt;
Definuje nastavení zabezpečení pro vazby služby MSMQ. Určuje, zda je povolen přenos nebo SOAP zabezpečení, a pokud ano, jaké úrovně režimu a ochranu ověřování se používají.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<– netMsmqBinding >  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Určuje typ zabezpečení, které řídí integrity, šifrování a ověřování. Platné hodnoty patří:<br /><br /> -None: To zakáže zabezpečení.<br />-Přenos: Ochrana a ověřování jsou nabízeny přenosu. To platí pro zabezpečení zpráv mezi dvěma fronty správci. Neexistuje žádné zabezpečení nabízené mezi aplikací a správce front. Existující aplikacím služby Msmq jsou funkčně srovnatelný s tímto typem režim zabezpečení.<br />-Zpráva: Určuje koncovou zabezpečení aplikací. Neexistuje žádné zabezpečení nabízené v přenosové vrstvě. Toto je podobná zabezpečení, které nabízí další standardní vazby.<br />-Obě: Nabízí zabezpečení v přenosu a zasílání zpráv vrstvy protokolu SOAP. Na obou úrovních vyžádáním stejných přihlašovacích údajů.<br /><br /> Výchozí hodnota je přenos. Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|Definuje nastavení zabezpečení protokolu SOAP zprávy. Tento element je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.|  
|[\<přenos >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro přenos MSMQ. Tento element je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Element vazby [ \<– netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
