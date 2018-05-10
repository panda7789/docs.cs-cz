---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 8354cff600f8c16a5ab9b4f6efd3c0b93a46276c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu
Čítače výkonu koncového bodu zachytit data, která zjistí, jak koncový bod přijímá zprávy. Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Instance jsou pojmenované pomocí tohoto vzoru:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data je podobná shromážděné pro jednotlivé operace, ale je pouze agregován přes koncový bod.  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku, WCF část název instance nahradí hodnotu hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
