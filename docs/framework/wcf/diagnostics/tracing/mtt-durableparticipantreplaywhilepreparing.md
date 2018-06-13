---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476317"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Služba Protokol WS-AT přijala zprávu opětovného přehrání z trvalého účastníka, které neodpovídají na přípravu. V důsledku toho byla transakce přerušena.  
  
## <a name="description"></a>Popis  
 Trasovat, pokud bylo přijato formou opakovaného přehrávání zprávy trvalého účastníka stále připravuje. Tato zpráva neplatné pro tento stav je a transakce přerušena.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Tato chyba může indiate, že trvalého účastníka (včetně podřízených TransactionManagers) došlo k zotavení z chyby, ale je jistí výstup transakce a požádat o jeho stav.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
