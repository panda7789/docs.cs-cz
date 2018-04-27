---
title: Architektura Mikroslužeb
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Architektura Mikroslužeb
keywords: Docker, Mikroslužeb, ASP.NET, kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78d3903e7ed4abf27e78812de87ccbcb9f733663
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="microservices-architecture"></a><span data-ttu-id="c2d43-104">Architektura Mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="c2d43-104">Microservices architecture</span></span>

<span data-ttu-id="c2d43-105">Jak již název napovídá, architektura mikroslužeb je přístup k vytvoření aplikace serveru jako sada malé služeb.</span><span class="sxs-lookup"><span data-stu-id="c2d43-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="c2d43-106">Každá služba běží ve svém vlastním procesu a komunikuje s dalšími procesy pomocí protokolů, jako je například HTTP nebo HTTPS, Websocket, nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span><span class="sxs-lookup"><span data-stu-id="c2d43-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="c2d43-107">Každý mikroslužbu implementuje určitou začátku do konce doménu nebo obchodní schopností v určité hranici kontextu a každý musí být vyvinutá samostatně a možno nasadit nezávisle.</span><span class="sxs-lookup"><span data-stu-id="c2d43-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="c2d43-108">Nakonec musí každý mikroslužbu vlastní jeho související domény datový model a logiku domény (suverenity a správa decentralizované dat) na základě různých datových technologií úložiště (SQL, NoSQL) a různé programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="c2d43-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="c2d43-109">Jaké velikost by měla být mikroslužbu?</span><span class="sxs-lookup"><span data-stu-id="c2d43-109">What size should a microservice be?</span></span> <span data-ttu-id="c2d43-110">Při vývoji mikroslužbu, velikost by neměl být důležité.</span><span class="sxs-lookup"><span data-stu-id="c2d43-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="c2d43-111">Důležité místo toho by měla být k vytvoření volně doplněná služby, abyste získali samostatnost vývoj, nasazení a škálování pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="c2d43-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="c2d43-112">Samozřejmě pokud určíte a navrhování mikroslužeb, můžete opakovat tak, aby byly co nejmenší, dokud jste příliš mnoho přímé závislosti s další mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c2d43-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="c2d43-113">Důležitější než je velikost mikroslužbu vnitřní soudržnost, které musí mít a jeho nezávislost z jiných služeb.</span><span class="sxs-lookup"><span data-stu-id="c2d43-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="c2d43-114">Proč architektura mikroslužeb?</span><span class="sxs-lookup"><span data-stu-id="c2d43-114">Why a microservices architecture?</span></span> <span data-ttu-id="c2d43-115">Stručně řečeno poskytuje dlouhodobé flexibility.</span><span class="sxs-lookup"><span data-stu-id="c2d43-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="c2d43-116">Mikroslužeb povolit lepší udržovatelnosti v systémech komplexní, velký a vysoce škálovatelné umožňují vytvářet aplikace založené na mnoho nezávisle nasadit služby nichž každá má granulární a autonomní životní cykly.</span><span class="sxs-lookup"><span data-stu-id="c2d43-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="c2d43-117">Další výhodou je mikroslužeb můžete škálovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="c2d43-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="c2d43-118">Místo nutnosti jednu monolitický aplikaci, která musí horizontální navýšení kapacity jako jednotku, můžete místo toho škálovat konkrétní mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c2d43-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="c2d43-119">Tímto způsobem je možné škálovat právě funkční oblast, která potřebuje další zpracování napájení nebo síťové šířky pásma pro podporu poptávky, nikoli škálování jiných oblastí aplikace, které nemusí být změněna.</span><span class="sxs-lookup"><span data-stu-id="c2d43-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="c2d43-120">To znamená úsporu nákladů, protože potřebujete méně hardwaru.</span><span class="sxs-lookup"><span data-stu-id="c2d43-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="c2d43-121">**Obrázek 4 až 6**.</span><span class="sxs-lookup"><span data-stu-id="c2d43-121">**Figure 4-6**.</span></span> <span data-ttu-id="c2d43-122">Monolitický nasazení a mikroslužeb přístup</span><span class="sxs-lookup"><span data-stu-id="c2d43-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="c2d43-123">Jak ukazuje obrázek 4 až 6, mikroslužeb přístup umožňuje agilní změny a rychlé iteraci každý mikroslužbu, protože můžete změnit konkrétní, malé oblasti komplexní, velký a škálovatelné aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2d43-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="c2d43-124">Architektury podrobných aplikace založené na mikroslužeb umožňuje průběžnou integraci a postupy nastavené průběžné doručování.</span><span class="sxs-lookup"><span data-stu-id="c2d43-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="c2d43-125">Také urychlí vytváření nových funkcí do aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2d43-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="c2d43-126">Podrobné složení aplikace také můžete spustit a otestovat mikroslužeb v izolaci a vyvíjí samostatně při zachování zrušte kontrakty mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="c2d43-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="c2d43-127">Tak dlouho, dokud nezměníte rozhraní nebo kontrakty, můžete změnit interní implementace žádné mikroslužbu nebo přidat další nové funkce, aniž by vás jiných mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c2d43-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="c2d43-128">Důležité aspekty povolit úspěch v přejdete do ostrého provozu je-li systém mikroslužeb jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c2d43-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="c2d43-129">Kontroluje stav a monitorování služeb a infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="c2d43-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="c2d43-130">Škálovatelné infrastruktury pro služby (to znamená, cloudu a orchestrators).</span><span class="sxs-lookup"><span data-stu-id="c2d43-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="c2d43-131">Zabezpečení návrhu a implementace na více úrovních: ověřování, autorizace, správu tajné klíče, zabezpečenou komunikaci, atd.</span><span class="sxs-lookup"><span data-stu-id="c2d43-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="c2d43-132">Doručení rychlé aplikace, obvykle s různými týmy zaměřené na různých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c2d43-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="c2d43-133">Postupy DevOps a CI/CD a infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="c2d43-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="c2d43-134">Z těchto jsou pouze první tři zahrnutých nebo byla zavedená v této příručce.</span><span class="sxs-lookup"><span data-stu-id="c2d43-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="c2d43-135">Poslední dva body, které se vztahují k životního cyklu aplikací, jsou popsané v další [Kontejnerizované Docker cyklu aplikací s Microsoft platforma a nástroje](https://aka.ms/dockerlifecycleebook) elektronických knih.</span><span class="sxs-lookup"><span data-stu-id="c2d43-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c2d43-136">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c2d43-136">Additional resources</span></span>

-   <span data-ttu-id="c2d43-137">**Označit Russinovichem. Mikroslužeb: Aplikaci revolution používá technologii cloudu**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="c2d43-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="c2d43-138">**Martin Fowler. Mikroslužeb**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="c2d43-138">**Martin Fowler. Microservices**
[*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="c2d43-139">**Martin Fowler. Mikroslužbu požadavky**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="c2d43-139">**Martin Fowler. Microservice Prerequisites**
[*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="c2d43-140">**Jimmy Nilsson. Bloku dat Cloud Computing**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="c2d43-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="c2d43-141">**Cesaru členka Torre. Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje** (ke stažení elektronická kniha) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="c2d43-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="c2d43-142">[Předchozí] (service-oriented-architecture.md) [Další] (data-sovereignty-per-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="c2d43-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
