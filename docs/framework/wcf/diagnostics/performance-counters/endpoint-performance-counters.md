---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: f07e318e39a68e689ec484b09fa743623cfb51d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158382"
---
# <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu
Čítače výkonu koncového bodu zaznamenávat data, která se ukáže, jak koncový bod přijímá zprávy. Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí nástroje Sledování výkonu. Tyto instance jsou pojmenovány použití tohoto modelu:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data se podobá shromážděné pro jednotlivé operace, ale pouze se agreguje přes koncový bod.  
  
> [!CAUTION]
>  Platí omezení na délku název instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
