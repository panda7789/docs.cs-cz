---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593747"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Zprávu nelze přesunout nebo odstranit.  
  
## <a name="description"></a>Popis  
 Trasování indikuje, že došlo k chybě při pokusu o přesunutí, odstranění nebo odmítnutí zprávy služby MSMQ.  
  
 Zprávy služby MSMQ jsou zaměstnány pomocí Windows Communication Foundation (WCF) (při použití s rozhraním NetMsmqBinding nebo MsmqIntegrationBinding). Toto trasování se vztahuje k zvolené hodnotě `ReceiveErrorHandling` vlastnosti v NetMsmqBinding nebo MsmqIntegrationBinding.  
  
 Toto trasování není indikativní pro celkové selhání systému. Označuje však, že u zprávy se nezdařilo dispozice zvolené nepoškozené zprávy. Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
