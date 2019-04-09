---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: f5d74d73cc43b500d3920ca03905f4eb7543619a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075532"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Služba protokolu WS-AT obdržela odpověď od trvalého účastníka, který neodpověděl na připravit. V důsledku toho byla transakce přerušena.  
  
## <a name="description"></a>Popis  
 Trasovaná, pokud se stále připravuje trvalého účastníka bylo přijato odpověď. Toto je neplatná zpráva pro tento stav a transakce bude přerušen.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Tato chyba může indiate, trvalého účastníka (včetně podřízených TransactionManagers) se zotavil po selhání, i když je jistí, jaké výsledek transakce a požádat o jeho stav.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
