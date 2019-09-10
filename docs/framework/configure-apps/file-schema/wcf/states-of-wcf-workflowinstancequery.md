---
title: <states>služby WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855036"
---
# <a name="states-of-wcf-workflowinstancequery"></a>\<stavy > WCF, \<workflowInstanceQuery >

Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.  
  
Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<stavy >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  

Žádné  
  
### <a name="child-elements"></a>Podřízené prvky
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.|  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.|  
  
## <a name="remarks"></a>Poznámky

Vrácené záznamy jsou filtrovány státy v této kolekci.  
  
Stav možné hodnoty jsou popsány v následující tabulce.  
  
|Stav|Popis|  
|-----------|-----------------|  
|Bylo přerušeno|Instance pracovního postupu byla zrušena.|  
|Byla dokončena|Instance pracovního postupu je dokončen.|  
|Odstranit|Instance pracovního postupu byl odstraněn.|  
|Nečinnosti|Instance pracovního postupu nečinnosti.|  
|Trvalé|Instance pracovního postupu je trvalý.|  
|Obnovení|Instance pracovního postupu po obnovení.|  
|Bylo zahájeno|Je spuštěn, instance pracovního postupu.|  
|UnhandledException|Instance pracovního postupu došlo k neošetřené výjimce.|  
|uvolněné|Instance pracovního postupu je uvolněn.|  
|Zrušeno|Instance pracovního postupu bylo zrušeno.|  
|Dočasně blokován.|Instance pracovního postupu je pozastaveno.|  
|Ukončen|Instance pracovního postupu je ukončeno.|  
|Pozastavení|Pozastavení je instance pracovního postupu.|  
  
## <a name="example"></a>Příklad

Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)
