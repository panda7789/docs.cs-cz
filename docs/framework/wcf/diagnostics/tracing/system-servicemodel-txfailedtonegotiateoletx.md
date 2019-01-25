---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 6aecc8f808d42c0096f6caef0574c72db6c53079
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528664"
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
