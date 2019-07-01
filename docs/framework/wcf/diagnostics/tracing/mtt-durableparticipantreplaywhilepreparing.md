---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486773"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Služba protokolu WS-AT obdržela odpověď od trvalého účastníka, který neodpověděl na připravit. V důsledku toho byla transakce přerušena.  
  
## <a name="description"></a>Popis  
 Trasovaná, pokud se stále připravuje trvalého účastníka bylo přijato odpověď. Toto je neplatná zpráva pro tento stav a transakce bude přerušen.  
  
## <a name="troubleshooting"></a>Poradce při potížích

Tato chyba může znamenat, že trvalého účastníka (včetně podřízených TransactionManagers) se zotavuje ze selhání; Nicméně je jistí, jaké výsledek transakce a požadavky její stav.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
