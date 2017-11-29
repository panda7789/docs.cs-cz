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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a258b315b5a8537de87a603b5d1ec0c18387ddbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nepodařilo se přijmout zprávu přes kanál protokolu HTTP.  
  
## <a name="description"></a>Popis  
 Trasování může být poslán jako upozornění nebo chybu. V obou případech jsou vydávány trasování, pokud pro příchozí požadavek HTTP se nenašel kompatibilní naslouchací proces a požadavek HTTP se zahodí. Toto může nastat, protože příkaz HTTP žádosti nebyla rozpoznána ve všech naslouchací proces protokolu HTTP, nebo protože byla žádné naslouchací proces naslouchání na adrese žádosti je určený pro. Trasování jsou vydávány jako upozornění v případě, že vlastním hostováním a jako chybu, pokud služba je hostovaná ve službě IIS.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
