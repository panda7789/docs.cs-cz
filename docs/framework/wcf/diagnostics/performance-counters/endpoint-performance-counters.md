---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 9aa741c4482e40a28a2744765114c21973547298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu
Čítače výkonu koncového bodu zachytit data, která zjistí, jak koncový bod přijímá zprávy. Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Instance jsou pojmenované pomocí tohoto vzoru:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data je podobná shromážděné pro jednotlivé operace, ale je pouze agregován přes koncový bod.  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
