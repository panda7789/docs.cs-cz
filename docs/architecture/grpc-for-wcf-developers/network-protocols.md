---
title: Síťové protokoly – gRPC pro vývojáře WCF
description: Přehled síťových protokolů gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cf99b2608d576765856c992679b93b6f21e796cf
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846396"
---
# <a name="network-protocols"></a><span data-ttu-id="b8d80-103">Síťové protokoly</span><span class="sxs-lookup"><span data-stu-id="b8d80-103">Network protocols</span></span>

<span data-ttu-id="b8d80-104">Na rozdíl od služby WCF používá gRPC jako základ pro svou síť protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b8d80-104">Unlike WCF, gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="b8d80-105">To nabízí významné výhody oproti WCF a protokolu SOAP, které pracují pouze s HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="b8d80-105">This offers significant advantages over WCF and SOAP, which only operate on HTTP/1.1.</span></span> <span data-ttu-id="b8d80-106">Pro vývojáře, kteří chtějí používat gRPC, se vzhledem k tomu, že neexistuje žádná alternativa k HTTP/2, by to bylo ideální okamžik pro prozkoumání HTTP/2 podrobněji a určení dalších výhod používání gRPC.</span><span class="sxs-lookup"><span data-stu-id="b8d80-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits to using gRPC.</span></span>

<span data-ttu-id="b8d80-107">Protokol HTTP/2 vydaný internetovou úlohou vysílaný v 2015 byl odvozený od experimentálního protokolu SPDY, který už používá Google.</span><span class="sxs-lookup"><span data-stu-id="b8d80-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="b8d80-108">Konkrétně je navržený tak, aby byl efektivnější, rychlejší a bezpečnější než HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="b8d80-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="b8d80-109">Klíčové funkce HTTP/2</span><span class="sxs-lookup"><span data-stu-id="b8d80-109">Key features of HTTP/2</span></span>

<span data-ttu-id="b8d80-110">Následující seznam uvádí některé klíčové funkce a výhody protokolu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="b8d80-110">The following list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="b8d80-111">Binární protokol</span><span class="sxs-lookup"><span data-stu-id="b8d80-111">Binary protocol</span></span>

<span data-ttu-id="b8d80-112">Cykly požadavků a odpovědí již nepotřebují textové příkazy.</span><span class="sxs-lookup"><span data-stu-id="b8d80-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="b8d80-113">Tím se zjednoduší a urychlí implementace příkazů.</span><span class="sxs-lookup"><span data-stu-id="b8d80-113">This simplifies and speeds up implementation of commands.</span></span> <span data-ttu-id="b8d80-114">Konkrétně analýza dat je rychlejší a používá méně paměti, latence sítě se zkracuje se zjevně souvisejícími vylepšeními rychlosti a existuje celkové lepší využití síťových prostředků.</span><span class="sxs-lookup"><span data-stu-id="b8d80-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="b8d80-115">Datové proudy</span><span class="sxs-lookup"><span data-stu-id="b8d80-115">Streams</span></span>

<span data-ttu-id="b8d80-116">Streamy umožňují vytvářet dlouhodobá připojení mezi odesílatelem a příjemcem, přes který se dá asynchronně odeslat víc zpráv nebo rámců.</span><span class="sxs-lookup"><span data-stu-id="b8d80-116">Streams allow for the creation of long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="b8d80-117">Více datových proudů může pracovat nezávisle na jednom připojení HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b8d80-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="b8d80-118">Vyžádat multiplexování přes jedno připojení TCP</span><span class="sxs-lookup"><span data-stu-id="b8d80-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="b8d80-119">Tato funkce je jednou z nejdůležitějších inovací HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b8d80-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="b8d80-120">Když povolíte více paralelních požadavků na data, je teď možné stahovat webové soubory souběžně z jednoho serveru.</span><span class="sxs-lookup"><span data-stu-id="b8d80-120">By allowing multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="b8d80-121">Websites se rychleji načítají a nutnost optimalizace se zkrátí.</span><span class="sxs-lookup"><span data-stu-id="b8d80-121">Websites load faster and the need for optimization is reduced.</span></span> <span data-ttu-id="b8d80-122">Blokování na konci řádku (HOL), kde musí být připravené odpovědi čekat, dokud nebude dokončena předchozí žádost, dojde také k omezení (i když se na úrovni transportu TCP stále může vyskytovat).</span><span class="sxs-lookup"><span data-stu-id="b8d80-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="b8d80-123">NetTCP jako výkon, více platforem</span><span class="sxs-lookup"><span data-stu-id="b8d80-123">NetTCP-like performance, cross-platform</span></span>

<span data-ttu-id="b8d80-124">V podstatě kombinace gRPC a HTTP/2 nabízí vývojářům alespoň ekvivalentní rychlost a efektivitu vazeb NetTCP pro WCF a v některých případech i větší rychlost a efektivitu.</span><span class="sxs-lookup"><span data-stu-id="b8d80-124">Fundamentally, the combination of gRPC and HTTP/2 offer developers at least the equivalent speed and efficiency of NetTCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="b8d80-125">Nicméně na rozdíl od NetTCP se gRPC přes HTTP/2 neomezuje na aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="b8d80-125">However, unlike NetTCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b8d80-126">[Předchozí](interface-definition-language.md)
>[Další](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="b8d80-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
