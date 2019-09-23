---
title: WS-* Protocols – gRPC pro vývojáře WCF
description: Kontrola protokolů WS-* podporovaných službou WCF a alternativami, které jsou k dispozici v gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cd9af401fc46297fc0c67f5b3e5d6b34177d6a87
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184027"
---
# <a name="ws--protocols"></a><span data-ttu-id="6c188-103">\* Protokoly WS</span><span class="sxs-lookup"><span data-stu-id="6c188-103">WS-\* protocols</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6c188-104">Jednou ze skutečných výhod práce s Windows Communication Foundation (WCF) bylo, že se podporovalo mnoho existujících protokolů _WS-\*_  Standard.</span><span class="sxs-lookup"><span data-stu-id="6c188-104">One of the real benefits of working with Windows Communication Foundation (WCF) was that it supported many of the existing _WS-\*_ standard protocols.</span></span> <span data-ttu-id="6c188-105">Tato část stručně popisuje, jak gRPC spravuje stejné WS-\* Protocols a diskutuje, jaké možnosti jsou k dispozici, pokud neexistuje žádná alternativa.</span><span class="sxs-lookup"><span data-stu-id="6c188-105">This section will briefly cover how gRPC manages the same WS-\* protocols and discuss what options are available when there's no alternative.</span></span>

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a><span data-ttu-id="6c188-106">Výměna metadat – WS-Policy, WS-Discovery atd.</span><span class="sxs-lookup"><span data-stu-id="6c188-106">Metadata Exchange - WS-Policy, WS-Discovery, and so on</span></span>

<span data-ttu-id="6c188-107">Služby SOAP zveřejňují dokumenty schématu WSDL (Web Services Description Language) s informacemi, jako jsou formáty dat, operace nebo možnosti komunikace.</span><span class="sxs-lookup"><span data-stu-id="6c188-107">SOAP services expose Web Services Description Language (WSDL) schema documents with information such as data formats, operations, or communication options.</span></span> <span data-ttu-id="6c188-108">Toto schéma se dá použít k vygenerování kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="6c188-108">This schema could be used to generate the client code.</span></span>

