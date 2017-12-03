---
title: '&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dde956ab80a41d15a6496f84432a2ae2a9d09b76
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a>&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;
Určuje typy deklarací identity k odebrání v federované přihlašovací údaje.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<wsFederatedBinding >  
\<Vazba >  
\<zabezpečení >  
\<Zpráva >  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Typ claimType|Identifikátor URI, který definuje typ deklarace k odebrání.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Určuje kolekci typů požadované deklarace identity. Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje. Například příchozí pověření musí mít sadu typy deklarací identity. Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
