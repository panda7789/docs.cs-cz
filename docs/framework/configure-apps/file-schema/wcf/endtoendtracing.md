---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1867e307ba004af821045e7d1b5775c470d8a3e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266751"
---
# <a name="endtoendtracing"></a>\<endToEndTracing>
Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.  
  
 \<system.ServiceModel>  
\<diagnostic>  
\<endToEndTracing>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`activityTracing`|Logická hodnota určující, zda je povoleno trasování činnosti.|  
|`messageFlowTracing`|Logická hodnota určující, zda je povoleno sledování toku zprávy.|  
|`propagateActivity`|Logická hodnota, která určuje, zda je atribut propagate nastaven na hodnotu true.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [Komplexní trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
