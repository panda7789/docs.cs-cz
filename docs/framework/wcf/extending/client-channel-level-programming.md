---
title: "Programování na úrovni kanálu klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a6ffe482c8d04314b79ee5bb7029d2583c56c363
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="d75d6-102">Programování na úrovni kanálu klienta</span><span class="sxs-lookup"><span data-stu-id="d75d6-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="d75d6-103">Toto téma popisuje, jak napsat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientská aplikace bez použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> třídy a jeho přidružený objekt modelu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-103">This topic describes how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="d75d6-104">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="d75d6-104">Sending Messages</span></span>  
 <span data-ttu-id="d75d6-105">Aby byl připraven k odesílání zpráv a přijímat a zpracovávat odpovědi, jsou požadovány následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d75d6-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1.  <span data-ttu-id="d75d6-106">Vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="d75d6-106">Create a binding.</span></span>  
  
2.  <span data-ttu-id="d75d6-107">Vytvoření postupu kanálu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-107">Build a channel factory.</span></span>  
  
3.  <span data-ttu-id="d75d6-108">Vytvoření kanálu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-108">Create a channel.</span></span>  
  
4.  <span data-ttu-id="d75d6-109">Odeslání požadavku a odpovědi pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d75d6-109">Send a request and read the reply.</span></span>  
  
5.  <span data-ttu-id="d75d6-110">Zavřete všechny objekty kanálu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="d75d6-111">Vytváření vazby</span><span class="sxs-lookup"><span data-stu-id="d75d6-111">Creating a Binding</span></span>  
 <span data-ttu-id="d75d6-112">Podobně jako přijímající případ (najdete v části [programování na úrovni služby kanálů](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), odesílání zpráv spustí tak, že vytvoříte vazbu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="d75d6-113">Tento příklad vytvoří novou <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a přidá <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> k jeho elementy kolekce.</span><span class="sxs-lookup"><span data-stu-id="d75d6-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="d75d6-114">Vytváření ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="d75d6-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="d75d6-115">Místo vytváření <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, momentálně se nám vytvořit <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> voláním <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na vazby, kde parametr typu je <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d75d6-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d75d6-116">Při naslouchacího procesu kanálu se používá na straně, která čeká na příchozí zprávy, objekty Factory kanál používá na straně, který iniciuje komunikace k vytvoření kanálu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="d75d6-117">Stejně jako naslouchací procesy kanál objekty Factory kanál musí být otevřeno nejprve předtím, než mohou být použity.</span><span class="sxs-lookup"><span data-stu-id="d75d6-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="d75d6-118">Vytvoření kanálu</span><span class="sxs-lookup"><span data-stu-id="d75d6-118">Creating a Channel</span></span>  
 <span data-ttu-id="d75d6-119">Potom říkáme <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> k vytvoření <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="d75d6-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="d75d6-120">Toto volání má adresu koncového bodu, se kterým chcete komunikovat pomocí nového kanálu vytváří.</span><span class="sxs-lookup"><span data-stu-id="d75d6-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="d75d6-121">Jakmile jsme kanál, jsme zavolat otevřete vložit soubor do stavu připraven na komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d75d6-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="d75d6-122">V závislosti na povaze přenos volání otevřete mohou iniciovat připojení ke koncovému bodu cílový nebo může nedělat nic vůbec v síti.</span><span class="sxs-lookup"><span data-stu-id="d75d6-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="d75d6-123">Odesílání požadavku a odpovědi pro čtení</span><span class="sxs-lookup"><span data-stu-id="d75d6-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="d75d6-124">Po máme otevřenou kanál, můžeme vytvořit zprávu a použijete metodu požadavku kanálu k odeslání požadavku a čekat na odpověď opět online.</span><span class="sxs-lookup"><span data-stu-id="d75d6-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="d75d6-125">Po návratu tato metoda máme odpovědi, která jsme může číst a zjistěte, co byla odpověď pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d75d6-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="d75d6-126">Zavírání objektů</span><span class="sxs-lookup"><span data-stu-id="d75d6-126">Closing Objects</span></span>  
 <span data-ttu-id="d75d6-127">Aby se zabránilo úniku prostředky, můžeme zavřít objekty použitých při komunikaci, pokud už je potřeba.</span><span class="sxs-lookup"><span data-stu-id="d75d6-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="d75d6-128">Následující příklad kódu ukazuje základní klient používá k odeslání zprávy a čtení odpovědi kanálu.</span><span class="sxs-lookup"><span data-stu-id="d75d6-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
