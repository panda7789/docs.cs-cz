---
title: 'Přenos: Součinnost TCP ve WSE 3.0'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ce948a9239e7a8171424fa9f1cf0fa8624d0156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="transport-wse-30-tcp-interoperability"></a>Přenos: Součinnost TCP ve WSE 3.0
Ukázka WSE 3.0 TCP interoperabilita přenosu ukazuje, jak implementovat duplexní relace TCP vlastní přenos Windows Communication Foundation (WCF). Také ukazuje, jak můžete použít rozšíření vrstvy kanálu rozhraní přenášených v síti s existující nasazené systémy. Následující kroky ukazují, jak vytvořit toto vlastní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosu:  
  
1.  Počínaje soket TCP vytvořit klientských a serverových implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , pomocí DIME rámců zobrazit hranice zpráv.  
  
2.  Vytvoření kanálu, který připojuje ke službě WSE TCP a odesílá rámcová zprávy přes klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Vytvořte naslouchací proces kanálu pro příjem příchozích připojení TCP a vytvoří odpovídající kanály.  
  
4.  Ujistěte se, že jsou všechny výjimky sítě normalizovány na příslušné odvozené třídy z <xref:System.ServiceModel.CommunicationException>.  
  
5.  Přidáte element vazby, který přidá vlastní přenos do zásobníku kanálu. Další informace najdete v tématu [přidávání Element vazby].  
  
## <a name="creating-iduplexsessionchannel"></a>Vytváření IDuplexSessionChannel  
 Prvním krokem při psaní WSE 3.0 TCP interoperabilita přenosu je vytvoření implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` odvozená z <xref:System.ServiceModel.Channels.ChannelBase>. Logiku odesílání zprávy se skládá ze dvou částí hlavní: (1) do bajtů a (2) formulování těchto bajtů a je pošlete přenášený kódování zprávy.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Kromě toho zámek se provede tak, aby volání Send() zachovat záruky IDuplexSessionChannel v daném pořadí a tak, aby správně synchronizovaní volání základní soketu.  
  
 `WseTcpDuplexSessionChannel` používá <xref:System.ServiceModel.Channels.MessageEncoder> pro převod <xref:System.ServiceModel.Channels.Message> do a z byte []. Protože je na přenos `WseTcpDuplexSessionChannel` zodpovídá taky za použití nakonfigurovaný kanál pomocí vzdálené adresy. `EncodeMessage` zapouzdří logiku pro tento převod.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Jednou <xref:System.ServiceModel.Channels.Message> je zakódován do bajtů, je třeba přenést v drátové síti. To vyžaduje systém pro definování hranice zpráv. WSE 3.0 používá verzi [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) jako jeho rámcovacích protokol. `WriteData` zapouzdří logice rámcovacích zabalit byte [] do sady záznamů DIME.  
  
 Logika pro příjem zprávy je velmi podobné. Hlavní složitost zpracovává fakt, že soket čtení může vrátit menší počet bajtů, než se požadovaly. Pro příjem zprávy, `WseTcpDuplexSessionChannel` čte bajtů vypnout sítě, dekóduje rámcovacích DIME a pak použije <xref:System.ServiceModel.Channels.MessageEncoder> pro zapnutí byte [] do <xref:System.ServiceModel.Channels.Message>.  
  
 Základní `WseTcpDuplexSessionChannel` předpokládá obdrží připojené soketu. Základní třída zpracovává vypnutí soketu. Existují tři míst, na které rozhraní s uzavření soketu:  
  
-   OnAbort – zavřete soketu ungracefully (pevné Zavřít).  
  
-   Na [Begin] zavřete – zavřete soket řádně (logicky Zavřít).  
  
-   relace. CloseOutputSession – vypnutí výstupní datový proud (poloviční Zavřít).  
  
## <a name="channel-factory"></a>Vytvoření postupu kanálu  
 Dalším krokem při psaní přenos TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klienta kanály.  
  
-   `WseTcpChannelFactory` odvozená z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. Je objekt factory, který přepíše `OnCreateChannel` k vytvoření klienta kanály.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` Přidá do základní logiku `WseTcpDuplexSessionChannel` pro připojení k serveru TCP `channel.Open` čas. Nejprve je přeložit na IP adresu, název hostitele, jak je znázorněno v následujícím kódu.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Potom název hostitele je připojený k první dostupná IP adresa ve smyčce, jak je znázorněno v následujícím kódu.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   V rámci kanálu kontraktu, všechny výjimky, specifické pro doménu jsou zabalená, jako například `SocketException` v <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Naslouchací proces kanálu  
 Dalším krokem při psaní přenos TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro přijetí serveru kanály.  
  
