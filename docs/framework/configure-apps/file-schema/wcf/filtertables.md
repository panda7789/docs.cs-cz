---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 028681acffcd93633807bdb1c6fa78aab98011c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablesgt"></a>&lt;filterTables&gt;
Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv, když odpovídá filtru.  
  
 \<system.serviceModel >  
\<směrování >  
\<routingTables >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtry >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Směrovací tabulky, které obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Konfigurační oddíl, který obsahuje filtrech směrování a směrovacích tabulek.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
