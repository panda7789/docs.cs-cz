---
title: "Vlastní vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a3da437f742c46a2229aa00db732b5437ec15e3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="custom-bindings"></a><span data-ttu-id="50c4b-102">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="50c4b-102">Custom Bindings</span></span>
<span data-ttu-id="50c4b-103">Můžete použít <xref:System.ServiceModel.Channels.CustomBinding> třídy, pokud jeden z vazby poskytované systémem nesplňuje požadavky na služby.</span><span class="sxs-lookup"><span data-stu-id="50c4b-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="50c4b-104">Všechny vazby se vytvářejí na základě uspořádanou sadu elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="50c4b-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="50c4b-105">Vlastní vazby jde integrovat přímo ze sady elementů vazby poskytované systémem nebo může zahrnovat prvky uživatelem definované vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="50c4b-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="50c4b-106">Vlastní vazby elementů, například můžete použít k povolení použití nové přenosy nebo kodéry na koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="50c4b-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="50c4b-107">Pracovní příklady najdete v tématu [vazby ukázky vlastních](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span><span class="sxs-lookup"><span data-stu-id="50c4b-107">For working examples, see [Custom Binding Samples](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="50c4b-108">[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="50c4b-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="50c4b-109">Vytváření vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="50c4b-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="50c4b-110">Vlastní vazby je vytvořený pomocí <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktor z kolekce elementů, které jsou "skládaný" v určitém pořadí vazby:</span><span class="sxs-lookup"><span data-stu-id="50c4b-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="50c4b-111">V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> třídu, která umožňuje toku transakcí.</span><span class="sxs-lookup"><span data-stu-id="50c4b-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="50c4b-112">Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> třídu, která poskytuje relaci a jak jsou definovány ve specifikaci WS-ReliableMessaging řazení mechanismy.</span><span class="sxs-lookup"><span data-stu-id="50c4b-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="50c4b-113">Relaci můžete křížová zprostředkovatele protokolu SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="50c4b-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="50c4b-114">Dále je volitelný <xref:System.ServiceModel.Channels.SecurityBindingElement> třídu, která poskytuje funkce zabezpečení, jako je například autorizace, ověřování, ochrana a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="50c4b-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
-   <span data-ttu-id="50c4b-115">Dále je volitelný <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> třídu, která umožňuje mít dva způsobem duplexní komunikace s transportní protokol, který nepodporuje duplexní komunikace nativně, jako je například HTTP.</span><span class="sxs-lookup"><span data-stu-id="50c4b-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
-   <span data-ttu-id="50c4b-116">Dále je volitelný <xref:System.ServiceModel.Channels.OneWayBindingElement>) třídu, která poskytuje jednosměrnou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="50c4b-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
-   <span data-ttu-id="50c4b-117">Další je na prvek vazby zabezpečení volitelné datový proud, který může být jedna z následujících.</span><span class="sxs-lookup"><span data-stu-id="50c4b-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="50c4b-118">Dále je požadované zpráva kódování prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="50c4b-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="50c4b-119">Můžete použít vlastní kodér zpráv nebo jeden z tři vazby kódování zprávy:</span><span class="sxs-lookup"><span data-stu-id="50c4b-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="50c4b-120">V dolní části je element požadované přenosu.</span><span class="sxs-lookup"><span data-stu-id="50c4b-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="50c4b-121">Můžete použít vlastní přenos nebo jeden z následujících elementů přenosové vazby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje:</span><span class="sxs-lookup"><span data-stu-id="50c4b-121">You can use your own transport or one of the following transport binding elements [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides:</span></span>  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="50c4b-122">Následující tabulka shrnuje možnosti pro jednotlivé úrovně.</span><span class="sxs-lookup"><span data-stu-id="50c4b-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="50c4b-123">Vrstva</span><span class="sxs-lookup"><span data-stu-id="50c4b-123">Layer</span></span>|<span data-ttu-id="50c4b-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="50c4b-124">Options</span></span>|<span data-ttu-id="50c4b-125">Požadováno</span><span class="sxs-lookup"><span data-stu-id="50c4b-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="50c4b-126">Transakce</span><span class="sxs-lookup"><span data-stu-id="50c4b-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="50c4b-127">Ne</span><span class="sxs-lookup"><span data-stu-id="50c4b-127">No</span></span>|  
|<span data-ttu-id="50c4b-128">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="50c4b-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="50c4b-129">Ne</span><span class="sxs-lookup"><span data-stu-id="50c4b-129">No</span></span>|  
|<span data-ttu-id="50c4b-130">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="50c4b-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="50c4b-131">Ne</span><span class="sxs-lookup"><span data-stu-id="50c4b-131">No</span></span>|  
|<span data-ttu-id="50c4b-132">Kódování</span><span class="sxs-lookup"><span data-stu-id="50c4b-132">Encoding</span></span>|<span data-ttu-id="50c4b-133">Text, vlastní binární zpráva přenosu optimalizace mechanismus (MTOM),</span><span class="sxs-lookup"><span data-stu-id="50c4b-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="50c4b-134">Ano</span><span class="sxs-lookup"><span data-stu-id="50c4b-134">Yes</span></span>|  
|<span data-ttu-id="50c4b-135">Přenos</span><span class="sxs-lookup"><span data-stu-id="50c4b-135">Transport</span></span>|<span data-ttu-id="50c4b-136">TCP, HTTP, HTTPS, pojmenované kanály (také označované jako IPC), Peer-to-Peer (P2P), služba Řízení front zpráv (MSMQ), vlastní</span><span class="sxs-lookup"><span data-stu-id="50c4b-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="50c4b-137">Ano</span><span class="sxs-lookup"><span data-stu-id="50c4b-137">Yes</span></span>|  
  
 <span data-ttu-id="50c4b-138">Kromě toho můžete definovat vlastní prvky vazby a vložte je mezi některé z předchozích definované vrstvy.</span><span class="sxs-lookup"><span data-stu-id="50c4b-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c4b-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="50c4b-139">See Also</span></span>  
 [<span data-ttu-id="50c4b-140">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="50c4b-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="50c4b-141">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50c4b-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="50c4b-142">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="50c4b-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="50c4b-143">Postupy: Přizpůsobení vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="50c4b-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [<span data-ttu-id="50c4b-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="50c4b-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="50c4b-145">Vlastní vazba</span><span class="sxs-lookup"><span data-stu-id="50c4b-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
