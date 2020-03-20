---
title: Co je .NET for Apache Spark?
description: Získejte informace o rozhraní .NET pro Apache Spark, bezplatném open source a multiplatformním rámci pro analýzu velkých objemů dat, které odvádí Spark kamkoli, kam píšete kód .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458200"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="37d5d-103">Co je .NET for Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="37d5d-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="37d5d-104">[Apache Spark](what-is-spark.md) je univerzální distribuovaný procesor ový modul pro analýzu velkých datových sad – obvykle terabajtů nebo petabajtů dat.</span><span class="sxs-lookup"><span data-stu-id="37d5d-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="37d5d-105">S rozhraním .NET pro Apache Spark, bezplatnou, otevřenou a multiplatformní podporou .NET pro populární open source rámec pro analýzu velkých objemů dat, můžete nyní přidat sílu Apache Spark do vašich aplikací pro velké objemy dat pomocí jazyků, které už znáte.</span><span class="sxs-lookup"><span data-stu-id="37d5d-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="37d5d-106">Proč zvolit rozhraní .NET pro Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="37d5d-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="37d5d-107">.NET pro Apache Spark umožňuje vývojářům se zkušenostmi s rozhraním .NET nebo základy kódu k účasti ve světě analýzy velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="37d5d-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="37d5d-108">.NET pro Apache Spark poskytuje vysoce výkonná rozhraní API pro použití Spark z C# a F#.</span><span class="sxs-lookup"><span data-stu-id="37d5d-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="37d5d-109">Pomocí c# a f#, můžete přistupovat:</span><span class="sxs-lookup"><span data-stu-id="37d5d-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="37d5d-110">DataFrame a SparkSQL pro práci se strukturovanými daty.</span><span class="sxs-lookup"><span data-stu-id="37d5d-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="37d5d-111">Spark Structured Streaming pro práci s streamovanými daty.</span><span class="sxs-lookup"><span data-stu-id="37d5d-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="37d5d-112">Spark SQL pro psaní dotazů se syntaxí SQL.</span><span class="sxs-lookup"><span data-stu-id="37d5d-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="37d5d-113">Integrace strojového učení pro rychlejší školení a predikci (to znamená použít rozhraní .NET pro Apache Spark vedle [ML.NET).](https://dot.net/ml)</span><span class="sxs-lookup"><span data-stu-id="37d5d-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="37d5d-114">.NET pro Apache Spark je kompatibilní s .NET Standard, formální specifikace rozhraní API .NET, které jsou společné napříč implementacemi .NET.</span><span class="sxs-lookup"><span data-stu-id="37d5d-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="37d5d-115">To znamená, že můžete použít rozhraní .NET pro Apache Spark kdekoli, kde napíšete kód .NET, což vám umožní znovu použít všechny znalosti, dovednosti, kód a knihovny, které již máte jako vývojář .NET.</span><span class="sxs-lookup"><span data-stu-id="37d5d-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="37d5d-116">.NET pro Apache Spark běží na Windows, Linux a macOS pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="37d5d-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="37d5d-117">Je také spuštěn v systému Windows pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37d5d-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="37d5d-118">Své aplikace můžete nasadit do všech hlavních poskytovatelů cloudu, včetně Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks a Databricks na AWS.</span><span class="sxs-lookup"><span data-stu-id="37d5d-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="37d5d-119">.NET pro architekturu Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37d5d-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="37d5d-120">Vazba jazyka C#/ F# na Spark je napsána na nové vrstvě Interop Spark, která nabízí snadnější rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="37d5d-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="37d5d-121">Tato nová vrstva Spark interop byl napsán pomocí osvědčených postupů pro rozšíření jazyka a optimalizuje pro interop a výkon.</span><span class="sxs-lookup"><span data-stu-id="37d5d-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="37d5d-122">Dlouhodobě lze tuto rozšiřitelnost použít pro přidání podpory pro jiné jazyky ve Sparku.</span><span class="sxs-lookup"><span data-stu-id="37d5d-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="37d5d-123">![.NET pro architekturu Apache Spark](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="37d5d-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="37d5d-124">O podpoře interop pro rozšíření jazyka Spark se můžete dozvědět v [návrhu](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="37d5d-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="37d5d-125">.NET pro výkon Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37d5d-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="37d5d-126">Ve srovnání s Pythonem a Scalou používajícím [benchmark TPC-H](http://www.tpc.org/tpch/)si rozhraní .NET pro Apache Spark ve většině případů vede dobře a je 2x rychlejší než Python, když je rozhodující výkon uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="37d5d-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="37d5d-127">Stále se snaží zlepšit a porovnat výkonnost.</span><span class="sxs-lookup"><span data-stu-id="37d5d-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="37d5d-128">Chcete-li provést vlastní srovnávací testy, podívejte se na srovnávací testy dostupné na [rozhraní .NET pro Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="37d5d-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="37d5d-129">.NET pro plán Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37d5d-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="37d5d-130">Další informace o krátkodobých a dlouhodobých plánech z oficiálního [plánu .NET pro Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="37d5d-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="37d5d-131">Nadace .NET</span><span class="sxs-lookup"><span data-stu-id="37d5d-131">.NET Foundation</span></span>

<span data-ttu-id="37d5d-132">Projekt .NET pro Apache Spark je součástí [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="37d5d-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="37d5d-133">Contributions (Příspěvky)</span><span class="sxs-lookup"><span data-stu-id="37d5d-133">Contributions</span></span>

<span data-ttu-id="37d5d-134">Tým .NET pro Apache Spark podporuje příspěvky, problémy githubu i žádosti o přijetí vyžádat.</span><span class="sxs-lookup"><span data-stu-id="37d5d-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="37d5d-135">Nejprve vyhledejte [existující problém](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="37d5d-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="37d5d-136">Pokud nemůžete najít existující problém, [otevřete nový problém](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="37d5d-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="37d5d-137">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37d5d-137">Next steps</span></span>

<span data-ttu-id="37d5d-138">Zkuste .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37d5d-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="37d5d-139">Kurz: Začínáme s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37d5d-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
