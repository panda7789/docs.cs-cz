---
title: Protokolování událostí ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 0c74b93be026007a5593372c938cf73e08fafb15
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797807"
---
# <a name="event-logging-in-wcf"></a>Protokolování událostí ve WCF
Windows Communication Foundation (WCF) sleduje interní události v protokolu událostí systému Windows.  
  
## <a name="viewing-event-logs"></a>Zobrazení protokolů událostí  
 Protokolování událostí je ve výchozím nastavení povoleno automaticky a neexistuje žádný mechanismus k jeho zakázání. Události zaznamenané službou WCF lze zobrazit pomocí Prohlížeč událostí. Chcete-li spustit tento nástroj, klikněte na tlačítko **Start**, klikněte na příkaz **Ovládací panely**, dvakrát klikněte na panel **Nástroje pro správu**a potom dvakrát klikněte na položku **Prohlížeč událostí**.  
  
### <a name="application-event-log"></a>Protokol událostí aplikace  
 **Protokol událostí aplikace** obsahuje většinu událostí generovaných službou WCF. Většina položek značí, že se konkrétní funkce pro aplikaci nepovedlo spustit. Příklady:  
  
- Protokolování a trasování zpráv: Technologie WCF zapisuje událost do protokolu událostí, pokud se nezdařila trasování a protokolování zpráv. Ne každé selhání trasování ale vyvolá událost. Aby se zabránilo úplnému vyplňování protokolu událostí při selhání trasování, WCF pro takovou událost implementuje nedostupnosti období 10 minut. To znamená, že pokud WCF zapíše selhání trasování do protokolu událostí, nebude tak znovu po dobu nejméně 10 minut.  
  
- Sdílený naslouchací proces: Služba sdílení portů WCF TCP protokoluje událost, když se nepovede spustit.  
  
- Službu Protokoluje události, když se služba nespustí.  
  
- Kritické a chybové události, například chyby při spuštění nebo selhání  
  
- Protokolování zpráv je zapnuté: Protokoluje události, když je zapnuto protokolování zpráv. Je třeba informovat správce o tom, že se v záhlaví a subjektech zpráv můžou protokolovat informace specifické pro danou aplikaci.  
  
- Událost je protokolována při `enableLoggingKnownPII` nastavení atributu `machineSettings` v prvku `machine.config` souboru. Tento atribut určuje, jestli má kterákoli aplikace spuštěná v počítači oprávnění protokolovat známé identifikovatelné osobní údaje (PII).  
  
- `true` `enableLoggingKnownPII` `machine.config` `machineSettings` Pokud je atributvsouborunebonastavennaprokonkrétníaplikaciprozapínáníprotokolováníPII,aleatributvprvkusouborujenastaven`logKnownPii` `app.config` `web.config` do `false`je zaznamenána událost. Kromě toho, pokud `logKnownPii` jsou a `enableLoggingKnownPII` nastaveny na `true`a je zaznamenána událost. Další informace o těchto nastaveních konfigurace najdete v části zabezpečení v tématu [Konfigurace protokolování zpráv](../configuring-message-logging.md) .  
  
### <a name="security-event-log"></a>Protokol událostí zabezpečení  
 **Protokol událostí zabezpečení** obsahuje události auditu zabezpečení, které jsou protokolovány službou WCF.  
  
### <a name="system-event-log"></a>Protokol systémových událostí  
 WCF neprotokoluje cokoli v **protokolu systémových událostí**.  
  
### <a name="event-log-entries"></a>Položky protokolu událostí  
 **Zdrojem** události je název sestavení, které generuje položku protokolu.  
  
 Typ položky protokolu událostí se používá k označení závažnosti události. Každá událost musí být jednoho typu, který aplikace indikuje při hlášení události. Prohlížeč událostí používá tento typ k určení, která ikona se má zobrazit v zobrazení seznamu protokolu. Jiný typ události položky protokolu událostí naleznete v tématu <xref:System.Diagnostics.EventLogEntryType>.  
  
 Když při zobrazení události v Prohlížeč událostí kliknete na Další informace, Prohlížeč událostí může odesílat informace přes Internet. Další informace najdete v nápovědě k Prohlížeč událostí.  
  
## <a name="see-also"></a>Viz také:

- [Správa a diagnostika](../index.md)
- [Události – obecné referenční informace](events-general-reference.md)
