---
title: '&lt;add&gt; – &lt;entries&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 5a61aefd92390eefb95d1f3e39236e53fa264990
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151498"
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;add&gt; – &lt;entries&gt;
Představuje položku směrování, která se mapuje na koncový bod klienta, který byl předtím definovaný filtr. Tomuto filtru odpovídá zprávy se odešlou do tohoto cílového místa.  
  
 \<system.serviceModel>  
\<směrování >  
\<filterTables >  
\<filterTable >  
\<položky >  
\<add>  
  
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
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|backupList|Řetězec, který určuje referenci na záložní seznam koncových bodů.|  
|endpoint|Řetězec, který určuje referenci na koncový bod klienta, který bude přijímat zprávy, které odpovídají filtru určeném `filterName` atribut.|  
|filterName|Řetězec, který určuje odkaz na prvek filtru.|  
|priorita|Celé číslo, které určuje priorita této položky.<br /><br /> Položky v tabulce směrování se vyhodnotí na základě priority, 0 je nejnižší priorita. Všechny položky s konkrétní prioritou jsou vyhodnocovány současně, pokud neexistuje odpovídající položka nebyl nalezen aktuální priorita, se vyhodnotí na další úroveň priority.<br /><br /> Tato hodnota je volitelná.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Konfigurační oddíl, který obsahuje položky směrování mapování.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
