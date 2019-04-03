---
title: 'Přenos: Interoperabilita TCP ve WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 342c9c39eaa755363615dd83933cf00480e01c91
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842353"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="42968-102">Přenos: Interoperabilita TCP ve WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="42968-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="42968-103">Ukázka přenosu interoperabilita TCP ve WSE 3.0 ukazuje, jak implementovat duplexní relace TCP jako vlastní přenosu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="42968-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="42968-104">Také ukazuje, jak můžete použít rozšíření vrstvy kanálu rozhraní přenosu s existujícími systémy nasazené.</span><span class="sxs-lookup"><span data-stu-id="42968-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="42968-105">Následující kroky ukazují, jak vytvořit tento vlastní přenos WCF:</span><span class="sxs-lookup"><span data-stu-id="42968-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1.  <span data-ttu-id="42968-106">Počínaje soket TCP vytvořit klienta a serveru implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , které používají od sebe odděluje hranice zprávy DIME rámců.</span><span class="sxs-lookup"><span data-stu-id="42968-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="42968-107">Vytvoření postupu kanálu, který se připojí ke službě WSE TCP a odesílá zprávy orámované přes klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="42968-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="42968-108">Vytvořte naslouchací proces kanálu přijímat příchozí připojení protokolu TCP a vytvořit odpovídající kanály.</span><span class="sxs-lookup"><span data-stu-id="42968-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="42968-109">Ujistěte se, že všechny výjimky pro konkrétní sítě jsou normalizovány na příslušné třídy odvozené z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="42968-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="42968-110">Přidejte prvek vazby, který přidá vlastní přenosu do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="42968-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="42968-111">Další informace najdete v tématu [přidání prvku vazby].</span><span class="sxs-lookup"><span data-stu-id="42968-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="42968-112">Vytváření IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="42968-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="42968-113">Prvním krokem při psaní přenosu Interoperability TCP ve WSE 3.0, je vytvořit implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> nahoře <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="42968-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="42968-114">`WseTcpDuplexSessionChannel` je odvozen od <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="42968-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="42968-115">Logiku odesílání zprávy se skládá ze dvou hlavních částí: (1) do bajtů a (2) rámců těchto bajtů a poslat mu na lince kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="42968-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="42968-116">Kromě toho se zámek používá tak, aby volání Send() zachovat záruku IDuplexSessionChannel v pořadí a tak, aby volání do základního soketu se synchronizují správně.</span><span class="sxs-lookup"><span data-stu-id="42968-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="42968-117">`WseTcpDuplexSessionChannel` používá <xref:System.ServiceModel.Channels.MessageEncoder> pro převod <xref:System.ServiceModel.Channels.Message> do a z byte [].</span><span class="sxs-lookup"><span data-stu-id="42968-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="42968-118">Protože se jedná přenos `WseTcpDuplexSessionChannel` zodpovídá také za použití vzdálenou adresu, který byl nakonfigurován kanál.</span><span class="sxs-lookup"><span data-stu-id="42968-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="42968-119">`EncodeMessage` zapouzdří logiku pro tento převod.</span><span class="sxs-lookup"><span data-stu-id="42968-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="42968-120">Jakmile <xref:System.ServiceModel.Channels.Message> je zakódován do bajtů, je třeba přenést na lince.</span><span class="sxs-lookup"><span data-stu-id="42968-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="42968-121">To vyžaduje systém pro definování hranice zpráv.</span><span class="sxs-lookup"><span data-stu-id="42968-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="42968-122">WSE 3.0 používá verzi [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) jako protokol pro jeho rámce.</span><span class="sxs-lookup"><span data-stu-id="42968-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="42968-123">`WriteData` zapouzdří logiku rámce při zabalení byte [] do sady záznamů DIME.</span><span class="sxs-lookup"><span data-stu-id="42968-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="42968-124">Logika pro příjem zpráv je velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="42968-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="42968-125">Hlavní složitost zpracovává skutečnost, že soketu čtení může vrátit méně bajtů než bylo požadováno.</span><span class="sxs-lookup"><span data-stu-id="42968-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="42968-126">Při příjmu zprávy, `WseTcpDuplexSessionChannel` přečte bajtů vypnutí přenosu, dekóduje DIME rámce a poté použije <xref:System.ServiceModel.Channels.MessageEncoder> při zapínání byte [] do <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="42968-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="42968-127">Základní `WseTcpDuplexSessionChannel` předpokládá, že bude dostávat připojený soket.</span><span class="sxs-lookup"><span data-stu-id="42968-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="42968-128">Základní třída zpracovává vypnutí soketu.</span><span class="sxs-lookup"><span data-stu-id="42968-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="42968-129">Existují tři míst, na které rozhraní se uzavření soketu:</span><span class="sxs-lookup"><span data-stu-id="42968-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="42968-130">OnAbort – zavřete soketu ungracefully (pevné Zavřít).</span><span class="sxs-lookup"><span data-stu-id="42968-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="42968-131">Na [Begin] zavřete – soketu řádně uzavřít (měkké Zavřít).</span><span class="sxs-lookup"><span data-stu-id="42968-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="42968-132">relace. CloseOutputSession – vypnutí výstupní datový proud (poloviční Zavřít).</span><span class="sxs-lookup"><span data-stu-id="42968-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="42968-133">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="42968-133">Channel Factory</span></span>  
 <span data-ttu-id="42968-134">Dalším krokem při psaní přenosu protokolu TCP je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klientů.</span><span class="sxs-lookup"><span data-stu-id="42968-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="42968-135">`WseTcpChannelFactory` je odvozen od <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="42968-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="42968-136">Je objekt factory, který přepíše `OnCreateChannel` k vytvoření kanálů klienta.</span><span class="sxs-lookup"><span data-stu-id="42968-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="42968-137">`ClientWseTcpDuplexSessionChannel` Přidá do základní logiku `WseTcpDuplexSessionChannel` pro připojení k serveru TCP `channel.Open` čas.</span><span class="sxs-lookup"><span data-stu-id="42968-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="42968-138">Nejprve je přeložit na IP adresu, název hostitele, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="42968-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="42968-139">Potom název hostitele je připojen k první dostupná IP adresa ve smyčce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="42968-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="42968-140">Jako součást smlouvy channel jakékoli specifického pro doménu výjimky jsou obaleny, jako například `SocketException` v <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="42968-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="42968-141">Modul pro naslouchání kanálu</span><span class="sxs-lookup"><span data-stu-id="42968-141">Channel Listener</span></span>  
 <span data-ttu-id="42968-142">Dalším krokem při psaní přenosu protokolu TCP je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelListener> pro příjem kanálů.</span><span class="sxs-lookup"><span data-stu-id="42968-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="42968-143">`WseTcpChannelListener` je odvozen od <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > a přepsání při otevření [Begin] a [Begin] Zavřít řídit dobu života jeho naslouchání soketu.</span><span class="sxs-lookup"><span data-stu-id="42968-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="42968-144">V při otevření je tak, aby naslouchala na IP_ANY vytvořili soketu.</span><span class="sxs-lookup"><span data-stu-id="42968-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="42968-145">Implementace rozšířené můžete vytvořit druhý soketu také poslouchat protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="42968-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="42968-146">Můžete povolit také IP adresu, která zadaný v názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="42968-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="42968-147">Při přijetí nového soketu kanálu serveru je inicializována s tento soket.</span><span class="sxs-lookup"><span data-stu-id="42968-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="42968-148">Vstup a výstup je již implementováno základní třídy, takže tento kanál zodpovídá za inicializaci soketu.</span><span class="sxs-lookup"><span data-stu-id="42968-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="42968-149">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="42968-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="42968-150">Teď, když jsou vytvořeny objekty pro vytváření a kanály, se musí se zveřejnit pro modul runtime ServiceModel prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="42968-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="42968-151">Vazba je kolekce elementů vazby, který představuje komunikační balík přidružené k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="42968-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="42968-152">Každý prvek v zásobníku je reprezentován element vazby.</span><span class="sxs-lookup"><span data-stu-id="42968-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="42968-153">V ukázce je element vazby `WseTcpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="42968-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="42968-154">Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a přepíše následující metody k vytváření továrny spojené s využitím naší vazby.</span><span class="sxs-lookup"><span data-stu-id="42968-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="42968-155">Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="42968-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="42968-156">TCP ve WSE testovací konzole</span><span class="sxs-lookup"><span data-stu-id="42968-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="42968-157">Testovací kód pro tento přenos ukázkový používání je k dispozici v TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="42968-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="42968-158">Následující pokyny ukazují, jak nastavit WSE `TcpSyncStockService` vzorku.</span><span class="sxs-lookup"><span data-stu-id="42968-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="42968-159">Testovací kód vytvoří vlastní vazby, který používá jako kódování MTOM a `WseTcpTransport` přenos.</span><span class="sxs-lookup"><span data-stu-id="42968-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="42968-160">Rovněž nastaví verze AddressingVersion být podmínky ve WSE 3.0, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="42968-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="42968-161">Skládá se ze dvou testy – jeden test nastaví zadaný kód generovaný z WSE 3.0 WSDL pomocí klienta.</span><span class="sxs-lookup"><span data-stu-id="42968-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="42968-162">Druhý test používá WCF jako klient a server odesíláním zpráv přímo přes kanál rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="42968-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="42968-163">Při spuštění ukázky, očekává se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="42968-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="42968-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="42968-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="42968-165">Server:</span><span class="sxs-lookup"><span data-stu-id="42968-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="42968-166">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="42968-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="42968-167">Pro tuto ukázku spustit, je zapotřebí WSE 3.0 a WSE `TcpSyncStockService` ukázka nainstalované.</span><span class="sxs-lookup"><span data-stu-id="42968-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="42968-168">Můžete si stáhnout [WSE 3.0 z webu MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="42968-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42968-169">Protože WSE 3.0 není podporována na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nemůžou instalovat ani spouštět `TcpSyncStockService` ukázka v tomto operačním systému.</span><span class="sxs-lookup"><span data-stu-id="42968-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="42968-170">Po instalaci `TcpSyncStockService` ukázkový, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="42968-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="42968-171">Otevřít `TcpSyncStockService` v sadě Visual Studio (Všimněte si, že ukázky TcpSyncStockService se instaluje s WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="42968-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="42968-172">Není součástí této ukázky kódu).</span><span class="sxs-lookup"><span data-stu-id="42968-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="42968-173">Nastavte StockService projekt jako spouštěný projekt.</span><span class="sxs-lookup"><span data-stu-id="42968-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="42968-174">Otevření StockService.cs v projektu StockService a Odkomentujte atribut [zásad] na `StockService` třídy.</span><span class="sxs-lookup"><span data-stu-id="42968-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="42968-175">Zakáže zabezpečení z ukázky.</span><span class="sxs-lookup"><span data-stu-id="42968-175">This disables security from the sample.</span></span> <span data-ttu-id="42968-176">Zatímco WCF můžou spolupracovat s WSE 3.0 zabezpečené koncové body, zabezpečení je zakázané, aby zachovat tuto ukázku, zaměřuje na vlastní přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="42968-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="42968-177">Stisknutím klávesy F5 pro spuštění `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="42968-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="42968-178">Služba se spustí v novém okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="42968-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="42968-179">Tato ukázka přenosu protokolu TCP otevřete v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42968-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="42968-180">Aktualizovat proměnnou "hostname" v TestCode.cs tak, aby odpovídaly názvu počítač se systémem `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="42968-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="42968-181">Stisknutím klávesy F5 spusťte ukázku přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="42968-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="42968-182">Testovací klient přenosu protokolu TCP začíná v nové konzole.</span><span class="sxs-lookup"><span data-stu-id="42968-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="42968-183">Klient vyžádá akcií ze služby a potom zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="42968-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
