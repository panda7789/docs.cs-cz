---
title: Distribuovaná data
description: Architekt cloudových nativních aplikací .NET pro Azure | Distribuovaná data pro nativní cloudové aplikace
ms.date: 06/30/2019
ms.openlocfilehash: b715ae5203264a023bc9f911aa74ee222afe3d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087449"
---
# <a name="distributed-data-for-cloud-native-apps"></a><span data-ttu-id="f5e4b-103">Distribuovaná data pro cloudové nativní aplikace</span><span class="sxs-lookup"><span data-stu-id="f5e4b-103">Distributed data for cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f5e4b-104">Při sestavování nativního cloudového systému, který se skládá z mnoha nezávislých mikroslužeb, si myslíte, jak si myslíte o změnách v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-104">When constructing a cloud-native system that consists of many independent microservices, the way you think about data storage changes.</span></span>

<span data-ttu-id="f5e4b-105">Tradiční aplikace monolitické přilákat centralizované úložiště dat zobrazené na obrázku 5-1.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-105">Traditional monolithic applications favor a centralized data store shown in Figure 5-1.</span></span>

![Jedna databáze monolitické](./media/single-monolithic-database.png)

<span data-ttu-id="f5e4b-107">**Obrázek 5-1**.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-107">**Figure 5-1**.</span></span> <span data-ttu-id="f5e4b-108">Jedna databáze monolitické</span><span class="sxs-lookup"><span data-stu-id="f5e4b-108">Single monolithic database</span></span>

<span data-ttu-id="f5e4b-109">Všimněte si na předchozím obrázku, jak všechny součásti aplikace využívají jednu relační databázi.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-109">Note in the previous figure how all of the application components consume a single relational database.</span></span>

<span data-ttu-id="f5e4b-110">Tento přístup má spoustu výhod.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-110">There are many benefits to this approach.</span></span> <span data-ttu-id="f5e4b-111">Je jednoduché dotazování na data rozložená mezi více tabulek a je jednoduché implementovat [transakce kyseliny](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) , které zajistí konzistenci dat.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-111">It's straightforward to query data spread across  multiple tables, and it's straightforward to implement [ACID transactions](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) that ensure data consistency.</span></span> <span data-ttu-id="f5e4b-112">Vždy se dokončí *okamžitou konzistencí*: buď všechny aktualizace dat, nebo žádná z nich.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-112">You always end up with *immediate consistency*: either all your data updates or none of it does.</span></span>

<span data-ttu-id="f5e4b-113">Systémy nativní pro Cloud jsou upřednostněny datovou architekturu na obrázku 5-2, ve které každá mikroslužba vlastní a zapouzdřuje své vlastní data.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-113">Cloud-native systems favor a data architecture shown in Figure 5-2 in which each microservice owns and encapsulates its own data.</span></span>

![Více databází napříč mikroslužbami](./media/data-across-microservices.png)

<span data-ttu-id="f5e4b-115">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-115">**Figure 5-2**.</span></span> <span data-ttu-id="f5e4b-116">Více databází napříč mikroslužbami</span><span class="sxs-lookup"><span data-stu-id="f5e4b-116">Multiple databases across microservices</span></span>

<span data-ttu-id="f5e4b-117">Všimněte si, jak je předchozí obrázek vlastníkem každé mikroslužby, a zapouzdřuje úložiště dat IT a zpřístupňuje data na vnějším světě z jeho veřejného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-117">Note how in the previous figure each microservice owns and encapsulates it data store and only exposes data to the outside world from its public API.</span></span>

<span data-ttu-id="f5e4b-118">Tento model umožňuje, aby se každá mikroslužba nezávisle vyvinula bez nutnosti koordinovat změny schématu dat s ostatními mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-118">This model enables each microservice to evolve independently without having to coordinate data schema changes with other microservices.</span></span> <span data-ttu-id="f5e4b-119">Každá mikroslužba je bezplatná pro implementaci úložiště dat (relační databáze, databáze dokumentů, úložiště hodnot typu klíč-hodnota), který nejlépe odpovídá jeho potřebám.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-119">Each microservice is free to implement the data store (relational database, document database, key-value store) type that best matches its needs.</span></span> <span data-ttu-id="f5e4b-120">V době běhu může každá mikroslužba odpovídajícím způsobem škálovat data.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-120">At runtime, each microservice can scale its data accordingly.</span></span> <span data-ttu-id="f5e4b-121">To je znázorněno na obrázku 5-3:</span><span class="sxs-lookup"><span data-stu-id="f5e4b-121">This is shown in Figure 5-3:</span></span>

![Trvalost dat Polyglot](./media/polyglot-data-persistence.png)

<span data-ttu-id="f5e4b-123">**Obrázek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-123">**Figure 5-3**.</span></span> <span data-ttu-id="f5e4b-124">Trvalost dat Polyglot</span><span class="sxs-lookup"><span data-stu-id="f5e4b-124">Polyglot data persistence</span></span>

<span data-ttu-id="f5e4b-125">Všimněte si, jak ukazuje předchozí obrázek katalog produktů a mikroslužby inventáře, které přijímají relační databáze, objednávání mikroslužeb, databázi dokumentů NoSql a službu nákupní košík, což je externí úložiště hodnot klíčů.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-125">Note how in the previous figure the product catalog and inventory microservices adopt relational databases, the ordering microservice, a NoSql document database, and the shopping cart microservice, which is an external key-value store.</span></span> <span data-ttu-id="f5e4b-126">I když relační databáze zůstávají důležité pro mikroslužby se složitými daty, databáze NoSQL získaly značnou oblíbenou službu, která nabízí přizpůsobivost, rychlé vyhledávání a vysokou dostupnost.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-126">While relational databases remain relevant for microservices with complex data, NoSQL databases have gained considerable popularity, providing adaptability, fast lookup, and high availability.</span></span> <span data-ttu-id="f5e4b-127">Bez jejich schématu umožňuje vývojářům přesunout se od architektury typových datových tříd a ORMs, které vedou ke změně nákladného a časově náročného.</span><span class="sxs-lookup"><span data-stu-id="f5e4b-127">Their schemaless nature allows developers to move away from an architecture of typed data classes and ORMs that make change expensive and time-consuming.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f5e4b-128">[Předchozí](service-mesh-communication-infrastructure.md)
>[Další](data-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f5e4b-128">[Previous](service-mesh-communication-infrastructure.md)
[Next](data-patterns.md)</span></span>
