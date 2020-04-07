---
title: Elastické vyhledávání v aplikacích nativních pro cloud
description: Přečtěte si o přidávání funkcí elastického vyhledávání do aplikací nativních pro cloud.
author: robvet
ms.date: 03/02/2020
ms.openlocfilehash: da6b9402cf266f5a298b05cf837805b2377bc75a
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805559"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="b8c8c-103">Elastické vyhledávání v aplikaci nativní pro cloud</span><span class="sxs-lookup"><span data-stu-id="b8c8c-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b8c8c-104">Elasticsearch je distribuovaný vyhledávací a analytický systém, který umožňuje komplexní možnosti vyhledávání napříč různými typy dat.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="b8c8c-105">Je to open source a široce populární.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-105">It's open source and widely popular.</span></span> <span data-ttu-id="b8c8c-106">Zvažte, jak následující společnosti integrovat Elasticsearch do jejich aplikace:</span><span class="sxs-lookup"><span data-stu-id="b8c8c-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="b8c8c-107">[Wikipedie](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pro fulltextové a přírůstkové (vyhledávání při psaní) vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="b8c8c-108">[GitHub](https://www.elastic.co/customers/github) indexovat a vystavit více než 8 milionů repozitářů kódu.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="b8c8c-109">[Docker](https://www.elastic.co/customers/docker) pro to, aby jeho kontejnerové knihovny zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="b8c8c-110">Elastické vyhledávání je postaveno na fulltextovém vyhledávači [Apache Lucene.](https://lucene.apache.org/core/)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="b8c8c-111">Lucene poskytuje vysoce výkonné indexování dokumentů a dotazování.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="b8c8c-112">Indexuje data pomocí invertovaného indexovacího schématu – namísto mapování stránek na klíčová slova mapuje klíčová slova na stránky stejně jako glosář na konci knihy.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="b8c8c-113">Lucene má výkonné možnosti syntaxe dotazu a může dotazovat data podle:</span><span class="sxs-lookup"><span data-stu-id="b8c8c-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="b8c8c-114">Termín (celé slovo)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-114">Term (a full word)</span></span>
- <span data-ttu-id="b8c8c-115">Předpona (spuštění-s word)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="b8c8c-116">Zástupný znak\*(pomocí filtrů " " nebo "?"</span><span class="sxs-lookup"><span data-stu-id="b8c8c-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="b8c8c-117">Fráze (posloupnost textu v dokumentu)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="b8c8c-118">Logická hodnota (komplexní hledání kombinující dotazy)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="b8c8c-119">Zatímco Lucene poskytuje nízkoúrovňové instalatérské práce pro vyhledávání, Elasticsearch poskytuje server, který sedí na vrcholu Lucene.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="b8c8c-120">Elasticsearch přidává funkce vyšší úrovně pro zjednodušení pracovní Lucene, včetně ROZHRANÍ RESTful API pro přístup k lucene indexování a vyhledávání funkce.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="b8c8c-121">Poskytuje také distribuovanou infrastrukturu schopnou masivní škálovatelnosti, odolnosti proti chybám a vysoké dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="b8c8c-122">Pro větší cloudové nativní aplikace se složitými požadavky na vyhledávání je Elasticsearch k dispozici jako spravovaná služba v Azure.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="b8c8c-123">Microsoft Azure Marketplace obsahuje předem nakonfigurované šablony, které můžou vývojáři použít k nasazení clusteru Elastického vyhledávání v Azure.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="b8c8c-124">Na webu Microsoft Azure Marketplace můžou vývojáři používat předkonfigurované šablony vytvořené k rychlému nasazení clusteru Elastického vyhledávání v Azure.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="b8c8c-125">Pomocí nabídky spravované Azure můžete nasadit až 50 datových uzlů, 20 koordinačních uzlů a tři vyhrazené hlavní uzly.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="b8c8c-126">Souhrn</span><span class="sxs-lookup"><span data-stu-id="b8c8c-126">Summary</span></span>

<span data-ttu-id="b8c8c-127">Tato kapitola představila podrobný pohled na data v cloudových nativních systémech.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="b8c8c-128">Začali jsme kontrastním ukládáním dat v monolitických aplikacích se vzory ukládání dat v cloudových systémech.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="b8c8c-129">Podívali jsme se na datové vzory implementované v systémech nativních na cloudu, včetně dotazů napříč službami, distribuovaných transakcí a vzorců pro řešení velkoobjemových systémů.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="b8c8c-130">Kontrastovali jsme SQL s NoSQL daty.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="b8c8c-131">Podívali jsme se na možnosti úložiště dat dostupné v Azure, které zahrnují možnosti zaměřené na Microsoft i open source.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="b8c8c-132">Nakonec jsme diskutovali ukládání do mezipaměti a elastické vyhledávání v aplikaci nativní pro cloud.</span><span class="sxs-lookup"><span data-stu-id="b8c8c-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="b8c8c-133">Odkazy</span><span class="sxs-lookup"><span data-stu-id="b8c8c-133">References</span></span>

- [<span data-ttu-id="b8c8c-134">Model dělení zodpovědnosti příkazů a dotazů (CQRS – Command and Query Responsibility Segregation)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="b8c8c-135">Vzor získávání událostí</span><span class="sxs-lookup"><span data-stu-id="b8c8c-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="b8c8c-136">Proč není RDBMS Partition Tolerantní v Cap ověnčené teoretiku a proč je k dispozici?</span><span class="sxs-lookup"><span data-stu-id="b8c8c-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="b8c8c-137">Zhmotněný pohled</span><span class="sxs-lookup"><span data-stu-id="b8c8c-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="b8c8c-138">Vše, co opravdu potřebujete vědět o open source databázích</span><span class="sxs-lookup"><span data-stu-id="b8c8c-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="b8c8c-139">Model kompenzační transakce</span><span class="sxs-lookup"><span data-stu-id="b8c8c-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="b8c8c-140">Vzor ságy</span><span class="sxs-lookup"><span data-stu-id="b8c8c-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="b8c8c-141">Saga vzory | Jak implementovat obchodní transakce pomocí mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="b8c8c-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="b8c8c-142">Model kompenzační transakce</span><span class="sxs-lookup"><span data-stu-id="b8c8c-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="b8c8c-143">Získání za 9-Ball: Cosmos DB konzistence úrovně vysvětlil</span><span class="sxs-lookup"><span data-stu-id="b8c8c-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="b8c8c-144">Zkoumání různých typů NoSQL databází část II</span><span class="sxs-lookup"><span data-stu-id="b8c8c-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="b8c8c-145">V databázích RDBMS, NoSQL a NewSQL. Rozhovor s Johnem Ryanem</span><span class="sxs-lookup"><span data-stu-id="b8c8c-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="b8c8c-146">SQL vs NoSQL vs NewSQL: Úplné porovnání</span><span class="sxs-lookup"><span data-stu-id="b8c8c-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="b8c8c-147">DASH: Čtyři vlastnosti Kubernetes-Nativní databáze</span><span class="sxs-lookup"><span data-stu-id="b8c8c-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="b8c8c-148">Švábdb</span><span class="sxs-lookup"><span data-stu-id="b8c8c-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="b8c8c-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="b8c8c-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="b8c8c-150">JugabyteDB</span><span class="sxs-lookup"><span data-stu-id="b8c8c-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="b8c8c-151">Vitess (Rak.)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="b8c8c-152">Elasticsearch: Definitivní průvodce</span><span class="sxs-lookup"><span data-stu-id="b8c8c-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="b8c8c-153">Úvod do Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="b8c8c-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="b8c8c-154">[Předchozí](azure-caching.md)
>[další](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="b8c8c-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
