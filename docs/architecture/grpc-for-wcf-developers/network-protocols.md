---
title: Síťové protokoly – gRPC pro vývojáře WCF
description: Přehled síťových protokolů gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 1ceb140f7b7ac7e796a87612ebb9d21e28d33968
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628485"
---
# <a name="network-protocols"></a><span data-ttu-id="d72cf-103">Síťové protokoly</span><span class="sxs-lookup"><span data-stu-id="d72cf-103">Network protocols</span></span>

<span data-ttu-id="d72cf-104">Na rozdíl od Windows Communication Foundation (WCF) používá gRPC jako základ pro svou síť protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="d72cf-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="d72cf-105">To nabízí významné výhody oproti WCF a protokolu SOAP, které fungují pouze na HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="d72cf-105">This offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="d72cf-106">Pro vývojáře, kteří chtějí používat gRPC, se vzhledem k tomu, že neexistuje žádná alternativa k HTTP/2, by to bylo ideální okamžik pro prozkoumání HTTP/2 podrobněji a určení dalších výhod používání gRPC.</span><span class="sxs-lookup"><span data-stu-id="d72cf-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="d72cf-107">Protokol HTTP/2 vydaný internetovou úlohou vysílaný v 2015 byl odvozený od experimentálního protokolu SPDY, který už používá Google.</span><span class="sxs-lookup"><span data-stu-id="d72cf-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="d72cf-108">Konkrétně je navržený tak, aby byl efektivnější, rychlejší a bezpečnější než HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="d72cf-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="d72cf-109">Klíčové funkce HTTP/2</span><span class="sxs-lookup"><span data-stu-id="d72cf-109">Key features of HTTP/2</span></span>

<span data-ttu-id="d72cf-110">Tento seznam obsahuje některé klíčové funkce a výhody protokolu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="d72cf-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="d72cf-111">Binární protokol</span><span class="sxs-lookup"><span data-stu-id="d72cf-111">Binary protocol</span></span>

<span data-ttu-id="d72cf-112">Cykly požadavků a odpovědí již nepotřebují textové příkazy.</span><span class="sxs-lookup"><span data-stu-id="d72cf-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="d72cf-113">Tím se zjednoduší a urychlí implementace příkazů.</span><span class="sxs-lookup"><span data-stu-id="d72cf-113">This simplifies and speeds up implementation of commands.</span></span> <span data-ttu-id="d72cf-114">Konkrétně analýza dat je rychlejší a používá méně paměti, latence sítě se zkracuje se zjevně souvisejícími vylepšeními rychlosti a existuje celkové lepší využití síťových prostředků.</span><span class="sxs-lookup"><span data-stu-id="d72cf-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="d72cf-115">Datové proudy</span><span class="sxs-lookup"><span data-stu-id="d72cf-115">Streams</span></span>

<span data-ttu-id="d72cf-116">Streamy umožňují vytvářet dlouhodobá připojení mezi odesílatelem a příjemcem, přes který se dá asynchronně odeslat víc zpráv nebo rámců.</span><span class="sxs-lookup"><span data-stu-id="d72cf-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="d72cf-117">Více datových proudů může pracovat nezávisle na jednom připojení HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="d72cf-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="d72cf-118">Vyžádat multiplexování přes jedno připojení TCP</span><span class="sxs-lookup"><span data-stu-id="d72cf-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="d72cf-119">Tato funkce je jednou z nejdůležitějších inovací HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="d72cf-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="d72cf-120">Vzhledem k tomu, že umožňuje více paralelních požadavků na data, je nyní možné stahovat webové soubory souběžně z jednoho serveru.</span><span class="sxs-lookup"><span data-stu-id="d72cf-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="d72cf-121">Websites se rychleji načítají a nutnost optimalizace se zkrátí.</span><span class="sxs-lookup"><span data-stu-id="d72cf-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="d72cf-122">Blokové blokování (HOL), ve kterém musí být připravené odpovědi čekat, dokud nebude dokončena předchozí žádost, dojde také k omezení (i když se na úrovni protokolu TCP-Transport stále může vyskytovat).</span><span class="sxs-lookup"><span data-stu-id="d72cf-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="d72cf-123">Výkon typu NET. TCP, platforma pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="d72cf-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="d72cf-124">V podstatě kombinace gRPC a HTTP/2 nabízí vývojářům přinejmenším ekvivalentní rychlost a efektivitu vazeb NET. TCP pro WCF a v některých případech i větší rychlost a efektivitu.</span><span class="sxs-lookup"><span data-stu-id="d72cf-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="d72cf-125">Ale na rozdíl od NET. TCP, gRPC přes HTTP/2 není omezený na aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="d72cf-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d72cf-126">[Předchozí](interface-definition-language.md)
>[Další](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="d72cf-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
