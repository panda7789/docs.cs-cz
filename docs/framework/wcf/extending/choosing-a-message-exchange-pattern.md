---
title: "Výběr vzorce výměny zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab9a894ad57a5324d466e0eb94e49e2cf6104a19
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="choosing-a-message-exchange-pattern"></a>Výběr vzorce výměny zpráv
Prvním krokem při psaní vlastních přenosu je rozhodnout, které *zprávy exchange vzory* (nebo MEPs) jsou povinné pro kanál vyvíjíte. Toto téma popisuje možnosti dostupné a popisuje různé požadavky. Toto je první úloha v seznamu úkolů vývoj kanálu popsané v [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Šest vzory Exchange zpráv  
 Existují tři MEPs zvolit:  
  
-   Datagram (<xref:System.ServiceModel.Channels.IInputChannel> a <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Pokud používáte datagram MEP, klient odešle zprávu pomocí *fire a zapomněli* exchange. A fire a zapomněli exchange je ten, který vyžaduje out-of-band potvrzení úspěšné doručení. Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí službu. Operaci odeslání po úspěšném dokončení na konci klienta, nezaručuje to, že vzdálený koncový bod se zobrazila zpráva. Datagram je základní stavební blok pro zasílání zpráv, jak můžete vytvořit vlastní protokoly nad jeho – včetně protokoly spolehlivé a bezpečné protokoly. Implementace klienta datagram kanály <xref:System.ServiceModel.Channels.IOutputChannel> implementovat rozhraní a služba datagramu kanály <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.  
  
-   Požadavků a odpovědí (<xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     V této MEP je odeslána zpráva a odpoví. Vzor se skládá z dvojice požadavků a odpovědí. Příkladem volání požadavků a odpovědí jsou vzdálených volání procedur (RPC) a prohlížeče GET požadavky. Tento vzor se také označuje jako poloduplexní. V této MEP klienta kanály implementovat <xref:System.ServiceModel.Channels.IRequestChannel> a implementaci služby kanály <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplexní (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     Duplexní MEP umožňuje libovolný počet zpráv, které mají být odeslány klientem a přijaté v libovolném pořadí. Duplexní MEP je třeba je telefonní hovor, kde je jednotlivých slov použitém zprávu. Vzhledem k tomu, že na obou stranách můžete odesílat a přijímat v této MEP, rozhraní implementované kanály klienta a služby je <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Výběr vzorce výměny zpráv](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Tři vzory exchange základní zpráva. Shora dolů: datagram, požadavků a odpovědí a duplexní režim.  
  
 Každý z těchto MEPs může také podporovat *relací*. Relace (a provádění <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> typu <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) korelaci všechny zprávy odeslané a přijaté v kanálu. Vzor požadavků a odpovědí je samostatné relaci dvě zprávy, jako jsou korelační požadavku a odpovědi. Naproti tomu vzor požadavků a odpovědí, který podporuje relací znamená, že všechny páry požadavků a odpovědí v tomto kanálu jsou korelační mezi sebou. To vám dává celkem šest MEPs zvolit:  
  
-   Datagram  
  
-   Požadavek odpověď  
  
-   Duplex  
  
-   Datagram s relací  
  
-   Požadavků a odpovědí s relací  
  
-   Duplexní režim s relací  
  
> [!NOTE]
>  Pro přenosu UDP pouze MEP, která je podporována je datagram, protože UDP je ze své podstaty ještě efektivněji a zapomněli protokolu.  
  
## <a name="sessions-and-sessionful-channels"></a>Relace a Sessionful kanály  
 Na světě sítě jsou orientované na připojení protokoly (například TCP) a protokoly bez připojení (například UDP). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá termín relace rozumí abstrakce logické jako připojení. Relacemi WCF protokoly jsou podobná orientovaná na připojení síťové protokoly a protokoly nerelační WCF jsou podobná připojení méně síťových protokolů.  
  
 V modelu objektu kanál každé logické relaci manifesty jako instanci kanál s relacemi. Proto všechny nové relace vytvoření klient a přijal na službu, odpovídá nové kanálu relací na každé straně. Následující diagram ukazuje, nahoře, struktura nerelační kanály a v dolní části, struktura relacemi kanály.  
  
 ![Výběr vzorce výměny zpráv](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Klient vytvoří nové kanálu relací a odešle zprávu. Na straně služby naslouchací proces kanálu nástroje obdrží tuto zprávu a zjistí, že patří do novou relaci tak, aby se vytvoří nový kanál s relacemi a předá ji do aplikace (jako reakce na aplikaci volání AcceptChannel na naslouchací proces kanálu nástroje). Aplikace se pak obdrží tuto zprávu a všechny následné zprávy odeslané ve stejné relaci prostřednictvím kanálu stejné relací.  
  
 Jiného klienta (nebo stejného klienta) vytvoří nové sessionful a odešle zprávu. Naslouchací proces kanálu nástroje zjišťuje, tato zpráva je v nové relaci a vytvoří nový kanál s relacemi, a postup se opakuje.  
  
 Bez relace neexistuje žádný korelace mezi kanály a relace. Proto vytvoří naslouchací proces kanálu jenom jeden kanál, pomocí kterého jsou všechny přijaté zprávy doručí aplikaci. Neexistuje žádná zpráva, protože neexistuje žádná relace v rámci které má udržovat zpráva pořadí řazení. Horní části na předchozím obrázku znázorňuje nerelační zpráva systému exchange.  
  
## <a name="starting-and-terminating-sessions"></a>Spuštění a ukončení relace  
 Jednoduše vytvořením nového kanálu relací jsou spuštěné relace na straně klienta. Když služba obdrží zprávu, která byla odeslána v nové relaci jsou spuštěny služby. Relace ukončena, zavřít nebo přerušení kanál s relacemi.  
  
 Výjimkou je <xref:System.ServiceModel.Channels.IDuplexSessionChannel> používaný pro odesílání a přijímání zpráv ve tvaru relacemi, duplexní komunikace. Je možné, že jedné straně budou chtít zastavit odesílání zpráv, ale i nadále přijímat zprávy proto při použití <xref:System.ServiceModel.Channels.IDuplexSessionChannel> mechanismus, který vám umožní zavřete výstup relace označující odeslat další zprávy, nebudou ale ponechali relaci vstupní otevřít, takže budete moci přijímat zprávy.  
  
 Obecně platí relace jsou uzavřeny na straně pro odchozí a ne na straně pro příchozí. To znamená kanály relacemi výstup je možné uzavřít, a tím řádně ukončení relace. Zavření kanálu relacemi výstup způsobí, že odpovídající kanálu relací vstupní k vrácení hodnoty null pro volání aplikace <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Ale nesmí relacemi vstupní kanály uzavřen, není-li <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , vrátí hodnotu null, která určuje, že relace již byl uzavřen. Pokud <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> má není vrátil hodnotu null, zavření vstupní kanál s relacemi může vyvolat výjimku, protože obdržet neočekávanou zprávy při zavírání. Pokud příjemce, které chcete ukončit relaci před odesílatele, by měly volat <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na vstupní kanál, který náhle ukončí relace.  
  
## <a name="writing-sessionful-channels"></a>Zápis Sessionful kanály  
 Jako autor kanálu relací jsou pár věcí, které musíte provést kanál zajistit relací. Na straně odesílání kanál, musí:  
  
-   Pro každý nový kanál vytvořte novou relaci a přidružte ji k nové relaci id, které jsou jedinečné řetězce. Nebo získejte novou relaci z kanálu relací níže v zásobníku.  
  
-   Pro každá zpráva odeslaná pomocí tohoto kanálu Pokud kanál vytvořit relaci (na rozdíl od jeho získání z vrstvy níže), budete muset přidružit relace zprávy. Pro kanály protokolů to je obvykle potřeba přidání hlavičky SOAP. Pro přenosové kanály je obvykle důvodem vytvořením nového připojení přenosu nebo přidání informací o relaci rámcovacích protokolu.  
  
-   Každá zpráva odeslaná pomocí tohoto kanálu budete muset zadat záruky doručení uvedených výše. Pokud se spoléhat na kanál níže zadejte relace, bude tento kanál také poskytovat záruky doručení. Pokud zadáváte relaci sami, potřebujete implementovat tyto záruky jako součást vaší protokolu. Obecně platí Pokud píšete protokol kanálu, který předpokládá WCF na obou stranách můžete vyžadují přenos TCP nebo kanál spolehlivé zasílání zpráv a spoléhají na některý zajistit relaci.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> je volána v kanálu, proveďte nezbytné práce k ukončení relace pomocí zadaného časového limitu nebo výchozí nastavení. To může být stejně jednoduché jako volání <xref:System.ServiceModel.ICommunicationObject.Close%2A> na kanálu níže můžete (Pokud jste právě získali relace z něj) nebo odesílání speciální protokolu SOAP zprávy nebo uzavřením připojení přenosu.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Abort%2A> je volána v kanálu, bude relace ukončena náhle bez provádění vstupně-výstupní operace. To může znamenat žádným způsobem nebo může zahrnovat přerušení připojení k síti nebo jiný prostředek.  
  
 Na straně příjmu kanál, musí:  
  
-   Pro příchozí zprávy musí rozpoznat naslouchací proces kanálu nástroje, které patří do relace. Pokud je to první zprávu v relaci, musíte vytvořit nový kanál a vrátit z volání naslouchací proces kanálu nástroje <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. V opačném případě musí naslouchací proces kanálu nástroje najít existující kanálu, který odpovídá relace a doručení zprávy prostřednictvím tohoto kanálu.  
  
-   Pokud kanál poskytuje relace (spolu s záruky požadované doručení) může být na straně příjmu nutné provést některé akce, jako je například změnit pořadí zprávy nebo odeslání potvrzení.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Close%2A> je volána v kanálu, proveďte nezbytné práce k ukončení relace zadaného časového limitu nebo výchozí nastavení. To může vést k výjimkám, pokud kanál přijme zprávu o při čekání na časový limit pro uzavření vyprší. Je to způsobeno kanál bude ve stavu ukončovací přijme nějakou zprávu, takže by výjimku.  
  
-   Když <xref:System.ServiceModel.ICommunicationObject.Abort%2A> je volána v kanálu, bude relace ukončena náhle bez provádění vstupně-výstupní operace. To znovu, může to znamenat žádným způsobem nebo může zahrnovat přerušení připojení k síti nebo jiný prostředek.  
  
## <a name="see-also"></a>Viz také  
 [Přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md)
