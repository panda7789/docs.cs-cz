---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 71eff5c656a4782056ac518f105f73bc549da336
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb. Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Instance jsou pojmenované pomocí následujícího vzorce:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
