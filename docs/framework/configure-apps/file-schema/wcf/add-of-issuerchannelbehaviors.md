---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 65c76cba696ae388d6184eaaa70a1f2f5a301e1c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271791"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<add> of \<issuerChannelBehaviors>
Přidá chování koncového bodu se použije při komunikaci se službou tokenů zabezpečení.  
  
> [!NOTE]
>  Pokud jakékoliv chování koncového bodu obsahuje [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, bude vyvolána výjimka.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials>  
\<issuedToken>  
\<issuerChannelBehaviors> Element  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|issuerAddress|Identifikátor URI vystavitele tokenu zabezpečení komunikovat.|  
|behaviorConfiguration|Název chování koncového bodu definované ve stejném souboru konfigurace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Obsahuje kolekci chování koncového bodu klienta Windows Communication Foundation (WCF) se použije při komunikaci s určeným službám tokenu služby.|  
  
## <a name="remarks"></a>Poznámky  
 `issuerAddress` obsahuje identifikátor URI, který chce komunikaci s klientem služby tokenů zabezpečení. `behaviorConfiguration` odkazuje na chování koncového bodu, který aplikace používá v kanálech vytvořené technologií Windows Communication Foundation (WCF) Chcete-li získat od služby tokenů zabezpečení vydané tokeny.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
- [Postupy: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
