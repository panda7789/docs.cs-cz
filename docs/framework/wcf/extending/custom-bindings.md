---
title: Vlastní vazby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 4a1174dd1cd6ea785c118c61428ba73d1347316c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663881"
---
# <a name="custom-bindings"></a><span data-ttu-id="c2b8d-102">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c2b8d-102">Custom Bindings</span></span>

<span data-ttu-id="c2b8d-103">Můžete použít <xref:System.ServiceModel.Channels.CustomBinding> třídy, pokud jedna z vazeb poskytovaných systémem nesplňuje požadavky na vaši službu.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="c2b8d-104">Všechny vazby jsou konstruovány ze seřazené sady elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="c2b8d-105">Vlastní vazby se dají ze sady prvků vazeb poskytovaných systémem nebo může obsahovat elementy uživatelem definované vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="c2b8d-106">Můžete použít vlastní vazby prvky, například umožní použít nové přenosy nebo kodérů na koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="c2b8d-107">Příklady práce, naleznete v tématu [vlastní vazby ukázky](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c2b8d-107">For working examples, see [Custom Binding Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="c2b8d-108">Další informace najdete v tématu [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="c2b8d-108">For more information, see [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="c2b8d-109">Vytvoření vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c2b8d-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="c2b8d-110">Vlastní vazby je vytvořený <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktoru z kolekce vazby prvky, které jsou "skládaný" v určitém pořadí:</span><span class="sxs-lookup"><span data-stu-id="c2b8d-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="c2b8d-111">V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> třídu, která umožňuje toku transakce.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="c2b8d-112">Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> třída, která poskytuje relaci a jak je definováno ve specifikaci WS-ReliableMessaging řazení mechanismy.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="c2b8d-113">Relaci můžete různé zprostředkovatele protokolu SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="c2b8d-114">Dále je volitelný <xref:System.ServiceModel.Channels.SecurityBindingElement> třída, která poskytuje funkce zabezpečení, jako je například autorizace, ověřování, ochrany a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="c2b8d-115">Dále je volitelný <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> třídu, která umožňuje mít dva stejně, jako duplexní komunikaci s přenosový protokol, který nepodporuje duplexní komunikaci nativně, jako je například HTTP.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="c2b8d-116">Dále je volitelný <xref:System.ServiceModel.Channels.OneWayBindingElement>) třída, která poskytuje jednosměrnou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="c2b8d-117">Dále je element vazby zabezpečení volitelné datového proudu, který může být jedna z následujících akcí.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="c2b8d-118">Dále je element vazby kódování zprávy vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="c2b8d-119">Můžete použít vlastní kodér zpráv nebo jeden ze tří vazby kódování zprávy:</span><span class="sxs-lookup"><span data-stu-id="c2b8d-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="c2b8d-120">V dolní části je prvek vyžaduje přenos.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="c2b8d-121">Můžete použít vlastní přenos nebo jednu z následujících elementů přenosové vazby, kterou poskytuje Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="c2b8d-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="c2b8d-122">Následující tabulka shrnuje možnosti pro každou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="c2b8d-123">Vrstva</span><span class="sxs-lookup"><span data-stu-id="c2b8d-123">Layer</span></span>|<span data-ttu-id="c2b8d-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c2b8d-124">Options</span></span>|<span data-ttu-id="c2b8d-125">Požadováno</span><span class="sxs-lookup"><span data-stu-id="c2b8d-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="c2b8d-126">Transakce</span><span class="sxs-lookup"><span data-stu-id="c2b8d-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="c2b8d-127">Ne</span><span class="sxs-lookup"><span data-stu-id="c2b8d-127">No</span></span>|
|<span data-ttu-id="c2b8d-128">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="c2b8d-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="c2b8d-129">Ne</span><span class="sxs-lookup"><span data-stu-id="c2b8d-129">No</span></span>|
|<span data-ttu-id="c2b8d-130">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c2b8d-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="c2b8d-131">Ne</span><span class="sxs-lookup"><span data-stu-id="c2b8d-131">No</span></span>|
|<span data-ttu-id="c2b8d-132">Kódování</span><span class="sxs-lookup"><span data-stu-id="c2b8d-132">Encoding</span></span>|<span data-ttu-id="c2b8d-133">Text, vlastní binární soubor, zpráv přenosu optimalizace mechanismus (MTOM),</span><span class="sxs-lookup"><span data-stu-id="c2b8d-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="c2b8d-134">Ano</span><span class="sxs-lookup"><span data-stu-id="c2b8d-134">Yes</span></span>|
|<span data-ttu-id="c2b8d-135">Přenos</span><span class="sxs-lookup"><span data-stu-id="c2b8d-135">Transport</span></span>|<span data-ttu-id="c2b8d-136">TCP, HTTP, HTTPS, pojmenované kanály (označované také jako IPC) Peer-to-Peer (P2P), služba Řízení front zpráv (MSMQ), vlastní</span><span class="sxs-lookup"><span data-stu-id="c2b8d-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="c2b8d-137">Ano</span><span class="sxs-lookup"><span data-stu-id="c2b8d-137">Yes</span></span>|

<span data-ttu-id="c2b8d-138">Kromě toho můžete definovat vlastní elementy vazby a vložit mezi všechny předchozí definované vrstvy.</span><span class="sxs-lookup"><span data-stu-id="c2b8d-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2b8d-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2b8d-139">See also</span></span>

- [<span data-ttu-id="c2b8d-140">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="c2b8d-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="c2b8d-141">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c2b8d-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c2b8d-142">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="c2b8d-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="c2b8d-143">Postupy: Přizpůsobení vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c2b8d-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
- [<span data-ttu-id="c2b8d-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c2b8d-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c2b8d-145">Vlastní vazba</span><span class="sxs-lookup"><span data-stu-id="c2b8d-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
