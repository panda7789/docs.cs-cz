---
title: '&lt;windows&gt; elementu &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6687f93be26dedcb34f08770708c072742fdd4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a>&lt;windows&gt; elementu &lt;clientCredentials&gt;
Určuje nastavení pro pověření systému Windows, který se má použít k reprezentování klienta.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials >  
\<Windows >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Nastaví zosobnění předvoleb, které klient komunikuje se serverem. Režim zosobnění, který klient vybere nevynucuje na serveru. Platné hodnoty patří:<br /><br /> -Identifikace: Na serveru můžete získat identitu a oprávnění klienta, ale nelze zosobnit klienta.<br />-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.<br />-Delegování: Server může zosobnit kontext zabezpečení klienta na vzdálené systémy.<br />-Anonymní: Server nelze zosobnit nebo identifikaci klienta.<br />-None: Není přiřazen úroveň zosobnění.<br /><br /> Výchozí hodnota je identifikace. Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Nastavení této vlastnosti na `true` povoluje ověřování na starší verzi protokolu NTLM, pokud není k dispozici protokolu Kerberos.<br /><br /> Nastavení této vlastnosti na `false` způsobí, že [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aby best effort vyvolá výjimku, pokud se používá protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemusí zabránit odesílány prostřednictvím sítě pověření NTLM.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření, která používá k ověření klienta ke službě.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
