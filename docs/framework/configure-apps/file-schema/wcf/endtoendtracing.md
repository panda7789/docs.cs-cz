---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 78a69256a391e97ff1962eea923f09115c4ebadd
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150107"
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.  
  
 \<system.ServiceModel>  
\<diagnostiky >  
\<endToEndTracing >  
  
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
|[\<Diagnostika >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [Komplexní trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
