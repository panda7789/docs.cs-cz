---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 22992b4dfad4b4867adda0fcbbd8ecc5eb67d87e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160143"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Služba protokolu WS-AT vypršel časový limit čekání na odpověď na zprávu z nestálého účastníka. Výsledek transakce může mít nejistým výsledkem vrátí účastníka.  
  
## <a name="description"></a>Popis  
 Trasovaná při nestálého účastníka se rozhodl potvrzení nebo přerušení, ale neodpověděl na požadavek na zápis nebo vrácení zpět v daném čase.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Ujistěte se, že se všichni účastníci Volatile neodpoví v daném čase. Výchozí časové období je 180 sekund.  Pokud to není dostatečné, zvýšit `VolatileOutcomeDelay` časovače zásady pro WS-AT.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
