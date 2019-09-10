---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855200"
---
# <a name="filtertables"></a>\<filterTables >
Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTables >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtry>](filters-of-routing.md)|Směrovací tabulka obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> směrování](routing.md)|Konfigurační oddíl, který obsahuje filtry směrování a směrovací tabulky.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
