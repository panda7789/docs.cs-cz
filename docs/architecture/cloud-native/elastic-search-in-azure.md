---
title: Elasticsearch v cloudových nativních aplikacích
description: Přečtěte si, jak přidat funkce elastického vyhledávání do cloudových nativních aplikací.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 6ea237eddc89a8c6843d6b34b05b1b71515a99b6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794875"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="0d6b9-103">Elasticsearch v cloudové nativní aplikaci</span><span class="sxs-lookup"><span data-stu-id="0d6b9-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0d6b9-104">Elasticsearch je distribuovaný systém vyhledávání a analýzy, který umožňuje komplexní možnosti vyhledávání napříč různými typy dat.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="0d6b9-105">Je to open source a široce populární.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-105">It's open source and widely popular.</span></span> <span data-ttu-id="0d6b9-106">Vezměte v úvahu, jak následující společnosti integrují Elasticsearch do své aplikace:</span><span class="sxs-lookup"><span data-stu-id="0d6b9-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="0d6b9-107">[Wikipedii](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pro fulltextové a přírůstkové vyhledávání (hledání při psaní).</span><span class="sxs-lookup"><span data-stu-id="0d6b9-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="0d6b9-108">[GitHub](https://www.elastic.co/customers/github) pro indexování a vystavení více než 8 000 000 úložišť kódu.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="0d6b9-109">[Docker](https://www.elastic.co/customers/docker) pro zjištění, že je knihovna kontejnerů zjistitelná.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="0d6b9-110">Elasticsearch je postaven na začátku fulltextového vyhledávacího modulu [Apache Lucene](https://lucene.apache.org/core/) .</span><span class="sxs-lookup"><span data-stu-id="0d6b9-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="0d6b9-111">Lucene nabízí vysoce výkonné indexování dokumentů a dotazování.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="0d6b9-112">Indexuje data pomocí obráceného indexového schématu – místo mapování stránek na klíčová slova mapuje klíčová slova na stránky stejně jako Glosář na konci knihy.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="0d6b9-113">Lucene má výkonné možnosti syntaxe dotazů a může dotazovat data podle:</span><span class="sxs-lookup"><span data-stu-id="0d6b9-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="0d6b9-114">Termín (celé slovo)</span><span class="sxs-lookup"><span data-stu-id="0d6b9-114">Term (a full word)</span></span> 
- <span data-ttu-id="0d6b9-115">Prefix (začíná – s Wordem)</span><span class="sxs-lookup"><span data-stu-id="0d6b9-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="0d6b9-116">Zástupný znak (s použitím filtrů\*nebo?)</span><span class="sxs-lookup"><span data-stu-id="0d6b9-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="0d6b9-117">Fráze (sekvence textu v dokumentu)</span><span class="sxs-lookup"><span data-stu-id="0d6b9-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="0d6b9-118">Logická hodnota (složitá hledání kombinují dotazy)</span><span class="sxs-lookup"><span data-stu-id="0d6b9-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="0d6b9-119">I když Lucene nabízí pro hledání nízké úrovně, Elasticsearch poskytuje server, který je umístěný na Lucene.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="0d6b9-120">Elasticsearch přidává funkce vyšší úrovně, které zjednodušují práci s Lucene, včetně rozhraní RESTful API pro přístup k funkcím indexování a vyhledávání v aplikaci Lucene.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene’s indexing and searching functionality.</span></span> <span data-ttu-id="0d6b9-121">Poskytuje taky distribuovanou infrastrukturu, která podporuje obrovské škálovatelnost, odolnost proti chybám a vysokou dostupnost.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="0d6b9-122">Pro větší cloudové nativní aplikace s požadavky na hledání je Elasticsearch k dispozici jako spravovaná služba v Azure.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="0d6b9-123">Služba Microsoft Azure Marketplace funkce předkonfigurovaných šablon, které můžou vývojáři použít k nasazení clusteru Elasticsearch v Azure.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="0d6b9-124">Z Microsoft Azure Marketplace můžou vývojáři využít předem nakonfigurované šablony, pomocí kterých můžete rychle nasadit cluster Elasticsearch v Azure.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="0d6b9-125">Pomocí nabídky spravované v Azure můžete nasadit až 50 datových uzlů, 20 koordinačních uzlů a tři vyhrazené hlavní uzly.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="0d6b9-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="0d6b9-126">Summary</span></span>

