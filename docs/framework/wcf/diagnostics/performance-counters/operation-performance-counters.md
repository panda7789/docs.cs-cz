---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916198"
---
# <a name="operation-performance-counters"></a>Čítače provozního výkonu
Čítače provozního výkonu se nacházejí v rámci `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Každá operace má jednotlivé instance. To znamená že pokud má daný kontrakt 10 operací, jsou 10 instancí čítače operace spojené s touto smlouvou. Instance objektů jsou pojmenovány pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Tento čítač umožňuje měřit využití volání a jak dobře fungují operace.  
  
> [!CAUTION]
>  Platí omezení na délku název instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
