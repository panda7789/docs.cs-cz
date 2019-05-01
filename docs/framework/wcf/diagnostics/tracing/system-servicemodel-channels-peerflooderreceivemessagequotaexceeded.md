---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950641"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Rychlost přijímání příchozích zpráv je příliš vysoká.  
  
## <a name="description"></a>Popis  
 Trasování nastane při pokusu o zpracování příchozích zpráv. Zprávu nelze předat konkrétní sousední, protože se překročila kvótu nastavenou pro tuto sousední. Příčinou je selhání reagovat sousední vymazání nevyřízených položek nevyřízené zprávy pro tuto sousedem.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Snížit rychlost odesílání zpráv v rámci síť.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
