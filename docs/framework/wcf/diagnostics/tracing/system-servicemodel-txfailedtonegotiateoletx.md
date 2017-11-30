---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Vyjednávání protokolu OleTransactions se nepodařilo dokončit pro koordinaci zadaný kontext.  
  
## <a name="description"></a>Popis  
 Sledovat, když příchozí transakci s informacemi o OleTx nemůže použít připojené OleTx informace a bude patří zpět a místo toho použít WS-AT.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Označuje potenciální problém s komunikací služby MSDTC RPC mezi počítači. Pokud mnoho z těchto trasování se zobrazí v protokolu, může způsobit závažný snížení výkonu.  V případě potřeby OleTx není nastavena `OleTxUpgradeEnabled` na 0 v konfiguraci registrů WS-AT.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
