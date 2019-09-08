---
title: Vlastní vazby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: a4b3abfe9be25c9080a362eb4a6e4c7b070528f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797233"
---
# <a name="custom-bindings"></a><span data-ttu-id="96a85-102">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="96a85-102">Custom Bindings</span></span>

<span data-ttu-id="96a85-103">Třídu můžete použít, <xref:System.ServiceModel.Channels.CustomBinding> když jedna z vazeb poskytnutých systémem nesplňuje požadavky vaší služby.</span><span class="sxs-lookup"><span data-stu-id="96a85-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="96a85-104">Všechny vazby jsou zhotoveny z seřazené sady prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="96a85-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="96a85-105">Vlastní vazby mohou být sestaveny ze sady prvků vazby poskytovaných systémem nebo mohou zahrnovat uživatelsky definované vlastní prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="96a85-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="96a85-106">Můžete použít vlastní prvky vazby, například k povolení použití nových přenosů nebo kodérů na koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="96a85-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="96a85-107">Pracovní příklady najdete v tématu [vlastní ukázky vazeb](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="96a85-107">For working examples, see [Custom Binding Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="96a85-108">Další informace najdete v tématu [ \<CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="96a85-108">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="96a85-109">Konstrukce vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="96a85-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="96a85-110">Vlastní vazba je vytvořena pomocí <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktoru z kolekce prvků vazby, které jsou "skládané" v určitém pořadí:</span><span class="sxs-lookup"><span data-stu-id="96a85-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="96a85-111">V horní části je volitelná <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> třída, která umožňuje přesměrovat transakce.</span><span class="sxs-lookup"><span data-stu-id="96a85-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="96a85-112">Další je volitelná <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> třída, která poskytuje mechanismy pro relaci a řazení, jak je definováno ve specifikaci WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="96a85-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="96a85-113">Relace může vzájemně přenášet zprostředkovatele SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="96a85-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="96a85-114">Další je volitelná <xref:System.ServiceModel.Channels.SecurityBindingElement> třída, která poskytuje funkce zabezpečení, jako je například autorizace, ověřování, ochrana a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="96a85-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="96a85-115">Další je volitelná <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> třída, která umožňuje obousměrnou duplexní komunikaci s transportním protokolem, který nativně nepodporuje duplexní komunikaci, jako je například http.</span><span class="sxs-lookup"><span data-stu-id="96a85-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="96a85-116">Další je volitelná <xref:System.ServiceModel.Channels.OneWayBindingElement>třída, která poskytuje jednosměrnou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="96a85-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="96a85-117">Další je volitelný element vazby zabezpečení datového proudu, který může být jeden z následujících.</span><span class="sxs-lookup"><span data-stu-id="96a85-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="96a85-118">Další je povinný element vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="96a85-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="96a85-119">Můžete použít svůj vlastní kodér zpráv nebo jednu ze tří vazeb kódování zpráv:</span><span class="sxs-lookup"><span data-stu-id="96a85-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="96a85-120">V dolní části je požadovaný transportní prvek.</span><span class="sxs-lookup"><span data-stu-id="96a85-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="96a85-121">Můžete použít vlastní přenos nebo jeden z následujících elementů transportních vazeb Windows Communication Foundation (WCF) poskytuje:</span><span class="sxs-lookup"><span data-stu-id="96a85-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="96a85-122">Následující tabulka shrnuje možnosti pro každou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="96a85-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="96a85-123">Vrstva</span><span class="sxs-lookup"><span data-stu-id="96a85-123">Layer</span></span>|<span data-ttu-id="96a85-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="96a85-124">Options</span></span>|<span data-ttu-id="96a85-125">Požadováno</span><span class="sxs-lookup"><span data-stu-id="96a85-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="96a85-126">Transakce</span><span class="sxs-lookup"><span data-stu-id="96a85-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="96a85-127">Ne</span><span class="sxs-lookup"><span data-stu-id="96a85-127">No</span></span>|
|<span data-ttu-id="96a85-128">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="96a85-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="96a85-129">Ne</span><span class="sxs-lookup"><span data-stu-id="96a85-129">No</span></span>|
|<span data-ttu-id="96a85-130">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="96a85-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="96a85-131">Ne</span><span class="sxs-lookup"><span data-stu-id="96a85-131">No</span></span>|
|<span data-ttu-id="96a85-132">Kódování</span><span class="sxs-lookup"><span data-stu-id="96a85-132">Encoding</span></span>|<span data-ttu-id="96a85-133">Text, binární, mechanizmus pro optimalizaci přenosu zpráv (MTOM), vlastní</span><span class="sxs-lookup"><span data-stu-id="96a85-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="96a85-134">Ano</span><span class="sxs-lookup"><span data-stu-id="96a85-134">Yes</span></span>|
|<span data-ttu-id="96a85-135">Přepravu</span><span class="sxs-lookup"><span data-stu-id="96a85-135">Transport</span></span>|<span data-ttu-id="96a85-136">TCP, HTTP, HTTPS, pojmenované kanály (označované také jako IPC), peer-to-peer (P2P), řízení front zpráv (označované také jako MSMQ), vlastní</span><span class="sxs-lookup"><span data-stu-id="96a85-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="96a85-137">Ano</span><span class="sxs-lookup"><span data-stu-id="96a85-137">Yes</span></span>|

<span data-ttu-id="96a85-138">Kromě toho můžete definovat vlastní prvky vazby a vkládat je mezi kteroukoli z předchozích definovaných vrstev.</span><span class="sxs-lookup"><span data-stu-id="96a85-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="96a85-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96a85-139">See also</span></span>

- [<span data-ttu-id="96a85-140">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="96a85-140">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="96a85-141">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="96a85-141">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="96a85-142">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="96a85-142">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="96a85-143">Postupy: Přizpůsobení systémem poskytované vazby</span><span class="sxs-lookup"><span data-stu-id="96a85-143">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [<span data-ttu-id="96a85-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96a85-144">\<customBinding></span></span>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="96a85-145">Vlastní vazba</span><span class="sxs-lookup"><span data-stu-id="96a85-145">Custom Binding</span></span>](../samples/custom-binding.md)
