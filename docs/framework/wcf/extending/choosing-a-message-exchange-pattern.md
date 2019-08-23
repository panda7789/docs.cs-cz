---
title: Výběr vzorce výměny zpráv
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 518a21ef34d52ef4b70871ba8bad7876374dd319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951864"
---
# <a name="choosing-a-message-exchange-pattern"></a>Výběr vzorce výměny zpráv
Prvním krokem při psaní vlastního přenosu je rozhodování o tom, které *vzory výměny zpráv* (nebo MEPs) se vyžadují pro kanál, který vyvíjíte. Toto téma popisuje dostupné možnosti a popisuje různé požadavky. Toto je první úkol v seznamu úkolů vývoj kanálu, který je popsaný v tématu [Vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Šest vzorců výměny zpráv  
 Existují tři MEPsy, ze kterých si můžete vybrat:  
  
- Datagram (<xref:System.ServiceModel.Channels.IInputChannel> a <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Při použití dataMEP datagramu pošle klient zprávu s výměnou *požáru a zapomenutí* . Výměna požáru a zapomenutí je taková, která vyžaduje vzdálené potvrzení úspěšného doručení. Zpráva může být ztracena při přenosu a nikdy se nespojit se službou. Pokud se operace odeslání na konci klienta úspěšně dokončí, nezaručuje, že vzdálený koncový bod obdrží zprávu. Datagram je základní stavební blok pro zasílání zpráv, protože můžete sestavovat vlastní protokoly nad ním, včetně spolehlivých protokolů a zabezpečených protokolů. Kanály datagramů klienta <xref:System.ServiceModel.Channels.IOutputChannel> implementují rozhraní a kanály Datagram Service <xref:System.ServiceModel.Channels.IInputChannel> implementující rozhraní.  
  
- Požadavek-odpověď (<xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     V tomto MEP zpráva se pošle a odpověď se přijme. Vzor se skládá z párů požadavků a odpovědí. Příklady volání požadavků na odezvu jsou vzdálená volání procedur (RPC) a požadavky GET prohlížeče. Tento model se také označuje jako poloduplexní. V tomto MEP implementují klientské kanály <xref:System.ServiceModel.Channels.IRequestChannel> a implementuje <xref:System.ServiceModel.Channels.IReplyChannel>kanály pro služby.  
  
- Duplexní<xref:System.ServiceModel.Channels.IDuplexChannel>přenos ()  
  
     Duplexní MEP umožňuje klientovi poslat libovolný počet zpráv a přijatý v libovolném pořadí. Duplexní MEP je jako telefonická konverzace, kde každé mluvené slovo je zpráva. Vzhledem k tomu, že obě strany mohou v tomto MEP odesílat a přijímat, rozhraní implementované kanály klienta a služby <xref:System.ServiceModel.Channels.IDuplexChannel>je.  
  
 ![Výběr vzoru výměny zprávy](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Tři základní vzory výměny zpráv. Shora dolů: datagram, Request-response a duplexní režim.  
  
 Každý z těchto MEPs může také podporovat *relace*. Relace (a implementace <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> typu <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) koreluje všechny zprávy odeslané a přijaté na kanálu. Vzor požadavků a odpovědí je samostatná relace dvou zpráv, protože se jedná o korelační požadavek a odpověď. Oproti tomu vzor požadavek-odpověď, který podporuje relace, implikuje vzájemnou korelaci mezi všemi páry požadavků a odpovědí na daném kanálu. Získáte tak celkem šest MEPs, ze kterých si můžete vybrat:  
  
- Datagram  
  
- Požadavek – odpověď  
  
- Duplex  
  
- Datagram s relacemi  
  
- Požadavek-odpověď s relacemi  
  
- Duplexní s relacemi  
  
> [!NOTE]
> Pro přenos UDP je jedinou podporovanou MEP datagram, protože UDP je ze své podstaty protokolem požáru a zapomenout.  
  
## <a name="sessions-and-sessionful-channels"></a>Relace a kanály s relacemi  
 V cloudu sítě jsou k dispozici protokoly orientované na připojení (například protokol TCP) a protokoly bez připojení (například UDP). WCF používá termín relace k označení logické abstrakce podobné připojení. Relační protokoly WCF jsou podobné síťovým protokolům orientovaným na připojení a protokoly WCF bez relací jsou podobné síťovým protokolům bez připojení.  
  
 V objektovém modelu kanálu jednotlivé logické relace se manifestují jako instance kanálu s relacemi. Proto každá nová relace vytvořená klientem a přijatá ve službě odpovídá novému kanálu na každé straně. Následující diagram znázorňuje v horní části strukturu kanálů bez relací a dolní část struktury kanálů, které jsou v relaci.  
  
 ![Výběr vzoru výměny zprávy](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Klient vytvoří nový kanál s relací a pošle zprávu. Naslouchací proces kanálu na straně služby obdrží tuto zprávu a zjistí, že patří do nové relace, takže vytvoří nový kanál s relací a předá ho aplikaci (v reakci na aplikaci volající AcceptChannel v naslouchací službě kanálu). Aplikace potom obdrží tuto zprávu a všechny následné zprávy odeslané ve stejné relaci prostřednictvím stejného kanálu relace.  
  
 Jiný klient (nebo stejný klient) vytvoří novou relaci a pošle zprávu. Naslouchací proces kanálu detekuje tuto zprávu v nové relaci a vytvoří nový kanál s relací a proces se opakuje.  
  
 Bez relací nedochází k žádné korelaci mezi kanály a relacemi. Proto naslouchací proces kanálu vytvoří pouze jeden kanál, přes který aplikace doručuje všechny přijaté zprávy. K dispozici není žádné řazení zpráv, protože v ní není žádná relace, ve které by bylo možné zachovat pořadí zpráv. V horní části předchozího obrázku je znázorněna výměna zpráv v nerelačních zprávách.  
  
## <a name="starting-and-terminating-sessions"></a>Spuštění a ukončení relací  
 Relace se spouští v klientovi pouhým vytvořením nového kanálu s relacemi. Spouští se ve službě, když služba obdrží zprávu odeslanou v nové relaci. Podobně se relace ukončí zavřením nebo přerušením kanálu s relacemi.  
  
 Výjimkou je ta, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> která se používá pro posílání i přijímání zpráv v duplexní komunikačním vzoru relace. Je možné, že jedna strana bude chtít přestat odesílat zprávy, ale nadále přijímat zprávy, když použijete <xref:System.ServiceModel.Channels.IDuplexSessionChannel> mechanismus, který umožňuje zavřít výstupní relaci, což znamená, že nebudete odesílat žádné další zprávy, ale zachováte vstupní relaci. otevřené, což vám umožní nadále přijímat zprávy.  
  
 Obecně platí, že relace budou uzavřeny na straně odchozí a nikoli na straně příchozí. To znamená, že je možné zavřít výstupní kanály s relacemi, čímž se čistě ukončí relace. Při zavření výstupního kanálu relace dojde k tomu, že odpovídající vstupní kanál relace vrátí hodnotu null do aplikace <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> volající <xref:System.ServiceModel.Channels.IDuplexSessionChannel>na.  
  
 Vstupní kanály relace by však neměly být uzavřeny, <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> Pokud není <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na hodnotě null, což značí, že relace je již zavřena. <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> Pokud<xref:System.ServiceModel.Channels.IDuplexSessionChannel> v nevrátil hodnotu null, může ukončení vstupního kanálu relace vyvolat výjimku, protože při zavírání může docházet k neočekávaným zprávám. Pokud si příjemce přeje ukončit relaci před odesílatelem, měl by zavolat <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na vstupní kanál, který náhle ukončí relaci.  
  
## <a name="writing-sessionful-channels"></a>Zápis kanálů relací  
 Jako autor kanálu v relaci je potřeba, aby váš kanál měl k dispozici několik věcí. Na straně odeslání váš kanál potřebuje:  
  
- U každého nového kanálu vytvořte novou relaci a přidružte ji k novému ID relace, které je jedinečný řetězec. Nebo získejte novou relaci z kanálu relace pod zásobníkem.  
  
- U každé zprávy odeslané pomocí tohoto kanálu, pokud kanál vytvořil relaci (na rozdíl od jejího získání od vrstvy níže), je třeba přidružit zprávu k relaci. V případě kanálů protokolu se to obvykle provádí přidáním hlavičky SOAP. Pro přenosové kanály se to obvykle provádí vytvořením nového transportního připojení nebo přidáním informací o relaci do protokolu rámců.  
  
- U každé zprávy odeslané pomocí tohoto kanálu musíte poskytnout záruky doručení uvedené výše. Pokud se spoléháte na kanál, který následuje za tím, že zadáte relaci, bude tento kanál také poskytovat záruky pro doručování. Pokud zadáváte relaci sami, musíte tyto záruky implementovat jako součást vašeho protokolu. Obecně platí, že pokud píšete kanál protokolu, který na obou stranách předpokládá službu WCF, budete pravděpodobně vyžadovat přenos TCP nebo kanál spolehlivého zasílání zpráv a spoléhat na jednu z nich k poskytnutí relace.  
  
- Když <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> se ve vašem kanálu volá, proveďte potřebnou práci, aby se relace zavřela buď pomocí zadaného časového limitu, nebo s výchozím nastavením. To může být jednoduché jako volání <xref:System.ServiceModel.ICommunicationObject.Close%2A> na kanál níže (Pokud jste právě získali relaci z tohoto kanálu) nebo odesláním speciální zprávy protokolu SOAP nebo ukončením připojení přenosu.  
  
- Když <xref:System.ServiceModel.ICommunicationObject.Abort%2A> se ve vašem kanálu volá, ukončí relaci bez provedení vstupně-výstupních operací. To může znamenat, že se nic nestane, nebo může zahrnovat přerušení síťového připojení nebo nějakého jiného prostředku.  
  
 Na straně příjmu váš kanál potřebuje:  
  
- Pro každou příchozí zprávu musí naslouchací proces kanálu detekovat relaci, ke které patří. Pokud se jedná o první zprávu v relaci, musí naslouchací proces kanálu vytvořit nový kanál a vrátit ho z volání do <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. V opačném případě musí naslouchací proces kanálu najít existující kanál, který odpovídá relaci a doručuje zprávu prostřednictvím tohoto kanálu.  
  
- Pokud váš kanál poskytuje relaci (spolu s požadovanými zárukami na doručení), může být vyžadována strana příjmu k provádění některých akcí, jako je například změna pořadí zpráv nebo odesílání potvrzení.  
  
- Když <xref:System.ServiceModel.ICommunicationObject.Close%2A> se ve vašem kanálu volá, proveďte potřebnou práci, aby se relace zavřela buď na zadaný časový limit, nebo na výchozí. To může vést k výjimkám, pokud kanál obdrží zprávu při čekání na vypršení časového limitu ukončení. To je proto, že kanál bude ve stavu ukončení, když obdrží zprávu, takže by se vyvolal.  
  
- Když <xref:System.ServiceModel.ICommunicationObject.Abort%2A> se ve vašem kanálu volá, ukončí relaci bez provedení vstupně-výstupních operací. To může znamenat, že se nic nestane, nebo může způsobit přerušení síťového připojení nebo nějakého jiného prostředku.  
  
## <a name="see-also"></a>Viz také:

- [Přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md)
