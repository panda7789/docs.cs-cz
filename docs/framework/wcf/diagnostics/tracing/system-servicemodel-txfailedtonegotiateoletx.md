---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 7f376244343a75c16d5d2355642d626f666e42bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33483828"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Vyjednávání protokolu OleTransactions se nepodařilo dokončit pro koordinaci zadaný kontext.  
  
## <a name="description"></a>Popis  
 Sledovat, když příchozí transakci s informacemi o OleTx nemůže použít připojené OleTx informace a bude patří zpět a místo toho použít WS-AT.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Označuje potenciální problém s komunikací služby MSDTC RPC mezi počítači. Pokud mnoho z těchto trasování se zobrazí v protokolu, může způsobit závažný snížení výkonu.  V případě potřeby OleTx není nastavena `OleTxUpgradeEnabled` na 0 v konfiguraci registrů WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
