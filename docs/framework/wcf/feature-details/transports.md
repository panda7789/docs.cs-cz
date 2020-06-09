---
title: Přenosy ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598668"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="6c12c-102">Přenosy ve službě Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6c12c-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="6c12c-103">Transportní vrstva je na nejnižší úrovni zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="6c12c-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="6c12c-104">Hlavní přenos používaný v Windows Communication Foundation (WCF) jsou HTTP, HTTPS, TCP a pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="6c12c-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="6c12c-105">Témata v této části popisují výběr mezi těmito přenosy, konfiguraci přenosu a nastavení vlastností optimalizace.</span><span class="sxs-lookup"><span data-stu-id="6c12c-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="6c12c-106">WCF zahrnuje další přenosy.</span><span class="sxs-lookup"><span data-stu-id="6c12c-106">WCF includes additional transports.</span></span> <span data-ttu-id="6c12c-107">Informace o přenosech služby Řízení front zpráv (označované také jako MSMQ) najdete v tématu [fronty a spolehlivé relace](queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="6c12c-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="6c12c-108">Informace o přenosu peer-to-peer najdete v tématu [sítě peer-](peer-to-peer-networking.md)to-peer.</span><span class="sxs-lookup"><span data-stu-id="6c12c-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c12c-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6c12c-109">In This Section</span></span>  
 [<span data-ttu-id="6c12c-110">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="6c12c-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="6c12c-111">V této části najdete popis tří hlavních přenosů a důležitých informací o výběru jedné z nich.</span><span class="sxs-lookup"><span data-stu-id="6c12c-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="6c12c-112">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="6c12c-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="6c12c-113">Popisuje faktory, které je třeba zvážit při výběru prvku vazby s kódováním zpráv.</span><span class="sxs-lookup"><span data-stu-id="6c12c-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="6c12c-114">Streamování přenosu zpráv</span><span class="sxs-lookup"><span data-stu-id="6c12c-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="6c12c-115">V této části najdete popis postupu konfigurace přenosové vrstvy pro streamování.</span><span class="sxs-lookup"><span data-stu-id="6c12c-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="6c12c-116">Konfigurace HTTP a HTTPS</span><span class="sxs-lookup"><span data-stu-id="6c12c-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="6c12c-117">V této části najdete popis postupu konfigurace prvků vazby přenosu HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c12c-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="6c12c-118">Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací</span><span class="sxs-lookup"><span data-stu-id="6c12c-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="6c12c-119">Popisuje, jak používat vyhrazené WCFURL rezervace.</span><span class="sxs-lookup"><span data-stu-id="6c12c-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="6c12c-120">Přenosové kvóty</span><span class="sxs-lookup"><span data-stu-id="6c12c-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="6c12c-121">Popisuje okolnosti při nastavení kvót dostupných v transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="6c12c-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="6c12c-122">Práce s překlady adres (NAT) a bránami firewall</span><span class="sxs-lookup"><span data-stu-id="6c12c-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="6c12c-123">V této části najdete popis postupu konfigurace přenosové vrstvy při posílání nebo přijímání zpráv za bránou firewall nebo při překladu síťových adres (NAT).</span><span class="sxs-lookup"><span data-stu-id="6c12c-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="6c12c-124">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="6c12c-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="6c12c-125">Popisuje, jak používat součást služby WCF pro sdílení portů Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="6c12c-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6c12c-126">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="6c12c-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="6c12c-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6c12c-127">Related Sections</span></span>  
 [<span data-ttu-id="6c12c-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="6c12c-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="6c12c-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="6c12c-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
