---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bdc68fd2b629c538c097dab4e1cf3f89b7f3a091
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810184"
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb. Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Instance jsou pojmenované pomocí následujícího vzorce:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku, WCF část název instance nahradí hodnotu hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
