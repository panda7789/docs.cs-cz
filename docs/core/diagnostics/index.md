---
title: Přehled diagnostických nástrojů – .NET Core
description: Přehled nástrojů a technik, které jsou k dispozici pro diagnostiku aplikací .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 20374c53769bf19901b042e0909175718665b523
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341483"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Jaké diagnostické nástroje jsou k dispozici v .NET Core?

Software se vždy chová podle očekávání, ale rozhraní .NET Core obsahuje nástroje a rozhraní API, které vám pomohou rychle a efektivně diagnostikovat tyto problémy.

Tento článek vám pomůže najít různé nástroje, které potřebujete.

## <a name="managed-debuggers"></a>Spravované ladicí programy

[Spravované ladicí programy](managed-debuggers.md) umožňují pracovat s programem. Pozastavení, přírůstkové provádění, prozkoumání a obnovení, vám poskytne přehled o chování kódu. Ladicí program je první volbou pro diagnostiku funkčních problémů, které je možné snadno reprodukovat.

## <a name="logging-and-tracing"></a>Protokolování a trasování

[Protokolování a trasování](logging-tracing.md) jsou související techniky. Odkazují na instrumentaci kódu k vytváření souborů protokolu. Soubory zaznamenávají podrobnosti o tom, co program dělá. Pomocí těchto podrobností lze diagnostikovat nejsložitější problémy. V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.

## <a name="unit-testing"></a>Testování jednotek

[Testování částí](../testing/index.md) je klíčovou součástí kontinuální integrace a nasazování vysoce kvalitního softwaru. Testy jednotek jsou navržené tak, aby vám při přerušení nějakého upozornění poskytovala včasné varování.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET Core dotnet – globální nástroje diagnostiky

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-Counters](dotnet-counters.md) je nástroj pro monitorování výkonu, který slouží k monitorování stavu první úrovně a vyšetřování výkonu. Sleduje hodnoty čítačů výkonu publikované prostřednictvím rozhraní <xref:System.Diagnostics.Tracing.EventCounter> API. Například můžete rychle monitorovat věci, jako je využití procesoru nebo četnost výjimek vyvolaných v aplikaci .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

Nástroj [dotnet-dump](dotnet-dump.md) je způsob, jak shromažďovat a analyzovat základní výpisy paměti Windows a Linux bez nativního ladicího programu.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core zahrnuje to, co se říká `EventPipe`, prostřednictvím které jsou dostupná diagnostická data. Nástroj [dotnet-Trace](dotnet-trace.md) umožňuje využívat zajímavá data profilace z vaší aplikace, která vám pomůžou ve scénářích, kdy je potřeba, aby aplikace v hlavní příčině běžely pomalu.

## <a name="net-core-diagnostics-tutorials"></a>Kurzy pro diagnostiku .NET Core

### <a name="debug-a-memory-leak"></a>Ladění nevrácené paměti

[Kurz: ladění](debug-memory-leak.md) nevrácené paměti pomocí ladění procházení paměti Nástroj [dotnet-Counters](dotnet-counters.md) slouží k potvrzení nevracení a k diagnostice nevracení slouží nástroj [dotnet-dump](dotnet-dump.md) .
