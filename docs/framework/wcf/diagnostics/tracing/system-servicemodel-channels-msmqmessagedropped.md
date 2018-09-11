---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 07bef8b391a03f2c011e1d1a7c7fb4fad908e022
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276581"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ vyřadit zprávu.  
  
## <a name="description"></a>Popis  
 Trasování označuje, že zprávy MSMQ byla vynechána. Zprávy služby MSMQ můžete vyřadit, když Windows Communication Foundation (WCF) (používá se NetMsmqBinding nebo vazbu MsmqIntegrationBinding) se nepodařilo zpracovat. Tyto zprávy jsou označovány jako počet nezpracovatelných zpráv.  
  
 Nezpracovatelná zpráva se zahodí, kdy `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Drop`. Vyřazené zprávy je odebrána z fronty a není už zotavit.  
  
 Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546)
