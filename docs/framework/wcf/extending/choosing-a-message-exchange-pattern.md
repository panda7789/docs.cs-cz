---
title: Výběr vzorce výměny zpráv
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 98788fb89fc68dc1220d9bf8d9ad89df5ca69e6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157737"
---
# <a name="choosing-a-message-exchange-pattern"></a>Výběr vzorce výměny zpráv
Prvním krokem při psaní vlastních přenosu je rozhodnout, které *zpráv exchange vzory* (nebo MEPs) jsou požadovány pro kanál, kterou vyvíjíte. Toto téma popisuje dostupné možnosti a tento článek popisuje různé požadavky. Toto je první úkol v seznamu úkolů vývoj kanálu je popsáno v [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Šest vzory zpráv Exchange  
 Existují tři MEPs lze vybírat:  
  
-   Datagram (<xref:System.ServiceModel.Channels.IInputChannel> a <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Při použití datagram MEP, klient odešle zprávu pomocí *vypal a zapomeň* exchange. A vypal a zapomeň exchange je ten, který vyžaduje out-of-band potvrzení úspěšné dodání. Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí služby. Pokud se operace odeslání se úspěšně dokončí na straně klienta, není zaručeno, že vzdálený koncový bod přijal zprávu. Datagram je základním stavebním blokem pro zasílání zpráv, jak můžete vytvářet vlastní protokoly, dojde k jeho zvýraznění – včetně protokolů spolehlivé a zabezpečené protokoly. Implementace klienta datagram kanály <xref:System.ServiceModel.Channels.IOutputChannel> implementovat rozhraní a služba datagramu kanály <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.  
  
-   Request-Response (<xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     V tomto MEP je odeslána zpráva a přijetí odpovědi. Vzor se skládá z dvojice žádost odpověď. Odpověď na požadavek volání příklady vzdálených volání procedur (RPC) a prohlížeč GET požadavky. Tento model se také označuje jako poloduplexní. V tomto MEP kanály klientů implementovat <xref:System.ServiceModel.Channels.IRequestChannel> a implementují kanály service <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplexní (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     Duplexní MEP umožňuje libovolný počet zpráv pro klientem odesílat a přijímat v libovolném pořadí. Duplexní MEP je jako je telefonní hovor, kde je zpráva každého slova, se kterým se mluví. Vzhledem k tomu, že obě strany můžete odesílat a přijímat v tomto MEP, rozhraní implementované pomocí kanálů klient a služba je <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Výběr vzoru výměny zpráv](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Tři vzory základní zprávy exchange. Shora dolů: datagram, typu žádost odpověď a přenos.  
  
 Každá z těchto MEPs může také podporovat *relace*. Relace (a provádění <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> typu <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) koreluje všechny zprávy odeslané a přijaté v kanálu. Model typu žádost odpověď je samostatné relace dvě zprávy, jako jsou korelována žádost a odpověď. Vzor typu žádost odpověď, která podporuje relací naproti tomu znamená, že všechny páry žádostí a odpovědí v tomto kanálu jsou korelována mezi sebou. To vám dává celkem šest MEPs lze vybírat:  
  
-   Datagram  
  
-   Žádost odpověď  
  
-   Duplex  
  
-   Datagram s relacemi  
  
-   U relací typu žádost odpověď  
  
-   Duplexní režim s relacemi  
  
> [!NOTE]
>  Pro přenos UDP pouze MEP, který je podporovaný totiž datagram, UDP je ze své podstaty spustit a zapomenout protokolu.  
  
## <a name="sessions-and-sessionful-channels"></a>Relace a který neobsahuje relace kanály  
 Na světě sítě existují připojení objektově orientovaný protokoly (například TCP) a protokoly bez připojení (například UDP). WCF používá termín relace jejich logické abstrakce jako připojení. Protokoly s relacemi WCF jsou podobné připojovací síťové protokoly a protokoly nerelační WCF jsou podobné připojení bez síťových protokolů.  
  
 V objektovém modelu kanál každou logickou relaci manifesty jako instance kanál s relacemi. Proto všechny nové relace vytvořil klienta a přijmout na službě, odpovídá nový kanál s relacemi na každé straně. Následující diagram znázorňuje, v horní části, struktura nerelační kanály a v dolní části, struktura duplexních kanálů s relacemi.  
  
 ![Výběr vzoru výměny zpráv](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Klient vytvoří nový kanál s relacemi a odešle zprávu. Modul pro naslouchání kanálu na straně služeb, obdrží tuto zprávu a zjistí, že patří do novou relaci tak, aby se vytvoří nový kanál s relacemi a předá ji do aplikace (jako reakce aplikace při volání AcceptChannel na modul pro naslouchání kanálu). Aplikace pak obdrží tuto zprávu a všechny následné zprávy odeslané v rámci jedné relace prostřednictvím stejné kanál s relacemi.  
  
 Jiného klienta (nebo stejného klienta) vytvoří nové který neobsahuje relace a odešle zprávu. Modul pro naslouchání kanálu zjistí tato zpráva je v nové relaci a vytvoří nový kanál s relacemi, a postup se opakuje.  
  
 Bez relace neexistuje žádná korelace mezi kanály a relací. Modul pro naslouchání kanálu proto vytvoří jenom jeden kanál, přes který všechny přijaté zprávy doručovaly do aplikace. Neexistuje žádná zpráva řazení, protože neexistuje žádná relace, ve kterém se mají zachovat pořadí zpráv. Horní části na předchozím obrázku je znázorněný nerelační zprávy exchange.  
  
## <a name="starting-and-terminating-sessions"></a>Spuštění a ukončení relací  
 Relace se spustí v klientském počítači tak, že jednoduše vytvoříte nový kanál s relacemi. Když služba přijímá zprávy, která byla odeslána v nové relaci jsou spuštěny na službu. Stejně tak relace jsou ukončeny zavření nebo ukončení kanál s relacemi.  
  
 Výjimkou je <xref:System.ServiceModel.Channels.IDuplexSessionChannel> používaný pro odesílání a přijímání zpráv ve vzoru s relacemi duplexní komunikaci. Je možné, že jedna strana budou chtít zastavit odesílání zpráv, ale i nadále přijímat zprávy proto při použití <xref:System.ServiceModel.Channels.IDuplexSessionChannel> je mechanismus, který vám umožní zavřít výstupní relace označující odeslat další zprávy, nebudou ale ponechali relaci vstupu otevřít, abyste mohli nadále přijímat zprávy.  
  
 Relace jsou obecně platí, Uzavřeno na straně odchozí a ne na straně příchozí. To znamená kanálů s relacemi výstup můžete zavřít, a tím čistě ukončení relace. Zavření kanál s relacemi výstup způsobí, že odpovídající vstupní kanál s relacemi k vrácení hodnoty null pro volání aplikace <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Ale by neměly duplexních kanálů vstupní uzavřen, není-li <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> vrátí hodnotu null, která znamená, že relace je už zavřený. Pokud <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> se ne vrátila hodnotu null, zavírání vstupní kanál s relacemi může vyvolat výjimku protože obdržet neočekávané zprávy při zavírání. Je-li ukončit relaci před odesílatele a příjemce si přeje, měla by volat <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na vstupní kanál, který náhle ukončí relace.  
  
## <a name="writing-sessionful-channels"></a>Zápis který neobsahuje relace kanály  
 Jako autor kanál s relacemi existuje několik věcí, které váš kanál musíte udělat, abyste relací zadejte. Na straně odesílání kanálu potřebuje:  
  
-   Pro každý nový kanál vytvoří se nová relace a přidružte ji k nové relaci id, které jsou jedinečné řetězce. Nebo získat novou relaci z kanálu relací níže v zásobníku.  
  
-   Pro každou zprávu odeslaných pomocí tohoto kanálu Pokud váš kanál vytvořit relace (na rozdíl od získání ho z vrstvy níže), musíte přidružit k relaci zprávy. Pro kanály protokolů je obvykle to tak, že přidáte záhlaví SOAP. Pro přenosové kanály obvykle stačí vytváření nového připojení přenosu nebo přidání informací o relaci protokolu rámce.  
  
-   Každá zpráva odeslaná pomocí tohoto kanálu potřebujete poskytovat záruky doručení uvedených výše. Pokud se spoléháte na kanálu níže, abychom vám poskytli relace, bude tento kanál také poskytovat záruky doručení. Pokud zadáváte relaci sami, budete muset implementovat jako součást váš protokol záruk. Obecně platí Pokud vytváříte kanál protokolu, který předpokládá WCF na obou stranách můžete vyžadovat přenosu protokolu TCP nebo kanál spolehlivé zasílání zpráv a Spolehněte se na jednu relaci poskytnout.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> je volána na kanál, provedení potřebné práce k ukončení relace pomocí zadaného časového limitu nebo výchozí hodnotu. To může být stejně jednoduché jako volání funkce <xref:System.ServiceModel.ICommunicationObject.Close%2A> na kanálu níže (Pokud jste právě získali relace z něj) nebo odesílání zprávy protokolu SOAP speciální nebo zavření připojení přenosu.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Abort%2A> je volána na kanál, ukončení relace náhle bez provádění vstupně-výstupních operací. To může znamenat nicneděláním nebo může zahrnovat přerušení připojení k síti nebo jiný prostředek.  
  
 Na straně příjmu kanálu potřebuje:  
  
-   Pro příchozí zprávy musí odhalit modul pro naslouchání kanálu, do které patří do relace. Pokud je toto první zprávu v relaci, modul pro naslouchání kanálu musíte vytvořit nový kanál a vrátit ji z volání <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. Jinak modul pro naslouchání kanálu musí najít existující kanál, který odpovídá relace a doručit zprávu přes tento kanál.  
  
-   Pokud váš kanál, je poskytování relace (spolu s záruky doručení požadované) na straně příjmu může být vyžadováno provést některé akce, jako je změna pořadí zpráv nebo odeslání potvrzení.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Close%2A> je volána na kanál, provedení potřebné k ukončení relace zadaný časový limit nebo výchozí hodnotu. To může vést k výjimkám Pokud kanál obdrží zprávu při čekání na časový limit pro uzavření vyprší. Důvodem je skutečnost, že kanál bude ve stavu zavírání obdrží zprávu, takže by výjimku.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Abort%2A> je volána na kanál, ukončení relace náhle bez provádění vstupně-výstupních operací. To znovu, může to znamenat nicneděláním nebo může zahrnovat přerušení připojení k síti nebo jiný prostředek.  
  
## <a name="see-also"></a>Viz také:

- [Přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md)
