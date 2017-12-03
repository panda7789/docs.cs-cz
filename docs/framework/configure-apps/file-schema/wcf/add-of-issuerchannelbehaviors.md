---
title: "&lt;add&gt; – &lt;issuerChannelBehaviors&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea76a96597796b10c97ea57ca38c3bda453468c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;add&gt; – &lt;issuerChannelBehaviors&gt;
Přidá chování koncového bodu, který se má použít při komunikaci s služby tokenů zabezpečení.  
  
> [!NOTE]
>  Pokud obsahuje všechny chování koncového bodu [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, bude vyvolána výjimka.  
  
 \<systém. ServiceModel >  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials >  
\<issuedToken >  
\<issuerChannelBehaviors > elementu  
\<Přidat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|issuerAddress|Identifikátor URI vydavatel tokenu zabezpečení ke komunikaci s.|  
|behaviorConfiguration|Název koncový bod chování definované ve stejném souboru konfigurace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Obsahuje kolekci [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] koncový bod chování klientů, který se má použít při komunikaci s určeným službám tokenu služby.|  
  
## <a name="remarks"></a>Poznámky  
 `issuerAddress`obsahuje identifikátor URI služby tokenů zabezpečení, který chce klienta ke komunikaci s. `behaviorConfiguration`odkazuje na koncový bod chování, které aplikace se používá v kanály vytvořené [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] získat vystavené tokeny od služby tokenů zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Postupy: vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
