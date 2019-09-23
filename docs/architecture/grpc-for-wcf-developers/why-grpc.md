---
title: Proč se gRPC doporučuje pro vývojáře WCF – gRPC pro vývojáře WCF
description: Diskuzi o tom, proč se gRPC hodí pro vývojáře WCF, kteří chtějí migrovat na moderní architektury a platformy.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7e80936eb36bbba92958c349b5f1c0cb389d6b8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184034"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a><span data-ttu-id="b6424-103">Proč se doporučuje gRPC pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="b6424-103">Why gRPC is recommended for WCF developers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b6424-104">Předtím, než se začnete do jazyka a technik gRPC, je vhodné pojednávat o tom, proč je gRPC správným řešením pro vývojáře WCF, kteří chtějí migrovat na .NET Core, a to s ohledem na dostupné alternativy.</span><span class="sxs-lookup"><span data-stu-id="b6424-104">Before diving deeply into the language and techniques of gRPC, it's worth discussing why gRPC is the right solution for WCF developers who want to migrate to .NET Core, given there are alternatives available.</span></span>

## <a name="similarity-to-wcf"></a><span data-ttu-id="b6424-105">Podobnost k WCF</span><span class="sxs-lookup"><span data-stu-id="b6424-105">Similarity to WCF</span></span>

<span data-ttu-id="b6424-106">I když je jeho implementace a přístup odlišná, vlastní zkušenosti s vývojem a používáním služeb gRPC by měly být pro vývojáře WCF velmi intuitivní.</span><span class="sxs-lookup"><span data-stu-id="b6424-106">Although its implementation and approach is different, the actual experience of developing and consuming services with gRPC should be very intuitive for WCF developers.</span></span> <span data-ttu-id="b6424-107">Základní cíl, který umožňuje psaní kódu, jako kdyby byl klient a server na stejné platformě, nemuseli se starat o sítě.</span><span class="sxs-lookup"><span data-stu-id="b6424-107">The underlying goal of making it possible to code as though the client and server were on the same platform, without needing to worry about networking, is the same.</span></span> <span data-ttu-id="b6424-108">Obě platformy sdílí princip deklarování a následné implementace rozhraní, a to i v případě, že proces pro deklarování tohoto rozhraní je jiný.</span><span class="sxs-lookup"><span data-stu-id="b6424-108">Both platforms share the principle of declaring and then implementing an interface, even though the process for declaring that interface is different.</span></span> <span data-ttu-id="b6424-109">A jak uvidíte v kapitole 5, různé typy volání RPC, které podporuje mapa gRPC, velmi dobře na různé vazby, které jsou dostupné pro služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b6424-109">And as you'll see in chapter 5, the different types of RPC calls supported by gRPC map very well to the different bindings available to WCF services.</span></span>

## <a name="benefits-of-grpc"></a><span data-ttu-id="b6424-110">Výhody gRPC</span><span class="sxs-lookup"><span data-stu-id="b6424-110">Benefits of gRPC</span></span>

<span data-ttu-id="b6424-111">Další důvody, proč gRPC představuje více než další řešení:</span><span class="sxs-lookup"><span data-stu-id="b6424-111">Additional reasons why gRPC stands above other solutions are:</span></span>

### <a name="performance"></a><span data-ttu-id="b6424-112">Výkon</span><span class="sxs-lookup"><span data-stu-id="b6424-112">Performance</span></span>

<span data-ttu-id="b6424-113">Jak už bylo popsáno, použití HTTP/2 místo HTTP/1.1 odstraní požadavek na zprávy čitelné pro čtení a místo toho používá menší rychlejší binární protokol.</span><span class="sxs-lookup"><span data-stu-id="b6424-113">As already discussed, using HTTP/2 rather than HTTP/1.1 removes the requirement for human-readable messages and instead uses the smaller faster binary protocol.</span></span> <span data-ttu-id="b6424-114">To je efektivnější pro počítače k analýze.</span><span class="sxs-lookup"><span data-stu-id="b6424-114">This is more efficient for computers to parse.</span></span> <span data-ttu-id="b6424-115">HTTP/2 podporuje také multiplexování požadavků přes jedno připojení, které umožňuje posílání odpovědí ihned po jejich dokončení, aniž by bylo nutné čekat ve frontě (problém v HTTP/1.1 se označuje jako "blokování na začátku řádku").</span><span class="sxs-lookup"><span data-stu-id="b6424-115">HTTP/2 also supports multiplexing requests over a single connection enabling responses to be sent as soon as they're ready without the need to wait in a queue (an issue in HTTP/1.1 known as "head-of-line (HOL) blocking").</span></span> <span data-ttu-id="b6424-116">Při použití gRPC je potřeba mít méně prostředků, díky čemuž je vhodné řešení používat pro mobilní zařízení a pomalejší sítě.</span><span class="sxs-lookup"><span data-stu-id="b6424-116">Fewer resources are needed when using gRPC, which makes it a good solution to use for mobile devices and over slower networks.</span></span>

