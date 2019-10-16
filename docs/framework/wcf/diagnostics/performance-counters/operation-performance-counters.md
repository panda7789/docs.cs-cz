---
title: Čítače provozního výkonu
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 59c75dacb2a01f1b85d67d5cc1651dbc55b6aa8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320167"
---
# <a name="operation-performance-counters"></a>Čítače provozního výkonu
Čítače výkonu operace se při zobrazení pomocí nástroje sledování výkonu (Perfmon. exe) nacházejí v objektu výkonu `ServiceModelOperation 4.0.0.0`. Každá operace má jednotlivou instanci. To znamená, že pokud má daný kontrakt 10 operací, je k této smlouvě přidruženo 10 instancí čítače operací. Instance objektů jsou pojmenovány pomocí následujícího vzoru:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Tento čítač vám umožní změřit způsob, jakým se volání používá, a to, jak dobře probíhá operace.  
  
> [!CAUTION]
> Délka názvu instance čítače výkonu je omezena. Pokud název instance čítače Windows Communication Foundation (WCF) přesahuje maximální délku, WCF nahradí část názvu instance hodnotou hash.  
  
## <a name="see-also"></a>Viz také:

- [Čítače výkonu](index.md)
