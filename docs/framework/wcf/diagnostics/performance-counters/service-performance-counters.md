---
title: Čítače výkonu služby
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 929ddcb2f271b7488270ea39e7a3a0037158c855
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320031"
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby. Lze je najít v objektu výkonu @no__t 0 při zobrazení pomocí nástroje Performance Monitor (Perfmon. exe). Instance jsou pojmenovány pomocí následujícího vzoru:  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](index.md)
