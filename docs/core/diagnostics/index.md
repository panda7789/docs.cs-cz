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
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Jaké diagnostické nástroje jsou k dispozici v rozhraní .NET Core?

Software se ne vždy chová tak, jak byste očekávali, ale rozhraní .NET Core má nástroje a rozhraní API, které vám pomohou tyto problémy rychle a efektivně diagnostikovat.

Tento článek vám pomůže najít různé nástroje, které potřebujete.

## <a name="managed-debuggers"></a>Spravované ladicí programy

[Spravované ladicí program](managed-debuggers.md) umožňuje interakci s programem. Pozastavení, postupné provádění, zkoumání a obnovení vám umožní nahlédnout do chování vašeho kódu. Ladicí program je první volbou pro diagnostiku funkčních problémů, které lze snadno reprodukovat.

## <a name="logging-and-tracing"></a>Protokolování a trasování

[Protokolování a trasování](logging-tracing.md) jsou související techniky. Odkazují na instrumentační kód k vytvoření souborů protokolu. Soubory zaznamenávají podrobnosti o tom, co program dělá. Tyto detaily lze použít k diagnostice nejsložitějších problémů. V kombinaci s časovými razítky jsou tyto techniky také cenné při vyšetřování výkonu.

## <a name="unit-testing"></a>Testování částí

[Testování částí](../testing/index.md) je klíčovou součástí průběžné integrace a nasazování vysoce kvalitního softwaru. Testy částí jsou navrženy tak, aby vám včasné varování, když něco rozbít.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Globální nástroje pro diagnostiku dotnet .NET Core

### <a name="dotnet-counters"></a>dotnet-counters

[čítače dotnet](dotnet-counters.md) je nástroj pro sledování výkonu pro monitorování stavu první úrovně a sledování výkonu. Sleduje hodnoty čítače výkonu <xref:System.Diagnostics.Tracing.EventCounter> publikované prostřednictvím rozhraní API. Můžete například rychle sledovat věci, jako je využití procesoru nebo rychlost výjimky jsou vyvolány v aplikaci .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

[Nástroj dotnet-dump](dotnet-dump.md) je způsob, jak shromažďovat a analyzovat výpisy jádra systému Windows a Linux bez nativního ladicího programu.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core zahrnuje to, co se `EventPipe` nazývá prostřednictvím, které jsou vystavena diagnostická data. Nástroj [dotnet-trace](dotnet-trace.md) umožňuje využívat zajímavá data profilování z vaší aplikace, která vám můžou pomoct ve scénářích, kde je potřeba způsobit pomalé aplikace.

## <a name="net-core-diagnostics-tutorials"></a>Kurzy diagnostiky .NET Core

### <a name="debug-a-memory-leak"></a>Ladění nevrácené paměti

[Kurz: Ladění nevracení paměti](debug-memory-leak.md) prochází hledání min. nevracení paměti. Nástroj [dotnet-counters](dotnet-counters.md) se používá k potvrzení nevracení a nástroj [dotnet-dump](dotnet-dump.md) se používá k diagnostice nevracení.
