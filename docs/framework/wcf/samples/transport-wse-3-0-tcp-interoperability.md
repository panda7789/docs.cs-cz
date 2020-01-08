---
title: 'Přenos: Součinnost TCP ve WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 8166e1c378bc745eb8c9f37d6982642e754813cb
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544625"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="b79e9-102">Přenos: Součinnost TCP ve WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="b79e9-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="b79e9-103">Ukázka přenosu interoperability TCP v WSE 3,0 ukazuje, jak implementovat relaci duplexního připojení TCP jako vlastní přenos Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b79e9-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="b79e9-104">Také ukazuje, jak můžete použít rozšiřitelnost vrstvy kanálu na rozhraní s existujícími nasazenými systémy.</span><span class="sxs-lookup"><span data-stu-id="b79e9-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="b79e9-105">Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:</span><span class="sxs-lookup"><span data-stu-id="b79e9-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="b79e9-106">Počínaje soketem TCP vytvořte implementace klienta a serveru <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, které používají rámce DIME k vymezení hranic zpráv.</span><span class="sxs-lookup"><span data-stu-id="b79e9-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="b79e9-107">Vytvořte továrnu kanálu, který se připojí ke službě WSE TCP a odešle rámce v rámci klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="b79e9-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="b79e9-108">Vytvořte naslouchací proces kanálu, který přijme příchozí připojení TCP a vytvoří odpovídající kanály.</span><span class="sxs-lookup"><span data-stu-id="b79e9-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="b79e9-109">Zajistěte, aby všechny výjimky specifické pro síť byly normalizovány na příslušnou odvozenou třídu <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b79e9-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="b79e9-110">Přidejte prvek vazby, který přidá vlastní přenos do zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="b79e9-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="b79e9-111">Další informace naleznete v tématu [přidání prvku vazby].</span><span class="sxs-lookup"><span data-stu-id="b79e9-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="b79e9-112">Vytváření IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="b79e9-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="b79e9-113">Prvním krokem při psaní přenosu interoperability TCP v WSE 3,0 je vytvoření implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> nad <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="b79e9-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="b79e9-114">`WseTcpDuplexSessionChannel` jsou odvozeny z <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="b79e9-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="b79e9-115">Logika odeslání zprávy se skládá ze dvou hlavních částí: (1) kódování zprávy do bajtů a (2) zařadí do rámců tyto bajty a odesílají je na kabel.</span><span class="sxs-lookup"><span data-stu-id="b79e9-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="b79e9-116">Kromě toho se povede zámek, aby volání Send () zachovala záruku IDuplexSessionChannel a aby se správně synchronizoval volání základního soketu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="b79e9-117">`WseTcpDuplexSessionChannel` používá <xref:System.ServiceModel.Channels.MessageEncoder> pro překládání <xref:System.ServiceModel.Channels.Message> na Byte [] a z něj.</span><span class="sxs-lookup"><span data-stu-id="b79e9-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="b79e9-118">Vzhledem k tomu, že se jedná o přenos, `WseTcpDuplexSessionChannel` zodpovídá taky za použití vzdálené adresy, se kterou byl kanál nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="b79e9-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="b79e9-119">`EncodeMessage` zapouzdřuje logiku pro tento převod.</span><span class="sxs-lookup"><span data-stu-id="b79e9-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="b79e9-120">Jakmile je <xref:System.ServiceModel.Channels.Message> kódovaný do bajtů, musí se přenést na síťový kabel.</span><span class="sxs-lookup"><span data-stu-id="b79e9-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="b79e9-121">To vyžaduje systém pro definování hranic zprávy.</span><span class="sxs-lookup"><span data-stu-id="b79e9-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="b79e9-122">WSE 3,0 používá jako svůj protokol rámců verzi [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) .</span><span class="sxs-lookup"><span data-stu-id="b79e9-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="b79e9-123">`WriteData` zapouzdřuje logiku rámců a zabalí bajt [] do sady záznamů DIME.</span><span class="sxs-lookup"><span data-stu-id="b79e9-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="b79e9-124">Logika pro příjem zpráv je velmi podobná.</span><span class="sxs-lookup"><span data-stu-id="b79e9-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="b79e9-125">Hlavní složitost zpracovává fakt, že čtení soketu může vracet méně bajtů, než bylo vyžádáno.</span><span class="sxs-lookup"><span data-stu-id="b79e9-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="b79e9-126">Chcete-li dostávat zprávu, `WseTcpDuplexSessionChannel` čte bajty z přenosů, dekóduje rámce DIME a pak používá <xref:System.ServiceModel.Channels.MessageEncoder> pro přepínání bajtu [] na <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="b79e9-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="b79e9-127">Základní `WseTcpDuplexSessionChannel` předpokládá, že obdrží připojený soket.</span><span class="sxs-lookup"><span data-stu-id="b79e9-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="b79e9-128">Základní třída zpracovává vypnutí soketu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="b79e9-129">Rozhraní se uzávěrkou soketu má tři místa:</span><span class="sxs-lookup"><span data-stu-id="b79e9-129">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="b79e9-130">Přerušení – neúspěšné zavření soketu (tvrdý uzávěr)</span><span class="sxs-lookup"><span data-stu-id="b79e9-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="b79e9-131">Zapnuto [begin] Close--uzavřete soket korektně (měkký zavření).</span><span class="sxs-lookup"><span data-stu-id="b79e9-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="b79e9-132">jednání. Vyvolání třídy CloseOutputSession – vypnutí odchozího datového proudu (polovina zavření).</span><span class="sxs-lookup"><span data-stu-id="b79e9-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="b79e9-133">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="b79e9-133">Channel Factory</span></span>  
 <span data-ttu-id="b79e9-134">Dalším krokem při psaní přenosu protokolu TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály.</span><span class="sxs-lookup"><span data-stu-id="b79e9-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="b79e9-135">`WseTcpChannelFactory` jsou odvozeny z <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="b79e9-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="b79e9-136">Je to objekt pro vytváření, který Přepisuje `OnCreateChannel` a vytváří klientské kanály.</span><span class="sxs-lookup"><span data-stu-id="b79e9-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="b79e9-137">`ClientWseTcpDuplexSessionChannel` přidá k základnímu `WseTcpDuplexSessionChannel` logiku pro připojení k serveru TCP v `channel.Open` čase.</span><span class="sxs-lookup"><span data-stu-id="b79e9-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="b79e9-138">Nejprve je název hostitele přeložen na IP adresu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="b79e9-139">Pak je název hostitele připojen k první dostupné IP adrese ve smyčce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="b79e9-140">V rámci kontraktu kanálu jsou všechny výjimky specifické pro doménu zabaleny, například `SocketException` v <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b79e9-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="b79e9-141">Naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="b79e9-141">Channel Listener</span></span>  
 <span data-ttu-id="b79e9-142">Dalším krokem při psaní přenosu protokolu TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro příjem serverových kanálů.</span><span class="sxs-lookup"><span data-stu-id="b79e9-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="b79e9-143">`WseTcpChannelListener` jsou odvozeny z <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel > a přepsání na [begin] Open a na [begin] blízko pro řízení životnosti jejího naslouchajícího soketu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="b79e9-144">V otevřeném se vytvoří soket pro naslouchání na IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="b79e9-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="b79e9-145">Pokročilejší implementace mohou vytvořit druhý soket pro naslouchání také na protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="b79e9-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="b79e9-146">Můžou taky umožňovat zadání IP adresy v názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="b79e9-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="b79e9-147">Při přijetí nového soketu se na tomto soketu inicializuje serverový kanál.</span><span class="sxs-lookup"><span data-stu-id="b79e9-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="b79e9-148">Všechny vstupy a výstupy jsou již implementovány v základní třídě, takže tento kanál je zodpovědný za inicializaci soketu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="b79e9-149">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="b79e9-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="b79e9-150">Teď, když jsou továrny a kanály sestavené, musí být zpřístupněny modulu runtime ServiceModel prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="b79e9-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="b79e9-151">Vazba je kolekce elementů vazby, které představují komunikační zásobník přidružený k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="b79e9-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="b79e9-152">Každý prvek v zásobníku je reprezentován prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="b79e9-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="b79e9-153">V ukázce je prvek vazby `WseTcpTransportBindingElement`, který je odvozen z <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b79e9-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="b79e9-154">Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a Přepisuje následující metody pro sestavování továrn přidružených k naší vazbě.</span><span class="sxs-lookup"><span data-stu-id="b79e9-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="b79e9-155">Obsahuje také členy pro klonování `BindingElement` a vracení našeho schématu (WSE. TCP).</span><span class="sxs-lookup"><span data-stu-id="b79e9-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="b79e9-156">Konzola testu WSE TCP</span><span class="sxs-lookup"><span data-stu-id="b79e9-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="b79e9-157">Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="b79e9-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="b79e9-158">Následující pokyny ukazují, jak nastavit ukázku WSE `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="b79e9-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="b79e9-159">Testovací kód vytvoří vlastní vazbu, která používá MTOM jako kódování a `WseTcpTransport` jako přenos.</span><span class="sxs-lookup"><span data-stu-id="b79e9-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="b79e9-160">Také nastaví verze AddressingVersion tak, aby byl vyhovující WSE 3,0, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="b79e9-161">Skládá se ze dvou testů – jeden test nastaví typového klienta pomocí kódu vygenerovaného z WSE 3,0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="b79e9-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="b79e9-162">Druhý test používá WCF jako klienta i server tím, že odesílá zprávy přímo nad rozhraní API kanálu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="b79e9-163">Při spuštění ukázky se očekává následující výstup.</span><span class="sxs-lookup"><span data-stu-id="b79e9-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="b79e9-164">Client:</span><span class="sxs-lookup"><span data-stu-id="b79e9-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="b79e9-165">Server:</span><span class="sxs-lookup"><span data-stu-id="b79e9-165">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b79e9-166">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b79e9-166">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b79e9-167">Ke spuštění této ukázky musíte mít WSE 3,0 a nainstalovanou ukázku WSE `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="b79e9-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="b79e9-168">WSE 3,0 si můžete stáhnout [z webu MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="b79e9-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b79e9-169">Vzhledem k tomu, že WSE 3,0 není v systému Windows Server 2008 podporován, nelze nainstalovat nebo spustit ukázku `TcpSyncStockService` v tomto operačním systému.</span><span class="sxs-lookup"><span data-stu-id="b79e9-169">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="b79e9-170">Po instalaci ukázky `TcpSyncStockService` udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="b79e9-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="b79e9-171">Otevřete `TcpSyncStockService` v aplikaci Visual Studio (Všimněte si, že je nainstalovaná ukázka TcpSyncStockService s WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="b79e9-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="b79e9-172">Není součástí tohoto ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="b79e9-172">It is not part of this sample's code).</span></span>  
  
    2. <span data-ttu-id="b79e9-173">Nastavte projekt StockService jako spouštěcí projekt.</span><span class="sxs-lookup"><span data-stu-id="b79e9-173">Set the StockService project as the start up project.</span></span>  
  
    3. <span data-ttu-id="b79e9-174">Otevřete StockService.cs v projektu StockService a přidejte do něj atribut [Policy] ve třídě `StockService`.</span><span class="sxs-lookup"><span data-stu-id="b79e9-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="b79e9-175">Tím se zakáže zabezpečení z ukázky.</span><span class="sxs-lookup"><span data-stu-id="b79e9-175">This disables security from the sample.</span></span> <span data-ttu-id="b79e9-176">I když může WCF spolupracovat s WSE 3,0 zabezpečenými koncovými body, zabezpečení je zakázané, aby se tato ukázka zaměřila na vlastní přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="b79e9-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="b79e9-177">Stisknutím klávesy F5 spusťte `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="b79e9-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="b79e9-178">Služba se spustí v novém okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="b79e9-178">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="b79e9-179">Otevřete tuto ukázku přenosu TCP v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b79e9-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="b79e9-180">Aktualizujte proměnnou hostname v TestCode.cs tak, aby odpovídala názvu počítače, na kterém je spuštěný `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="b79e9-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="b79e9-181">Stisknutím klávesy F5 spusťte ukázku přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="b79e9-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="b79e9-182">Klient TCP Transport test se spustí v nové konzole.</span><span class="sxs-lookup"><span data-stu-id="b79e9-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="b79e9-183">Klient požaduje od služby skladové nabídky a potom zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="b79e9-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
