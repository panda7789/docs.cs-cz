---
title: 'Přenos: Interoperabilita TCP ve WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 9b73f9ef93ebfabf2b1c39363bd64785e2892956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941036"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Přenos: Interoperabilita TCP ve WSE 3.0
Ukázka přenosu interoperability TCP v WSE 3,0 ukazuje, jak implementovat relaci duplexního připojení TCP jako vlastní přenos Windows Communication Foundation (WCF). Také ukazuje, jak můžete použít rozšiřitelnost vrstvy kanálu na rozhraní s existujícími nasazenými systémy. Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:  
  
1. Počínaje soketem TCP vytvořte implementace klientů a serverů systému <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , které používají rámce DIME k vymezení hranic zpráv.  
  
2. Vytvořte továrnu kanálu, který se připojí ke službě WSE TCP a pošle v rámci klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s rámcové zprávy.  
  
3. Vytvořte naslouchací proces kanálu, který přijme příchozí připojení TCP a vytvoří odpovídající kanály.  
  
4. Zajistěte, aby všechny výjimky specifické pro síť byly normalizovány na příslušnou odvozenou třídu třídy <xref:System.ServiceModel.CommunicationException>.  
  
5. Přidejte prvek vazby, který přidá vlastní přenos do zásobníku kanálů. Další informace naleznete v tématu [přidání prvku vazby].  
  
## <a name="creating-iduplexsessionchannel"></a>Vytváření IDuplexSessionChannel  
 Prvním krokem při psaní přenosů mezi <xref:System.ServiceModel.Channels.IDuplexSessionChannel> WSE 3,0 TCP je vytvoření implementace na začátku. <xref:System.Net.Sockets.Socket> `WseTcpDuplexSessionChannel`je odvozen z <xref:System.ServiceModel.Channels.ChannelBase>. Logika odeslání zprávy se skládá ze dvou hlavních částí: (1) zakódování zprávy do bajtů a (2) zařadí do rámců tyto bajty a odesílají je na kabel.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Kromě toho se povede zámek, aby volání Send () zachovala záruku IDuplexSessionChannel a aby se správně synchronizoval volání základního soketu.  
  
 `WseTcpDuplexSessionChannel`používá pro překlad typu <xref:System.ServiceModel.Channels.Message> a na Byte []. <xref:System.ServiceModel.Channels.MessageEncoder> Vzhledem k tomu, že se `WseTcpDuplexSessionChannel` jedná o přenos, zodpovídá taky za použití vzdálené adresy, se kterou byl kanál nakonfigurovaný. `EncodeMessage`Zapouzdřuje logiku pro tento převod.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message> Jakmile je kód kódovaný do bajtů, je nutné ho přenést na síťový kabel. To vyžaduje systém pro definování hranic zprávy. WSE 3,0 používá jako svůj protokol rámců verzi [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) . `WriteData`Zapouzdřuje logiku rámců a zabalí bajt [] do sady záznamů DIME.  
  
 Logika pro příjem zpráv je velmi podobná. Hlavní složitost zpracovává fakt, že čtení soketu může vracet méně bajtů, než bylo vyžádáno. Chcete-li přijmout zprávu `WseTcpDuplexSessionChannel` , přečte bajty z přenosů, dekóduje rámce DIME a pak <xref:System.ServiceModel.Channels.MessageEncoder> použije příkaz pro zapnutí <xref:System.ServiceModel.Channels.Message>bajtu [] na.  
  
 Základní `WseTcpDuplexSessionChannel` předpokládá, že obdrží připojený soket. Základní třída zpracovává vypnutí soketu. Rozhraní se uzávěrkou soketu má tři místa:  
  
- Přerušení – neúspěšné zavření soketu (tvrdý uzávěr)  
  
- Zapnuto [begin] Close--uzavřete soket korektně (měkký zavření).  
  
- jednání. Vyvolání třídy CloseOutputSession – vypnutí odchozího datového proudu (polovina zavření).  
  
## <a name="channel-factory"></a>Vytvoření postupu kanálu  
 Dalším krokem při psaní přenosu protokolu TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály.  
  
