---
title: Co je .NET for Apache Spark?
description: Přečtěte si o rozhraní .NET pro Apache Spark, bezplatném, open source a mezi platformami pro analýzu velkých objemů dat pro různé platformy, které zabírají Spark kdekoli, kde píšete kód .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: c31b50a20ac08bcde077e1e85ee915435a99fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395848"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="a59b7-103">Co je .NET for Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="a59b7-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="a59b7-104">[Apache Spark](what-is-spark.md) je univerzální modul pro zpracování distribuovaných dat pro analýzy prostřednictvím rozsáhlých datových sad – obvykle terabajtů nebo petabajty dat.</span><span class="sxs-lookup"><span data-stu-id="a59b7-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="a59b7-105">Díky rozhraní .NET pro Apache Spark, bezplatné, open source a podporu rozhraní .NET pro více platforem pro oblíbenou Open Source analýzu velkých objemů dat, teď můžete do aplikací pro velké objemy dat přidat sílu Apache Spark pomocí jazyků, které už znáte.</span><span class="sxs-lookup"><span data-stu-id="a59b7-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="a59b7-106">Proč zvolit .NET pro Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="a59b7-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="a59b7-107">.NET for Apache Spark umožňuje vývojářům využít prostředí .NET nebo základy kódu, aby se mohli zúčastnit celosvětovosti analýz velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="a59b7-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="a59b7-108">.NET for Apache Spark poskytuje rozhraní API pro vysoké výkon pro použití C# Sparku z a F#.</span><span class="sxs-lookup"><span data-stu-id="a59b7-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="a59b7-109">Pomocí C# a F#můžete získat přístup k:</span><span class="sxs-lookup"><span data-stu-id="a59b7-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="a59b7-110">Datový rámec a SparkSQL pro práci se strukturovanými daty</span><span class="sxs-lookup"><span data-stu-id="a59b7-110">DataFrame and SparkSQL for working with structured data</span></span>
* <span data-ttu-id="a59b7-111">Strukturované streamování Sparku pro práci s datovými proudy</span><span class="sxs-lookup"><span data-stu-id="a59b7-111">Spark Structured Streaming for working with streaming data</span></span>
* <span data-ttu-id="a59b7-112">Spark SQL pro zápis dotazů pomocí syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="a59b7-112">Spark SQL for writing queries with SQL syntax</span></span>
* <span data-ttu-id="a59b7-113">Integrace služby Machine Learning pro rychlejší školení a předpovědi (tj. použití .NET pro Apache Spark společně s [ml.NET](http://dot.net/ml))</span><span class="sxs-lookup"><span data-stu-id="a59b7-113">Machine learning integration for faster training and prediction (i.e. use .NET for Apache Spark alongside [ML.NET](http://dot.net/ml))</span></span>

<span data-ttu-id="a59b7-114">Rozhraní .NET pro Apache Spark je kompatibilní s .NET Standard, formální specifikace rozhraní .NET API, která jsou společná pro implementace v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a59b7-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="a59b7-115">To znamená, že můžete použít rozhraní .NET pro Apache Spark kdekoli napíšete kód .NET, který vám umožní znovu použít všechny znalosti, dovednosti, kód a knihovny, které už máte jako vývojář rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a59b7-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="a59b7-116">Rozhraní .NET pro Apache Spark běží na systémech Windows, Linux a macOS pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a59b7-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="a59b7-117">Také se spouští ve Windows pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a59b7-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="a59b7-118">Své aplikace můžete nasadit do všech největších poskytovatelů cloudu, včetně Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks a datacihlů na AWS.</span><span class="sxs-lookup"><span data-stu-id="a59b7-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="a59b7-119">Architektura rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a59b7-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="a59b7-120">Vazba C#/ F# jazyk na Spark je zapsána na nové vrstvě interoperability Spark, která nabízí snadnější rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="a59b7-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="a59b7-121">Tato nová vrstva interoperability Spark byla napsaná pomocí osvědčených postupů pro jazykové rozšíření a optimalizuje pro interoperabilitu a výkon.</span><span class="sxs-lookup"><span data-stu-id="a59b7-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="a59b7-122">Dlouhodobá tato rozšiřitelnost se dá použít k přidání podpory pro jiné jazyky ve Sparku.</span><span class="sxs-lookup"><span data-stu-id="a59b7-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="a59b7-123">@no__t – 0.NET pro Apache Spark architektury @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="a59b7-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="a59b7-124">Informace o podpoře spolupráce pro jazykové rozšíření Spark z návrhu najdete v [části](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="a59b7-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="a59b7-125">.NET pro Apache Spark výkon</span><span class="sxs-lookup"><span data-stu-id="a59b7-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="a59b7-126">V porovnání s Pythonem a Scala pomocí [srovnávacího testu TPC-H](http://www.tpc.org/tpch/)využije .net pro Apache Spark ve většině případů dobře a je dvojnásobější, než Python, pokud je důležitý výkon funkce definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a59b7-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="a59b7-127">Pro zlepšení výkonu a srovnávací testy výkonu probíhá nepřetržité úsilí.</span><span class="sxs-lookup"><span data-stu-id="a59b7-127">There is an ongoing effort to improve and benchmark performance.</span></span> 

<span data-ttu-id="a59b7-128">Pokud chcete vlastní srovnávací testy, přečtěte si srovnávací testy dostupné v [rozhraní .NET pro Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="a59b7-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="a59b7-129">Plán .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a59b7-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="a59b7-130">Přečtěte si o krátkodobých a dlouhodobých plánech z oficiálního [rozhraní .NET pro Apache Spark plán](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="a59b7-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="a59b7-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="a59b7-131">.NET Foundation</span></span>

<span data-ttu-id="a59b7-132">Projekt .NET for Apache Spark je součástí [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="a59b7-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="a59b7-133">Věcný</span><span class="sxs-lookup"><span data-stu-id="a59b7-133">Contributions</span></span>

<span data-ttu-id="a59b7-134">.NET for Apache Spark Team podporuje příspěvky, i žádosti GitHubu a žádosti o přijetí změn.</span><span class="sxs-lookup"><span data-stu-id="a59b7-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="a59b7-135">Nejprve vyhledejte [existující problém](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="a59b7-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="a59b7-136">Pokud nemůžete najít existující problém, [otevřete nový problém](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="a59b7-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a59b7-137">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a59b7-137">Next steps</span></span>

<span data-ttu-id="a59b7-138">Vyzkoušejte .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="a59b7-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a59b7-139">Kurz: Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a59b7-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
