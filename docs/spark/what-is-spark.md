---
title: Co je Apache Spark?
description: Seznamte se s Apache Spark a scénáři velkých objemů dat.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458177"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="c7cf7-103">Co je Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="c7cf7-103">What is Apache Spark?</span></span>

<span data-ttu-id="c7cf7-104">[Apache Spark](https://spark.apache.org/) je open source paralelní zpracování framework, který podporuje zpracování v paměti pro zvýšení výkonu aplikací, které analyzují velké objemy dat.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="c7cf7-105">Řešení pro velké objemy dat jsou navržena tak, aby zpracovávala data, která jsou příliš velká nebo složitá pro tradiční databáze.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="c7cf7-106">Spark zpracovává velké množství dat v paměti, což je mnohem rychlejší než alternativy založené na disku.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="c7cf7-107">Běžné scénáře velkých objemů dat</span><span class="sxs-lookup"><span data-stu-id="c7cf7-107">Common big data scenarios</span></span>

<span data-ttu-id="c7cf7-108">Architekturu velkých objemů dat můžete zvážit, pokud potřebujete ukládat a zpracovávat velké objemy dat, transformovat nestrukturovaná data nebo zpracovávat streamovaná data.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="c7cf7-109">Spark je univerzální distribuovaný procesorový modul, který lze použít pro několik scénářů velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="c7cf7-110">Extrakce, transformace a načtení (ETL)</span><span class="sxs-lookup"><span data-stu-id="c7cf7-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="c7cf7-111">[Extrahovat, transformovat a načíst (ETL)](/azure/architecture/data-guide/relational-data/etl) je proces shromažďování dat z jednoho nebo více zdrojů, úpravy dat a přesunutí dat do nového úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="c7cf7-112">Data lze transformovat několika způsoby, včetně:</span><span class="sxs-lookup"><span data-stu-id="c7cf7-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="c7cf7-113">Filtrování</span><span class="sxs-lookup"><span data-stu-id="c7cf7-113">Filtering</span></span>
* <span data-ttu-id="c7cf7-114">Řazení</span><span class="sxs-lookup"><span data-stu-id="c7cf7-114">Sorting</span></span>
* <span data-ttu-id="c7cf7-115">Agregaci</span><span class="sxs-lookup"><span data-stu-id="c7cf7-115">Aggregating</span></span>
* <span data-ttu-id="c7cf7-116">Připojení</span><span class="sxs-lookup"><span data-stu-id="c7cf7-116">Joining</span></span>
* <span data-ttu-id="c7cf7-117">Čištění</span><span class="sxs-lookup"><span data-stu-id="c7cf7-117">Cleaning</span></span>
* <span data-ttu-id="c7cf7-118">Odstranění duplicit</span><span class="sxs-lookup"><span data-stu-id="c7cf7-118">Deduplicating</span></span>
* <span data-ttu-id="c7cf7-119">Ověřování</span><span class="sxs-lookup"><span data-stu-id="c7cf7-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="c7cf7-120">Zpracování datových proudů v reálném čase</span><span class="sxs-lookup"><span data-stu-id="c7cf7-120">Real-time data stream processing</span></span>

<span data-ttu-id="c7cf7-121">Streamování dat v reálném čase jsou data v pohybu.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="c7cf7-122">Telemetrie ze zařízení IoT, weblogy a clickstreams jsou všechny příklady streamování dat.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="c7cf7-123">Data v reálném čase mohou být zpracována za účelem poskytování užitečných informací, jako je například geoprostorová analýza, vzdálené monitorování a detekce anomálií.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="c7cf7-124">Stejně jako relační data můžete filtrovat, agregovat a připravovat streamovaná data před přesunutím dat do výstupníjím propadu.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="c7cf7-125">Apache Spark podporuje [zpracování datových proudů v reálném čase](/azure/architecture/data-guide/big-data/real-time-processing) prostřednictvím streamování [Spark](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="c7cf7-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="c7cf7-126">Dávkové zpracování</span><span class="sxs-lookup"><span data-stu-id="c7cf7-126">Batch processing</span></span>

<span data-ttu-id="c7cf7-127">[Dávkové zpracování](/azure/architecture/data-guide/big-data/batch-processing) je zpracování velkých objemů dat v klidovém stavu.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="c7cf7-128">Můžete filtrovat, agregovat a připravit velmi velké datové sady pomocí dlouhotrvající úlohy paralelně.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="c7cf7-129">Strojové učení prostřednictvím mllibu</span><span class="sxs-lookup"><span data-stu-id="c7cf7-129">Machine learning through MLlib</span></span>

<span data-ttu-id="c7cf7-130">Strojové učení se používá pro pokročilé analytické problémy.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="c7cf7-131">Počítač může použít existující data k prognóze nebo předvídání budoucího chování, výsledků a trendů.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="c7cf7-132">Knihovna strojového učení Apache Spark, [MLlib](https://spark.apache.org/mllib/), obsahuje několik algoritmů a nástrojů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="c7cf7-133">Zpracování grafů přes GraphX</span><span class="sxs-lookup"><span data-stu-id="c7cf7-133">Graph processing through GraphX</span></span>

<span data-ttu-id="c7cf7-134">Graf je kolekce uzlů propojených hranami.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="c7cf7-135">Databázi grafů můžete použít, pokud máte hierarchická data nebo data s propojenými relacemi.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="c7cf7-136">Tato data můžete zpracovávat pomocí [rozhraní GraphX](https://spark.apache.org/graphx/) API Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="c7cf7-137">SQL a strukturované zpracování dat se Spark SQL</span><span class="sxs-lookup"><span data-stu-id="c7cf7-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="c7cf7-138">Pokud pracujete se strukturovanými (formátovanými) daty, můžete použít dotazy SQL v aplikaci Spark pomocí [Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="c7cf7-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="c7cf7-139">Architektura Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c7cf7-139">Apache Spark architecture</span></span>

<span data-ttu-id="c7cf7-140">Apache Spark, který používá architekturu master/worker, má tři hlavní součásti: ovladač, vykonavatelé a správce clusteru.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="c7cf7-142">Ovladač</span><span class="sxs-lookup"><span data-stu-id="c7cf7-142">Driver</span></span>

<span data-ttu-id="c7cf7-143">Ovladač se skládá z vašeho programu, jako je konzolová aplikace C# a relace Spark.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="c7cf7-144">Relace Spark převezme váš program a rozdělí jej na menší úkoly, které jsou zpracovány vykonavatelé.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="c7cf7-145">Exekutoři</span><span class="sxs-lookup"><span data-stu-id="c7cf7-145">Executors</span></span>

<span data-ttu-id="c7cf7-146">Každý vykonavatel nebo pracovní uzel obdrží úlohu od ovladače a provede tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="c7cf7-147">Prováděcí moduly jsou umístěny v entitě známé jako cluster.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="c7cf7-148">Správce clusteru</span><span class="sxs-lookup"><span data-stu-id="c7cf7-148">Cluster manager</span></span>

<span data-ttu-id="c7cf7-149">Správce clusteru komunikuje s ovladačem i prováděcími moduly s:</span><span class="sxs-lookup"><span data-stu-id="c7cf7-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="c7cf7-150">Správa přidělení prostředků</span><span class="sxs-lookup"><span data-stu-id="c7cf7-150">Manage resource allocation</span></span>
* <span data-ttu-id="c7cf7-151">Spravovat rozdělení programů</span><span class="sxs-lookup"><span data-stu-id="c7cf7-151">Manage program division</span></span>
* <span data-ttu-id="c7cf7-152">Spravovat spuštění programu</span><span class="sxs-lookup"><span data-stu-id="c7cf7-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="c7cf7-153">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="c7cf7-153">Language support</span></span>

<span data-ttu-id="c7cf7-154">Apache Spark podporuje následující programovací jazyky:</span><span class="sxs-lookup"><span data-stu-id="c7cf7-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="c7cf7-155">Scala</span><span class="sxs-lookup"><span data-stu-id="c7cf7-155">Scala</span></span>
* <span data-ttu-id="c7cf7-156">Python</span><span class="sxs-lookup"><span data-stu-id="c7cf7-156">Python</span></span>
* <span data-ttu-id="c7cf7-157">Java</span><span class="sxs-lookup"><span data-stu-id="c7cf7-157">Java</span></span>
* <span data-ttu-id="c7cf7-158">SQL</span><span class="sxs-lookup"><span data-stu-id="c7cf7-158">SQL</span></span>
* <span data-ttu-id="c7cf7-159">R</span><span class="sxs-lookup"><span data-stu-id="c7cf7-159">R</span></span>
* <span data-ttu-id="c7cf7-160">.NET</span><span class="sxs-lookup"><span data-stu-id="c7cf7-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="c7cf7-161">Zapalovací api</span><span class="sxs-lookup"><span data-stu-id="c7cf7-161">Spark APIs</span></span>

<span data-ttu-id="c7cf7-162">Apache Spark podporuje následující api:</span><span class="sxs-lookup"><span data-stu-id="c7cf7-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="c7cf7-163">Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="c7cf7-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="c7cf7-164">Spark Java API</span><span class="sxs-lookup"><span data-stu-id="c7cf7-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="c7cf7-165">Spark Python API</span><span class="sxs-lookup"><span data-stu-id="c7cf7-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="c7cf7-166">Spark R API</span><span class="sxs-lookup"><span data-stu-id="c7cf7-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="c7cf7-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), vestavěné funkce</span><span class="sxs-lookup"><span data-stu-id="c7cf7-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="c7cf7-168">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c7cf7-168">Next steps</span></span>

<span data-ttu-id="c7cf7-169">Zjistěte, jak můžete používat Apache Spark ve vaší aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="c7cf7-170">S rozhraním .NET pro Apache Spark mohou vývojáři se zkušenostmi s rozhraním .NET a obchodní logikou psát dotazy na velká data v c# a F#.</span><span class="sxs-lookup"><span data-stu-id="c7cf7-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c7cf7-171">Co je .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c7cf7-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
