---
title: "Omezení distribuce zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 191baa2df4a6a5a4fe8139e8b7ad36bd1c60b40d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="limiting-message-distribution"></a>Omezení distribuce zpráv
Rovnocenného kanálu je záměrné všesměrového vysílání mřížku. Svůj základní flooding model spočívá v distribuci každá zpráva odeslaná do všech členů tohoto oka kteréhokoli člena mřížku. To se hodí v situacích, kde každé zprávy vygenerované metodou členem je relevantní a užitečné pro všechny ostatní členy (například konverzační skupina). Ale mnoho aplikací mít občasné potřebu omezení distribuce zpráv. Například pokud nového člena spojí mřížku a chce načíst poslední zprávou odeslanou přes síť, tento požadavek není nutné k zaplnění na každého člena OK. Žádost může být omezen na téměř okolí, nebo může být odfiltrována místně vygenerovanou zprávy. Zprávy mohou rovněž odeslány do jednotlivých uzlu na OK. Toto téma popisuje použití počet směrování, šíření filtru zpráv, filtrem místní nebo přímé připojení k řízení, jak se předávají zprávy v průběhu OK a obsahuje obecné pokyny pro výběr přístup.  
  
## <a name="hop-counts"></a>Počet směrování  
 Koncept `PeerHopCount` je podobná TTL (Time-To-Live) používá v protokolu IP. Hodnota `PeerHopCount` je vázaný na instanci zprávy a určuje, kolikrát by měly být předávány zprávu před probíhá vyřazování. Pokaždé, když je přijata zpráva rovnocenného kanálu klientem, klient hledá se zobrazí, pokud `PeerHopCount` je zadán. Pokud je zadán, pak snižuje klienta ke směrování počet hodnotu jednou před předáním zprávy do sousedních uzlů. Když klient obdrží zprávu s nulovou hodnotou počet směrování, klient zprávu zpracuje, ale není předávat zprávy okolí.  
  
 Počet směrování mohou být přidány do zprávy můžete přidat `PeerHopCount` jako atribut použít vlastnost nebo pole v implementaci třídy zprávy. To můžete nastavit na konkrétní hodnotu před odesláním zprávy na mřížku. Tímto způsobem můžete počet směrování k omezení distribuce zpráv v rámci mřížky, pokud je to nezbytné, potenciálně zabraňující duplikace nepotřebné zprávy. To je užitečné v případech, kde OK obsahuje vysoké množství redundantních dat, nebo odesílání zprávy pro okamžité Sousedé BGP nebo Sousedé BGP v rámci několik segmentů směrování.  
  
-   Fragmenty kódu a související informace najdete v tématu [rovnocenného kanálu blog](http://go.microsoft.com/fwlink/?LinkID=114531) (http://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>Šíření filtr zpráv  
 `MessagePropagationFilter`můžete použít pro vlastní řízení zahlcení zprávy, zejména v případě, že obsah zprávy nebo jiných konkrétních scénářů určit šíření. Filtr rozhoduje šíření pro každou zprávu, které procházejí uzlu. To platí pro zprávy, které pochází jinde v mřížce, vaše uzlu přijal i zprávy vytvořené v aplikaci. Filtr má přístup ke zprávě a jeho vzniku, takže rozhodnutí o předávání nebo vyřazuje zprávy může být založen na úplné informace, které jsou k dispozici.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter>je abstraktní základní třídu s jedinou funkci <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. První argument volání metody předá úplnou kopii zprávy. Všechny změny na zprávu neovlivní skutečné zprávy. Poslední argument volání metody, které identifikuje počátek zprávy (`PeerMessageOrigination.Local` nebo `PeerMessageOrigination.Remote`). Konkrétní implementace této metody musí vracet konstanta z <xref:System.ServiceModel.PeerMessagePropagation> výčtu označující, že zprávy je k přeposlání do místních aplikací (`Local`), přesměrovaná ke vzdáleným klientům (`Remote`), obě (`LocalAndRemote`), nebo žádný z nich (`None`). Tento filtr lze použít přímým přístupem k odpovídající položce `PeerNode` objekt a zadání instanci odvozené šíření filtrovat třídy v `PeerNode.MessagePropagationFilter` vlastnost. Zkontrolujte, zda filtr šíření připojen před otevřením rovnocenného kanálu.  
  
-   Fragmenty kódu a související informace najdete v tématu [rovnocenného kanálu blog](http://go.microsoft.com/fwlink/?LinkID=114532) (http://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Kontaktování jednotlivého uzlu v mřížce  
 Nelze kontaktovat jednotlivého uzlu v mřížku nastavení místní filtr, nebo nastavením přímé připojení.  
  
 Pokud uzly v mřížku každé jednotlivé ID, lze zadat ID cílové implementace zprávu. Místní filtru můžete nastavit tak, že napíšete funkci v vaší kontrakt zprávy, která bude obsahovat pouze zprávy do aktuálního uzlu Pokud je zadané ID cílové odpovídá jeho ID. OK určena k přenosu zpráv, tak nebude muset vám být účtovány režii nastavením nového připojení. Je však ke ztrátě efektivitu vzhledem k tomu, že je zpráva odeslána mnohokrát v rámci OK. To funguje dobře pro odesílání zpráv na jednotlivé členy mřížky, pokud jsou zprávy příliš často ani příliš velký.  
  
 Pro trvalý, širokopásmové připojení jsou vhodnější než přímé připojení. Můžete odeslat informace o připojení přes síť a poté nastavit přímé připojení dle vlastního výběru k odesílání a příjem zpráv.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Výběr přístup pro omezení distribuce zpráv  
 Po zjištění scénář, ve kterém je potřeba k omezení distribuce zpráv, položte si následující otázky:  
  
-   **Kdo** musí zpráva? Jedním sousedním uzlu? Uzel někde jinde v mřížce? Poloviční OK?  
  
-   **Jak často** tuto zprávu zašle?  
  
-   Jaký typ z **šířky pásma** použije tuto zprávu?  
  
 Odpovědi na tyto otázky vám může pomoct určit, jestli se má používat počet směrování, šíření filtru zpráv, filtrem místní nebo přímé připojení k. Vezměte v úvahu následující obecné pokyny:  
  
-   **Kdo**  
  
    -   *Jednotlivé uzlu*: filtru místní nebo přímé připojení.  
  
    -   *Okolí v rámci určitých okolí*: PeerHopCount.  
  
    -   *Komplexní podmnožinu OK*: Třída MessagePropagationFilter.  
  
-   **Jak často**  
  
    -   *Velmi často*: přímé připojení, PeerHopCount, Třída MessagePropagationFilter.  
  
    -   *Příležitostně*: místní filtru.  
  
-   **Využití šířky pásma**  
  
    -   *Vysoká*: přímé připojení, méně vhodné používat Třída MessagePropagationFilter nebo místní filtru.  
  
    -   *Nízká*: žádné, přímé připojení nejspíš potřeba.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření aplikace rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
