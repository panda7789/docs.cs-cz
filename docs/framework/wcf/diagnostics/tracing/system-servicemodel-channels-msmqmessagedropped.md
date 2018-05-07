---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: ad05a2b8552cc09d45e950e2c3336d86be918963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ vyřadit zprávu.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že služby MSMQ zpráva byla vyřazena. Zprávy služby MSMQ můžete vyřadit, když Windows Communication Foundation (WCF) (používá se s – NetMsmqBinding nebo – MsmqIntegrationBinding) se nepodařilo zpracovat. Takové zprávy se označují jako poškozených zpráv.  
  
 Nezpracovatelná zpráva je vynechána, kdy `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Drop`. Vyřazené zprávy je odebrána z fronty a nadále již není použitelná pro obnovení.  
  
 V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546)
