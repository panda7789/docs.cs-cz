---
title: Protokolování událostí ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: adff5bf2fad9f78fccbb606a5bd27f2f1dc32647
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638754"
---
# <a name="event-logging-in-wcf"></a>Protokolování událostí ve WCF
Windows Communication Foundation (WCF) sleduje interní události v protokolu událostí Windows.  
  
## <a name="viewing-event-logs"></a>Zobrazení protokolů událostí  
 Ve výchozím nastavení je automaticky povoleno protokolování událostí a neexistuje žádný mechanismus pro jeho zakázání. Události zapsané podle WCF lze zobrazit pomocí prohlížeče událostí. Chcete-li spustit tento nástroj, klikněte na tlačítko **Start**, klikněte na tlačítko **ovládací panely**, dvakrát klikněte na **nástroje pro správu**a potom dvakrát klikněte na **Prohlížeč událostí**.  
  
### <a name="application-event-log"></a>Protokol událostí aplikace  
 **Protokolu událostí aplikace** obsahuje většinu události generované modulem WCF. Většina položek znamenat, že konkrétní funkce se nepodařilo spustit pro aplikaci. Příklady:  
  
- Protokolování a trasování zpráv: Selhání trasování a protokolování zpráv WCF zapisuje události do protokolu událostí. Nicméně ne každá chyba trasování aktivuje událost. Abyste zabránili se zcela naplněna trasování chyb protokolu událostí, implementuje WCF období nedostupnosti 10minutový pro takovou událost. To znamená, že pokud WCF selhání trasování zapíše do protokolu událostí, nebude to znovu po dobu minimálně 10 minut.  
  
- Sdílené naslouchací proces: Službu WCF TCP Port Sharing protokoluje událost v případě, že ji nebude možné spustit.  
  
- [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: Protokoly událostí, pokud službu nepodaří spustit.  
  
- Kritické události a chyby, jako je například selhání spuštění nebo selhání  
  
- Zapnout protokolování zpráv: Protokoluje události při protokolování zpráv je zapnutá. Cílem je upozornit správce v záhlaví zpráv a úřadů, které mohou být zaznamenány citlivé informace specifické pro aplikaci.  
  
- Zaprotokoluje událost, která při `enableLoggingKnownPII` atribut `machineSettings` elementu `machine.config` soubor. Tento atribut určuje, pokud žádné aplikaci spuštěné na počítači oprávnění k přihlášení známého identifikovatelné osobní údaje (PII).  
  
- Pokud `logKnownPii` atribut buď `app.config` nebo `web.config` soubor je nastavený na `true` pro danou aplikaci k zapnutí protokolování identifikovatelné osobní údaje, ale `enableLoggingKnownPII` atribut `machineSettings` elementu `machine.config` soubor k `false`, zaprotokoluje událost, která. Kromě toho, pokud obě `logKnownPii` a `enableLoggingKnownPII` jsou nastaveny na `true`, a je zaznamenána událost. Další informace o těchto nastaveních konfigurace najdete v článku sekci zabezpečení [konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tématu.  
  
### <a name="security-event-log"></a>Protokol událostí zabezpečení  
 **Protokolu událostí zabezpečení** obsahuje události auditu zabezpečení, které jsou zapsané podle WCF.  
  
### <a name="system-event-log"></a>Protokol událostí systému  
 WCF není přihlášení něco **protokolu událostí systému**.  
  
### <a name="event-log-entries"></a>Položky protokolu událostí  
 **Zdroj** události je název sestavení, který generuje položku protokolu.  
  
 Typ položky protokolu událostí se používá k označení závažnosti události. Každá událost musí být jeden typ, který aplikace určuje, kdy hlásí události. V prohlížeči událostí na základě tohoto typu určit, jaká ikona bude zobrazena v zobrazení seznamu protokolu. Typ různé události položka protokolu událostí, naleznete v tématu <xref:System.Diagnostics.EventLogEntryType>.  
  
 Po kliknutí na "Další informace" při zobrazení událostí v prohlížeči událostí, Prohlížeč událostí může posílání informací přes Internet. Další informace naleznete v nápovědě k prohlížeči událostí.  
  
## <a name="see-also"></a>Viz také:

- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Události – obecné referenční informace](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
