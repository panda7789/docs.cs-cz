---
title: Přehled diagnostických nástrojů – .NET Core
description: Přehled nástrojů a technik, které jsou k dispozici pro diagnostiku aplikací .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: dc64c03ee9c8cee6a5b3c5cc089b4a1a2c27f84a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924779"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="ca663-103">Jaké diagnostické nástroje jsou k dispozici v .NET Core?</span><span class="sxs-lookup"><span data-stu-id="ca663-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="ca663-104">Software se vždy chová podle očekávání, ale rozhraní .NET Core obsahuje nástroje a rozhraní API, které vám pomohou rychle a efektivně diagnostikovat tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="ca663-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="ca663-105">Tento článek vám pomůže najít různé nástroje, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="ca663-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="ca663-106">Spravované ladicí programy</span><span class="sxs-lookup"><span data-stu-id="ca663-106">Managed debuggers</span></span>

<span data-ttu-id="ca663-107">[Spravované ladicí programy](managed-debuggers.md) umožňují pracovat s programem.</span><span class="sxs-lookup"><span data-stu-id="ca663-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="ca663-108">Pozastavení, přírůstkové provádění, prozkoumání a obnovení, vám poskytne přehled o chování kódu.</span><span class="sxs-lookup"><span data-stu-id="ca663-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="ca663-109">Ladicí program je první volbou pro diagnostiku funkčních problémů, které je možné snadno reprodukovat.</span><span class="sxs-lookup"><span data-stu-id="ca663-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="ca663-110">Protokolování a trasování</span><span class="sxs-lookup"><span data-stu-id="ca663-110">Logging and tracing</span></span>

<span data-ttu-id="ca663-111">[Protokolování a trasování](logging-tracing.md) jsou související techniky.</span><span class="sxs-lookup"><span data-stu-id="ca663-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="ca663-112">Odkazují na instrumentaci kódu k vytváření souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="ca663-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="ca663-113">Soubory zaznamenávají podrobnosti o tom, co program dělá.</span><span class="sxs-lookup"><span data-stu-id="ca663-113">The files record the details of what a program does.</span></span> <span data-ttu-id="ca663-114">Pomocí těchto podrobností lze diagnostikovat nejsložitější problémy.</span><span class="sxs-lookup"><span data-stu-id="ca663-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="ca663-115">V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.</span><span class="sxs-lookup"><span data-stu-id="ca663-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="ca663-116">Testování částí</span><span class="sxs-lookup"><span data-stu-id="ca663-116">Unit testing</span></span>

<span data-ttu-id="ca663-117">[Testování částí](../testing/index.md) je klíčovou součástí kontinuální integrace a nasazování vysoce kvalitního softwaru.</span><span class="sxs-lookup"><span data-stu-id="ca663-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="ca663-118">Testy jednotek jsou navržené tak, aby vám při přerušení nějakého upozornění poskytovala včasné varování.</span><span class="sxs-lookup"><span data-stu-id="ca663-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="ca663-119">.NET Core dotnet – globální nástroje diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ca663-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="ca663-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="ca663-120">dotnet-counters</span></span>

<span data-ttu-id="ca663-121">[dotnet-Counters](dotnet-counters.md) je nástroj pro monitorování výkonu, který slouží k monitorování stavu první úrovně a vyšetřování výkonu.</span><span class="sxs-lookup"><span data-stu-id="ca663-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="ca663-122">Sleduje hodnoty čítačů výkonu publikované prostřednictvím <xref:System.Diagnostics.Tracing.EventCounter> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ca663-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="ca663-123">Například můžete rychle monitorovat věci, jako je využití procesoru nebo četnost výjimek vyvolaných v aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ca663-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="ca663-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="ca663-124">dotnet-dump</span></span>

<span data-ttu-id="ca663-125">Nástroj [dotnet-dump](dotnet-dump.md) je způsob, jak shromažďovat a analyzovat základní výpisy paměti Windows a Linux bez nativního ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ca663-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="ca663-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ca663-126">dotnet-trace</span></span>

<span data-ttu-id="ca663-127">.NET Core zahrnuje to, co se nazývá, `EventPipe` prostřednictvím kterého jsou dostupná diagnostická data.</span><span class="sxs-lookup"><span data-stu-id="ca663-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="ca663-128">Nástroj [dotnet-Trace](dotnet-trace.md) umožňuje využívat zajímavá data profilace z vaší aplikace, která vám pomůžou ve scénářích, kdy je potřeba, aby aplikace v hlavní příčině běžely pomalu.</span><span class="sxs-lookup"><span data-stu-id="ca663-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="ca663-129">Kurzy diagnostiky .NET Core</span><span class="sxs-lookup"><span data-stu-id="ca663-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="ca663-130">Ladění nevrácené paměti</span><span class="sxs-lookup"><span data-stu-id="ca663-130">Debug a memory leak</span></span>

<span data-ttu-id="ca663-131">[Kurz: ladění](debug-memory-leak.md) nevrácené paměti pomocí ladění procházení paměti</span><span class="sxs-lookup"><span data-stu-id="ca663-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="ca663-132">Nástroj [dotnet-Counters](dotnet-counters.md) slouží k potvrzení nevracení a k diagnostice nevracení slouží nástroj [dotnet-dump](dotnet-dump.md) .</span><span class="sxs-lookup"><span data-stu-id="ca663-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="ca663-133">Ladění vysokého využití procesoru</span><span class="sxs-lookup"><span data-stu-id="ca663-133">Debug high CPU usage</span></span>

<span data-ttu-id="ca663-134">[Kurz: ladění vysokého využití procesoru](debug-highcpu.md) vás provede šetřením vysokého využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="ca663-134">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="ca663-135">K potvrzení vysokého využití procesoru používá nástroj [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="ca663-135">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="ca663-136">Pak vás provede pomocí [trasování pro nástroj Performance Analysis ( `dotnet-trace` )](dotnet-trace.md) nebo Linux, `perf` který shromáždí a zobrazí profil využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="ca663-136">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="ca663-137">Ladění – zablokování</span><span class="sxs-lookup"><span data-stu-id="ca663-137">Debug deadlock</span></span>

<span data-ttu-id="ca663-138">[Kurz: zablokování ladění](debug-deadlock.md) ukazuje, jak používat nástroj [dotnet-dump](dotnet-dump.md) k prozkoumání vláken a zámků.</span><span class="sxs-lookup"><span data-stu-id="ca663-138">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