-   `WseTcpChannelListener` odvozená z <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > a přepsání na otevřete [Begin] a [Begin] zavřete na řídí životnost jeho naslouchání soketu. V při otevření je tak, aby naslouchala na IP_ANY vytvořili soketu. Pokročilejší implementace můžete vytvořit druhý soketu také naslouchat na IPv6. Můžete povolit také IP adresu, kterou být zadaný v názvu hostitele.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Při přijetí nové soketu se server kanál, který je inicializován tento soketu. Všechny vstupní a výstupní je již implementováno v základní třídě, takže tento kanál zodpovídá za inicializaci soketu.  
  
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Teď, když jsou vytvořeny objekty pro vytváření a kanály, se musí se zveřejnit pro modul runtime ServiceModel prostřednictvím vazbu. Vazba je kolekci elementů vazby, která reprezentuje komunikačního balíku přidružená adresa služby. Každý prvek v zásobníku je reprezentována prvku vazby.  
  
 V ukázce je prvku vazby `WseTcpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>. Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a přepíše následující metody pro vytvoření objektů Factory související s naše vazby.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>Konzole testovací WSE TCP  
 Testovacího kódu pro použití přenosu Tato ukázka je dostupná v TestCode.cs. Následující pokyny vám ukážou, jak nastavit WSE `TcpSyncStockService` ukázka.  
  
 Testovací kód vytvoří vlastní vazby, který používá jako kódování MTOM a `WseTcpTransport` jako přenosu. Je také nastaví třídu AddressingVersion tak, aby se shoduje s WSE 3.0, jak je znázorněno v následujícím kódu.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Obsahuje dva testy – jeden test nastaví typový klient pomocí kód, který vygenerovala z schématu WSDL WSE 3.0. Druhý test používá [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jako klient a server tak, že odesílání zpráv přímo na základě kanál rozhraní API.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pokud chcete tuto ukázku spustit, musíte mít WSE 3.0 a WSE `TcpSyncStockService` ukázka nainstalována. Můžete si stáhnout [WSE 3.0 z webu MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Protože WSE 3.0 není podporována na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nemůžou instalovat ani spouštět `TcpSyncStockService` ukázku v tomto operačním systému.  
  
1.  Po instalaci `TcpSyncStockService` ukázkové, postupujte takto:  
  
    1.  Otevřete `TcpSyncStockService` v sadě Visual Studio (Všimněte si, že ukázka TcpSyncStockService je instalován s WSE 3.0. Není součástí této ukázce kódu).  
  
    2.  Nastavte projekt StockService jako počáteční projekt.  
  
    3.  Otevřete StockService.cs v projektu StockService a Odkomentujte atribut [zásad] na `StockService` třídy. To zakáže zabezpečení od vzorku. Při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] můžou spolupracovat s WSE 3.0 zabezpečené koncové body, aby tato ukázka se zaměřuje na vlastní přenos TCP je zakázána zabezpečení.  
  
    4.  Stisknutím klávesy F5 spusťte `TcpSyncStockService`. Služba se spustí v nové okno konzoly.  
  
    5.  Tato ukázka přenos TCP otevřete v sadě Visual Studio.  
  
    6.  Aktualizujte proměnné "název hostitele" v TestCode.cs tak, aby odpovídaly názvu počítač se systémem `TcpSyncStockService`.  
  
    7.  Stisknutím klávesy F5 spusťte ukázkové přenos TCP.  
  
    8.  Spustí se v nové konzole testovacího klienta přenos TCP. Klient požaduje akcií ze služby a potom zobrazí výsledky v okna konzoly.  
  
## <a name="see-also"></a>Viz také
