---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855275"
---
# <a name="entries"></a>\<> položky
Záznam směrování obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se odesílají zprávy, když se filtr shoduje.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtru**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> položky**  
  
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
|[\<Filtry>](filters-of-routing.md)|Mapuje filtr na koncový bod klienta, který byl dříve definován. Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> směrování](routing.md)|Konfigurační oddíl, který obsahuje směrovací tabulku.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
