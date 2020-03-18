---
title: Přehled diagnostických nástrojů - .NET Core
description: Přehled nástrojů a technik, které jsou k dispozici pro diagnostiku aplikací .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399047"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="9f29d-103">Jaké diagnostické nástroje jsou k dispozici v rozhraní .NET Core?</span><span class="sxs-lookup"><span data-stu-id="9f29d-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="9f29d-104">Software se ne vždy chová tak, jak byste očekávali, ale rozhraní .NET Core má nástroje a rozhraní API, které vám pomohou tyto problémy rychle a efektivně diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="9f29d-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="9f29d-105">Tento článek vám pomůže najít různé nástroje, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="9f29d-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="9f29d-106">Spravované ladicí programy</span><span class="sxs-lookup"><span data-stu-id="9f29d-106">Managed debuggers</span></span>

<span data-ttu-id="9f29d-107">[Spravované ladicí program](managed-debuggers.md) umožňuje interakci s programem.</span><span class="sxs-lookup"><span data-stu-id="9f29d-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="9f29d-108">Pozastavení, postupné provádění, zkoumání a obnovení vám umožní nahlédnout do chování vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="9f29d-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="9f29d-109">Ladicí program je první volbou pro diagnostiku funkčních problémů, které lze snadno reprodukovat.</span><span class="sxs-lookup"><span data-stu-id="9f29d-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="9f29d-110">Protokolování a trasování</span><span class="sxs-lookup"><span data-stu-id="9f29d-110">Logging and tracing</span></span>

<span data-ttu-id="9f29d-111">[Protokolování a trasování](logging-tracing.md) jsou související techniky.</span><span class="sxs-lookup"><span data-stu-id="9f29d-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="9f29d-112">Odkazují na instrumentační kód k vytvoření souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="9f29d-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="9f29d-113">Soubory zaznamenávají podrobnosti o tom, co program dělá.</span><span class="sxs-lookup"><span data-stu-id="9f29d-113">The files record the details of what a program does.</span></span> <span data-ttu-id="9f29d-114">Tyto detaily lze použít k diagnostice nejsložitějších problémů.</span><span class="sxs-lookup"><span data-stu-id="9f29d-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="9f29d-115">V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.</span><span class="sxs-lookup"><span data-stu-id="9f29d-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="9f29d-116">Testování částí</span><span class="sxs-lookup"><span data-stu-id="9f29d-116">Unit testing</span></span>

<span data-ttu-id="9f29d-117">[Testování částí](../testing/index.md) je klíčovou součástí průběžné integrace a nasazování vysoce kvalitního softwaru.</span><span class="sxs-lookup"><span data-stu-id="9f29d-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="9f29d-118">Testy částí jsou navrženy tak, aby vám včasné varování, když něco rozbít.</span><span class="sxs-lookup"><span data-stu-id="9f29d-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="9f29d-119">Globální nástroje pro diagnostiku dotnet .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f29d-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="9f29d-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="9f29d-120">dotnet-counters</span></span>

<span data-ttu-id="9f29d-121">[čítače dotnet](dotnet-counters.md) je nástroj pro sledování výkonu pro monitorování stavu první úrovně a sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="9f29d-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="9f29d-122">Sleduje hodnoty čítače výkonu <xref:System.Diagnostics.Tracing.EventCounter> publikované prostřednictvím rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9f29d-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="9f29d-123">Můžete například rychle sledovat věci, jako je využití procesoru nebo rychlost výjimky jsou vyvolány v aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f29d-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="9f29d-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="9f29d-124">dotnet-dump</span></span>

<span data-ttu-id="9f29d-125">[Nástroj dotnet-dump](dotnet-dump.md) je způsob, jak shromažďovat a analyzovat výpisy jádra systému Windows a Linux bez nativního ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="9f29d-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="9f29d-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9f29d-126">dotnet-trace</span></span>

<span data-ttu-id="9f29d-127">.NET Core zahrnuje to, co se `EventPipe` nazývá prostřednictvím, které jsou vystavena diagnostická data.</span><span class="sxs-lookup"><span data-stu-id="9f29d-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="9f29d-128">Nástroj [dotnet-trace](dotnet-trace.md) umožňuje využívat zajímavá data profilování z vaší aplikace, která vám můžou pomoct ve scénářích, kde je potřeba způsobit pomalé aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f29d-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="9f29d-129">Kurzy diagnostiky .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f29d-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="9f29d-130">Ladění nevrácené paměti</span><span class="sxs-lookup"><span data-stu-id="9f29d-130">Debug a memory leak</span></span>

<span data-ttu-id="9f29d-131">[Kurz: Ladění nevracení paměti](debug-memory-leak.md) prochází hledání min. nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="9f29d-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="9f29d-132">Nástroj [dotnet-counters](dotnet-counters.md) se používá k potvrzení nevracení a nástroj [dotnet-dump](dotnet-dump.md) se používá k diagnostice nevracení.</span><span class="sxs-lookup"><span data-stu-id="9f29d-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
