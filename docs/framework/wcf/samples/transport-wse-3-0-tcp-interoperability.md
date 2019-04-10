---
title: 'Přenos: Interoperabilita TCP ve WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: cc483e44e625534d87ea94e84fc984f0aff880f9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324211"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Přenos: Interoperabilita TCP ve WSE 3.0
Ukázka přenosu interoperabilita TCP ve WSE 3.0 ukazuje, jak implementovat duplexní relace TCP jako vlastní přenosu Windows Communication Foundation (WCF). Také ukazuje, jak můžete použít rozšíření vrstvy kanálu rozhraní přenosu s existujícími systémy nasazené. Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:  
  
1. Počínaje soket TCP vytvořit klienta a serveru implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , které používají od sebe odděluje hranice zprávy DIME rámců.  
  
2. Vytvoření postupu kanálu, který se připojí ke službě WSE TCP a odesílá zprávy orámované přes klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3. Vytvořte naslouchací proces kanálu přijímat příchozí připojení protokolu TCP a vytvořit odpovídající kanály.  
  
4. Ujistěte se, že všechny výjimky pro konkrétní sítě jsou normalizovány na příslušné třídy odvozené z <xref:System.ServiceModel.CommunicationException>.  
  
5. Přidejte prvek vazby, který přidá vlastní přenosu do zásobníku kanálu. Další informace najdete v tématu [přidání prvku vazby].  
  
## <a name="creating-iduplexsessionchannel"></a>Vytváření IDuplexSessionChannel  
 Prvním krokem při psaní přenosu Interoperability TCP ve WSE 3.0, je vytvořit implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> nahoře <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` Je odvozen od <xref:System.ServiceModel.Channels.ChannelBase>. Logiku odesílání zprávy se skládá ze dvou hlavních částí: (1) do bajtů a (2) rámců těchto bajtů a poslat mu na lince kódování zprávy.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Kromě toho se zámek používá tak, aby volání Send() zachovat záruku IDuplexSessionChannel v pořadí a tak, aby volání do základního soketu se synchronizují správně.  
  
 `WseTcpDuplexSessionChannel` používá <xref:System.ServiceModel.Channels.MessageEncoder> pro převod <xref:System.ServiceModel.Channels.Message> do a z byte []. Protože se jedná přenos `WseTcpDuplexSessionChannel` zodpovídá také za použití vzdálenou adresu, který byl nakonfigurován kanál. `EncodeMessage` zapouzdří logiku pro tento převod.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Jakmile <xref:System.ServiceModel.Channels.Message> je zakódován do bajtů, je třeba přenést na lince. To vyžaduje systém pro definování hranice zpráv. WSE 3.0 používá verzi [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) jako protokol pro jeho rámce. `WriteData` zapouzdří logiku rámce při zabalení byte [] do sady záznamů DIME.  
  
 Logika pro příjem zpráv je velmi podobné. Hlavní složitost zpracovává skutečnost, že soketu čtení může vrátit méně bajtů než bylo požadováno. Při příjmu zprávy, `WseTcpDuplexSessionChannel` přečte bajtů vypnutí přenosu, dekóduje DIME rámce a poté použije <xref:System.ServiceModel.Channels.MessageEncoder> při zapínání byte [] do <xref:System.ServiceModel.Channels.Message>.  
  
 Základní `WseTcpDuplexSessionChannel` předpokládá, že bude dostávat připojený soket. Základní třída zpracovává vypnutí soketu. Existují tři míst, na které rozhraní se uzavření soketu:  
  
-   OnAbort – zavřete soketu ungracefully (pevné Zavřít).  
  
-   Na [Begin] zavřete – soketu řádně uzavřít (měkké Zavřít).  
  
-   relace. CloseOutputSession – vypnutí výstupní datový proud (poloviční Zavřít).  
  
## <a name="channel-factory"></a>Vytvoření postupu kanálu  
 Dalším krokem při psaní přenosu protokolu TCP je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klientů.  
  
-   `WseTcpChannelFactory` je odvozen od <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. Je objekt factory, který přepíše `OnCreateChannel` k vytvoření kanálů klienta.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` Přidá do základní logiku `WseTcpDuplexSessionChannel` pro připojení k serveru TCP `channel.Open` čas. Nejprve je přeložit na IP adresu, název hostitele, jak je znázorněno v následujícím kódu.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Potom název hostitele je připojen k první dostupná IP adresa ve smyčce, jak je znázorněno v následujícím kódu.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Jako součást smlouvy channel jakékoli specifického pro doménu výjimky jsou obaleny, jako například `SocketException` v <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Modul pro naslouchání kanálu  
 Dalším krokem při psaní přenosu protokolu TCP je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelListener> pro příjem kanálů.  
  
