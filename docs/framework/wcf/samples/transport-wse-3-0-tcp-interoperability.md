---
title: "Přenos: Součinnost TCP ve WSE 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50bd1492c4e2e8941a77f344c04414a763390e89
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="db10f-102">Přenos: Součinnost TCP ve WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="db10f-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="db10f-103">Ukázka WSE 3.0 TCP interoperabilita přenosu ukazuje, jak implementovat duplexní relace TCP jako vlastní [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] přenosu.</span><span class="sxs-lookup"><span data-stu-id="db10f-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="db10f-104">Také ukazuje, jak můžete použít rozšíření vrstvy kanálu rozhraní přenášených v síti s existující nasazené systémy.</span><span class="sxs-lookup"><span data-stu-id="db10f-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="db10f-105">Následující kroky ukazují, jak vytvořit toto vlastní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosu:</span><span class="sxs-lookup"><span data-stu-id="db10f-105">The following steps show how to build this custom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport:</span></span>  
  
1.  <span data-ttu-id="db10f-106">Počínaje soket TCP vytvořit klientských a serverových implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , pomocí DIME rámců zobrazit hranice zpráv.</span><span class="sxs-lookup"><span data-stu-id="db10f-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="db10f-107">Vytvoření kanálu, který připojuje ke službě WSE TCP a odesílá rámcová zprávy přes klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="db10f-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="db10f-108">Vytvořte naslouchací proces kanálu pro příjem příchozích připojení TCP a vytvoří odpovídající kanály.</span><span class="sxs-lookup"><span data-stu-id="db10f-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="db10f-109">Ujistěte se, že jsou všechny výjimky sítě normalizovány na příslušné odvozené třídy z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="db10f-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="db10f-110">Přidáte element vazby, který přidá vlastní přenos do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="db10f-110">Add a binding element that adds the custom transport to a channel stack.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="db10f-111">[Přidání prvku vazby].</span><span class="sxs-lookup"><span data-stu-id="db10f-111"> [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="db10f-112">Vytváření IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="db10f-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="db10f-113">Prvním krokem při psaní WSE 3.0 TCP interoperabilita přenosu je vytvoření implementace <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="db10f-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="db10f-114">`WseTcpDuplexSessionChannel`odvozená z <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="db10f-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="db10f-115">Logiku odesílání zprávy se skládá ze dvou částí hlavní: (1) do bajtů a (2) formulování těchto bajtů a je pošlete přenášený kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="db10f-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="db10f-116">Kromě toho zámek se provede tak, aby volání Send() zachovat záruky IDuplexSessionChannel v daném pořadí a tak, aby správně synchronizovaní volání základní soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="db10f-117">`WseTcpDuplexSessionChannel`používá <xref:System.ServiceModel.Channels.MessageEncoder> pro převod <xref:System.ServiceModel.Channels.Message> do a z byte [].</span><span class="sxs-lookup"><span data-stu-id="db10f-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="db10f-118">Protože je na přenos `WseTcpDuplexSessionChannel` zodpovídá taky za použití nakonfigurovaný kanál pomocí vzdálené adresy.</span><span class="sxs-lookup"><span data-stu-id="db10f-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="db10f-119">`EncodeMessage`zapouzdří logiku pro tento převod.</span><span class="sxs-lookup"><span data-stu-id="db10f-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="db10f-120">Jednou <xref:System.ServiceModel.Channels.Message> je zakódován do bajtů, je třeba přenést v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="db10f-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="db10f-121">To vyžaduje systém pro definování hranice zpráv.</span><span class="sxs-lookup"><span data-stu-id="db10f-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="db10f-122">WSE 3.0 používá verzi [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) jako jeho rámcovacích protokol.</span><span class="sxs-lookup"><span data-stu-id="db10f-122">WSE 3.0 uses a version of [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="db10f-123">`WriteData`zapouzdří logice rámcovacích zabalit byte [] do sady záznamů DIME.</span><span class="sxs-lookup"><span data-stu-id="db10f-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="db10f-124">Logika pro příjem zprávy je velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="db10f-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="db10f-125">Hlavní složitost zpracovává fakt, že soket čtení může vrátit menší počet bajtů, než se požadovaly.</span><span class="sxs-lookup"><span data-stu-id="db10f-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="db10f-126">Pro příjem zprávy, `WseTcpDuplexSessionChannel` čte bajtů vypnout sítě, dekóduje rámcovacích DIME a pak použije <xref:System.ServiceModel.Channels.MessageEncoder> pro zapnutí byte [] do <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="db10f-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="db10f-127">Základní `WseTcpDuplexSessionChannel` předpokládá obdrží připojené soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="db10f-128">Základní třída zpracovává vypnutí soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="db10f-129">Existují tři míst, na které rozhraní s uzavření soketu:</span><span class="sxs-lookup"><span data-stu-id="db10f-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="db10f-130">OnAbort – zavřete soketu ungracefully (pevné Zavřít).</span><span class="sxs-lookup"><span data-stu-id="db10f-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="db10f-131">Na [Begin] zavřete – zavřete soket řádně (logicky Zavřít).</span><span class="sxs-lookup"><span data-stu-id="db10f-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="db10f-132">relace. CloseOutputSession – vypnutí výstupní datový proud (poloviční Zavřít).</span><span class="sxs-lookup"><span data-stu-id="db10f-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="db10f-133">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="db10f-133">Channel Factory</span></span>  
 <span data-ttu-id="db10f-134">Dalším krokem při psaní přenos TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klienta kanály.</span><span class="sxs-lookup"><span data-stu-id="db10f-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="db10f-135">`WseTcpChannelFactory`odvozená z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="db10f-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="db10f-136">Je objekt factory, který přepíše `OnCreateChannel` k vytvoření klienta kanály.</span><span class="sxs-lookup"><span data-stu-id="db10f-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="db10f-137">`ClientWseTcpDuplexSessionChannel`Přidá do základní logiku `WseTcpDuplexSessionChannel` pro připojení k serveru TCP `channel.Open` čas.</span><span class="sxs-lookup"><span data-stu-id="db10f-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="db10f-138">Nejprve je přeložit na IP adresu, název hostitele, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="db10f-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="db10f-139">Potom název hostitele je připojený k první dostupná IP adresa ve smyčce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="db10f-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="db10f-140">V rámci kanálu kontraktu, všechny výjimky, specifické pro doménu jsou zabalená, jako například `SocketException` v <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="db10f-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="db10f-141">Naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="db10f-141">Channel Listener</span></span>  
 <span data-ttu-id="db10f-142">Dalším krokem při psaní přenos TCP je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro přijetí serveru kanály.</span><span class="sxs-lookup"><span data-stu-id="db10f-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="db10f-143">`WseTcpChannelListener`odvozená z <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > a přepsání na otevřete [Begin] a [Begin] zavřete na řídí životnost jeho naslouchání soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="db10f-144">V při otevření je tak, aby naslouchala na IP_ANY vytvořili soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="db10f-145">Pokročilejší implementace můžete vytvořit druhý soketu také naslouchat na IPv6.</span><span class="sxs-lookup"><span data-stu-id="db10f-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="db10f-146">Můžete povolit také IP adresu, kterou být zadaný v názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="db10f-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="db10f-147">Při přijetí nové soketu se server kanál, který je inicializován tento soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="db10f-148">Všechny vstupní a výstupní je již implementováno v základní třídě, takže tento kanál zodpovídá za inicializaci soketu.</span><span class="sxs-lookup"><span data-stu-id="db10f-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="db10f-149">Přidání prvku vazby</span><span class="sxs-lookup"><span data-stu-id="db10f-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="db10f-150">Teď, když jsou vytvořeny objekty pro vytváření a kanály, se musí se zveřejnit pro modul runtime ServiceModel prostřednictvím vazbu.</span><span class="sxs-lookup"><span data-stu-id="db10f-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="db10f-151">Vazba je kolekci elementů vazby, která reprezentuje komunikačního balíku přidružená adresa služby.</span><span class="sxs-lookup"><span data-stu-id="db10f-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="db10f-152">Každý prvek v zásobníku je reprezentována prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="db10f-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="db10f-153">V ukázce je prvku vazby `WseTcpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="db10f-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="db10f-154">Podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> a přepíše následující metody pro vytvoření objektů Factory související s naše vazby.</span><span class="sxs-lookup"><span data-stu-id="db10f-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="db10f-155">Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="db10f-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="db10f-156">Konzole testovací WSE TCP</span><span class="sxs-lookup"><span data-stu-id="db10f-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="db10f-157">Testovacího kódu pro použití přenosu Tato ukázka je dostupná v TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="db10f-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="db10f-158">Následující pokyny vám ukážou, jak nastavit WSE `TcpSyncStockService` ukázka.</span><span class="sxs-lookup"><span data-stu-id="db10f-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="db10f-159">Testovací kód vytvoří vlastní vazby, který používá jako kódování MTOM a `WseTcpTransport` jako přenosu.</span><span class="sxs-lookup"><span data-stu-id="db10f-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="db10f-160">Je také nastaví třídu AddressingVersion tak, aby se shoduje s WSE 3.0, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="db10f-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="db10f-161">Obsahuje dva testy – jeden test nastaví typový klient pomocí kód, který vygenerovala z schématu WSDL WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="db10f-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="db10f-162">Druhý test používá [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jako klient a server tak, že odesílání zpráv přímo na základě kanál rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="db10f-162">The second test uses [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="db10f-163">Při spuštění ukázky, očekává se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="db10f-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="db10f-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="db10f-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="db10f-165">Server:</span><span class="sxs-lookup"><span data-stu-id="db10f-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="db10f-166">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="db10f-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="db10f-167">Pokud chcete tuto ukázku spustit, musíte mít WSE 3.0 a WSE `TcpSyncStockService` ukázka nainstalována.</span><span class="sxs-lookup"><span data-stu-id="db10f-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="db10f-168">Můžete si stáhnout [WSE 3.0 z webu MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="db10f-168">You can download [WSE 3.0 from MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db10f-169">Protože WSE 3.0 není podporována na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nemůžou instalovat ani spouštět `TcpSyncStockService` ukázku v tomto operačním systému.</span><span class="sxs-lookup"><span data-stu-id="db10f-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="db10f-170">Po instalaci `TcpSyncStockService` ukázkové, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="db10f-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="db10f-171">Otevřete `TcpSyncStockService` v sadě Visual Studio (Všimněte si, že ukázka TcpSyncStockService je instalován s WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="db10f-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="db10f-172">Není součástí této ukázce kódu).</span><span class="sxs-lookup"><span data-stu-id="db10f-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="db10f-173">Nastavte projekt StockService jako počáteční projekt.</span><span class="sxs-lookup"><span data-stu-id="db10f-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="db10f-174">Otevřete StockService.cs v projektu StockService a Odkomentujte atribut [zásad] na `StockService` třídy.</span><span class="sxs-lookup"><span data-stu-id="db10f-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="db10f-175">To zakáže zabezpečení od vzorku.</span><span class="sxs-lookup"><span data-stu-id="db10f-175">This disables security from the sample.</span></span> <span data-ttu-id="db10f-176">Při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] můžou spolupracovat s WSE 3.0 zabezpečené koncové body, aby tato ukázka se zaměřuje na vlastní přenos TCP je zakázána zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db10f-176">While [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="db10f-177">Stisknutím klávesy F5 spusťte `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="db10f-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="db10f-178">Služba se spustí v nové okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="db10f-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="db10f-179">Tato ukázka přenos TCP otevřete v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db10f-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="db10f-180">Aktualizujte proměnné "název hostitele" v TestCode.cs tak, aby odpovídaly názvu počítač se systémem `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="db10f-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="db10f-181">Stisknutím klávesy F5 spusťte ukázkové přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="db10f-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="db10f-182">Spustí se v nové konzole testovacího klienta přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="db10f-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="db10f-183">Klient požaduje akcií ze služby a potom zobrazí výsledky v okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="db10f-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db10f-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="db10f-184">See Also</span></span>
