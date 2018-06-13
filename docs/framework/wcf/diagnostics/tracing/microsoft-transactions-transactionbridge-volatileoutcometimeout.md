---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475628"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Čekání na odpověď na zprávu o výsledek od volatile účastníka vypršel časový limit služby protokolu WS-AT. Výsledek transakce může mít nejistých účastník vrátí.  
  
## <a name="description"></a>Popis  
 Sledovat, když se rozhodla potvrzení nebo přerušení Volatile účastník, ale neodpověděl na žádost o potvrzení nebo vrácení změn v rámci dané množství času.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zajistěte, aby všichni účastníci Volatile schopné reagovat v rámci daného časového intervalu. Výchozí období je 180 sekund.  Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro služby WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
