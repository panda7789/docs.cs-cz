---
title: 'Klient: Objekty pro vytváření kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3f045f56f7b73c5416e7a21a3afde29d22212d68
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182434"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="49e3c-102">Klient: Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="49e3c-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="49e3c-103">Toto téma popisuje vytvoření vytvoření objektů pro vytváření kanálů a kanály.</span><span class="sxs-lookup"><span data-stu-id="49e3c-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="49e3c-104">Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="49e3c-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="49e3c-105">Objekty pro vytváření kanálů zodpovídají za vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="49e3c-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="49e3c-106">Kanály vytvořené objekty pro vytváření kanálů se používají pro zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="49e3c-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="49e3c-107">Tyto kanály jsou zodpovědné za z vrstvy výše se zobrazuje zpráva, provádění jakékoli zpracování je nezbytné pak posílání zprávy na vrstvě níže.</span><span class="sxs-lookup"><span data-stu-id="49e3c-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="49e3c-108">Tento proces je znázorněný následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="49e3c-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="49e3c-109">![Klientské objekty pro vytváření a kanály](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="49e3c-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="49e3c-110">Vytvoří objekt pro vytváření kanálů kanály.</span><span class="sxs-lookup"><span data-stu-id="49e3c-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="49e3c-111">Při zavření, objekty pro vytváření kanálů zodpovídají za zavření všechny kanály, které vytvořili, které ještě nebyly uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="49e3c-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="49e3c-112">Upozorňujeme, že model asymetrického zde protože při zavření kanálu naslouchacího procesu se jenom zastaví přijímání nových kanálů, ale ponechá stávajících prodejních kanálů otevřít tak, aby může i dál příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="49e3c-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="49e3c-113">WCF poskytuje pomocné rutiny základní třídy pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="49e3c-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="49e3c-114">(Diagram tříd pomocných rutin kanál popsané v tomto tématu, naleznete v tématu [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="49e3c-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="49e3c-115"><xref:System.ServiceModel.Channels.CommunicationObject> Implementuje třída <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavového stroje popsaný v kroku 2 z [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="49e3c-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="49e3c-116"><xref:System.ServiceModel.Channels.ChannelManagerBase> Implementuje třída <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotné základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="49e3c-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49e3c-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> Třídy funguje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídy, která implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="49e3c-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
-   <span data-ttu-id="49e3c-118"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Implementuje třída <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a slučuje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="49e3c-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
-   <span data-ttu-id="49e3c-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> Implementuje třída <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="49e3c-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="49e3c-120">Postará se o správu základního stavu.</span><span class="sxs-lookup"><span data-stu-id="49e3c-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="49e3c-121">Podle následující diskuse [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="49e3c-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="49e3c-122">Vytvoření objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="49e3c-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="49e3c-123">`UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="49e3c-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="49e3c-124">Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pro poskytnutí přístupu k verze kodér zprávy.</span><span class="sxs-lookup"><span data-stu-id="49e3c-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="49e3c-125">Ukázka také přepisuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> k dovolí naše instanci <xref:System.ServiceModel.Channels.BufferManager> když změní stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="49e3c-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="49e3c-126">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="49e3c-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="49e3c-127">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="49e3c-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="49e3c-128">Konstruktor ověří argumenty a vytvoří cíl <xref:System.Net.EndPoint> objektu na základě <xref:System.ServiceModel.EndpointAddress> , který je předán.</span><span class="sxs-lookup"><span data-stu-id="49e3c-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="49e3c-129">Přepsané <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soket, který se používá k odesílání zpráv do to <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="49e3c-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="49e3c-130">Kanál můžete zavřít, bez výpadku nebo ungracefully.</span><span class="sxs-lookup"><span data-stu-id="49e3c-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="49e3c-131">Pokud kanál je uzavřen řádně soketu se zavře a základní třídy je provedeno volání `OnClose` metoda.</span><span class="sxs-lookup"><span data-stu-id="49e3c-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="49e3c-132">Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěn.</span><span class="sxs-lookup"><span data-stu-id="49e3c-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="49e3c-133">Implementace `Send()` a `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="49e3c-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="49e3c-134">Tím je prolomen na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="49e3c-134">This breaks down into two main sections.</span></span> <span data-ttu-id="49e3c-135">Nejprve serializovat zprávu do bajtového pole:</span><span class="sxs-lookup"><span data-stu-id="49e3c-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="49e3c-136">Odešlete na lince Výsledná data:</span><span class="sxs-lookup"><span data-stu-id="49e3c-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="49e3c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="49e3c-137">See Also</span></span>  
 [<span data-ttu-id="49e3c-138">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="49e3c-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)
