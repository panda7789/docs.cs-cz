---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 18a9e6336b70341f5da9c7b73cbd3f9bd3f958c7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044276"
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby. Lze je najít v `ServiceModelService 4.0.0.0` objektu výkonu při zobrazení pomocí nástroje Performance Monitor (Perfmon. exe). Instance jsou pojmenovány pomocí následujícího vzoru:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
