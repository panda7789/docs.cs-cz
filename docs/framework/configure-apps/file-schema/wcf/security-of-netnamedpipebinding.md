---
title: "&lt;security&gt; – &lt;netNamedPipeBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fb5d1d3a767a9f4034473baad271c40677cedca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a>&lt;security&gt; – &lt;netNamedPipeBinding&gt;
Definuje nastavení zabezpečení pro vazbu.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<– netNamedPipeBinding >  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Určuje typ zabezpečení, který se použije pro tuto vazbu. Platné hodnoty patří:<br /><br /> -None: To zakáže zabezpečení.<br />-Přenos: Zabezpečení je zajištěno pomocí základního zabezpečení přenosu na základě. Je možné kontrolovat úroveň ochrany s Tento režim.<br />-Výchozí hodnota je přenos. Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|transport|Definuje nastavení zabezpečení pro přenos. Tento element je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Element vazby [ \<– netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Výběr typu přihlašovacích údajů](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
