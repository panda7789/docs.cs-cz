---
title: 'Klient: Objekty pro vytváření kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185697"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="e4dba-102">Klient: Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="e4dba-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="e4dba-103">Toto téma popisuje vytvoření kanálu továrny a kanály.</span><span class="sxs-lookup"><span data-stu-id="e4dba-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="e4dba-104">Objekty pro vytváření kanálů a kanály</span><span class="sxs-lookup"><span data-stu-id="e4dba-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="e4dba-105">Továrny kanálu jsou zodpovědné za vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="e4dba-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="e4dba-106">Kanály vytvořené továrnami kanálů se používají pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="e4dba-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="e4dba-107">Tyto kanály jsou zodpovědné za získání zprávy z výše uvedené vrstvy, provádění jakéhokoli zpracování je nezbytné, pak odeslání zprávy do vrstvy níže.</span><span class="sxs-lookup"><span data-stu-id="e4dba-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="e4dba-108">Následující obrázek ilustruje tento proces.</span><span class="sxs-lookup"><span data-stu-id="e4dba-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="e4dba-109">![Klientské továrny a kanály](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="e4dba-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="e4dba-110">Factory kanálu vytvoří kanály.</span><span class="sxs-lookup"><span data-stu-id="e4dba-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="e4dba-111">Při zavření jsou továrny kanálů zodpovědné za uzavření všech kanálů, které vytvořily a které ještě nejsou uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="e4dba-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="e4dba-112">Všimněte si, že model je asymetrický, protože když je naslouchací proces kanálu uzavřen, přestane přijímat pouze nové kanály, ale ponechá existující kanály otevřené, aby mohly pokračovat v přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="e4dba-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="e4dba-113">WCF poskytuje základní třídy pomocné soubory pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="e4dba-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="e4dba-114">(Diagram tříd pomocných kanálů popsaných v tomto tématu naleznete v tématu [Přehled modelu kanálu](channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="e4dba-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="e4dba-115">Třída <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavový počítač popsaný v kroku 2 [vývoj kanálů](developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="e4dba-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="e4dba-116">Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4dba-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e4dba-117">Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> pracuje ve <xref:System.ServiceModel.Channels.ChannelBase>spojení s , což je <xref:System.ServiceModel.Channels.IChannel>základní třída, která implementuje .</span><span class="sxs-lookup"><span data-stu-id="e4dba-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="e4dba-118">Třída <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.IChannelFactory> a `CreateChannel` konsoliduje `OnCreateChannel` přetížení do jedné abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="e4dba-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="e4dba-119">Třída <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="e4dba-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="e4dba-120">Stará se o základní státní řízení.</span><span class="sxs-lookup"><span data-stu-id="e4dba-120">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="e4dba-121">Následující diskuse je založena na [transportu: UDP](../samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="e4dba-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="e4dba-122">Vytvoření továrny kanálu</span><span class="sxs-lookup"><span data-stu-id="e4dba-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="e4dba-123">Pochází `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="e4dba-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="e4dba-124">Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> poskytnout přístup k verzi zprávy kodéru zprávy.</span><span class="sxs-lookup"><span data-stu-id="e4dba-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="e4dba-125">Ukázka také <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> přepíše strhnout <xref:System.ServiceModel.Channels.BufferManager> naši instanci při přechodu stavového počítače.</span><span class="sxs-lookup"><span data-stu-id="e4dba-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="e4dba-126">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="e4dba-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="e4dba-127">Nářadí `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="e4dba-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="e4dba-128">Konstruktor ověří argumenty a vytvoří <xref:System.Net.EndPoint> cílový objekt <xref:System.ServiceModel.EndpointAddress> na základě, který je předán palců</span><span class="sxs-lookup"><span data-stu-id="e4dba-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="e4dba-129">Přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soket, který slouží <xref:System.Net.EndPoint>k odesílání zpráv do tohoto .</span><span class="sxs-lookup"><span data-stu-id="e4dba-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="e4dba-130">Kanál může být uzavřen elegantně nebo ungracefully.</span><span class="sxs-lookup"><span data-stu-id="e4dba-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="e4dba-131">Pokud je kanál řádně uzavřen, soket je uzavřen a `OnClose` je provedeno volání metody základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e4dba-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="e4dba-132">Pokud to vyvolá výjimku, `Abort` volání infrastruktury k zajištění kanálu je vyčištěna.</span><span class="sxs-lookup"><span data-stu-id="e4dba-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="e4dba-133">`Send()` Implementovat `BeginSend()` / `EndSend()`a .</span><span class="sxs-lookup"><span data-stu-id="e4dba-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="e4dba-134">To se rozdělí na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="e4dba-134">This breaks down into two main sections.</span></span> <span data-ttu-id="e4dba-135">Nejprve serialize zprávy do bajtového pole:</span><span class="sxs-lookup"><span data-stu-id="e4dba-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="e4dba-136">Poté odešlete výsledná data na drát:</span><span class="sxs-lookup"><span data-stu-id="e4dba-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4dba-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4dba-137">See also</span></span>

- [<span data-ttu-id="e4dba-138">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="e4dba-138">Developing Channels</span></span>](developing-channels.md)
