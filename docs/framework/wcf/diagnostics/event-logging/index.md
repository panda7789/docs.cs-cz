---
title: "Protokolování událostí ve WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4028772caef8e5c0301ab3a6a0bde2f180d821ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="event-logging-in-wcf"></a>Protokolování událostí ve WCF
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]trasuje interní události v protokolu událostí systému Windows.  
  
## <a name="viewing-event-logs"></a>Zobrazení protokolů událostí  
 Ve výchozím nastavení je automaticky povoleno protokolování událostí a neexistuje žádný mechanismus ji zakázat. Události zapsané podle [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] lze zobrazit pomocí prohlížeče událostí. Chcete-li spustit tento nástroj, klikněte na tlačítko **spustit**, klikněte na tlačítko **ovládací panely**, dvakrát klikněte na **nástroje pro správu**a potom dvakrát klikněte na **Prohlížeč událostí**.  
  
### <a name="application-event-log"></a>Protokol událostí aplikace  
 **Protokolu událostí aplikace** obsahuje většinu událostí generovaných [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Položky budou indikovat, že určité funkce se nepodařilo spustit pro aplikaci. Příklady:  
  
-   Protokolování zpráv nebo trasování: [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , zapíše se událost do protokolu událostí při trasování a protokolování zpráv selže. Ne každý selhání trasování však aktivuje událost. Abyste zabránili v protokolu událostí se zcela naplněna trasování chyb, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] implementuje období přerušení spojení 10 minut pro takové události. To znamená, že pokud [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] selhání trasování zapíše do protokolu událostí, nebude proto znovu provádět minimálně 10 minut.  
  
-   Sdílené naslouchací proces: Službu WCF TCP Port Sharing protokoluje nějakou událost, když se nepodaří spustit.  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: Protokoluje události, když se službu nepodaří spustit.  
  
-   Kritické události a chyby, jako je například selhání spuštění nebo dojde k chybě  
  
-   Protokolování zpráv zapnuté: protokoluje události při protokolování zpráv zapnuté. Toto je upozornění správce v záhlaví zprávy a obsah mohou být zaznamenány citlivé informace specifické pro aplikaci.  
  
-   Událost je protokolována při `enableLoggingKnownPII` atribut `machineSettings` element `machine.config` soubor. Tento atribut určuje, jestli všechny aplikace spuštěné na počítači je povolené do protokolu známé identifikovatelné osobní údaje (PII).  
  
-   Pokud `logKnownPii` atribut buď `app.config` nebo `web.config` soubor pro `true` pro konkrétní aplikaci chcete zapnout protokolování PII, ale `enableLoggingKnownPII` atribut `machineSettings` element `machine.config` soubor k `false`, se zaprotokoluje událost. Kromě toho, pokud obě `logKnownPii` a `enableLoggingKnownPII` jsou nastaveny na `true`, a je zaznamenána událost. Další informace o konfiguraci těchto nastavení najdete v části zabezpečení [konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tématu.  
  
### <a name="security-event-log"></a>Protokol událostí zabezpečení  
 **Protokolu událostí zabezpečení** obsahuje události auditu zabezpečení, které jsou zaznamenány službou WCF.  
  
### <a name="system-event-log"></a>Protokol událostí systému  
 WCF neprotokoluje nic v **protokolu událostí systému**.  
  
### <a name="event-log-entries"></a>Položky protokolu událostí  
 **Zdroj** události je název sestavení, které generuje položku protokolu.  
  
 Typ položka do protokolu událostí se používá k označení závažnost událost. Každá událost musí být jeden typ, který aplikace určuje, kdy oznámí události. V prohlížeči událostí tohoto typu používá k určení která ikona v zobrazení seznamu protokolu. Různé události typu položka do protokolu událostí, naleznete v části <xref:System.Diagnostics.EventLogEntryType>.  
  
 Když kliknete na tlačítko "Další informace o" při zobrazení události v prohlížeči událostí, v prohlížeči událostí může odeslat informace přes Internet. Další informace najdete v nápovědě k prohlížeči událostí.  
  
## <a name="see-also"></a>Viz také  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Události – obecné referenční informace](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
