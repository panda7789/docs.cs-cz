---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f790e294b832f43a595d0636c60a8a67da5ad56a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147885"
---
# <a name="ltfiltertablegt"></a>&lt;filterTable&gt;
Představuje směrovací tabulku, která obsahuje seznam filtrů určených k vyhodnocení zpráv a koncový bod klienta pro směrování zpráv v případě ohodnocení filtru hodnotou true.  
  
 \<system.serviceModel>  
\<směrování >  
\<routingTables >  
\<Tabulka >  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|name|Řetězec obsahující jedinečný název tohoto konfiguračního prvku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtry>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Konfigurační oddíl, který obsahuje směrovací tabulky.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
