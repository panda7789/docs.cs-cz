---
title: 'Přenos: Součinnost TCP ve WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 55c59fe3a677d3aea8de62ae714e1007cfcbb86a
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121286"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Přenos: Součinnost TCP ve WSE 3.0
Ukázka přenosu interoperability protokolu WSE 3.0 TCP ukazuje, jak implementovat duplexní relaci Protokolu TCP jako vlastní přenos WCF (Windows Communication Foundation). Také ukazuje, jak můžete použít rozšiřitelnost vrstvy kanálu k rozhraní přes drát s existujícími nasazenými systémy. Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:  
  
1. Počínaje soketem TCP vytvořte klientské a serverové <xref:System.ServiceModel.Channels.IDuplexSessionChannel> implementace, které používají rámování DIME k vymezení hranic zpráv.  
  
2. Vytvořte továrnu kanálu, která se připojí ke službě WSE <xref:System.ServiceModel.Channels.IDuplexSessionChannel>TCP a odesílá zprávy zarámované přes s klienta.  
  
3. Vytvořte naslouchací proces kanálu pro přijetí příchozích připojení TCP a vytvoření odpovídajících kanálů.  
  
4. Ujistěte se, že všechny výjimky specifické pro síť <xref:System.ServiceModel.CommunicationException>jsou normalizovány na příslušnou odvozenou třídu .  
  
5. Přidejte element vazby, který přidá vlastní přenos do zásobníku kanálu. Další informace naleznete v tématu [Přidání elementu vazby].  
  
## <a name="creating-iduplexsessionchannel"></a>Vytváření kanálu iduplexsessionchannel  
 Prvním krokem při psaní WSE 3.0 TCP interoperability přenosu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> je vytvořit <xref:System.Net.Sockets.Socket>implementaci na vrcholu . `WseTcpDuplexSessionChannel`pochází z <xref:System.ServiceModel.Channels.ChannelBase>. Logika odeslání zprávy se skládá ze dvou hlavních částí: (1) Kódování zprávy do bajtů a (2) rámování těchto bajtů a jejich odeslání na lince.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Kromě toho je přijata zámek tak, aby Send() volání zachovat iDuplexSessionChannel v pořadí záruky a tak, aby volání podkladového soketu jsou synchronizovány správně.  
  
 `WseTcpDuplexSessionChannel`používá <xref:System.ServiceModel.Channels.MessageEncoder> pro překlad do <xref:System.ServiceModel.Channels.Message> a a byte[]. Vzhledem k tomu, že se jedná o přenos, `WseTcpDuplexSessionChannel` je také zodpovědný za použití vzdálené adresy, která kanál byl nakonfigurován s. `EncodeMessage`zapouzdřuje logiku pro tento převod.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Jakmile <xref:System.ServiceModel.Channels.Message> je kódován do bajtů, musí být přenášen na drátě. To vyžaduje systém pro definování hranic zprávy. WSE 3.0 používá verzi [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) jako protokol rámování. `WriteData`zapouzdřuje logiku rámování pro zalomení bajtu[] do sady záznamů DIME.  
  
 Logika pro příjem zpráv je velmi podobná. Hlavní složitost je zpracování skutečnost, že čtení soketu může vrátit méně bajtů, než byly požadovány. Chcete-li přijmout `WseTcpDuplexSessionChannel` zprávu, přečte bajty z drátu, dekóduje rámdime a pak použije <xref:System.ServiceModel.Channels.MessageEncoder> <xref:System.ServiceModel.Channels.Message>pro přeměnu bajta na .  
  
 Základna `WseTcpDuplexSessionChannel` předpokládá, že obdrží připojený soket. Základní třída zpracovává vypnutí soketu. Existují tři místa, která rozhraní s uzavření mašketu:  
  
- OnAbort -- zavřete soket ungracefully (hard close).  
  
- On[Begin]Close -- zavřete zásuvku elegantně (soft close).  
  
- Relace. CloseOutputSession -- vypnutí odchozídatový proud (polovina zavřít).  
  
## <a name="channel-factory"></a>Vytvoření postupu kanálu  
 Dalším krokem při psaní přenosu TCP je <xref:System.ServiceModel.Channels.IChannelFactory> vytvoření implementace pro klientské kanály.  
  
