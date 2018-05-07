---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: f79f5703c621951029f3e7f6a36a3d0ebeca58a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nepodařilo se přijmout zprávu přes kanál protokolu HTTP.  
  
## <a name="description"></a>Popis  
 Trasování může být poslán jako upozornění nebo chybu. V obou případech jsou vydávány trasování, pokud pro příchozí požadavek HTTP se nenašel kompatibilní naslouchací proces a požadavek HTTP se zahodí. Toto může nastat, protože příkaz HTTP žádosti nebyla rozpoznána ve všech naslouchací proces protokolu HTTP, nebo protože byla žádné naslouchací proces naslouchání na adrese žádosti je určený pro. Trasování jsou vydávány jako upozornění v případě, že vlastním hostováním a jako chybu, pokud služba je hostovaná ve službě IIS.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