<span data-ttu-id="6c188-109">gRPC funguje nejlépe, když se servery a klienti generují ze stejných `.proto` souborů, ale volitelné rozšíření reflexe serveru poskytuje způsob, jak vystavit dynamické informace z běžícího serveru.</span><span class="sxs-lookup"><span data-stu-id="6c188-109">gRPC works best when servers and clients are generated from the same `.proto` files, but a server reflection optional extension does provide a way to expose dynamic information from a running server.</span></span> <span data-ttu-id="6c188-110">Další informace naleznete v článku balíček NuGet [Grpc. reflexe](https://nuget.org/packages/Grpc.Reflection) a [reflexe serveru Grpc C# ](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .</span><span class="sxs-lookup"><span data-stu-id="6c188-110">For more information, see the [Grpc.Reflection](https://nuget.org/packages/Grpc.Reflection) NuGet package and the [gRPC C# Server Reflection](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) article.</span></span>

<span data-ttu-id="6c188-111">Protokol WS-Discovery se používá k vyhledání služeb v místní síti.</span><span class="sxs-lookup"><span data-stu-id="6c188-111">The WS-Discovery protocol is used to locate services on a local network.</span></span> <span data-ttu-id="6c188-112">služby gRPC se obecně nacházejí v systému DNS nebo v registru služby, jako je Consul nebo ZooKeeper.</span><span class="sxs-lookup"><span data-stu-id="6c188-112">gRPC services are generally located using DNS or a service registry such as Consul or ZooKeeper.</span></span>

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a><span data-ttu-id="6c188-113">Zabezpečení – WS-Security, WS-Federation, šifrování XML atd.</span><span class="sxs-lookup"><span data-stu-id="6c188-113">Security – WS-Security, WS-Federation, XML Encryption, and so on</span></span>

<span data-ttu-id="6c188-114">Zabezpečení, ověřování a autorizace jsou podrobněji popsány v [kapitole 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="6c188-114">Security, authentication, and authorization are covered in much more detail in [Chapter 6](security.md).</span></span> <span data-ttu-id="6c188-115">Ale tady se zaznamená, že na rozdíl od WCF gRPC nepodporuje šifrování WS-Security, WS Federation nebo XML.</span><span class="sxs-lookup"><span data-stu-id="6c188-115">But it's worth noting here that, unlike WCF, gRPC doesn't support WS-Security, WS Federation, or XML Encryption.</span></span> <span data-ttu-id="6c188-116">I tak gRPC poskytuje vynikající zabezpečení; veškerý síťový provoz v gRPC se při použití HTTP/2 přes protokol TLS automaticky zašifruje a certifikáty x509 se můžou použít pro vzájemné ověřování klientů a serverů.</span><span class="sxs-lookup"><span data-stu-id="6c188-116">Even so, gRPC provides excellent security; all gRPC network traffic is automatically encrypted when using HTTP/2 over TLS, and X509 certificates may be used for mutual client/server authentication.</span></span>

## <a name="ws-reliablemessaging"></a><span data-ttu-id="6c188-117">WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="6c188-117">WS-ReliableMessaging</span></span>

<span data-ttu-id="6c188-118">gRPC neposkytuje ekvivalent WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="6c188-118">gRPC does not provide an equivalent to WS-ReliableMessaging.</span></span> <span data-ttu-id="6c188-119">Sémantika opakování by měla být zpracována v kódu, pravděpodobně u knihovny, jako je [Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="6c188-119">Retry semantics should be handled in code, possibly with a library like [Polly](https://github.com/App-vNext/Polly).</span></span> <span data-ttu-id="6c188-120">Při spuštění v Kubernetes nebo podobných prostředích orchestrace můžou [sítě](service-mesh.md) taky pomáhat zajistit spolehlivé zasílání zpráv mezi službami.</span><span class="sxs-lookup"><span data-stu-id="6c188-120">When running in Kubernetes or similar orchestration environments, [service meshes](service-mesh.md) can also help to provide reliable messaging between services.</span></span>

## <a name="ws-transaction-ws-coordination"></a><span data-ttu-id="6c188-121">WS-Transaction, WS-koordinace</span><span class="sxs-lookup"><span data-stu-id="6c188-121">WS-Transaction, WS-Coordination</span></span>

<span data-ttu-id="6c188-122">Implementace distribuovaných transakcí ve službě WCF používá Windows DTC (Distributed Transaction Coordinator) nebo MSDTC.</span><span class="sxs-lookup"><span data-stu-id="6c188-122">WCF's implementation of distributed transactions uses Windows’ Microsoft Distributed Transaction Coordinator or MSDTC.</span></span> <span data-ttu-id="6c188-123">Spolupracuje se správci prostředků, kteří ho konkrétně podporují, jako jsou SQL Server, MSMQ nebo systémy souborů Windows.</span><span class="sxs-lookup"><span data-stu-id="6c188-123">It works with resource managers that specifically support it, like SQL Server, MSMQ, or Windows file systems.</span></span> <span data-ttu-id="6c188-124">V rámci moderních mikroslužeb na světě se v části kvůli širší škále používaných technologií nerovná.</span><span class="sxs-lookup"><span data-stu-id="6c188-124">In the modern microservices world, in part due to the wider range of technologies in use, there is no equivalent as yet.</span></span> <span data-ttu-id="6c188-125">Diskuzi o transakcích naleznete v [příloze a](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="6c188-125">For a discussion of transactions, see [Appendix A](appendix.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6c188-126">[Předchozí](error-handling.md)
>[Další](migrate-wcf-to-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="6c188-126">[Previous](error-handling.md)
[Next](migrate-wcf-to-grpc.md)</span></span>