- `WseTcpChannelFactory`je odvozen z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. Jedná se o továrnu, `OnCreateChannel` která přepisuje vytváření klientských kanálů.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`Přidá logiku do základu `WseTcpDuplexSessionChannel` pro připojení k serveru TCP v `channel.Open` čase. Nejprve je název hostitele přeložen na IP adresu, jak je znázorněno v následujícím kódu.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Pak je název hostitele připojen k první dostupné IP adrese ve smyčce, jak je znázorněno v následujícím kódu.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- `SocketException` V rámci kontraktu kanálu jsou všechny výjimky specifické pro doménu zabaleny, například v <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Naslouchací proces kanálu  
 Dalším krokem při psaní přenosu protokolu TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro příjem serverových kanálů.  
  
- `WseTcpChannelListener`je odvozen z <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > a potlačení na [begin] Open a na [begin] blízko pro řízení životnosti jejího naslouchajícího soketu. V otevřeném se vytvoří soket pro naslouchání na IP_ANY. Pokročilejší implementace mohou vytvořit druhý soket pro naslouchání také na protokolu IPv6. Můžou taky umožňovat zadání IP adresy v názvu hostitele.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Při přijetí nového soketu se na tomto soketu inicializuje serverový kanál. Všechny vstupy a výstupy jsou již implementovány v základní třídě, takže tento kanál je zodpovědný za inicializaci soketu.  
  
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Teď, když jsou továrny a kanály sestavené, musí být zpřístupněny modulu runtime ServiceModel prostřednictvím vazby. Vazba je kolekce elementů vazby, které představují komunikační zásobník přidružený k adrese služby. Každý prvek v zásobníku je reprezentován prvkem vazby.  
  
 V ukázce je prvek vazby, který je `WseTcpTransportBindingElement`odvozen z. <xref:System.ServiceModel.Channels.TransportBindingElement> Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a Přepisuje následující metody pro sestavování továrn přidružených k naší vazbě.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Obsahuje také členy pro klonování `BindingElement` a vracení našeho schématu (WSE. TCP).  
  
## <a name="the-wse-tcp-test-console"></a>Konzola testu WSE TCP  
 Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v TestCode.cs. Následující pokyny ukazují, jak nastavit ukázku WSE `TcpSyncStockService` .  
  
 Testovací kód vytvoří vlastní vazbu, která používá MTOM jako kódování a `WseTcpTransport` jako přenos. Také nastaví verze AddressingVersion tak, aby byl vyhovující WSE 3,0, jak je znázorněno v následujícím kódu.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Skládá se ze dvou testů – jeden test nastaví typového klienta pomocí kódu vygenerovaného z WSE 3,0 WSDL. Druhý test používá WCF jako klienta i server tím, že odesílá zprávy přímo nad rozhraní API kanálu.  
  
 Při spuštění ukázky se očekává následující výstup.  
  
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
  
 WebServer  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pro spuštění této ukázky musíte mít WSE 3,0 a nainstalovanou ukázku WSE `TcpSyncStockService` . WSE 3,0 si můžete stáhnout [z webu MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
> Vzhledem k tomu, že WSE 3,0 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]není podporován na, nelze nainstalovat nebo `TcpSyncStockService` spustit ukázku v tomto operačním systému.  
  
1. Po instalaci `TcpSyncStockService` ukázky postupujte následovně:  
  
    1. `TcpSyncStockService` Otevřete v aplikaci Visual Studio (Všimněte si, že je nainstalovaná ukázka TcpSyncStockService s WSE 3,0. Není součástí tohoto ukázkového kódu.  
  
    2. Nastavte projekt StockService jako spouštěcí projekt.  
  
    3. Otevřete StockService.cs v projektu StockService a odkomentujte atribut `StockService` [Policy] třídy. Tím se zakáže zabezpečení z ukázky. I když může WCF spolupracovat s WSE 3,0 zabezpečenými koncovými body, zabezpečení je zakázané, aby se tato ukázka zaměřila na vlastní přenos TCP.  
  
    4. Stisknutím klávesy F5 spusťte `TcpSyncStockService`. Služba se spustí v novém okně konzoly.  
  
    5. Otevřete tuto ukázku přenosu TCP v aplikaci Visual Studio.  
  
    6. Aktualizujte proměnnou hostname v TestCode.cs tak, aby odpovídala názvu počítače, na `TcpSyncStockService`kterém je spuštěný.  
  
    7. Stisknutím klávesy F5 spusťte ukázku přenosu protokolu TCP.  
  
    8. Klient TCP Transport test se spustí v nové konzole. Klient požaduje od služby skladové nabídky a potom zobrazí výsledky v okně konzoly.  
