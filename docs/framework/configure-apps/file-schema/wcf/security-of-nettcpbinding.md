---
title: "&lt;security&gt; – &lt;netTcpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bf42da647e598ad698bc36e6abff0d31350f3d96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>&lt;security&gt; – &lt;netTcpBinding&gt;
Definuje nastavení zabezpečení pro vazbu.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netTcpBinding>  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
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
|režim|Volitelné. Určuje typ zabezpečení, který se použije. Platné hodnoty jsou uvedeny níže. Výchozí hodnota je `Transport`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je vypnuté.|  
|Přenos|Zabezpečení přenosu je k dispozici přes TCP nebo SPNego používá protokol TLS. Služba pravděpodobně nutné nakonfigurovat s certifikáty protokolu SSL. Je možné kontrolovat úroveň ochrany s Tento režim.|  
|Zpráva|Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP. Ve výchozím nastavení je SOAP body šifrovaný a podepsaný. Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy. Ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.|  
|TransportWithMessageCredential|Zabezpečení přenosu je spolu s zabezpečení zpráv. Zabezpečení přenosu zajišťuje TLS přes TCP nebo SPNego a k zajištění integrity, šifrování a ověřování serveru. Zabezpečení zpráv protokolu SOAP poskytuje ověření klienta. Ve výchozím nastavení ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro přenos. Tento element je typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<Zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro zprávu. Tento element je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Element vazby [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Všechny standardní vazby poskytuje parametry pro řízení požadavky na zabezpečení přenosu. Tyto parametry obvykle zahrnují režim zabezpečení, který zadat, jestli se používá zabezpečení na úrovni zpráv nebo transportní vrstvy a výběr typu pověření klienta. Na základě volby možností tyto existuje, parametry zásobníku kanál je vytvořený pomocí příslušné zabezpečení.  
  
 Vazby poskytované systémem zadaný ve Windows Communication Foundation (WCF) jsou navržené tak, aby splňovaly některé z nejběžnějších požadavků scénáře sady. Každý z těchto vazeb umožňuje specifikaci požadavky na zabezpečení u některých konkrétních cílových scénářů.  
  
 Tento element konfigurace poskytuje zabezpečení specifikace pro `netTcpBinding`. Toto je bezpečné, spolehlivé a optimalizované vazbu vhodný pro komunikaci mezi počítači. Ve výchozím nastavení vygeneruje podpora protokolu TCP pro doručování zpráv a zabezpečení systému Windows pro zabezpečení zpráv a ověřování, WS-ReliableMessaging spolehlivost a zprávy v binární kódování runtime komunikačního balíku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
