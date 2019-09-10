---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 4ce0efbeb0a1d6f2409bb976102b8ec8821d5cdc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848993"
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby. Lze je najít v `ServiceModelService 4.0.0.0` objektu výkonu při zobrazení pomocí nástroje Performance Monitor (Perfmon. exe). Instance jsou pojmenovány pomocí následujícího vzoru:  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
