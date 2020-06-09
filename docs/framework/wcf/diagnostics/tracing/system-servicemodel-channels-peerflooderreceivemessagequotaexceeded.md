---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 93afa0b495e20c02c58ac1fa75c31715eaa0e8dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596087"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Míra příchozího příjmu zpráv je příliš vysoká.  
  
## <a name="description"></a>Popis  
 K tomuto trasování dochází při pokusu o zpracování příchozích zpráv. Zpráva nemohla být předána do konkrétního souseda, protože byla překročena kvóta nastavená pro daný sousední uzel. K tomu dochází, když nereagující sousední uzel nevymaže nevyřízené položky zpráv, které čekají na vyřízení pro daný sousední uzel.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Snižte rychlost odesílání zpráv v rámci sítě.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
