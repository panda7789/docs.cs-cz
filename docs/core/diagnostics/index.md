---
title: Přehled diagnostických nástrojů – .NET Core
description: Přehled nástrojů a technik, které jsou k dispozici pro diagnostiku aplikací .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715569"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="a96bc-103">Jaké diagnostické nástroje jsou k dispozici v .NET Core?</span><span class="sxs-lookup"><span data-stu-id="a96bc-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="a96bc-104">Software se vždy chová podle očekávání, ale rozhraní .NET Core obsahuje nástroje a rozhraní API, které vám pomohou rychle a efektivně diagnostikovat tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="a96bc-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="a96bc-105">Tento článek vám pomůže najít různé nástroje, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a96bc-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="a96bc-106">Spravované ladicí programy</span><span class="sxs-lookup"><span data-stu-id="a96bc-106">Managed debuggers</span></span>

<span data-ttu-id="a96bc-107">[Spravované ladicí programy](managed-debuggers.md) umožňují pracovat s programem.</span><span class="sxs-lookup"><span data-stu-id="a96bc-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="a96bc-108">Pozastavení, přírůstkové provádění, prozkoumání a obnovení, vám poskytne přehled o chování kódu.</span><span class="sxs-lookup"><span data-stu-id="a96bc-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="a96bc-109">Ladicí program je první volbou pro diagnostiku funkčních problémů, které je možné snadno reprodukovat.</span><span class="sxs-lookup"><span data-stu-id="a96bc-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="a96bc-110">Protokolování a trasování</span><span class="sxs-lookup"><span data-stu-id="a96bc-110">Logging and tracing</span></span>

<span data-ttu-id="a96bc-111">[Protokolování a trasování](logging-tracing.md) jsou související techniky.</span><span class="sxs-lookup"><span data-stu-id="a96bc-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="a96bc-112">Odkazují na instrumentaci kódu k vytváření souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="a96bc-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="a96bc-113">Soubory zaznamenávají podrobnosti o tom, co program dělá.</span><span class="sxs-lookup"><span data-stu-id="a96bc-113">The files record the details of what a program does.</span></span> <span data-ttu-id="a96bc-114">Pomocí těchto podrobností lze diagnostikovat nejsložitější problémy.</span><span class="sxs-lookup"><span data-stu-id="a96bc-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="a96bc-115">V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.</span><span class="sxs-lookup"><span data-stu-id="a96bc-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="a96bc-116">Testování jednotek</span><span class="sxs-lookup"><span data-stu-id="a96bc-116">Unit testing</span></span>

<span data-ttu-id="a96bc-117">[Testování částí](../testing/index.md) je klíčovou součástí kontinuální integrace a nasazování vysoce kvalitního softwaru.</span><span class="sxs-lookup"><span data-stu-id="a96bc-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="a96bc-118">Testy jednotek jsou navržené tak, aby vám při přerušení nějakého upozornění poskytovala včasné varování.</span><span class="sxs-lookup"><span data-stu-id="a96bc-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="a96bc-119">.NET Core dotnet – globální nástroje diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a96bc-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="a96bc-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="a96bc-120">dotnet-counters</span></span>

<span data-ttu-id="a96bc-121">[dotnet-Counters](dotnet-counters.md) je nástroj pro monitorování výkonu, který slouží k monitorování stavu první úrovně a vyšetřování výkonu.</span><span class="sxs-lookup"><span data-stu-id="a96bc-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="a96bc-122">Sleduje hodnoty čítačů výkonu publikované prostřednictvím rozhraní <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="a96bc-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="a96bc-123">Například můžete rychle monitorovat věci, jako je využití procesoru nebo četnost výjimek vyvolaných v aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a96bc-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="a96bc-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="a96bc-124">dotnet-dump</span></span>

<span data-ttu-id="a96bc-125">Nástroj [dotnet-dump](dotnet-dump.md) je způsob, jak shromažďovat a analyzovat základní výpisy paměti Windows a Linux bez nativního ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="a96bc-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="a96bc-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="a96bc-126">dotnet-trace</span></span>

<span data-ttu-id="a96bc-127">.NET Core zahrnuje to, co se říká `EventPipe`, prostřednictvím které jsou dostupná diagnostická data.</span><span class="sxs-lookup"><span data-stu-id="a96bc-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="a96bc-128">Nástroj [dotnet-Trace](dotnet-trace.md) umožňuje využívat zajímavá data profilace z vaší aplikace, která vám pomůžou ve scénářích, kdy je potřeba, aby aplikace v hlavní příčině běžely pomalu.</span><span class="sxs-lookup"><span data-stu-id="a96bc-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="a96bc-129">Kurzy diagnostiky .NET Core</span><span class="sxs-lookup"><span data-stu-id="a96bc-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="a96bc-130">Ladění nevrácené paměti</span><span class="sxs-lookup"><span data-stu-id="a96bc-130">Debug a memory leak</span></span>

<span data-ttu-id="a96bc-131">[Kurz: ladění](debug-memory-leak.md) nevrácené paměti pomocí ladění procházení paměti</span><span class="sxs-lookup"><span data-stu-id="a96bc-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="a96bc-132">Nástroj [dotnet-Counters](dotnet-counters.md) slouží k potvrzení nevracení a k diagnostice nevracení slouží nástroj [dotnet-dump](dotnet-dump.md) .</span><span class="sxs-lookup"><span data-stu-id="a96bc-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
