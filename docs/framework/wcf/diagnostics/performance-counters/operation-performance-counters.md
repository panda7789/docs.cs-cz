---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 31b0f92ae3477bd3c1de8c348a60e5c64d7c53cc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855678"
---
# <a name="operation-performance-counters"></a>Čítače provozního výkonu
Čítače výkonu operace se při zobrazení pomocí `ServiceModelOperation 4.0.0.0` nástroje sledování výkonu (Perfmon. exe) nacházejí v objektu výkonu. Každá operace má jednotlivou instanci. To znamená, že pokud má daný kontrakt 10 operací, je k této smlouvě přidruženo 10 instancí čítače operací. Instance objektů jsou pojmenovány pomocí následujícího vzoru:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Tento čítač vám umožní změřit způsob, jakým se volání používá, a to, jak dobře probíhá operace.  
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
