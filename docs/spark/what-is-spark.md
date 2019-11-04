---
title: Co je Apache Spark?
description: Přečtěte si o scénářích Apache Spark a velkých objemů dat.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458177"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="f8399-103">Co je Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="f8399-103">What is Apache Spark?</span></span>

<span data-ttu-id="f8399-104">[Apache Spark](https://spark.apache.org/) je open source platforma pro paralelní zpracování, která podporuje zpracování v paměti pro zvýšení výkonu aplikací, které analyzují velké objemy dat.</span><span class="sxs-lookup"><span data-stu-id="f8399-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="f8399-105">Řešení pro velké objemy dat jsou navržená tak, aby data, která jsou pro tradiční databáze moc velká nebo složitá.</span><span class="sxs-lookup"><span data-stu-id="f8399-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="f8399-106">Spark zpracovává velké objemy dat v paměti, což je mnohem rychlejší než v případě alternativ na disku.</span><span class="sxs-lookup"><span data-stu-id="f8399-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="f8399-107">Běžné scénáře s velkými objemy dat</span><span class="sxs-lookup"><span data-stu-id="f8399-107">Common big data scenarios</span></span>

<span data-ttu-id="f8399-108">Pokud potřebujete ukládat a zpracovávat velké objemy dat, transformovat nestrukturovaná data nebo zpracovávat streamovaná data, můžete zvážit architekturu velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="f8399-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="f8399-109">Spark je univerzální distribuovaný modul pro zpracování, který se dá použít pro několik scénářů velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="f8399-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="f8399-110">Extrakce, transformace a načítání (ETL)</span><span class="sxs-lookup"><span data-stu-id="f8399-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="f8399-111">[Extrakce, transformace a načítání (ETL)](/azure/architecture/data-guide/relational-data/etl) je proces shromažďování dat z jednoho nebo více zdrojů, úpravy dat a přesun dat do nového úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="f8399-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="f8399-112">Existuje několik způsobů, jak transformovat data, včetně:</span><span class="sxs-lookup"><span data-stu-id="f8399-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="f8399-113">Filtrování</span><span class="sxs-lookup"><span data-stu-id="f8399-113">Filtering</span></span>
* <span data-ttu-id="f8399-114">Řazení</span><span class="sxs-lookup"><span data-stu-id="f8399-114">Sorting</span></span>
* <span data-ttu-id="f8399-115">Agregování</span><span class="sxs-lookup"><span data-stu-id="f8399-115">Aggregating</span></span>
* <span data-ttu-id="f8399-116">Spojování</span><span class="sxs-lookup"><span data-stu-id="f8399-116">Joining</span></span>
* <span data-ttu-id="f8399-117">Čistil</span><span class="sxs-lookup"><span data-stu-id="f8399-117">Cleaning</span></span>
* <span data-ttu-id="f8399-118">Můžou</span><span class="sxs-lookup"><span data-stu-id="f8399-118">Deduplicating</span></span>
* <span data-ttu-id="f8399-119">Opětovné</span><span class="sxs-lookup"><span data-stu-id="f8399-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="f8399-120">Zpracování datových proudů v reálném čase</span><span class="sxs-lookup"><span data-stu-id="f8399-120">Real-time data stream processing</span></span>

<span data-ttu-id="f8399-121">Streamování dat nebo dat v reálném čase jsou data v pohybu.</span><span class="sxs-lookup"><span data-stu-id="f8399-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="f8399-122">V některých příkladech streamování dat jsou telemetrie ze zařízení IoT, Weblogs a stránkách.</span><span class="sxs-lookup"><span data-stu-id="f8399-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="f8399-123">Data v reálném čase lze zpracovat za účelem poskytnutí užitečných informací, jako jsou geoprostorové analýzy, vzdálené monitorování a detekce anomálií.</span><span class="sxs-lookup"><span data-stu-id="f8399-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="f8399-124">Stejně jako u relačních dat můžete filtrovat, agregovat a připravit streamovaná data, než data přesunete do výstupní jímky.</span><span class="sxs-lookup"><span data-stu-id="f8399-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="f8399-125">Apache Spark podporuje [zpracování datových proudů v reálném čase](/azure/architecture/data-guide/big-data/real-time-processing) prostřednictvím [streamování Sparku](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="f8399-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="f8399-126">Dávkové zpracování</span><span class="sxs-lookup"><span data-stu-id="f8399-126">Batch processing</span></span>

<span data-ttu-id="f8399-127">[Dávkové zpracování](/azure/architecture/data-guide/big-data/batch-processing) je zpracování velkých objemů dat v klidovém umístění.</span><span class="sxs-lookup"><span data-stu-id="f8399-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="f8399-128">Můžete filtrovat, agregovat a připravit velmi velké datové sady s využitím dlouhotrvajících úloh paralelně.</span><span class="sxs-lookup"><span data-stu-id="f8399-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="f8399-129">Machine Learning prostřednictvím MLlib</span><span class="sxs-lookup"><span data-stu-id="f8399-129">Machine learning through MLlib</span></span>

<span data-ttu-id="f8399-130">Strojové učení slouží k pokročilým analytickým problémům.</span><span class="sxs-lookup"><span data-stu-id="f8399-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="f8399-131">Počítač může používat stávající data k předpovědi nebo předpovědi budoucích chování, výsledků a trendů.</span><span class="sxs-lookup"><span data-stu-id="f8399-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="f8399-132">[MLlib](https://spark.apache.org/mllib/)je knihovna strojového učení, která obsahuje několik algoritmů a nástrojů strojového učení. Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f8399-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="f8399-133">Zpracování grafů prostřednictvím GraphX</span><span class="sxs-lookup"><span data-stu-id="f8399-133">Graph processing through GraphX</span></span>

<span data-ttu-id="f8399-134">Graf je kolekce uzlů, které jsou propojeny pomocí okrajů.</span><span class="sxs-lookup"><span data-stu-id="f8399-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="f8399-135">Pokud máte hierarchická data nebo data s propojenými vztahy, můžete použít databázi grafu.</span><span class="sxs-lookup"><span data-stu-id="f8399-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="f8399-136">Tato data můžete zpracovat pomocí rozhraní [GRAPHX](https://spark.apache.org/graphx/) API pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f8399-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="f8399-137">SQL a strukturované zpracování dat pomocí Spark SQL</span><span class="sxs-lookup"><span data-stu-id="f8399-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="f8399-138">Pokud pracujete se strukturovanými (formátovanými) daty, můžete v aplikaci Spark použít dotazy SQL pomocí [Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="f8399-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="f8399-139">Architektura Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f8399-139">Apache Spark architecture</span></span>

<span data-ttu-id="f8399-140">Apache Spark, která používá architekturu hlavního/pracovního procesu, má tři hlavní komponenty: ovladač, vykonavatelé a Správce clusteru.</span><span class="sxs-lookup"><span data-stu-id="f8399-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="f8399-142">Faktorů</span><span class="sxs-lookup"><span data-stu-id="f8399-142">Driver</span></span>

<span data-ttu-id="f8399-143">Ovladač se skládá z vašeho programu, jako C# Konzolová aplikace a z relace Spark.</span><span class="sxs-lookup"><span data-stu-id="f8399-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="f8399-144">Relace Spark přebírá program a rozděluje ho do menších úloh, které jsou zpracovávány vykonavateli.</span><span class="sxs-lookup"><span data-stu-id="f8399-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="f8399-145">Prováděcí moduly</span><span class="sxs-lookup"><span data-stu-id="f8399-145">Executors</span></span>

<span data-ttu-id="f8399-146">Každý vykonavatel nebo pracovní uzel přijme úkol od ovladače a provede tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="f8399-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="f8399-147">Vykonavatelé se nacházejí v entitě, která se označuje jako cluster.</span><span class="sxs-lookup"><span data-stu-id="f8399-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="f8399-148">Správce clusteru</span><span class="sxs-lookup"><span data-stu-id="f8399-148">Cluster manager</span></span>

<span data-ttu-id="f8399-149">Správce clusteru komunikuje s ovladačem i s prováděcími moduly pro:</span><span class="sxs-lookup"><span data-stu-id="f8399-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="f8399-150">Spravovat přidělení prostředků</span><span class="sxs-lookup"><span data-stu-id="f8399-150">Manage resource allocation</span></span>
* <span data-ttu-id="f8399-151">Spravovat rozdělení programu</span><span class="sxs-lookup"><span data-stu-id="f8399-151">Manage program division</span></span>
* <span data-ttu-id="f8399-152">Správa provádění programu</span><span class="sxs-lookup"><span data-stu-id="f8399-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="f8399-153">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="f8399-153">Language support</span></span>

<span data-ttu-id="f8399-154">Apache Spark podporuje následující programovací jazyky:</span><span class="sxs-lookup"><span data-stu-id="f8399-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="f8399-155">Scala</span><span class="sxs-lookup"><span data-stu-id="f8399-155">Scala</span></span>
* <span data-ttu-id="f8399-156">Python</span><span class="sxs-lookup"><span data-stu-id="f8399-156">Python</span></span>
* <span data-ttu-id="f8399-157">Java</span><span class="sxs-lookup"><span data-stu-id="f8399-157">Java</span></span>
* <span data-ttu-id="f8399-158">SQL</span><span class="sxs-lookup"><span data-stu-id="f8399-158">SQL</span></span>
* <span data-ttu-id="f8399-159">R</span><span class="sxs-lookup"><span data-stu-id="f8399-159">R</span></span>
* <span data-ttu-id="f8399-160">.NET</span><span class="sxs-lookup"><span data-stu-id="f8399-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="f8399-161">Rozhraní Spark API</span><span class="sxs-lookup"><span data-stu-id="f8399-161">Spark APIs</span></span>

<span data-ttu-id="f8399-162">Apache Spark podporuje následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="f8399-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="f8399-163">Rozhraní Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="f8399-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="f8399-164">Rozhraní Spark Java API</span><span class="sxs-lookup"><span data-stu-id="f8399-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="f8399-165">Rozhraní Spark Python API</span><span class="sxs-lookup"><span data-stu-id="f8399-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="f8399-166">Rozhraní Spark R API</span><span class="sxs-lookup"><span data-stu-id="f8399-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="f8399-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), integrované funkce</span><span class="sxs-lookup"><span data-stu-id="f8399-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="f8399-168">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f8399-168">Next steps</span></span>

<span data-ttu-id="f8399-169">Přečtěte si, jak můžete použít Apache Spark v aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="f8399-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="f8399-170">Díky rozhraní .NET pro Apache Spark můžou vývojáři s prostředím .NET a obchodní logikou zapisovat dotazy na C# velké F#objemy dat v a.</span><span class="sxs-lookup"><span data-stu-id="f8399-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f8399-171">Co je .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f8399-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
