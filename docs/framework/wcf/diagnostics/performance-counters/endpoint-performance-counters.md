---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 2352bc82998c8e87e72f331104446bac4fcb9fda
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040582"
---
# <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu
Čítače výkonu koncového bodu zachytí data, která odhalí, jak koncový bod přijímá zprávy. Lze je najít v `ServiceModelEndpoint 4.0.0.0` objektu výkonu při zobrazení pomocí nástroje sledování výkonu. Instance jsou pojmenovány pomocí tohoto vzoru:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data jsou podobná těm, která jsou shromažďována pro jednotlivé operace, ale jsou agregována pouze v rámci koncového bodu.  
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
