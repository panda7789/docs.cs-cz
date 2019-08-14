---
title: Protokolování a trasování – .NET Core
description: Úvod do protokolování a trasování .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 06781c6a5c1d771b1fa772539705cd1e2b3ad2d4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974129"
---
# <a name="net-core-logging-and-tracing"></a>Protokolování a trasování .NET Core

Protokolování a trasování jsou ve skutečnosti dva názvy pro stejnou techniku. Od počátečních dní počítačů se použila jednoduchá technika. Jednoduše zahrnuje instrumentaci aplikace pro zápis výstupu, který se má spotřebovat později.

## <a name="reasons-to-use-logging-and-tracing"></a>Důvody pro použití protokolování a trasování

Tato jednoduchá technika je překvapivě výkonná. Dá se použít v situacích, kdy dojde k chybě ladicího programu:

- Problémy, ke kterým dochází v dlouhých časových obdobích, mohou být obtížné ladit pomocí tradičního ladicího programu. Protokoly umožňují podrobnou kontrolu po dlouhou dobu. Naproti tomu ladicí programy jsou omezené na analýzu v reálném čase.
- Aplikace s více vlákny a distribuované aplikace jsou často obtížné ladit.  Připojení ladicího programu je v úmyslu změnit chování. Podrobné protokoly je možné analyzovat podle potřeby pro pochopení složitých systémů.
- Problémy v distribuovaných aplikacích mohou vzniknout ze složitých interakcí mezi mnoha komponentami a nemusí být vhodné připojit ladicí program ke každé části systému.
- Mnoho služeb by nemělo být zastaveno. Připojení ladicího programu často způsobuje chyby s časovým limitem.
- Problémy nejsou vždycky předvídatelné. Protokolování a trasování jsou navržené pro nízkou režii, takže programy můžou vždy nahrávat v případě, že dojde k problému.

## <a name="net-core-apis"></a>Rozhraní API .NET Core

### <a name="print-style-apis"></a>Styly tisku – rozhraní API

Třídy <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType> a<xref:System.Diagnostics.Debug?displayProperty=nameWithType> obsahují podobné rozhraní API stylu tisku, které je vhodné pro protokolování.

Volba stylu tiskového rozhraní API, které se má použít. Hlavní rozdíly:
- <xref:System.Console?displayProperty=nameWithType>
  - Vždy zapnuto a vždy zapisuje do konzoly.
  - Užitečné pro informace, které může zákazník potřebovat k zobrazení ve vydané verzi.
  - Vzhledem k tomu, že se jedná o nejjednodušší přístup, často se používá pro dočasné ladění ad-hoc. Tento kód ladění často nikdy není vrácen se změnami do správy zdrojového kódu.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Povoleno pouze v `TRACE` případě, že je definován.
  - <xref:System.Diagnostics.Trace.Listeners> Ve<xref:System.Diagnostics.DefaultTraceListener>výchozím nastavení zapisuje do přílohy.
  - Použijte toto rozhraní API při vytváření protokolů, které budou povolené ve většině sestavení.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Povoleno pouze v `DEBUG` případě, že je definován.
  - Zapisuje do připojeného ladicího programu.
  - `*nix` Pokud`COMPlus_DebugWriteToStdErr` je nastaveno, při zápisu do stderr.
  - Použijte toto rozhraní API při vytváření protokolů, které budou povoleny pouze v sestavení ladění.

### <a name="logging-events"></a>Události protokolování

Následující rozhraní API jsou podrobněji orientované na události. Místo protokolování jednoduchých řetězců, které protokolují objekty událostí.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource je primární rozhraní API pro trasování kořenového rozhraní .NET Core.
  - K dispozici ve všech verzích .NET Standard.
  - Povoluje pouze trasování serializovatelných objektů.
  - Zapisuje do připojených [posluchačů událostí](xref:System.Diagnostics.Tracing.EventListener).
  - .NET Core poskytuje naslouchací procesy pro:
    - EventPipe .NET Core na všech platformách
    - [Trasování událostí pro Windows (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Rozhraní trasování LTTng pro Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Je součástí .NET Core a jako [balíček NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pro .NET Framework.
  - Umožňuje vnitroprocesové trasování objektů, které nejsou serializovatelný.
  - Obsahuje most umožňující zápis vybraných polí protokolovaných objektů do <xref:System.Diagnostics.Tracing.EventSource>.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Poskytuje Konečný způsob, jak identifikovat zprávy protokolu vyplývající z konkrétní aktivity nebo transakce. Tento objekt lze použít ke korelaci protokolů napříč různými službami.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Pouze Windows.
  - Zapisuje zprávy do protokolu událostí systému Windows.
  - Správci systému očekávají závažné chybové zprávy aplikací, které se mají zobrazit v protokolu událostí systému Windows.

## <a name="ilogger-and-logging-frameworks"></a>ILogger a protokolovací rozhraní

Rozhraní API na nízké úrovni nemusí být správná volba pro vaše potřeby přihlašování. Možná budete chtít zvážit protokolovací rozhraní.

<xref:Microsoft.Extensions.Logging.ILogger> Rozhraní bylo použito k vytvoření společného protokolovacího rozhraní, ve kterém lze vkládat protokolovací nástroje pomocí injektáže závislosti.

Chcete-li například umožnit, aby vaše aplikace `ASP.NET` nejlépe vystavila podporu pro výběr integrovaných a platforem třetích stran:
- [ASP.NET integrovaná zprostředkovatelé protokolování](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET zprostředkovatelé protokolování třetích stran](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Protokolování souvisejících odkazů

- [Postupy: Podmíněně kompilovat pomocí trasování a ladění](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Postupy: Přidání příkazů trasování do kódu aplikace](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [Protokolování ASP.NET](/aspnet/core/fundamentals/logging) poskytuje přehled postupů protokolování, které podporuje.

- Interpolace řetězců může zjednodušit zápis kódu protokolování. [ C# ](../../csharp/language-reference/tokens/interpolated.md)

- <xref:System.Exception.Message?displayProperty=nameWithType> Vlastnost je užitečná pro protokolování výjimek.

- <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> Třída může být užitečná pro poskytování informací o zásobníku v protokolech.

## <a name="performance-considerations"></a>Důležité informace o výkonu

Formátování řetězce může trvat znatelné doby zpracování procesoru.

V důležitých aplikacích pro výkon doporučujeme:
- Vyhněte se velkým množstvím protokolování, když nikdo nenaslouchá. Vyhněte se vytváření drahých zpráv protokolování, a to tak, že zkontrolujete, jestli je povolené protokolování.
- Protokolujte, co je užitečné.
- Odložit ozdobný formátování do fáze analýzy.
