---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bbad8d743ff64aea923e7fbf62871e495253aea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nepodařilo se přijmout zprávu přes kanál protokolu HTTP.  
  
## <a name="description"></a>Popis  
 Trasování může být poslán jako upozornění nebo chybu. V obou případech jsou vydávány trasování, pokud pro příchozí požadavek HTTP se nenašel kompatibilní naslouchací proces a požadavek HTTP se zahodí. Toto může nastat, protože příkaz HTTP žádosti nebyla rozpoznána ve všech naslouchací proces protokolu HTTP, nebo protože byla žádné naslouchací proces naslouchání na adrese žádosti je určený pro. Trasování jsou vydávány jako upozornění v případě, že vlastním hostováním a jako chybu, pokud služba je hostovaná ve službě IIS.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
