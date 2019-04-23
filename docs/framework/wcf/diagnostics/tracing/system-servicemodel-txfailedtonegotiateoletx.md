---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097561"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Vyjednávání protokolu OleTransactions se nepodařilo dokončit pro zadaný koordinační kontext.  
  
## <a name="description"></a>Popis  
 Sledovat příchozí transakce s informacemi o OleTx nemůže použít připojené OleTx informace, a bude fall zpět a místo toho použít WS-AT.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Označuje potenciální problém s MSDTC RPC komunikaci mezi počítači. Pokud mnoho z těchto trasování v protokolu zobrazily, může dojít k závažný snížení výkonu.  Pokud OleTx není žádoucí, nastavte `OleTxUpgradeEnabled` na 0 v konfiguraci WS-AT registru.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
