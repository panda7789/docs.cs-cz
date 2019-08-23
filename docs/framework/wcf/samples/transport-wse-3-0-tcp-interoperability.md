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
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="c912b-102">Přenos: Interoperabilita TCP ve WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="c912b-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="c912b-103">Ukázka přenosu interoperability TCP v WSE 3,0 ukazuje, jak implementovat relaci duplexního připojení TCP jako vlastní přenos Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c912b-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="c912b-104">Také ukazuje, jak můžete použít rozšiřitelnost vrstvy kanálu na rozhraní s existujícími nasazenými systémy.</span><span class="sxs-lookup"><span data-stu-id="c912b-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="c912b-105">Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:</span><span class="sxs-lookup"><span data-stu-id="c912b-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="c912b-106">Počínaje soketem TCP vytvořte implementace klientů a serverů systému <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , které používají rámce DIME k vymezení hranic zpráv.</span><span class="sxs-lookup"><span data-stu-id="c912b-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="c912b-107">Vytvořte továrnu kanálu, který se připojí ke službě WSE TCP a pošle v rámci klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s rámcové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c912b-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="c912b-108">Vytvořte naslouchací proces kanálu, který přijme příchozí připojení TCP a vytvoří odpovídající kanály.</span><span class="sxs-lookup"><span data-stu-id="c912b-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="c912b-109">Zajistěte, aby všechny výjimky specifické pro síť byly normalizovány na příslušnou odvozenou třídu třídy <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="c912b-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="c912b-110">Přidejte prvek vazby, který přidá vlastní přenos do zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="c912b-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="c912b-111">Další informace naleznete v tématu [přidání prvku vazby].</span><span class="sxs-lookup"><span data-stu-id="c912b-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="c912b-112">Vytváření IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="c912b-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="c912b-113">Prvním krokem při psaní přenosů mezi <xref:System.ServiceModel.Channels.IDuplexSessionChannel> WSE 3,0 TCP je vytvoření implementace na začátku. <xref:System.Net.Sockets.Socket></span><span class="sxs-lookup"><span data-stu-id="c912b-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="c912b-114">`WseTcpDuplexSessionChannel`je odvozen z <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="c912b-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="c912b-115">Logika odeslání zprávy se skládá ze dvou hlavních částí: (1) zakódování zprávy do bajtů a (2) zařadí do rámců tyto bajty a odesílají je na kabel.</span><span class="sxs-lookup"><span data-stu-id="c912b-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="c912b-116">Kromě toho se povede zámek, aby volání Send () zachovala záruku IDuplexSessionChannel a aby se správně synchronizoval volání základního soketu.</span><span class="sxs-lookup"><span data-stu-id="c912b-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="c912b-117">`WseTcpDuplexSessionChannel`používá pro překlad typu <xref:System.ServiceModel.Channels.Message> a na Byte []. <xref:System.ServiceModel.Channels.MessageEncoder></span><span class="sxs-lookup"><span data-stu-id="c912b-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="c912b-118">Vzhledem k tomu, že se `WseTcpDuplexSessionChannel` jedná o přenos, zodpovídá taky za použití vzdálené adresy, se kterou byl kanál nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="c912b-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="c912b-119">`EncodeMessage`Zapouzdřuje logiku pro tento převod.</span><span class="sxs-lookup"><span data-stu-id="c912b-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="c912b-120"><xref:System.ServiceModel.Channels.Message> Jakmile je kód kódovaný do bajtů, je nutné ho přenést na síťový kabel.</span><span class="sxs-lookup"><span data-stu-id="c912b-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="c912b-121">To vyžaduje systém pro definování hranic zprávy.</span><span class="sxs-lookup"><span data-stu-id="c912b-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="c912b-122">WSE 3,0 používá jako svůj protokol rámců verzi [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) .</span><span class="sxs-lookup"><span data-stu-id="c912b-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="c912b-123">`WriteData`Zapouzdřuje logiku rámců a zabalí bajt [] do sady záznamů DIME.</span><span class="sxs-lookup"><span data-stu-id="c912b-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="c912b-124">Logika pro příjem zpráv je velmi podobná.</span><span class="sxs-lookup"><span data-stu-id="c912b-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="c912b-125">Hlavní složitost zpracovává fakt, že čtení soketu může vracet méně bajtů, než bylo vyžádáno.</span><span class="sxs-lookup"><span data-stu-id="c912b-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="c912b-126">Chcete-li přijmout zprávu `WseTcpDuplexSessionChannel` , přečte bajty z přenosů, dekóduje rámce DIME a pak <xref:System.ServiceModel.Channels.MessageEncoder> použije příkaz pro zapnutí <xref:System.ServiceModel.Channels.Message>bajtu [] na.</span><span class="sxs-lookup"><span data-stu-id="c912b-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="c912b-127">Základní `WseTcpDuplexSessionChannel` předpokládá, že obdrží připojený soket.</span><span class="sxs-lookup"><span data-stu-id="c912b-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="c912b-128">Základní třída zpracovává vypnutí soketu.</span><span class="sxs-lookup"><span data-stu-id="c912b-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="c912b-129">Rozhraní se uzávěrkou soketu má tři místa:</span><span class="sxs-lookup"><span data-stu-id="c912b-129">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="c912b-130">Přerušení – neúspěšné zavření soketu (tvrdý uzávěr)</span><span class="sxs-lookup"><span data-stu-id="c912b-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="c912b-131">Zapnuto [begin] Close--uzavřete soket korektně (měkký zavření).</span><span class="sxs-lookup"><span data-stu-id="c912b-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="c912b-132">jednání. Vyvolání třídy CloseOutputSession – vypnutí odchozího datového proudu (polovina zavření).</span><span class="sxs-lookup"><span data-stu-id="c912b-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="c912b-133">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="c912b-133">Channel Factory</span></span>  
 <span data-ttu-id="c912b-134">Dalším krokem při psaní přenosu protokolu TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály.</span><span class="sxs-lookup"><span data-stu-id="c912b-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="c912b-135">`WseTcpChannelFactory`je odvozen z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="c912b-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="c912b-136">Jedná se o továrnu, `OnCreateChannel` která přepisuje vytváření klientských kanálů.</span><span class="sxs-lookup"><span data-stu-id="c912b-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="c912b-137">`ClientWseTcpDuplexSessionChannel`Přidá logiku do základu `WseTcpDuplexSessionChannel` pro připojení k serveru TCP v `channel.Open` čase.</span><span class="sxs-lookup"><span data-stu-id="c912b-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="c912b-138">Nejprve je název hostitele přeložen na IP adresu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c912b-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="c912b-139">Pak je název hostitele připojen k první dostupné IP adrese ve smyčce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c912b-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="c912b-140">`SocketException` V rámci kontraktu kanálu jsou všechny výjimky specifické pro doménu zabaleny, například v <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="c912b-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="c912b-141">Naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="c912b-141">Channel Listener</span></span>  
 <span data-ttu-id="c912b-142">Dalším krokem při psaní přenosu protokolu TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro příjem serverových kanálů.</span><span class="sxs-lookup"><span data-stu-id="c912b-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="c912b-143">`WseTcpChannelListener`je odvozen z <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > a potlačení na [begin] Open a na [begin] blízko pro řízení životnosti jejího naslouchajícího soketu.</span><span class="sxs-lookup"><span data-stu-id="c912b-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="c912b-144">V otevřeném se vytvoří soket pro naslouchání na IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="c912b-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="c912b-145">Pokročilejší implementace mohou vytvořit druhý soket pro naslouchání také na protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="c912b-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="c912b-146">Můžou taky umožňovat zadání IP adresy v názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="c912b-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="c912b-147">Při přijetí nového soketu se na tomto soketu inicializuje serverový kanál.</span><span class="sxs-lookup"><span data-stu-id="c912b-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="c912b-148">Všechny vstupy a výstupy jsou již implementovány v základní třídě, takže tento kanál je zodpovědný za inicializaci soketu.</span><span class="sxs-lookup"><span data-stu-id="c912b-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="c912b-149">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="c912b-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="c912b-150">Teď, když jsou továrny a kanály sestavené, musí být zpřístupněny modulu runtime ServiceModel prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="c912b-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="c912b-151">Vazba je kolekce elementů vazby, které představují komunikační zásobník přidružený k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="c912b-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="c912b-152">Každý prvek v zásobníku je reprezentován prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="c912b-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="c912b-153">V ukázce je prvek vazby, který je `WseTcpTransportBindingElement`odvozen z. <xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="c912b-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="c912b-154">Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a Přepisuje následující metody pro sestavování továrn přidružených k naší vazbě.</span><span class="sxs-lookup"><span data-stu-id="c912b-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="c912b-155">Obsahuje také členy pro klonování `BindingElement` a vracení našeho schématu (WSE. TCP).</span><span class="sxs-lookup"><span data-stu-id="c912b-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="c912b-156">Konzola testu WSE TCP</span><span class="sxs-lookup"><span data-stu-id="c912b-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="c912b-157">Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="c912b-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="c912b-158">Následující pokyny ukazují, jak nastavit ukázku WSE `TcpSyncStockService` .</span><span class="sxs-lookup"><span data-stu-id="c912b-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="c912b-159">Testovací kód vytvoří vlastní vazbu, která používá MTOM jako kódování a `WseTcpTransport` jako přenos.</span><span class="sxs-lookup"><span data-stu-id="c912b-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="c912b-160">Také nastaví verze AddressingVersion tak, aby byl vyhovující WSE 3,0, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c912b-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="c912b-161">Skládá se ze dvou testů – jeden test nastaví typového klienta pomocí kódu vygenerovaného z WSE 3,0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="c912b-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="c912b-162">Druhý test používá WCF jako klienta i server tím, že odesílá zprávy přímo nad rozhraní API kanálu.</span><span class="sxs-lookup"><span data-stu-id="c912b-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="c912b-163">Při spuštění ukázky se očekává následující výstup.</span><span class="sxs-lookup"><span data-stu-id="c912b-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="c912b-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="c912b-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="c912b-165">WebServer</span><span class="sxs-lookup"><span data-stu-id="c912b-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c912b-166">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c912b-166">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c912b-167">Pro spuštění této ukázky musíte mít WSE 3,0 a nainstalovanou ukázku WSE `TcpSyncStockService` .</span><span class="sxs-lookup"><span data-stu-id="c912b-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="c912b-168">WSE 3,0 si můžete stáhnout [z webu MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="c912b-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c912b-169">Vzhledem k tomu, že WSE 3,0 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]není podporován na, nelze nainstalovat nebo `TcpSyncStockService` spustit ukázku v tomto operačním systému.</span><span class="sxs-lookup"><span data-stu-id="c912b-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="c912b-170">Po instalaci `TcpSyncStockService` ukázky postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="c912b-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="c912b-171">`TcpSyncStockService` Otevřete v aplikaci Visual Studio (Všimněte si, že je nainstalovaná ukázka TcpSyncStockService s WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="c912b-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="c912b-172">Není součástí tohoto ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="c912b-172">It is not part of this sample's code).</span></span>  
  
    2. <span data-ttu-id="c912b-173">Nastavte projekt StockService jako spouštěcí projekt.</span><span class="sxs-lookup"><span data-stu-id="c912b-173">Set the StockService project as the start up project.</span></span>  
  
    3. <span data-ttu-id="c912b-174">Otevřete StockService.cs v projektu StockService a odkomentujte atribut `StockService` [Policy] třídy.</span><span class="sxs-lookup"><span data-stu-id="c912b-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="c912b-175">Tím se zakáže zabezpečení z ukázky.</span><span class="sxs-lookup"><span data-stu-id="c912b-175">This disables security from the sample.</span></span> <span data-ttu-id="c912b-176">I když může WCF spolupracovat s WSE 3,0 zabezpečenými koncovými body, zabezpečení je zakázané, aby se tato ukázka zaměřila na vlastní přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="c912b-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="c912b-177">Stisknutím klávesy F5 spusťte `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="c912b-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="c912b-178">Služba se spustí v novém okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c912b-178">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="c912b-179">Otevřete tuto ukázku přenosu TCP v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c912b-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="c912b-180">Aktualizujte proměnnou hostname v TestCode.cs tak, aby odpovídala názvu počítače, na `TcpSyncStockService`kterém je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="c912b-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="c912b-181">Stisknutím klávesy F5 spusťte ukázku přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="c912b-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="c912b-182">Klient TCP Transport test se spustí v nové konzole.</span><span class="sxs-lookup"><span data-stu-id="c912b-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="c912b-183">Klient požaduje od služby skladové nabídky a potom zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c912b-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
