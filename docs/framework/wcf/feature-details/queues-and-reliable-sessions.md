---
title: Fronty a spolehlivé relace
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: af45fd86f673d0cc296f6593d9d5709d3e2b616e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596744"
---
# <a name="queues-and-reliable-sessions"></a>Fronty a spolehlivé relace
Fronty a spolehlivé relace jsou funkce Windows Communication Foundation (WCF), které implementují spolehlivé zasílání zpráv. Témata obsažená v této části popisují funkce spolehlivého zasílání zpráv WCF.  
  
 Spolehlivé zasílání zpráv je způsob, jakým spolehlivý zdroj zasílání zpráv (nazývaný zdroj) přenáší zprávy spolehlivě do cíle spolehlivého zasílání zpráv (označovaného jako cíl).  
  
 Spolehlivé zasílání zpráv má následující klíčové aspekty:  
  
- Převede záruky pro zprávy odesílané ze zdroje do cíle bez ohledu na selhání přenosu zprávy nebo selhání přenosu.  
  
- Oddělení zdroje a cíle od sebe navzájem, což poskytuje nezávislou chybu a obnovení zdroje a cíle a také spolehlivý přenos a doručování zpráv i v případě, že zdroj nebo cíl nejsou k dispozici.  
  
 Spolehlivé zasílání zpráv často přináší náklady na vysokou latenci. Latence je čas potřebný ke zprávě k dosažení cíle ze zdroje. Služba WCF proto nabízí následující typy spolehlivého zasílání zpráv:  
  
- [Spolehlivé relace](reliable-sessions.md), které nabízejí spolehlivý přenos bez nákladů na vysokou latenci  
  
- [Fronty v rámci WCF](queues-in-wcf.md), které nabízí spolehlivé přenosy i oddělení mezi zdrojem a cílem.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace poskytují ucelený spolehlivý přenos zpráv mezi zdrojem a cílem pomocí protokolu WS-ReliableMessaging bez ohledu na počet nebo typ dodavatelů, které oddělují koncové body zasílání zpráv (zdrojové a cílové). Patří sem všichni zprostředkovatelé přenosu, kteří nepoužívají protokol SOAP (například proxy servery HTTP) nebo zprostředkovatelé, kteří používají protokol SOAP (například směrovače nebo mosty založené na protokolu SOAP), které jsou požadovány pro zprávy, které mají tok mezi koncovými body. Spolehlivé relace používají okno přenosu v paměti k maskování selhání na úrovni zpráv SOAP a opětovnému navázání připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé přenosy zpráv s nízkou latencí. Poskytují zprávy protokolu SOAP prostřednictvím jakýchkoli proxy serverů nebo zprostředkovatelů, které odpovídají tomu, co protokol TCP poskytuje pro pakety přes přemostění IP adres. Další informace o spolehlivých relacích najdete v tématu [Reliable Sessions](reliable-sessions.md).  
  
## <a name="queues"></a>Fronty  
 Fronty v rámci WCF poskytují spolehlivé přenosy zpráv a oddělení mezi zdroji a cíli za cenu vysoké latence. Komunikace ve frontě WCF je postavená na službě Řízení front zpráv (označuje se také jako MSMQ).  
  
 Služba MSMQ je dodávána jako možnost se systémem Windows, který je spuštěn jako služba NT. Zachycuje zprávy pro přenos ve frontě přenosu za zdroj a doručuje je do cílové fronty. Cílová fronta přijímá zprávy jménem cíle pro pozdější doručení vždy, když jsou požadavky na zprávy určeny. Správci fronty MSMQ implementují spolehlivý protokol pro přenos zpráv, aby se zprávy během přenosu neztratily. Protokol může být nativní nebo založený na protokolu SOAP, jako je protokol SRMP (SOAP Reliable Messaging Protocol).  
  
 Oddělení, které je spojeno s přenosem spolehlivých zpráv mezi frontami, umožňuje aplikacím, které jsou volně propojeny a spolehlivě komunikovat. Na rozdíl od spolehlivých relací nemusí být zdroj a cíl spuštěn ve stejnou dobu. Tím se implicitně umožní scénáře, ve kterých jsou fronty v podstatě použité jako mechanismus Vyrovnávání zatížení, když dojde k neshodě mezi sazbou výroby zpráv a sazbou spotřeby zpráv podle cíle. Další informace o frontách najdete v tématu [fronty ve službě WCF](queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také

- [Fronty ve WCF](queues-in-wcf.md)
- [Fronty ve WCF](queuing-in-wcf.md)
- [Spolehlivé relace](reliable-sessions.md)
- [Spolehlivé relace – přehled](reliable-sessions-overview.md)
