---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136baabc0760826aa9ba76dc19862c9c4b60e16e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Rychlost přijímání příchozích zpráv je příliš vysoká.  
  
## <a name="description"></a>Popis  
 Trasování nastane při pokusu o zpracování příchozí zprávy. Zprávu nelze předat konkrétní sousedním, protože byla překročena kvóta pro tento sousedním nastavit. K tomu dochází, když dojde k vymazání nevyřízené položky zpráv čekající na vyřízení pro tento sousedním selhání reagovat sousedním.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Omezit rychlost odesílání zpráv v mřížce.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