### <a name="interoperability"></a><span data-ttu-id="b6424-117">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b6424-117">Interoperability</span></span>

<span data-ttu-id="b6424-118">K dispozici jsou nástroje a knihovny gRPC pro všechny hlavní programovací jazyky a platformy, včetně .NET, Java, Python, C++cestách, Node. js, SWIFT, DART, Ruby a php.</span><span class="sxs-lookup"><span data-stu-id="b6424-118">There are gRPC tools and libraries for all major programming languages and platforms, including .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby, and PHP.</span></span> <span data-ttu-id="b6424-119">Díky ukládání binárních přenosů do vyrovnávací paměti protokolů a efektivní generování kódu pro každou platformu můžou vývojáři vytvářet výkonné aplikace a pořád využívat plnou podporu pro víc platforem.</span><span class="sxs-lookup"><span data-stu-id="b6424-119">Thanks to the Protocol Buffers binary wire format and the efficient code generation for each platform, developers can build performant apps while still enjoying full cross-platform support.</span></span>

### <a name="usability-and-productivity"></a><span data-ttu-id="b6424-120">Použitelnost a produktivita</span><span class="sxs-lookup"><span data-stu-id="b6424-120">Usability and productivity</span></span>

<span data-ttu-id="b6424-121">gRPC je komplexní řešení RPC.</span><span class="sxs-lookup"><span data-stu-id="b6424-121">gRPC is a comprehensive RPC solution.</span></span> <span data-ttu-id="b6424-122">Funguje konzistentně napříč různými jazyky a platformami a nabízí vynikající nástroje, s využitím automaticky vygenerovaného často používaného automatického kódu, takže se do obchodní logiky zaměří více času pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b6424-122">It works consistently across multiple languages and platforms, and provides excellent tooling, with much of the necessary boilerplate code auto-generated, so more developer time is freed up to focus on business logic.</span></span>

### <a name="streaming"></a><span data-ttu-id="b6424-123">Streamování</span><span class="sxs-lookup"><span data-stu-id="b6424-123">Streaming</span></span>

<span data-ttu-id="b6424-124">gRPC má plnohodnotné obousměrné streamování, které poskytuje velmi podobné funkce jako plně duplexní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b6424-124">gRPC has full bidirectional streaming, which provides very similar functionality to WCF's full duplex services.</span></span> <span data-ttu-id="b6424-125">gRPC streaming může pracovat přes běžná připojení k Internetu, nástroje pro vyrovnávání zatížení a sítě.</span><span class="sxs-lookup"><span data-stu-id="b6424-125">gRPC streaming can operate over regular internet connections, load balancers, and service meshes.</span></span>

### <a name="deadlinetimeouts-and-cancellation"></a><span data-ttu-id="b6424-126">Konečný termín, vypršení časového limitu a zrušení</span><span class="sxs-lookup"><span data-stu-id="b6424-126">Deadline/timeouts and cancellation</span></span>

<span data-ttu-id="b6424-127">gRPC umožňuje klientům zadat maximální dobu, po kterou se RPC dokončí.</span><span class="sxs-lookup"><span data-stu-id="b6424-127">gRPC allows clients to specify a maximum time for an RPC to complete.</span></span> <span data-ttu-id="b6424-128">Pokud je překročen zadaný konečný termín, server může operaci zrušit nezávisle na klientovi.</span><span class="sxs-lookup"><span data-stu-id="b6424-128">If the specified deadline is exceeded the server can cancel the operation independently of the client.</span></span> <span data-ttu-id="b6424-129">Termíny a zrušení lze rozšířit prostřednictvím dalších volání gRPC, která vám pomůžou vyhodnotit omezení využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="b6424-129">Deadlines and cancellations can be propagated through further gRPC calls to help enforce resource usage limits.</span></span> <span data-ttu-id="b6424-130">Klienti mohou také přerušit operace, když je překročen konečný termín, nebo dříve, pokud je to nutné (např. z důvodu interakce s uživatelem).</span><span class="sxs-lookup"><span data-stu-id="b6424-130">Clients may also abort operations when a deadline is exceeded, or earlier if necessary (e.g. due to a user interaction).</span></span>

### <a name="security"></a><span data-ttu-id="b6424-131">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b6424-131">Security</span></span>

<span data-ttu-id="b6424-132">gRPC je implicitně zabezpečený při použití HTTP/2 přes komplexní šifrované připojení TLS.</span><span class="sxs-lookup"><span data-stu-id="b6424-132">gRPC is implicitly secure when using HTTP/2 over an TLS end-to-end encrypted connection.</span></span> <span data-ttu-id="b6424-133">Podpora ověřování klientského certifikátu (viz kapitola 6) dále zvyšuje zabezpečení a důvěryhodnost mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="b6424-133">Support for Client Certificate authentication (see chapter 6) further increases security and trust between client and server.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b6424-134">[Předchozí](network-protocols.md)
>[Další](protocol-buffers.md)</span><span class="sxs-lookup"><span data-stu-id="b6424-134">[Previous](network-protocols.md)
[Next](protocol-buffers.md)</span></span>
