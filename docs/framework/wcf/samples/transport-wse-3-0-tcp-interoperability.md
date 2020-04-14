---
title: 'Přenos: Součinnost TCP ve WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: f799f3b6968f31472acc7752846bab34351648db
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278896"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="2408f-102">Přenos: Součinnost TCP ve WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="2408f-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="2408f-103">Ukázka přenosu interoperability protokolu WSE 3.0 TCP ukazuje, jak implementovat duplexní relaci Protokolu TCP jako vlastní přenos WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="2408f-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="2408f-104">Také ukazuje, jak můžete použít rozšiřitelnost vrstvy kanálu k rozhraní přes drát s existujícími nasazenými systémy.</span><span class="sxs-lookup"><span data-stu-id="2408f-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="2408f-105">Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:</span><span class="sxs-lookup"><span data-stu-id="2408f-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="2408f-106">Počínaje soketem TCP vytvořte klientské a serverové <xref:System.ServiceModel.Channels.IDuplexSessionChannel> implementace, které používají rámování DIME k vymezení hranic zpráv.</span><span class="sxs-lookup"><span data-stu-id="2408f-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="2408f-107">Vytvořte továrnu kanálu, která se připojí ke službě WSE <xref:System.ServiceModel.Channels.IDuplexSessionChannel>TCP a odesílá zprávy zarámované přes s klienta.</span><span class="sxs-lookup"><span data-stu-id="2408f-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="2408f-108">Vytvořte naslouchací proces kanálu pro přijetí příchozích připojení TCP a vytvoření odpovídajících kanálů.</span><span class="sxs-lookup"><span data-stu-id="2408f-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="2408f-109">Ujistěte se, že všechny výjimky specifické pro síť <xref:System.ServiceModel.CommunicationException>jsou normalizovány na příslušnou odvozenou třídu .</span><span class="sxs-lookup"><span data-stu-id="2408f-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="2408f-110">Přidejte element vazby, který přidá vlastní přenos do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="2408f-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="2408f-111">Další informace naleznete v tématu [Přidání elementu vazby].</span><span class="sxs-lookup"><span data-stu-id="2408f-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="2408f-112">Vytváření kanálu iduplexsessionchannel</span><span class="sxs-lookup"><span data-stu-id="2408f-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="2408f-113">Prvním krokem při psaní WSE 3.0 TCP interoperability přenosu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> je vytvořit <xref:System.Net.Sockets.Socket>implementaci na vrcholu .</span><span class="sxs-lookup"><span data-stu-id="2408f-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="2408f-114">`WseTcpDuplexSessionChannel`pochází z <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="2408f-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="2408f-115">Logika odeslání zprávy se skládá ze dvou hlavních částí: (1) Kódování zprávy do bajtů a (2) rámování těchto bajtů a jejich odeslání na lince.</span><span class="sxs-lookup"><span data-stu-id="2408f-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="2408f-116">Kromě toho je přijata zámek tak, aby Send() volání zachovat iDuplexSessionChannel v pořadí záruky a tak, aby volání podkladového soketu jsou synchronizovány správně.</span><span class="sxs-lookup"><span data-stu-id="2408f-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="2408f-117">`WseTcpDuplexSessionChannel`používá <xref:System.ServiceModel.Channels.MessageEncoder> pro překlad do <xref:System.ServiceModel.Channels.Message> a a byte[].</span><span class="sxs-lookup"><span data-stu-id="2408f-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="2408f-118">Vzhledem k tomu, že se jedná o přenos, `WseTcpDuplexSessionChannel` je také zodpovědný za použití vzdálené adresy, která kanál byl nakonfigurován s.</span><span class="sxs-lookup"><span data-stu-id="2408f-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="2408f-119">`EncodeMessage`zapouzdřuje logiku pro tento převod.</span><span class="sxs-lookup"><span data-stu-id="2408f-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="2408f-120">Jakmile <xref:System.ServiceModel.Channels.Message> je kódován do bajtů, musí být přenášen na drátě.</span><span class="sxs-lookup"><span data-stu-id="2408f-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="2408f-121">To vyžaduje systém pro definování hranic zprávy.</span><span class="sxs-lookup"><span data-stu-id="2408f-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="2408f-122">WSE 3.0 používá verzi [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) jako protokol rámování.</span><span class="sxs-lookup"><span data-stu-id="2408f-122">WSE 3.0 uses a version of [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) as its framing protocol.</span></span> <span data-ttu-id="2408f-123">`WriteData`zapouzdřuje logiku rámování pro zalomení bajtu[] do sady záznamů DIME.</span><span class="sxs-lookup"><span data-stu-id="2408f-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="2408f-124">Logika pro příjem zpráv je podobná.</span><span class="sxs-lookup"><span data-stu-id="2408f-124">The logic for receiving messages is similar.</span></span> <span data-ttu-id="2408f-125">Hlavní složitost je zpracování skutečnost, že čtení soketu může vrátit méně bajtů, než byly požadovány.</span><span class="sxs-lookup"><span data-stu-id="2408f-125">The main complexity is handling the fact that a socket read can return fewer bytes than were requested.</span></span> <span data-ttu-id="2408f-126">Chcete-li přijmout `WseTcpDuplexSessionChannel` zprávu, přečte bajty z drátu, dekóduje rámdime a pak použije <xref:System.ServiceModel.Channels.MessageEncoder> <xref:System.ServiceModel.Channels.Message>pro přeměnu bajta na .</span><span class="sxs-lookup"><span data-stu-id="2408f-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="2408f-127">Základna `WseTcpDuplexSessionChannel` předpokládá, že obdrží připojený soket.</span><span class="sxs-lookup"><span data-stu-id="2408f-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="2408f-128">Základní třída zpracovává vypnutí soketu.</span><span class="sxs-lookup"><span data-stu-id="2408f-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="2408f-129">Existují tři místa, která rozhraní s uzavření mašketu:</span><span class="sxs-lookup"><span data-stu-id="2408f-129">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="2408f-130">OnAbort -- zavřete soket ungracefully (hard close).</span><span class="sxs-lookup"><span data-stu-id="2408f-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="2408f-131">On[Begin]Close -- zavřete zásuvku elegantně (soft close).</span><span class="sxs-lookup"><span data-stu-id="2408f-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="2408f-132">Relace. CloseOutputSession -- vypnutí odchozí datový proud (polovina zavřít).</span><span class="sxs-lookup"><span data-stu-id="2408f-132">session.CloseOutputSession -- shut down the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="2408f-133">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="2408f-133">Channel Factory</span></span>  
 <span data-ttu-id="2408f-134">Dalším krokem při psaní přenosu TCP je <xref:System.ServiceModel.Channels.IChannelFactory> vytvoření implementace pro klientské kanály.</span><span class="sxs-lookup"><span data-stu-id="2408f-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="2408f-135">`WseTcpChannelFactory`pochází z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<iDuplexSessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="2408f-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="2408f-136">Jedná se o továrnu, která přepíše `OnCreateChannel` vyrábět klientské kanály.</span><span class="sxs-lookup"><span data-stu-id="2408f-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="2408f-137">`ClientWseTcpDuplexSessionChannel`přidá logiku `WseTcpDuplexSessionChannel` k základně pro připojení `channel.Open` k serveru TCP v čase.</span><span class="sxs-lookup"><span data-stu-id="2408f-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="2408f-138">Nejprve je název hostitele přeložen na adresu IP, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2408f-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="2408f-139">Potom je název hostitele připojen k první dostupné IP adrese ve smyčce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2408f-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="2408f-140">Jako součást smlouvy kanálu jsou zabaleny všechny výjimky specifické `SocketException` <xref:System.ServiceModel.CommunicationException>pro doménu, například v .</span><span class="sxs-lookup"><span data-stu-id="2408f-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="2408f-141">Naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="2408f-141">Channel Listener</span></span>  
 <span data-ttu-id="2408f-142">Dalším krokem při psaní přenosu TCP je <xref:System.ServiceModel.Channels.IChannelListener> vytvoření implementace pro příjem serverových kanálů.</span><span class="sxs-lookup"><span data-stu-id="2408f-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="2408f-143">`WseTcpChannelListener`odvozuje <xref:System.ServiceModel.Channels.ChannelListenerBase> \<z IDuplexSessionChannel> a přepíše On[Begin]Open a On[Begin]Close řídit životnost jeho naslouchání soketu.</span><span class="sxs-lookup"><span data-stu-id="2408f-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="2408f-144">V OnOpen je vytvořen soket pro poslech na IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="2408f-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="2408f-145">Pokročilejší implementace můžete vytvořit druhý soket pro poslech na IPv6 také.</span><span class="sxs-lookup"><span data-stu-id="2408f-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="2408f-146">Mohou také povolit ip adresu, která má být zadána v názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="2408f-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="2408f-147">Při přijetí nového soketu je inicializován serverový kanál s tímto soketem.</span><span class="sxs-lookup"><span data-stu-id="2408f-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="2408f-148">Všechny vstupy a výstupy jsou již implementovány v základní třídě, takže tento kanál je zodpovědný za inicializaci soketu.</span><span class="sxs-lookup"><span data-stu-id="2408f-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="2408f-149">Přidání prvku vazby</span><span class="sxs-lookup"><span data-stu-id="2408f-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="2408f-150">Nyní továrny a kanály jsou sestaveny, musí být vystaveny ServiceModel runtime prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="2408f-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="2408f-151">Vazba je kolekce elementů vazby, která představuje zásobník komunikace přidružené k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="2408f-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="2408f-152">Každý prvek v zásobníku je reprezentován elementem vazby.</span><span class="sxs-lookup"><span data-stu-id="2408f-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="2408f-153">Ve vzorku je `WseTcpTransportBindingElement`prvek vazby , <xref:System.ServiceModel.Channels.TransportBindingElement>který je odvozen od .</span><span class="sxs-lookup"><span data-stu-id="2408f-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="2408f-154">Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a přepíše následující metody pro sestavení továren spojených s naší vazbou.</span><span class="sxs-lookup"><span data-stu-id="2408f-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="2408f-155">Obsahuje také členy pro `BindingElement` klonování a vrácení našeho schématu (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="2408f-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="2408f-156">Testovací konzola WSE TCP</span><span class="sxs-lookup"><span data-stu-id="2408f-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="2408f-157">Testovací kód pro použití tohoto přenosu vzorku je k dispozici v TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="2408f-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="2408f-158">Následující pokyny ukazují, jak nastavit `TcpSyncStockService` ukázku WSE.</span><span class="sxs-lookup"><span data-stu-id="2408f-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="2408f-159">Testovací kód vytvoří vlastní vazbu, která používá `WseTcpTransport` MTOM jako kódování a jako přenos.</span><span class="sxs-lookup"><span data-stu-id="2408f-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="2408f-160">Také nastaví AddressingVersion být v souladu s WSE 3.0, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2408f-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="2408f-161">Skládá se ze dvou testů – jeden test nastaví zadávaného klienta pomocí kódu generovaného z WSE 3.0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="2408f-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="2408f-162">Druhý test používá WCF jako klienta i server odesíláním zpráv přímo nad kanálem API.</span><span class="sxs-lookup"><span data-stu-id="2408f-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="2408f-163">Při spuštění ukázky se očekává následující výstup.</span><span class="sxs-lookup"><span data-stu-id="2408f-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="2408f-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="2408f-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="2408f-165">Server:</span><span class="sxs-lookup"><span data-stu-id="2408f-165">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="2408f-166">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2408f-166">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2408f-167">Chcete-li spustit tuto ukázku, musíte mít [nainstalovánvylepšení webových služeb (WSE) 3.0 pro microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) a ukázku WSE. `TcpSyncStockService`</span><span class="sxs-lookup"><span data-stu-id="2408f-167">To run this sample, you must have [Web Services Enhancements (WSE) 3.0 for Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) and the WSE `TcpSyncStockService` sample installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2408f-168">Vzhledem k tomu, že služba WSE 3.0 není v `TcpSyncStockService` systému Windows Server 2008 podporována, nelze v tomto operačním systému nainstalovat ani spustit ukázku.</span><span class="sxs-lookup"><span data-stu-id="2408f-168">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="2408f-169">Po instalaci `TcpSyncStockService` ukázky postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="2408f-169">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="2408f-170">Otevřete `TcpSyncStockService` v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2408f-170">Open the `TcpSyncStockService` in Visual Studio.</span></span> <span data-ttu-id="2408f-171">(Ukázka TcpSyncStockService je nainstalována s WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="2408f-171">(The TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="2408f-172">Není součástí kódu tohoto vzorku.)</span><span class="sxs-lookup"><span data-stu-id="2408f-172">It is not part of this sample's code.)</span></span>  
  
    2. <span data-ttu-id="2408f-173">Nastavte projekt Služby StockService jako počáteční projekt.</span><span class="sxs-lookup"><span data-stu-id="2408f-173">Set the StockService project as the start-up project.</span></span>  
  
    3. <span data-ttu-id="2408f-174">Otevřete StockService.cs v projektu StockService a zakomentujte atribut [Policy] ve `StockService` třídě.</span><span class="sxs-lookup"><span data-stu-id="2408f-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="2408f-175">Tím zakážete zabezpečení z ukázky.</span><span class="sxs-lookup"><span data-stu-id="2408f-175">This disables security from the sample.</span></span> <span data-ttu-id="2408f-176">Zatímco WCF můžete spolupracovat s WSE 3.0 zabezpečené koncové body, zabezpečení je zakázáno, aby tato ukázka zaměřená na vlastní přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="2408f-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="2408f-177">Stisknutím klávesy F5 spusťte tlačítko `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="2408f-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="2408f-178">Služba se spustí v novém okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="2408f-178">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="2408f-179">Otevřete tuto ukázku přenosu protokolu TCP v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2408f-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="2408f-180">Aktualizujte proměnnou "hostname" v TestCode.cs tak, aby odpovídala názvu počítače se `TcpSyncStockService`systémem .</span><span class="sxs-lookup"><span data-stu-id="2408f-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="2408f-181">Stisknutím klávesy F5 spusťte vzorek přenosu Protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="2408f-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="2408f-182">Klient testu přenosu Protokolu TCP se spustí v nové konzoli.</span><span class="sxs-lookup"><span data-stu-id="2408f-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="2408f-183">Klient požaduje kurzy akcií ze služby a potom zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="2408f-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
