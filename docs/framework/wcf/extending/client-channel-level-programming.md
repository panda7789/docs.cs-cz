---
title: Programování na úrovni kanálu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923263"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="9a104-102">Programování na úrovni kanálu klienta</span><span class="sxs-lookup"><span data-stu-id="9a104-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="9a104-103">Toto téma popisuje, jak psát aplikace klienta Windows Communication Foundation (WCF) bez použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> třídy a jeho přidruženého objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="9a104-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="9a104-104">Odesílání zpráv</span><span class="sxs-lookup"><span data-stu-id="9a104-104">Sending Messages</span></span>  
 <span data-ttu-id="9a104-105">Až bude připravená pro zasílání zpráv a příjem a zpracování odpovědi, se vyžaduje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="9a104-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="9a104-106">Vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="9a104-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="9a104-107">Vytvoření objektu pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="9a104-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="9a104-108">Vytvoření kanálu.</span><span class="sxs-lookup"><span data-stu-id="9a104-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="9a104-109">Odešle žádost a čtení odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9a104-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="9a104-110">Zavřete všechny objekty kanálu.</span><span class="sxs-lookup"><span data-stu-id="9a104-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="9a104-111">Vytvoření vazby</span><span class="sxs-lookup"><span data-stu-id="9a104-111">Creating a Binding</span></span>  
 <span data-ttu-id="9a104-112">Podobně jako přijímající případu (naleznete v tématu [programování na úrovni kanálu služby](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), odesílání zpráv začíná tím, že vytvoříte vazbu.</span><span class="sxs-lookup"><span data-stu-id="9a104-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="9a104-113">Tento příklad vytvoří nový <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a přidá <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> jeho elementů kolekce.</span><span class="sxs-lookup"><span data-stu-id="9a104-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="9a104-114">Vytváření třídy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="9a104-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="9a104-115">Místo vytváření <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, tentokrát vytvoříme <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> voláním <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> u vazby, kde je parametr typu <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a104-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a104-116">Zatímco strana, která čeká na příchozí zprávy používají moduly pro naslouchání kanálů, objekty pro vytváření kanálů používá na straně, který inicializuje komunikaci k vytvoření kanálu.</span><span class="sxs-lookup"><span data-stu-id="9a104-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="9a104-117">Stejně jako moduly pro naslouchání kanálů objekty pro vytváření kanálů musí byly nejprve otevřeny dříve, než je možné.</span><span class="sxs-lookup"><span data-stu-id="9a104-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="9a104-118">Vytvoření kanálu</span><span class="sxs-lookup"><span data-stu-id="9a104-118">Creating a Channel</span></span>  
 <span data-ttu-id="9a104-119">Potom říkáme <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> k vytvoření <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="9a104-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="9a104-120">Toto volání přebírá adresu koncového bodu, se kterou chceme, aby na komunikaci pomocí nového kanálu vytváří.</span><span class="sxs-lookup"><span data-stu-id="9a104-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="9a104-121">Jakmile budeme mít nějaký kanál, říkáme Otevřít na něj umístíte ve stavu Připraveno pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="9a104-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="9a104-122">V závislosti na povaze přenos toto volání Open může iniciovat připojení ke koncovému bodu cíl nebo může nedělat nic vůbec v síti.</span><span class="sxs-lookup"><span data-stu-id="9a104-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="9a104-123">Odesílání požadavku a odpovědi pro čtení</span><span class="sxs-lookup"><span data-stu-id="9a104-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="9a104-124">Jakmile budeme mít otevřený kanálu, můžete vytvořit zprávu a pomocí metody požadavku kanálu můžete odeslat požadavek a čekat na odpověď opět online.</span><span class="sxs-lookup"><span data-stu-id="9a104-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="9a104-125">Po návratu tato metoda máme zprávu odpovědi, který jsme může číst a zjistěte, co byla odpověď koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9a104-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="9a104-126">Zavírání objektů</span><span class="sxs-lookup"><span data-stu-id="9a104-126">Closing Objects</span></span>  
 <span data-ttu-id="9a104-127">Aby se zabránilo nevrácení prostředků, můžeme zavřít objekty používané v rámci komunikace, když už nejsou povinné.</span><span class="sxs-lookup"><span data-stu-id="9a104-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="9a104-128">Následující příklad kódu ukazuje základní klienta se objekt pro vytváření kanálů pro odeslání zprávy a čtení odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9a104-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
