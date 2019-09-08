---
title: 'Klient: Objekty pro vytváření kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3dfcca0d5492a3fa376ec184f4bdd9bfa03b53c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795860"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="1a6a6-102">Klient: Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="1a6a6-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="1a6a6-103">Toto téma popisuje vytváření kanálů a kanálů kanálu.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="1a6a6-104">Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="1a6a6-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="1a6a6-105">Továrny kanálů jsou zodpovědné za vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="1a6a6-106">Kanály vytvořené pomocí kanálů kanálu se používají pro posílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="1a6a6-107">Tyto kanály jsou zodpovědné za získání zprávy z vrstvy výše, provádění jakéhokoli zpracování je nezbytné a následné odeslání zprávy do vrstvy níže.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="1a6a6-108">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="1a6a6-109">![Klientské továrny a kanály](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="1a6a6-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="1a6a6-110">Objekt pro vytváření kanálů vytvoří kanály.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="1a6a6-111">Po uzavření jsou objekty kanálů zodpovědné za uzavírání všech kanálů, které vytvořili, které ještě nejsou uzavřené.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="1a6a6-112">Model je tady asymetrická, protože když se spustí naslouchací proces kanálu, zastaví se jenom příjem nových kanálů, ale existující kanály zůstanou otevřené, aby mohli dál přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="1a6a6-113">WCF poskytuje pomocníky pro základní třídy pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="1a6a6-114">(Diagram pomocných tříd kanálu popsaných v tomto tématu najdete v tématu [Přehled modelu kanálů](channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="1a6a6-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="1a6a6-115">Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynutila Stavový počítač popsaný v kroku 2 [Vývoj kanálů.](developing-channels.md) <xref:System.ServiceModel.Channels.CommunicationObject></span><span class="sxs-lookup"><span data-stu-id="1a6a6-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="1a6a6-116">Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje sjednocenou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase></span><span class="sxs-lookup"><span data-stu-id="1a6a6-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a6a6-117">Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třída, která implementuje <xref:System.ServiceModel.Channels.IChannel>. <xref:System.ServiceModel.Channels.ChannelManagerBase></span><span class="sxs-lookup"><span data-stu-id="1a6a6-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="1a6a6-118"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a<xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje přetíženído`OnCreateChannel` jedné abstraktní metody. `CreateChannel`</span><span class="sxs-lookup"><span data-stu-id="1a6a6-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="1a6a6-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje<xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="1a6a6-120">Je potřeba se starat o základní správu stavu.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="1a6a6-121">Následující diskuze jsou založené [na přenosu: Ukázka](../samples/transport-udp.md) UDP</span><span class="sxs-lookup"><span data-stu-id="1a6a6-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="1a6a6-122">Vytvoření objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="1a6a6-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="1a6a6-123">Je `UdpChannelFactory` odvozen z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="1a6a6-124">Vzor přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> , aby poskytoval přístup k verzi zprávy kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="1a6a6-125">Tato ukázka také přepisuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> , aby <xref:System.ServiceModel.Channels.BufferManager> při přechodu na stav počítače nemohly vztrhnout naši instanci.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="1a6a6-126">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="1a6a6-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="1a6a6-127">`UdpOutputChannel` Implementuje<xref:System.ServiceModel.Channels.IOutputChannel>rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="1a6a6-128">Konstruktor ověřuje argumenty a vytvoří cílový <xref:System.Net.EndPoint> objekt na základě <xref:System.ServiceModel.EndpointAddress> předaného objektu.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="1a6a6-129">Přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soket, který slouží k posílání zpráv <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="1a6a6-130">Kanál může být řádně uzavřený nebo neřádný.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="1a6a6-131">Pokud je kanál řádně uzavřený, soket je uzavřen a volání metody základní třídy `OnClose` je provedeno.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="1a6a6-132">Pokud to vyvolá výjimku, zavolá `Abort` infrastruktura, aby zajistila vyčištění kanálu.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="1a6a6-133">`Send()` Implementujte `BeginSend()`a ./ `EndSend()`</span><span class="sxs-lookup"><span data-stu-id="1a6a6-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="1a6a6-134">Tato část se rozdělí na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="1a6a6-134">This breaks down into two main sections.</span></span> <span data-ttu-id="1a6a6-135">Nejdřív zaserializovat zprávu do bajtového pole:</span><span class="sxs-lookup"><span data-stu-id="1a6a6-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="1a6a6-136">Pak odešlete výsledná data na kabel:</span><span class="sxs-lookup"><span data-stu-id="1a6a6-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a6a6-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a6a6-137">See also</span></span>

- [<span data-ttu-id="1a6a6-138">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="1a6a6-138">Developing Channels</span></span>](developing-channels.md)