<span data-ttu-id="0d6b9-127">V této části najdete podrobný přehled dat v systémech nativních pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="0d6b9-128">Začali jsme na rozdíl od ukládání dat v aplikacích v monolitické s využitím vzorů úložiště dat v nativních systémech cloudu.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="0d6b9-129">Prohlédli jsme se na vzorcích dat implementovaných v nativních systémech cloudu, včetně dotazů na různé služby, distribuovaných transakcí a vzorů, které se týkají systémů s vysokými objemy.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="0d6b9-130">NoSQL jsme na SQL data.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="0d6b9-131">Prohlédli jsme si možnosti úložiště dat dostupné v Azure, které obsahují možnosti orientované na Microsoft i open source.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="0d6b9-132">Nakonec jsme probrali ukládání do mezipaměti a Elasticsearch v cloudové nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0d6b9-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="0d6b9-133">Reference</span><span class="sxs-lookup"><span data-stu-id="0d6b9-133">References</span></span>

- [<span data-ttu-id="0d6b9-134">CQRS (Command and Query Responsibility Segregation) (CQRS) – vzor</span><span class="sxs-lookup"><span data-stu-id="0d6b9-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="0d6b9-135">Vzor zdroje událostí</span><span class="sxs-lookup"><span data-stu-id="0d6b9-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="0d6b9-136">RDBMSs vs. databáze NoSQL: Přehled</span><span class="sxs-lookup"><span data-stu-id="0d6b9-136">RDBMSs vs. NoSQL Databases: Overview</span></span>](https://maxivak.com/rdbms-vs-nosql-databases/)

- [<span data-ttu-id="0d6b9-137">Proč není RDBMS odolný proti oddílu v CAP věta a proč je k dispozici?</span><span class="sxs-lookup"><span data-stu-id="0d6b9-137">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="0d6b9-138">Materializované zobrazení</span><span class="sxs-lookup"><span data-stu-id="0d6b9-138">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="0d6b9-139">Všechno, co opravdu potřebujete znát o open source databázích</span><span class="sxs-lookup"><span data-stu-id="0d6b9-139">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="0d6b9-140">Vzor kompenzační transakce</span><span class="sxs-lookup"><span data-stu-id="0d6b9-140">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="0d6b9-141">Vzor Saga</span><span class="sxs-lookup"><span data-stu-id="0d6b9-141">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="0d6b9-142">Saga vzory | Implementace obchodních transakcí pomocí mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="0d6b9-142">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="0d6b9-143">Vzor kompenzační transakce</span><span class="sxs-lookup"><span data-stu-id="0d6b9-143">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="0d6b9-144">Seznámení za 9 míč: vysvětlení úrovní konzistence Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="0d6b9-144">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="0d6b9-145">Zkoumání různých typů databází NoSQL část II</span><span class="sxs-lookup"><span data-stu-id="0d6b9-145">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="0d6b9-146">V databázích RDBMS, NoSQL a NewSQL. Rozhovor s Jan Ryanou</span><span class="sxs-lookup"><span data-stu-id="0d6b9-146">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="0d6b9-147">SQL vs NoSQL vs NewSQL: úplné porovnání</span><span class="sxs-lookup"><span data-stu-id="0d6b9-147">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="0d6b9-148">POMLČKa: čtyři vlastnosti databáze Kubernetes-Native</span><span class="sxs-lookup"><span data-stu-id="0d6b9-148">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="0d6b9-149">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="0d6b9-149">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="0d6b9-150">TiDB</span><span class="sxs-lookup"><span data-stu-id="0d6b9-150">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="0d6b9-151">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="0d6b9-151">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="0d6b9-152">Vitess</span><span class="sxs-lookup"><span data-stu-id="0d6b9-152">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="0d6b9-153">Elasticsearch: konečný průvodce</span><span class="sxs-lookup"><span data-stu-id="0d6b9-153">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="0d6b9-154">Úvod do Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="0d6b9-154">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="0d6b9-155">[Předchozí](azure-caching.md)
>[Další](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="0d6b9-155">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