-   `WseTcpChannelListener` je odvozen od <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > a přepsání při otevření [Begin] a [Begin] Zavřít řídit dobu života jeho naslouchání soketu. V při otevření je tak, aby naslouchala na IP_ANY vytvořili soketu. Implementace rozšířené můžete vytvořit druhý soketu také poslouchat protokol IPv6. Můžete povolit také IP adresu, která zadaný v názvu hostitele.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Při přijetí nového soketu kanálu serveru je inicializována s tento soket. Vstup a výstup je již implementováno základní třídy, takže tento kanál zodpovídá za inicializaci soketu.  
  
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Teď, když jsou vytvořeny objekty pro vytváření a kanály, se musí se zveřejnit pro modul runtime ServiceModel prostřednictvím vazby. Vazba je kolekce elementů vazby, který představuje komunikační balík přidružené k adrese služby. Každý prvek v zásobníku je reprezentován element vazby.  
  
 V ukázce je element vazby `WseTcpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>. Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a přepíše následující metody k vytváření továrny spojené s využitím naší vazby.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>TCP ve WSE testovací konzole  
 Testovací kód pro tento přenos ukázkový používání je k dispozici v TestCode.cs. Následující pokyny ukazují, jak nastavit WSE `TcpSyncStockService` vzorku.  
  
 Testovací kód vytvoří vlastní vazby, který používá jako kódování MTOM a `WseTcpTransport` přenos. Rovněž nastaví verze AddressingVersion být podmínky ve WSE 3.0, jak je znázorněno v následujícím kódu.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Skládá se ze dvou testy – jeden test nastaví zadaný kód generovaný z WSE 3.0 WSDL pomocí klienta. Druhý test používá WCF jako klient a server odesíláním zpráv přímo přes kanál rozhraní API.  
  
 Při spuštění ukázky, očekává se následující výstup.  
  
 Klient:  
  
```  
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
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Pro tuto ukázku spustit, je zapotřebí WSE 3.0 a WSE `TcpSyncStockService` ukázka nainstalované. Můžete si stáhnout [WSE 3.0 z webu MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Protože WSE 3.0 není podporována na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nemůžou instalovat ani spouštět `TcpSyncStockService` ukázka v tomto operačním systému.  
  
1. Po instalaci `TcpSyncStockService` ukázkový, postupujte takto:  
  
    1.  Otevřít `TcpSyncStockService` v sadě Visual Studio (Všimněte si, že ukázky TcpSyncStockService se instaluje s WSE 3.0. Není součástí této ukázky kódu).  
  
    2.  Nastavte StockService projekt jako spouštěný projekt.  
  
    3.  Otevření StockService.cs v projektu StockService a Odkomentujte atribut [zásad] na `StockService` třídy. Zakáže zabezpečení z ukázky. Zatímco WCF můžou spolupracovat s WSE 3.0 zabezpečené koncové body, zabezpečení je zakázané, aby zachovat tuto ukázku, zaměřuje na vlastní přenosu protokolu TCP.  
  
    4.  Stisknutím klávesy F5 pro spuštění `TcpSyncStockService`. Služba se spustí v novém okně konzoly.  
  
    5.  Tato ukázka přenosu protokolu TCP otevřete v sadě Visual Studio.  
  
    6.  Aktualizovat proměnnou "hostname" v TestCode.cs tak, aby odpovídaly názvu počítač se systémem `TcpSyncStockService`.  
  
    7.  Stisknutím klávesy F5 spusťte ukázku přenosu protokolu TCP.  
  
    8.  Testovací klient přenosu protokolu TCP začíná v nové konzole. Klient vyžádá akcií ze služby a potom zobrazí výsledky v okně konzoly.  
