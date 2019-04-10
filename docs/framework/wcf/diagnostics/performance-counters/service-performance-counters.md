---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: dc31e05f82f232095f6560c8fdd9bf75c040e2ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210409"
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měření chování služby jako celek a slouží k diagnostice výkonu celou službu. Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Tyto instance jsou pojmenovány pomocí následujícího vzorce:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Platí omezení na délku název instance čítače výkonu. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotu hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