- `WseTcpChannelFactory`pochází z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<iDuplexSessionChannel>. Jedná se o továrnu, která přepíše `OnCreateChannel` vyrábět klientské kanály.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`přidá logiku `WseTcpDuplexSessionChannel` k základně pro připojení `channel.Open` k serveru TCP v čase. Nejprve je název hostitele přeložen na adresu IP, jak je znázorněno v následujícím kódu.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Potom je název hostitele připojen k první dostupné IP adrese ve smyčce, jak je znázorněno v následujícím kódu.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- Jako součást smlouvy kanálu jsou zabaleny všechny výjimky specifické `SocketException` <xref:System.ServiceModel.CommunicationException>pro doménu, například v .  
  
## <a name="channel-listener"></a>Naslouchací proces kanálu  
 Dalším krokem při psaní přenosu TCP je <xref:System.ServiceModel.Channels.IChannelListener> vytvoření implementace pro příjem serverových kanálů.  
  
- `WseTcpChannelListener`odvozuje <xref:System.ServiceModel.Channels.ChannelListenerBase> \<z IDuplexSessionChannel> a přepíše On[Begin]Open a On[Begin]Close řídit životnost jeho naslouchání soketu. V OnOpen je vytvořen soket pro poslech na IP_ANY. Pokročilejší implementace můžete vytvořit druhý soket pro poslech na IPv6 také. Mohou také povolit ip adresu, která má být zadána v názvu hostitele.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Při přijetí nového soketu je inicializován serverový kanál s tímto soketem. Všechny vstupy a výstupy jsou již implementovány v základní třídě, takže tento kanál je zodpovědný za inicializaci soketu.  
  
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Nyní továrny a kanály jsou sestaveny, musí být vystaveny ServiceModel runtime prostřednictvím vazby. Vazba je kolekce elementů vazby, která představuje zásobník komunikace přidružené k adrese služby. Každý prvek v zásobníku je reprezentován elementem vazby.  
  
 Ve vzorku je `WseTcpTransportBindingElement`prvek vazby , <xref:System.ServiceModel.Channels.TransportBindingElement>který je odvozen od . Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a přepíše následující metody pro sestavení továren spojených s naší vazbou.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Obsahuje také členy pro `BindingElement` klonování a vrácení našeho schématu (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>Testovací konzola WSE TCP  
 Testovací kód pro použití tohoto přenosu vzorku je k dispozici v TestCode.cs. Následující pokyny ukazují, jak nastavit `TcpSyncStockService` ukázku WSE.  
  
 Testovací kód vytvoří vlastní vazbu, která používá `WseTcpTransport` MTOM jako kódování a jako přenos. Také nastaví AddressingVersion být v souladu s WSE 3.0, jak je znázorněno v následujícím kódu.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Skládá se ze dvou testů – jeden test nastaví zadávaného klienta pomocí kódu generovaného z WSE 3.0 WSDL. Druhý test používá WCF jako klienta i server odesíláním zpráv přímo nad kanálem API.  
  
 Při spuštění ukázky se očekává následující výstup.  
  
 Klient:  
  
```console  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 Server:  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li spustit tuto ukázku, musíte mít [nainstalovánvylepšení webových služeb (WSE) 3.0 pro microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) a ukázku WSE. `TcpSyncStockService`
  
> [!NOTE]
> Vzhledem k tomu, že služba WSE 3.0 není v `TcpSyncStockService` systému Windows Server 2008 podporována, nelze v tomto operačním systému nainstalovat ani spustit ukázku.  
  
1. Po instalaci `TcpSyncStockService` ukázky postupujte takto:  
  
    1. Otevřete `TcpSyncStockService` v sadě Visual Studio (Všimněte si, že ukázka TcpSyncStockService je nainstalována s WSE 3.0. Není součástí kódu této ukázky).  
  
    2. Nastavte projekt Služby StockService jako počáteční projekt.  
  
    3. Otevřete StockService.cs v projektu StockService a zakomentujte atribut [Policy] ve `StockService` třídě. Tím zakážete zabezpečení z ukázky. Zatímco WCF můžete spolupracovat s WSE 3.0 zabezpečené koncové body, zabezpečení je zakázáno, aby tato ukázka zaměřená na vlastní přenos TCP.  
  
    4. Stisknutím klávesy F5 spusťte tlačítko `TcpSyncStockService`. Služba se spustí v novém okně konzoly.  
  
    5. Otevřete tuto ukázku přenosu protokolu TCP v sadě Visual Studio.  
  
    6. Aktualizujte proměnnou "hostname" v TestCode.cs tak, aby odpovídala názvu počítače se `TcpSyncStockService`systémem .  
  
    7. Stisknutím klávesy F5 spusťte vzorek přenosu Protokolu TCP.  
  
    8. Klient testu přenosu Protokolu TCP se spustí v nové konzoli. Klient požaduje kurzy akcií ze služby a potom zobrazí výsledky v okně konzoly.  
