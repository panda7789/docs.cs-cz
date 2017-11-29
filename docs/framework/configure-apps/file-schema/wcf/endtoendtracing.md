---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1bcd7405c5e3ebf2d1c156ff3bca9f473df9fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.  
  
 \<systém. ServiceModel >  
\<diagnostické >  
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
|`activityTracing`|Logická hodnota, která určuje, jestli je povolené trasování aktivity.|  
|`messageFlowTracing`|Logická hodnota, která určuje, jestli je povolené trasování v tok zpráv.|  
|`propagateActivity`|Logická hodnota, která určuje, zda je atribut propagate nastavena na hodnotu true.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Diagnostika >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Definuje nastavení WCF pro modul runtime kontroly a řízení pro správce.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [Konec Konec trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
