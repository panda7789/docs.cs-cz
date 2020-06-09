---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579018"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Vypršel časový limit služby protokolu WS-AT při čekání na odpověď na zprávu o výsledku od nestálého účastníka. Výsledek transakce může být nejistý, pokud účastník vrátí.  
  
## <a name="description"></a>Popis  
 Sledováno v případě, že se nestálý účastník rozhodl zapsat nebo přerušit, ale neodpověděl na žádost o potvrzení nebo vrácení zpět během daného časového intervalu.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Zajistěte, aby každý stálý účastník mohl reagovat v daném časovém intervalu. Výchozí časové období je 180 sekund.  Pokud to nestačí, zvyšte `VolatileOutcomeDelay` zásady časovače pro WS-AT.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
