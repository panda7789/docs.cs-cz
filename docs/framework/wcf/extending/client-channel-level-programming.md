---
title: Programování na úrovni kanálu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 4f24c558b1d5303b2417416beb14555539f498ea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797267"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="8073c-102">Programování na úrovni kanálu klienta</span><span class="sxs-lookup"><span data-stu-id="8073c-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="8073c-103">Toto téma popisuje, jak vytvořit klientskou aplikaci Windows Communication Foundation (WCF) bez použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> třídy a jejího přidruženého objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="8073c-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="8073c-104">Odesílání zpráv</span><span class="sxs-lookup"><span data-stu-id="8073c-104">Sending Messages</span></span>  
 <span data-ttu-id="8073c-105">Aby bylo možné odesílat zprávy a přijímat a zpracovávat odpovědi, je nutné provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="8073c-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="8073c-106">Vytvořte vazbu.</span><span class="sxs-lookup"><span data-stu-id="8073c-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="8073c-107">Sestavte objekt pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="8073c-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="8073c-108">Vytvořte kanál.</span><span class="sxs-lookup"><span data-stu-id="8073c-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="8073c-109">Odešlete žádost a přečtěte odpověď.</span><span class="sxs-lookup"><span data-stu-id="8073c-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="8073c-110">Zavřete všechny objekty kanálu.</span><span class="sxs-lookup"><span data-stu-id="8073c-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="8073c-111">Vytvoření vazby</span><span class="sxs-lookup"><span data-stu-id="8073c-111">Creating a Binding</span></span>  
 <span data-ttu-id="8073c-112">Podobně jako u přijímajícího případu (viz [programování na úrovni kanálu služby](service-channel-level-programming.md)), odesílání zpráv začíná vytvořením vazby.</span><span class="sxs-lookup"><span data-stu-id="8073c-112">Similar to the receiving case (see [Service Channel-Level Programming](service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="8073c-113">Tento příklad vytvoří nový <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> přidá do kolekce elementů.</span><span class="sxs-lookup"><span data-stu-id="8073c-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="8073c-114">Vytvoření třídy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="8073c-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="8073c-115">Místo vytvoření <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, tentokrát <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> vytvoříme voláním <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na vazbu, kde je <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>parametr typu.</span><span class="sxs-lookup"><span data-stu-id="8073c-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8073c-116">Zatímco naslouchací procesy kanálu používají stranu, která čeká na příchozí zprávy, používají se strany kanálů, které iniciují komunikaci k vytvoření kanálu.</span><span class="sxs-lookup"><span data-stu-id="8073c-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="8073c-117">Stejně jako naslouchací procesy kanálu musí být nejprve otevřeny objekty pro vytváření kanálů, aby bylo možné je použít.</span><span class="sxs-lookup"><span data-stu-id="8073c-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="8073c-118">Vytvoření kanálu</span><span class="sxs-lookup"><span data-stu-id="8073c-118">Creating a Channel</span></span>  
 <span data-ttu-id="8073c-119">Pak zavolejte <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IRequestChannel>vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8073c-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="8073c-120">Toto volání přebírá adresu koncového bodu, se kterým chceme komunikovat pomocí nového vytvořeného kanálu.</span><span class="sxs-lookup"><span data-stu-id="8073c-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="8073c-121">Jakmile budeme mít kanál, zavoláme na něj otevřené, abychom ho umístili do stavu připraveného ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="8073c-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="8073c-122">V závislosti na povaze přenosu může toto volání Open iniciovat připojení k cílovému koncovému bodu nebo nemůže v síti vůbec nic dělat.</span><span class="sxs-lookup"><span data-stu-id="8073c-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="8073c-123">Odeslání žádosti a čtení odpovědi</span><span class="sxs-lookup"><span data-stu-id="8073c-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="8073c-124">Po otevření kanálu můžeme vytvořit zprávu a použít metodu žádosti kanálu k odeslání požadavku a počkat, až se odpověď vrátí zpět.</span><span class="sxs-lookup"><span data-stu-id="8073c-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="8073c-125">Když se tato metoda vrátí, máme zprávu s odpovědí, kterou můžeme přečíst a zjistit, co byla odpověď koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8073c-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="8073c-126">Zavření objektů</span><span class="sxs-lookup"><span data-stu-id="8073c-126">Closing Objects</span></span>  
 <span data-ttu-id="8073c-127">Aby se předešlo nevracení prostředků, zavřou se objekty používané v komunikacích, když už je nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="8073c-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="8073c-128">Následující příklad kódu ukazuje základního klienta využívajícího objekt pro vytváření kanálů k odeslání zprávy a načtení odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8073c-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
