---
title: Spolehlivé služby
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: 78f492c7a7c5abd7b72c40fc5695b8d56003f822
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319891"
---
# <a name="reliable-services"></a>Spolehlivé služby
Fronty a spolehlivé relace jsou funkce Windows Communication Foundation (WCF), které implementují spolehlivé zasílání zpráv. Toto téma vysvětluje funkce spolehlivého zasílání zpráv ve službě WCF.  
  
 *Spolehlivé zasílání* zpráv je způsob, jakým spolehlivý zdroj zasílání zpráv (nazývaný *zdroj*) přenáší zprávy spolehlivě do cíle spolehlivého zasílání zpráv (označovaného jako *cíl*).  
  
 Spolehlivé zasílání zpráv provádí následující funkce:  
  
- Přenáší záruky pro zprávy odesílané ze zdroje do cíle bez ohledu na přenos zpráv nebo selhání přenosu.  
  
- Odděluje zdroj a cíl od sebe navzájem. To umožňuje nezávislé selhání a obnovení zdroje a cíle a také spolehlivého přenosu a doručování zpráv, i když není k dispozici zdroj nebo cíl.  
  
 Spolehlivé zasílání zpráv často přináší náklady na vysokou latenci. *Latence* je čas potřebný ke zprávě k dosažení cíle ze zdroje. Služba WCF proto nabízí následující typy spolehlivého zasílání zpráv:  
  
- [Spolehlivé relace](./feature-details/reliable-sessions.md), které nabízí spolehlivý přenos bez nákladů na vysokou latenci.  
  
- [Fronty ve službě WCF](./feature-details/queues-in-wcf.md), které nabízí spolehlivé přenosy i oddělení mezi zdrojem a cílem.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace poskytují ucelený spolehlivý přenos zpráv mezi zdrojem a cílem pomocí protokolu zasílání zpráv WS-Reliable bez ohledu na počet nebo typ zprostředkovatelů, které oddělují koncové body zasílání zpráv (zdrojové a cílové). Patří sem všichni zprostředkovatelé přenosu, kteří nepoužívají protokol SOAP (například proxy servery HTTP) nebo zprostředkovatelé, kteří používají protokol SOAP (například směrovače nebo mosty založené na protokolu SOAP), které jsou požadovány pro zprávy, které mají tok mezi koncovými body. Spolehlivé relace používají okno přenosu v paměti k maskování selhání na úrovni zpráv SOAP a opětovnému navázání připojení v případě selhání přenosu.  
  
 Spolehlivé relace poskytují spolehlivé přenosy zpráv s nízkou latencí. Poskytují zprávy protokolu SOAP prostřednictvím jakýchkoli proxy serverů nebo zprostředkovatelů, které odpovídají tomu, co protokol TCP poskytuje pro pakety přes přemostění IP adres. Další informace o spolehlivých relacích najdete v tématu [Reliable Sessions](./feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>vytvořil  
 Fronty v rámci WCF poskytují spolehlivé přenosy zpráv a oddělení mezi zdroji a cíli za cenu vysoké latence. Komunikace ve frontě WCF je postavená nad službou Řízení front zpráv (MSMQ).  
  
 Služba MSMQ je dodávána jako volitelná součást s Windows. Služba MSMQ je spuštěna jako služba systému Windows. Zachycuje zprávy pro přenos ve frontě přenosu za zdroj a doručuje je do cílové fronty. Cílová fronta přijímá zprávy jménem cíle pro pozdější doručení pokaždé, když cílový požadavek vyžádá. Správci služby MSMQ implementují spolehlivý protokol pro přenos zpráv, aby se zprávy během přenosu neztratily. Protokol může být nativní nebo protokol založený na protokolu SOAP nazvaný protokol SRMP (SOAP Reliable Messaging Protocol).  
  
 Oddělení, které je spojeno s přenosem spolehlivých zpráv mezi frontami, umožňuje aplikacím, které jsou volně propojeny a spolehlivě komunikovat. Na rozdíl od spolehlivých relací nemusí být zdroj a cíl spuštěn ve stejnou dobu. Tato možnost implicitně umožňuje scénáře, ve kterých jsou fronty v podstatě použité jako mechanismus Vyrovnávání zatížení, když se míra zdroje pro zpracování zpráv a míra cílové spotřeby zprávy neshodují. Další informace o frontách najdete v tématu [fronty ve službě WCF](./feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled spolehlivých relací](./feature-details/reliable-sessions-overview.md)
- [Zařazování do front ve WCF](./feature-details/queuing-in-wcf.md)
