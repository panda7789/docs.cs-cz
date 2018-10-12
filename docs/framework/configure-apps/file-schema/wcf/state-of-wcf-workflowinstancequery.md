---
title: '&lt;state&gt; služby WCF, &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 427cba7a51bfb908171e476cd703c6a40fd6e144
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123212"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a>&lt;state&gt; služby WCF, &lt;workflowInstanceQuery&gt;
Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.  
  
 Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<sledování >  
\<profily >  
\<profil trackingProfile >  
\<pracovní postup >  
\<workflowInstanceQueries >  
\<workflowInstanceQuery >  
\<stavy >  
\<Stav >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name"/>
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

|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.|  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|  
|-------------|-----------------|  
|[\<stavy >](states-of-wcf-workflowinstancequery.md)|Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.|  
  
## <a name="remarks"></a>Poznámky  

Vrácené záznamy jsou filtrovány státy v této kolekci.  
  
Stav možné hodnoty jsou popsány v následující tabulce:
  
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
      <state name="Started"/>  
    </states>  
  </workflowInstanceQuery>  
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
