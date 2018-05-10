---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 46b7d5ff071ebf1e3f790a9b56906d9908028ae9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="operation-performance-counters"></a>Čítače provozního výkonu
Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Každá operace má jednotlivé instance. To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy. Instance objektů jsou pojmenované pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku, WCF část název instance nahradí hodnotu hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
