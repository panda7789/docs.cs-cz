---
title: <bookmarkResumptionQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 36d169b78e78692c7b45c75d5d375bddbba1c66f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850102"
---
# <a name="bookmarkresumptionquery-of-wcf"></a>\<bookmarkResumptionQuery > WCF

Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.  
  
Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.|  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)
