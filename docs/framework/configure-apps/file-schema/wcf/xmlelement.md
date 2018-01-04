---
title: '&lt;xmlElement.&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 702b5ea1331aa0ac284d62809367a90e200a8ba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltxmlelementgt"></a>&lt;xmlElement.&gt;
Určuje element XML, který je odeslána v textu zprávy do služby tokenů zabezpečení Pokud požadování tokenu.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<wsFederatedBinding >  
\<Vazba >  
\<zabezpečení >  
\<Zpráva >  
\<tokenRequestParameters >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|xmlElement|Řetězec určující element XML, který je odeslána v textu zprávy do služby tokenů zabezpečení Pokud požadování tokenu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<tokenRequestParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Kolekce parametrů žádosti o token. Každý parametr je XML element.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Možnosti zabezpečení u vlastních vazeb](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)
