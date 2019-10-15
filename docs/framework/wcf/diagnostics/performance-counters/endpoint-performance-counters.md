---
title: Čítače výkonu koncového bodu
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 1b0f7462fea8843bcb0a0938a8034f405f30a6fb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320505"
---
# <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu
Čítače výkonu koncového bodu zachytí data, která odhalí, jak koncový bod přijímá zprávy. Lze je najít v objektu výkonu `ServiceModelEndpoint 4.0.0.0` při zobrazení pomocí nástroje sledování výkonu. Instance jsou pojmenovány pomocí tohoto vzoru:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 Data jsou podobná těm, která jsou shromažďována pro jednotlivé operace, ale jsou agregována pouze v rámci koncového bodu.  
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](index.md)
