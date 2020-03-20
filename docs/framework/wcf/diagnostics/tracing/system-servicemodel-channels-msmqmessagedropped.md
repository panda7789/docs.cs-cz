---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674802"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
Služba MSMQ zprávu vynechala.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že zpráva služby MSMQ byla vynechána. Zprávy služby MSMQ mohou být zrušeny, pokud je nelze zpracovat při službě WCF (wcf) systému Windows Communication Foundation (používané s vazací NetMsmqBinding nebo MsmqIntegrationBinding). Tyto zprávy jsou označovány jako poškozená zprávy.  
  
 Poškozená zpráva je `ReceiveErrorHandling` vynechána, pokud je vlastnost na NetMsmqBinding `Drop`nebo MsmqIntegrationBinding nastavena na . Vynechaná zpráva je odebrána z fronty a již není obnovitelná.  
  
 Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zpracování poškozená zpráva](../../feature-details/poison-message-handling.md)
