---
title: "&lt;add&gt; – &lt;namespaceTable&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394657abcebb42192fb7a8b57b0402bcacf37693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a>&lt;add&gt; – &lt;namespaceTable&gt;
Představuje konfiguraci elementu, který obsahuje obor názvů jako předpona mapování, která lze poté použít ve filtrech XPath pro směrování.  
  
 \<system.serviceModel >  
\<směrování >  
\<namespaceTable >  
\<Přidat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– obor názvů|Řetězec obsahující obor názvů.|  
|Předpona|Řetězec obsahující předponu pro tento obor názvů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
