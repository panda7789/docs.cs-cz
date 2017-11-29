---
title: "Klienta: Objekty pro vytváření kanálů a kanály"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91954f1fbc06de2dd61da30310da415fbd2e7cad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="49e7b-102">Klienta: Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="49e7b-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="49e7b-103">Toto téma popisuje vytvářet objekty pro vytváření kanálů a kanály.</span><span class="sxs-lookup"><span data-stu-id="49e7b-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="49e7b-104">Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="49e7b-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="49e7b-105">Objekty Factory kanál jsou zodpovědní za vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="49e7b-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="49e7b-106">Kanály vytvořený kanál objekty Factory se používají pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="49e7b-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="49e7b-107">Tyto kanály jsou zodpovědní za načtení zprávy z vrstvy výše, provádění, ať zpracování je nezbytné, pak odeslání zprávy do vrstvy níže.</span><span class="sxs-lookup"><span data-stu-id="49e7b-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="49e7b-108">Tento proces je znázorněný na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="49e7b-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="49e7b-109">![Objekty Factory klienta a kanály](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="49e7b-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="49e7b-110">Postup kanálu vytvoří kanály.</span><span class="sxs-lookup"><span data-stu-id="49e7b-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="49e7b-111">Při zavření, objekty Factory kanál jsou zodpovědní za zavřením žádné kanály, které se vytvářely, které nejsou dosud zavřena.</span><span class="sxs-lookup"><span data-stu-id="49e7b-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="49e7b-112">Všimněte si, že model asymetrické zde vzhledem k tomu, že při zavření naslouchací proces kanálu pouze zastaví přijetí nové kanály, ale nechá, které existující kanály otevřete tak, aby může i dál přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="49e7b-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="49e7b-113">Poskytuje pomocné rutiny základní třídy pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="49e7b-113"> provides base class helpers for this process.</span></span> <span data-ttu-id="49e7b-114">(Diagram kanál pomocných tříd, popsané v tomto tématu, najdete v části [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="49e7b-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="49e7b-115"><xref:System.ServiceModel.Channels.CommunicationObject> Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stav stavového stroje popsané v kroku 2 [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="49e7b-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="49e7b-116">''<xref:System.ServiceModel.Channels.ChannelManagerBase> Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="49e7b-116">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49e7b-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídu, která implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="49e7b-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="49e7b-118">''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a dojde ke konsolidaci `CreateChannel` přetížení do jednoho `OnCreateChannel` abstraktní metodu.</span><span class="sxs-lookup"><span data-stu-id="49e7b-118">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="49e7b-119">''<xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="49e7b-119">The``<xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="49e7b-120">Se má na starosti správu základních stavu.</span><span class="sxs-lookup"><span data-stu-id="49e7b-120">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="49e7b-121">Podle následující diskuzi [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="49e7b-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="49e7b-122">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="49e7b-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="49e7b-123">`UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="49e7b-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="49e7b-124">Ukázka přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> k poskytování přístupu k zpráva verzi kodér zpráv.</span><span class="sxs-lookup"><span data-stu-id="49e7b-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="49e7b-125">Ukázka také přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> přerušit naše instanci <xref:System.ServiceModel.Channels.BufferManager> když přejde stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="49e7b-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="49e7b-126">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="49e7b-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="49e7b-127">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="49e7b-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="49e7b-128">Ověří argumenty konstruktoru a vytvoří cíl <xref:System.Net.EndPoint> na základě objektu <xref:System.ServiceModel.EndpointAddress> , je předaná.</span><span class="sxs-lookup"><span data-stu-id="49e7b-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="49e7b-129">Přepsané <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soketu, který se používá k odeslání zprávy do tohoto <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="49e7b-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 <span data-ttu-id="49e7b-130">Kanál je možné uzavřít řádně nebo ungracefully.</span><span class="sxs-lookup"><span data-stu-id="49e7b-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="49e7b-131">Pokud je kanál řádně uzavřen soketu se zavře a je volána v základní třídě `OnClose` metoda.</span><span class="sxs-lookup"><span data-stu-id="49e7b-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="49e7b-132">Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěna.</span><span class="sxs-lookup"><span data-stu-id="49e7b-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="49e7b-133">Implementace `Send()` a `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="49e7b-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="49e7b-134">To rozdělí na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="49e7b-134">This breaks down into two main sections.</span></span> <span data-ttu-id="49e7b-135">Nejprve serializovat zprávy do bajtového pole:</span><span class="sxs-lookup"><span data-stu-id="49e7b-135">First serialize the message into a byte array:</span></span>  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="49e7b-136">Potom odešlete Výsledná data v drátové síti:</span><span class="sxs-lookup"><span data-stu-id="49e7b-136">Then send the resulting data on the wire:</span></span>  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="49e7b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="49e7b-137">See Also</span></span>  
 [<span data-ttu-id="49e7b-138">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="49e7b-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)
