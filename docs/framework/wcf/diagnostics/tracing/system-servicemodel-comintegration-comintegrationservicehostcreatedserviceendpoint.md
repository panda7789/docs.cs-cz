---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674781"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Zprávu nelze přesunout ani odstranit.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že při pokusu o přesunutí, odstranění nebo odmítnutí zprávy služby MSMQ došlo k chybě.  
  
 Zprávy služby MSMQ jsou používány službou WCF (Při použití s netmsmqbinding nebo MsmqIntegrationBinding). Toto trasování souvisí s `ReceiveErrorHandling` vybranou hodnotu vlastnosti na NetMsmqBinding nebo MsmqIntegrationBinding.  
  
 Toto trasování nesvědčí o celkové selhání systému. Však označuje, že vybrané poškozená zpráva dispozice se nezdařilo pro zprávu. Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
