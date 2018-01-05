---
title: "&lt;security&gt; – &lt;basicHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c0ef60cdb53ed504d1738e4e17329f7420943312
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a>&lt;security&gt; – &lt;basicHttpBinding&gt;
Definuje možnosti zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<systém. ServiceModel >  
\<vazby >  
\<basicHttpBinding >  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelné. Určuje typ zabezpečení, který se používá. Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|-Zprávy není zabezpečená při přenosu.|  
|Přenos|Zabezpečení je k dispozici použití přenosu HTTPS. Protokolu SOAP zprávy jsou zabezpečené pomocí protokolu HTTPS. Služba je ověřen u klienta pomocí certifikátu X.509 služby. Klient je ověřen pomocí ClientCredentialType zadaný. Najdete v článku [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|Zpráva|Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP. Ve výchozím nastavení je text šifrovaný a podepsaný. Pro tuto vazbu systému vyžaduje, aby certifikát serveru poskytnuta klientovi vzdálené správy. Jediné platné `ClientCredentialType` pro tuto vazbu `Certificate`.|  
|TransportWithMessageCredential|Ověření integrity a důvěrnosti serveru jsou poskytovány zabezpečení přenosu. Ověření klienta je k dispozici prostřednictvím zabezpečení zpráv protokolu SOAP. Tento režim je důležité, když se uživatel ověřuje pomocí uživatelského jména a hesla a je stávajícího nasazení HTTP pro přenos zpráv zabezpečení.|  
|TransportCredentialOnly|Tento režim neposkytuje integrity a důvěrnosti zpráv. Poskytuje ověření klienta založené na protokolu http. Tento režim musí být použit s opatrní. By být používána v prostředích, kde se jiným způsobem (například IPSec) zajišťuje zabezpečení přenosu a zajišťuje pouze ověřování klienta [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<přenos >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Definuje nastavení zabezpečení přenosu pro základní služba HTTP. Tento element odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<Zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Definuje nastavení zabezpečení zpráv pro základní služba HTTP. Tento element odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Element vazby [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení není zabezpečené zprávu protokolu SOAP a klient není ověřen. Tento element umožňuje konfigurovat nastavení dalšího ověření zabezpečení pro `basicHttpBinding` elementu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Výběr typu přihlašovacích údajů](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
