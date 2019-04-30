---
title: Přenosy ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933728"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="d201b-102">Přenosy ve službě Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d201b-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="d201b-103">Přenosové vrstvy je na nejnižší úrovni zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="d201b-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="d201b-104">Hlavní přenosy použít ve Windows Communication Foundation (WCF) jsou HTTP, HTTPS, TCP a pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="d201b-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="d201b-105">Témata v této části popisují výběru mezi tyto přenosy, přenos konfigurace a nastavení vlastnosti optimalizace.</span><span class="sxs-lookup"><span data-stu-id="d201b-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="d201b-106">WCF obsahuje další přenosy.</span><span class="sxs-lookup"><span data-stu-id="d201b-106">WCF includes additional transports.</span></span> <span data-ttu-id="d201b-107">Informace o přenosu služby Řízení front zpráv (MSMQ) najdete v tématu [fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="d201b-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="d201b-108">Informace o přenosu peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="d201b-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d201b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d201b-109">In This Section</span></span>  
 [<span data-ttu-id="d201b-110">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="d201b-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="d201b-111">Popisuje tři hlavní přenosy a důležité informace při výběru jednoho.</span><span class="sxs-lookup"><span data-stu-id="d201b-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="d201b-112">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="d201b-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="d201b-113">Popisuje faktory, které je třeba zvážit při výběru element vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="d201b-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="d201b-114">Streamování přenosu zpráv</span><span class="sxs-lookup"><span data-stu-id="d201b-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="d201b-115">Popisuje postup konfigurace přenosové vrstvy provedete streamování.</span><span class="sxs-lookup"><span data-stu-id="d201b-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="d201b-116">Konfigurace HTTP a HTTPS</span><span class="sxs-lookup"><span data-stu-id="d201b-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="d201b-117">Popisuje postup konfigurace elementů vazby přenosu HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d201b-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="d201b-118">Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací</span><span class="sxs-lookup"><span data-stu-id="d201b-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="d201b-119">Popisuje, jak používat s omezením pomocí specifikátoru WCFURL rezervace.</span><span class="sxs-lookup"><span data-stu-id="d201b-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="d201b-120">Přenosové kvóty</span><span class="sxs-lookup"><span data-stu-id="d201b-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="d201b-121">Popisuje důležité informace v nastavení kvót, které jsou k dispozici v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="d201b-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="d201b-122">Práce s překlady adres (NAT) a bránami firewall</span><span class="sxs-lookup"><span data-stu-id="d201b-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="d201b-123">Popisuje postup konfigurace přenosové vrstvy, když se zprávy odesílané nebo přijímané za bránou firewall nebo překlad síťových adres (NAT) je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d201b-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="d201b-124">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d201b-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="d201b-125">Popisuje postup používání sdílení portů Net.TCP komponent služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d201b-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d201b-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d201b-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="d201b-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d201b-127">Related Sections</span></span>  
 [<span data-ttu-id="d201b-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="d201b-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="d201b-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d201b-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
