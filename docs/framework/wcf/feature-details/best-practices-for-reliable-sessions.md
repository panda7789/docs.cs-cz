---
title: "Doporučené postupy pro spolehlivé relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea7266cb89a233146217d8cadd85839360351f71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-for-reliable-sessions"></a>Doporučené postupy pro spolehlivé relace

Toto téma popisuje osvědčené postupy pro spolehlivé relace.

## <a name="setting-maxtransferwindowsize"></a>Nastavení MaxTransferWindowSize

Spolehlivé relace v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] použít okno přenosu pro uložení zpráv na klientovi a služby. Konfigurovatelná vlastnost <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> Určuje, kolik zpráv, které mohou být uloženy okno přenosu.

U odesílatele to znamená, kolik zpráv, které mohou být uloženy okno přenos při čekání na potvrzení; na příjemce znamená to, kolik zpráv do vyrovnávací paměti pro službu.

Výběr správnou velikost ovlivňuje účinnost sítě a optimální kapacita služby. Následujících oddílech jsou upřesněny co je potřeba zvážit při výběru hodnotu této vlastnosti a vliv hodnoty.

Výchozí velikost okna přenosu je osmi zprávy.

### <a name="efficient-use-of-the-network"></a>Efektivní využití sítě

V tomto kontextu termín *sítě* odpovídá všechno použít jako základ pro komunikaci mezi klientem (odesílatel) a služby (příjemce). To zahrnuje připojení přenosu a všechny zprostředkovatele nebo mostů v mezi, včetně směrovače protokolu SOAP a HTTP proxy nebo brány firewall.

Efektivní využití sítě zajistí, že je plně použít dostatečnou kapacitu sítě. Obě množství dat, které se dá přenést za sekundu přes síť (*přenosová rychlost*) a doby potřebné k přenosu dat od odesilatele k příjemci (*latence*) vliv jak efektivně sítě je použít.

Na odesílatele, vlastnost <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> Určuje, kolik zpráv jeho přenos okno pojme při čekání na potvrzení. Pokud je latence sítě vysoké a aby se zajistilo přizpůsobivý odesílatele a využití efektivní sítě, měli byste zvýšit velikost okna přenosu.

I v případě, že odesílatel držela s přenosovou rychlost, latenci může být například vysoké pokud existuje několik prostředníci mezi odesílatele a příjemce nebo data musí projít míru ztrát zprostředkovatele nebo sítě. Odesílatel proto musí čekat potvrzení pro zprávy v okně jeho přenos před přijetím nové zprávy k odeslání v drátové síti. Menší vyrovnávací paměti s vysokou latencí menší platné využití sítě. Na druhé straně příliš vysoká. velikost okna přenosu může mít vliv na službu vzhledem k tomu, aby se do vysoká míra data odeslaná klientem, možná bude nutné službu.

### <a name="running-the-service-to-capacity"></a>Spuštěná služba kapacity

Tolik, jako síť se používá efektivně, ideálně také chcete službu spustit na optimální kapacitě. Vlastnost velikost okna přenos na příjemce udává, kolik zpráv příjemce může ukládat do vyrovnávací paměti. Tato zpráva ukládání do vyrovnávací paměti pomáhá nejen řízení toku sítě, ale také povoluje službu spustit na úplné kapacity. Například pokud vyrovnávací paměť je jednu zprávu a doručování zpráv rychleji, než služba dokáže zpracovat, pak v síti může vyřaďte zprávy a kapacity může být ke znehodnocení části nebo nedostatečně využité.

Používání vyrovnávací paměť zvyšuje dostupnost služby, jako souběžně obdrží a uloží zprávu při zpracování dříve přijatých zpráv.

Doporučujeme používat stejné `MaxTransferWindowSize` na odesílatele i příjemce.

### <a name="enabling-flow-control"></a>Povolení řízení toku

*Řízení toku* mechanismus, který zajišťuje, aby odesílatele a příjemce držet krok mezi sebou, to znamená, jsou zprávy spotřebované a reagovali na ni tak rychle, jak jste se vytváří. Velikost okna přenosu na klient a služba zajistí odesílatele a příjemce v rámci přiměřené období synchronizace.

Důrazně doporučujeme nastavit vlastnost <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> k `true` když používáte spolehlivé relace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.

## <a name="setting-maxpendingchannels"></a>Nastavení MaxPendingChannels

Při zápisu služba, která umožňuje komunikaci spolehlivé relace z různých klientů, je možné, že mnoho klientů vytvoření spolehlivé relace ve službě ve stejnou dobu. Odpověď služby v těchto situacích závisí na `MaxPendingChannels` vlastnost.

Odesílatel vytvoří kanál spolehlivé relace k příjemce, vytváří handshake mezi nimi spolehlivé relace. Po navázání spolehlivé relace kanál je uvést do fronty čekající kanál pro přijetí službou. `MaxPendingChannels` Vlastnost udává, kolik kanály může být v tomto stavu.

Je možné, má být ve stavu, kde ji nemůže přijímat další kanály pro službu. Pokud fronta je plná, pokus o vytvoření spolehlivé relace se odmítne a klient musí opakovat pokus.

Je také možné, že tyto kanály čekající na vyřízení ve frontě zůstat ve frontě delší dobu. Do té doby může dojít vypršení časového limitu nečinnosti na spolehlivé relace, způsobuje kanálu pro přechod do stavu chybou.

Při zápisu služby, která obsluhuje víc klientů současně, byste měli nastavit hodnotu, která je vhodná pro vaše potřeby. Nastavení příliš velkou hodnotu pro `MaxPendingChannels` vlastnost ovlivňuje pracovní sady.

Výchozí hodnota pro <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> je čtyři kanály.

## <a name="reliable-sessions-and-hosting"></a>Spolehlivé relace a hostování

Pokud webovou službu, která používá spolehlivé relace hostování, byste měli mít na paměti následující důležité informace:

- Spolehlivé relace jsou stavová a stavu se udržuje v domény aplikace. To znamená, že všechny zprávy, které jsou součástí spolehlivé relace musí být zpracovány do stejné domény aplikace. Webové farmy a webové zahrada, kde je větší než jeden uzel velikost farmy nebo zahrada nemůže zaručit toto omezení.

- Spolehlivé relace pomocí dva kanály protokolu HTTP (například pomocí `WsDualHttpBinding`) může vyžadovat více než výchozí dvě připojení za klienta HTTP. To znamená, že duplexní spolehlivé relace může vyžadovat až dvě připojení každého způsobem, protože souběžné aplikace a protokol zpráv může přenosu každý způsob v každém okamžiku. Za určitých podmínek v závislosti na vzorce výměny zpráv služby to znamená, že je možné k zablokování hostované webové služby pomocí duální HTTP a spolehlivé relace. Pokud chcete zvýšit počet povolených připojení prostřednictvím protokolu HTTP pro každého klienta, přidejte následující důležité konfigurační soubor (například *web.config* dotyčné služby):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Hodnota `maxconnection` atribut je počet připojení, které jsou potřeba. Minimální v takovém případě by měl být čtyři připojení.
