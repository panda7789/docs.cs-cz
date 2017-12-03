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
ms.openlocfilehash: d3919e48925eeb0d197c23da582836dec5bf6438
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Rychlost přijímání příchozích zpráv je příliš vysoká.  
  
## <a name="description"></a>Popis  
 Trasování nastane při pokusu o zpracování příchozí zprávy. Zprávu nelze předat konkrétní sousedním, protože byla překročena kvóta pro tento sousedním nastavit. K tomu dochází, když dojde k vymazání nevyřízené položky zpráv čekající na vyřízení pro tento sousedním selhání reagovat sousedním.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Omezit rychlost odesílání zpráv v mřížce.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
