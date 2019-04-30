---
title: Doporučené postupy pro spolehlivé relace
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857984"
---
# <a name="best-practices-for-reliable-sessions"></a>Doporučené postupy pro spolehlivé relace

Toto téma popisuje osvědčené postupy pro spolehlivé relace.

## <a name="setting-maxtransferwindowsize"></a>Nastavení MaxTransferWindowSize

Spolehlivé relace ve Windows Communication Foundation (WCF) použít okno přenos pro uložení zpráv na klienta a služby. Konfigurovatelné vlastnosti <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> označuje, kolik zpráv přenosu okna může obsahovat.

V odesílateli to znamená, kolik zpráv okna přenosu, podržte při čekání na potvrzení; na straně příjmu znamená to, kolik zpráv do vyrovnávací paměti pro službu.

Výběr správné velikosti má vliv na výkon sítě a optimální kapacita služby. Následující části popisují, co je potřeba zvážit při výběru hodnoty pro tuto vlastnost a dopad hodnotu.

Výchozí velikost okna přenosu je osm zpráv.

### <a name="efficient-use-of-the-network"></a>Efektivní využití sítě

V tomto kontextu termín *sítě* odpovídá všechno, co použít jako základ pro komunikaci mezi klientem (odesílatel) a služby (příjemce). To zahrnuje připojení přenosu a všechny zprostředkovatele nebo přemostění mezi, včetně směrovače protokolu SOAP a HTTP proxy servery a brány firewall.

Efektivní využití sítě zajistí, že je plně využíván kapacita sítě. Velikost dat, které mohou být převedeny v síti za sekundu (*datová rychlost*) a čas potřebný k přenosu dat od odesilatele k příjemci (*latence*) ovlivnit jak efektivně sítě se používá.

V odesílateli, vlastnost <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> označuje, kolik zpráv její okno přenosu, podržte při čekání na potvrzení. Pokud je vysoká latence sítě a aby se zajistilo responzivní odesílatele a využití sítě efektivní, měli byste zvýšit velikost okna přenosu.

I v případě, že odesílatel drží krok s přenosovou rychlost, latenci může být například vysoká Pokud několik zprostředkovatelů existovat mezi odesílatelem a příjemcem nebo data musí projít přes míru ztrát zprostředkovatele nebo sítě. Proto má odesílatel čekání na potvrzení pro zprávy v okně přenos před přijetím nového zprávy k odeslání na lince. Čím menší vyrovnávací paměti s vysokou latencí, je méně efektivní využití sítě. Na druhé straně příliš vysoká. velikost okna přenosu může mít vliv na službu vzhledem k tomu, že služba možná muset dohnat na vysoký informací odesílaném klientem.

### <a name="running-the-service-to-capacity"></a>Spuštěná služba ke kapacitě

Co nejvíce efektivní využití sítě v ideálním případě také chcete službu spustit na optimální kapacity. Vlastnost velikost okna přenosu na straně příjmu označuje, kolik zpráv příjemce lze uložit do vyrovnávací paměti. Tato zpráva ukládání do vyrovnávací paměti pomáhá nejen řízení toku sítě, ale taky umožňuje službě a kapacita se spustí. Například pokud vyrovnávací paměť je jedna zpráva a doručování zpráv rychleji, než služba může zpracovat je pak sítě může být vyřadit zprávy a kapacitu mohou být ztraceny, nebo historického.

Použití vyrovnávací paměti zvyšuje dostupnost služby, jak souběžně přijme a uloží zprávu vyrovnávací paměti při zpracování dříve přijaté zprávy.

Doporučujeme použít stejné `MaxTransferWindowSize` na odesílatele a příjemce.

### <a name="enabling-flow-control"></a>Povolení řízení toku

*Řízení toku* virtuálních sítí je mechanismus, který zajistí, že odesílatel a příjemce držet mezi sebou, tzn. zprávy jsou využité a reagovali na ni tak rychle, protože se vytvářejí. Velikost okna přenosu na klienta a služby zajišťuje, že jsou v rozumné okno synchronizace odesílatele a příjemce.

Důrazně doporučujeme, že nastavíte vlastnost <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> k `true` když používáte stabilní relace mezi klienta WCF a služby WCF.

## <a name="setting-maxpendingchannels"></a>Setting MaxPendingChannels

Při zápisu služba, která umožňuje komunikaci stabilní relace, od různých klientů, je možné mít mnoho klientů vytvořit stabilní relaci ke službě ve stejnou dobu. Odpovědi služby v těchto situacích závisí `MaxPendingChannels` vlastnost.

Pokud odesílatel vytvoří kanál stabilní relace pro příjemce, handshake mezi nimi vytváří stabilní relace. Po navázání spolehlivé relace kanál je umístěn ve frontě čeká na kanál pro přijetí službou. `MaxPendingChannels` Vlastnost určuje, kolik kanálů může být v tomto stavu.

Je možné, že služba bude ve stavu, ve kterém nemůže přijmout další kanály. Pokud fronta je plná, odmítl pokus o navázání spolehlivé relace a klient musí opakovat pokus.

Je také možné, že zůstávají ve frontě čeká na kanály ve frontě delší dobu. Do té doby může dojít vypršení časového limitu nečinnosti na ve stabilní relaci, způsobí kanálu pro přechod na chybovém stavu.

Při zápisu služby, která obsluhuje víc klientů současně, byste měli nastavit hodnotu, která je vhodná pro vaše potřeby. Nastavení příliš velkou hodnotu pro `MaxPendingChannels` vlastnost ovlivňuje vaši pracovní sadu.

Výchozí hodnota pro <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> je čtyři kanály.

## <a name="reliable-sessions-and-hosting"></a>Spolehlivé relace a hostování

Když webové hostování služba, která používá spolehlivé relace, je třeba mít na paměti následující důležité informace:

- Spolehlivé relace jsou stavové a stát se udržuje v doméně aplikace. To znamená, že všechny zprávy, které jsou součástí stabilní relace musí být zpracovány v téže doméně AppDomain. Toto omezení nemůže zaručit webových farem a zahrady web, kde je velikost farmy nebo kachnami větší než jeden uzel.

- Spolehlivé relace pomocí dvou kanály HTTP (například pomocí `WsDualHttpBinding`) může vyžadovat více než výchozí dvě připojení na klienta HTTP. To znamená, že duplexní stabilní relace může vyžadovat až dvě připojení jednotlivé možnosti přinesou, protože souběžné aplikace a protokol zpráv může přenos jednotlivé možnosti přinesou v daném okamžiku. Za určitých podmínek v závislosti na vzorce výměny zpráv služby to znamená, že je možné k zablokování hostované webové služby pomocí dvou HTTP a spolehlivé relace. Zvyšte počet povolených připojení prostřednictvím protokolu HTTP pro každého klienta, přidejte následující důležité konfigurační soubor (například *web.config* z příslušné služby):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Hodnota `maxconnection` atribut je počet připojení potřeba. Minimum v tomto případě by měl být čtyři připojení.
