---
title: "&lt;add&gt; – &lt;entries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1583ec3cab3ed43556dc066c1e4753ddf9845ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;add&gt; – &lt;entries&gt;
Představuje směrování položku, která se mapuje na koncový bod klienta, který byl předtím definovaný filtr. Zprávy odpovídajících tomuto filtru budou odeslány do tohoto cílového místa.  
  
 \<system.serviceModel >  
\<směrování >  
\<routingTables >  
\<Tabulka >  
\<položky >  
\<Přidat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|backupList|Řetězec, který určuje odkaz na zálohování seznam koncových bodů.|  
|endpoint|Řetězec, který určuje odkaz na koncový bod klienta, která bude přijímat zprávy, které odpovídají filtru určeného `filterName` atribut.|  
|filterName|Řetězec, který určuje odkaz na element filtru.|  
|Priorita|Celé číslo, které určuje prioritu této položky.<br /><br /> Položky v tabulce směrování se vyhodnotí na základě priority, se 0 znamená nejnižší prioritu. Všechny záznamy pro určitou prioritou vyhodnocují současně, pokud neexistuje odpovídající položka je nalezena pro aktuální prioritu, se vyhodnotí další úroveň priority.<br /><br /> Tato hodnota je volitelná.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Konfigurační oddíl, který obsahuje položky směrování mapování.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
