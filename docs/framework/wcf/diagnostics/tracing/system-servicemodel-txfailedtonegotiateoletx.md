---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601410"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Nepodařilo se dokončit vyjednávání protokolu OleTransactions pro zadaný koordinační kontext.  
  
## <a name="description"></a>Popis  
 Sledováno, když příchozí transakce s OleTx informacemi nedokáže použít připojené OleTx informace, a místo toho se vrátí k použití WS-AT.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Označuje potenciální problém s komunikací služby MSDTC RPC mezi počítači. Pokud se mnoho z těchto trasování objeví v protokolu, může to vést k drastickému poklesu výkonu.  Pokud OleTx není žádoucí, nastavte `OleTxUpgradeEnabled` na hodnotu 0 v konfiguraci registru WS-AT.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
