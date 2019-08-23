---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919001"
---
# <a name="endtoendtracing"></a>\<endToEndTracing >
Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.  
  
 \<system.ServiceModel>  
\<> diagnostiky  
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
|`activityTracing`|Logická hodnota, která určuje, zda je povoleno trasování aktivit.|  
|`messageFlowTracing`|Logická hodnota, která určuje, zda je povoleno sledování toku zprávy.|  
|`propagateActivity`|Logická hodnota určující, zda je atribut rozšíření nastaven na hodnotu true.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [Komplexní trasování](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
