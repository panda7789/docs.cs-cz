---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601898"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
Služba MSMQ vynechala zprávu.  
  
## <a name="description"></a>Popis  
 Trasování indikuje, že zpráva MSMQ byla vyřazena. Zprávy služby MSMQ je možné vyřadit, pokud Windows Communication Foundation (WCF) (používá se s NetMsmqBinding nebo MsmqIntegrationBinding) není schopen je zpracovat. Tyto zprávy se označují jako nepoškozené zprávy.  
  
 Pokud `ReceiveErrorHandling` je vlastnost na NetMsmqBinding nebo MsmqIntegrationBinding nastavena na hodnotu, je zahozena nezpracovatelná zpráva `Drop` . Vyřazená zpráva se odebere z fronty a už není obnovitelná.  
  
 Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
- [Zpracování nezpracovatelných zpráv](../../feature-details/poison-message-handling.md)
