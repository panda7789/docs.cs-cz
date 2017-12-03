---
title: "&lt;bookmarkResumptionQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124b05d8e1ce9831a1efb3c6e62cc5e9fd3058fc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a>&lt;bookmarkResumptionQuery&gt; služby WCF
Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.  
  
 Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel >  
\<sledování >  
\<trackingProfile >  
\<pracovní postup >  
\<bookmarkResumptionQueries >  
\<bookmarkResumptionQuery >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [Pracovní postup sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
