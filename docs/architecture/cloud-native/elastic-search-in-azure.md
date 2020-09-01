---
title: Elasticsearch v cloudových nativních aplikacích
description: Přečtěte si, jak přidat funkce elastického vyhledávání do cloudových nativních aplikací.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 70d1925d6b8c7bbe515ee4f178513dc61212ebce
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271799"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="acbff-103">Elasticsearch v cloudové nativní aplikaci</span><span class="sxs-lookup"><span data-stu-id="acbff-103">Elasticsearch in a cloud-native app</span></span>

<span data-ttu-id="acbff-104">Elasticsearch je distribuovaný systém vyhledávání a analýzy, který umožňuje komplexní možnosti vyhledávání napříč různými typy dat.</span><span class="sxs-lookup"><span data-stu-id="acbff-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="acbff-105">Je to open source a široce populární.</span><span class="sxs-lookup"><span data-stu-id="acbff-105">It's open source and widely popular.</span></span> <span data-ttu-id="acbff-106">Vezměte v úvahu, jak následující společnosti integrují Elasticsearch do své aplikace:</span><span class="sxs-lookup"><span data-stu-id="acbff-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="acbff-107">[Wikipedii](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pro fulltextové a přírůstkové vyhledávání (hledání při psaní).</span><span class="sxs-lookup"><span data-stu-id="acbff-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="acbff-108">[GitHub](https://www.elastic.co/customers/github) pro indexování a vystavení více než 8 000 000 úložišť kódu.</span><span class="sxs-lookup"><span data-stu-id="acbff-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="acbff-109">[Docker](https://www.elastic.co/customers/docker) pro zjištění, že je knihovna kontejnerů zjistitelná.</span><span class="sxs-lookup"><span data-stu-id="acbff-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="acbff-110">Elasticsearch je postaven na začátku fulltextového vyhledávacího modulu [Apache Lucene](https://lucene.apache.org/core/) .</span><span class="sxs-lookup"><span data-stu-id="acbff-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="acbff-111">Lucene nabízí vysoce výkonné indexování dokumentů a dotazování.</span><span class="sxs-lookup"><span data-stu-id="acbff-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="acbff-112">Indexuje data pomocí obráceného indexového schématu – místo mapování stránek na klíčová slova mapuje klíčová slova na stránky stejně jako Glosář na konci knihy.</span><span class="sxs-lookup"><span data-stu-id="acbff-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="acbff-113">Lucene má výkonné možnosti syntaxe dotazů a může dotazovat data podle:</span><span class="sxs-lookup"><span data-stu-id="acbff-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="acbff-114">Termín (celé slovo)</span><span class="sxs-lookup"><span data-stu-id="acbff-114">Term (a full word)</span></span>
- <span data-ttu-id="acbff-115">Prefix (začíná – s Wordem)</span><span class="sxs-lookup"><span data-stu-id="acbff-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="acbff-116">Zástupný znak (pomocí \* filtrů "" nebo "?")</span><span class="sxs-lookup"><span data-stu-id="acbff-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="acbff-117">Fráze (sekvence textu v dokumentu)</span><span class="sxs-lookup"><span data-stu-id="acbff-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="acbff-118">Logická hodnota (složitá hledání kombinují dotazy)</span><span class="sxs-lookup"><span data-stu-id="acbff-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="acbff-119">I když Lucene nabízí pro hledání nízké úrovně, Elasticsearch poskytuje server, který je umístěný na Lucene.</span><span class="sxs-lookup"><span data-stu-id="acbff-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="acbff-120">Elasticsearch přidává funkce vyšší úrovně, které zjednodušují práci s Lucene, včetně rozhraní RESTful API pro přístup k funkcím indexování a vyhledávání v aplikaci Lucene.</span><span class="sxs-lookup"><span data-stu-id="acbff-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="acbff-121">Poskytuje taky distribuovanou infrastrukturu, která podporuje obrovské škálovatelnost, odolnost proti chybám a vysokou dostupnost.</span><span class="sxs-lookup"><span data-stu-id="acbff-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="acbff-122">Pro větší cloudové nativní aplikace s požadavky na hledání je Elasticsearch k dispozici jako spravovaná služba v Azure.</span><span class="sxs-lookup"><span data-stu-id="acbff-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="acbff-123">Služba Microsoft Azure Marketplace funkce předkonfigurovaných šablon, které můžou vývojáři použít k nasazení clusteru Elasticsearch v Azure.</span><span class="sxs-lookup"><span data-stu-id="acbff-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="acbff-124">Z Microsoft Azure Marketplace můžou vývojáři využít předem nakonfigurované šablony, pomocí kterých můžete rychle nasadit cluster Elasticsearch v Azure.</span><span class="sxs-lookup"><span data-stu-id="acbff-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="acbff-125">Pomocí nabídky spravované v Azure můžete nasadit až 50 datových uzlů, 20 koordinačních uzlů a tři vyhrazené hlavní uzly.</span><span class="sxs-lookup"><span data-stu-id="acbff-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="acbff-126">Souhrn</span><span class="sxs-lookup"><span data-stu-id="acbff-126">Summary</span></span>

<span data-ttu-id="acbff-127">V této části najdete podrobný přehled dat v systémech nativních pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="acbff-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="acbff-128">Začali jsme na rozdíl od ukládání dat v aplikacích v monolitické s využitím vzorů úložiště dat v nativních systémech cloudu.</span><span class="sxs-lookup"><span data-stu-id="acbff-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="acbff-129">Prohlédli jsme se na vzorcích dat implementovaných v nativních systémech cloudu, včetně dotazů na různé služby, distribuovaných transakcí a vzorů, které se týkají systémů s vysokými objemy.</span><span class="sxs-lookup"><span data-stu-id="acbff-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="acbff-130">NoSQL jsme na SQL data.</span><span class="sxs-lookup"><span data-stu-id="acbff-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="acbff-131">Prohlédli jsme si možnosti úložiště dat dostupné v Azure, které obsahují možnosti orientované na Microsoft i open source.</span><span class="sxs-lookup"><span data-stu-id="acbff-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="acbff-132">Nakonec jsme probrali ukládání do mezipaměti a Elasticsearch v cloudové nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="acbff-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="acbff-133">Reference</span><span class="sxs-lookup"><span data-stu-id="acbff-133">References</span></span>

- [<span data-ttu-id="acbff-134">Model dělení zodpovědnosti příkazů a dotazů (CQRS – Command and Query Responsibility Segregation)</span><span class="sxs-lookup"><span data-stu-id="acbff-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="acbff-135">Vzor zdroje událostí</span><span class="sxs-lookup"><span data-stu-id="acbff-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="acbff-136">Proč není RDBMS odolný proti oddílu v CAP věta a proč je k dispozici?</span><span class="sxs-lookup"><span data-stu-id="acbff-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="acbff-137">Materialized View</span><span class="sxs-lookup"><span data-stu-id="acbff-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="acbff-138">Všechno, co opravdu potřebujete znát o open source databázích</span><span class="sxs-lookup"><span data-stu-id="acbff-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="acbff-139">Model kompenzační transakce</span><span class="sxs-lookup"><span data-stu-id="acbff-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="acbff-140">Vzor Saga</span><span class="sxs-lookup"><span data-stu-id="acbff-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="acbff-141">Saga vzory | Implementace obchodních transakcí pomocí mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="acbff-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="acbff-142">Model kompenzační transakce</span><span class="sxs-lookup"><span data-stu-id="acbff-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="acbff-143">Seznámení za 9 míč: vysvětlení úrovní konzistence Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="acbff-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="acbff-144">Zkoumání různých typů databází NoSQL část II</span><span class="sxs-lookup"><span data-stu-id="acbff-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="acbff-145">V databázích RDBMS, NoSQL a NewSQL. Rozhovor s Jan Ryanou</span><span class="sxs-lookup"><span data-stu-id="acbff-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="acbff-146">SQL vs NoSQL vs NewSQL: úplné porovnání</span><span class="sxs-lookup"><span data-stu-id="acbff-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="acbff-147">POMLČKa: čtyři vlastnosti databáze Kubernetes-Native</span><span class="sxs-lookup"><span data-stu-id="acbff-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="acbff-148">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="acbff-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="acbff-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="acbff-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="acbff-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="acbff-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="acbff-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="acbff-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="acbff-152">Elasticsearch: konečný průvodce</span><span class="sxs-lookup"><span data-stu-id="acbff-152">Elasticsearch: The Definitive Guide</span></span>](https://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="acbff-153">Úvod do Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="acbff-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="acbff-154">[Předchozí](azure-caching.md) 
> [Další](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="acbff-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
