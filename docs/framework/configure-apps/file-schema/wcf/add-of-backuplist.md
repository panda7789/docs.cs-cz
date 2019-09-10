---
title: <add> z <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850554"
---
# <a name="add-of-backuplist"></a>\<Přidat > \<> backupList
Představuje prvek konfigurace, který definuje element záložního koncového bodu.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupList >** ](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec, který určuje název koncového bodu zálohy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> směrování](routing.md)|Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
