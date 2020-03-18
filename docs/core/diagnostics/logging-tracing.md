---
title: Protokolování a trasování – jádro .NET Core
description: Úvod do protokolování a trasování jádra .NET.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714413"
---
# <a name="net-core-logging-and-tracing"></a>Protokolování a trasování jádra .NET

Protokolování a trasování jsou opravdu dva názvy pro stejnou techniku. Jednoduchá technika se používá od prvních dnů počítačů. Jednoduše zahrnuje instrumentace aplikace pro zápis výstupu, který má být spotřebován později.

## <a name="reasons-to-use-logging-and-tracing"></a>Důvody pro použití protokolování a trasování

Tato jednoduchá technika je překvapivě silná. Lze jej použít v situacích, kdy ladicí program selže:

- Problémy vyskytující se v průběhu dlouhé časové období, může být obtížné ladit s tradiční ladicí program. Protokoly umožňují podrobnou posmrtnou kontrolu zahrnující dlouhou dobu. Naproti tomu ladicí programy jsou omezeny na analýzu v reálném čase.
- Vícevláknové aplikace a distribuované aplikace jsou často obtížné ladit.  Připojení ladicího programu má tendenci měnit chování. Podrobné protokoly lze analyzovat podle potřeby pochopit složité systémy.
- Problémy v distribuovaných aplikacích mohou vzniknout z komplexní interakce mezi mnoha součástmi a nemusí být rozumné připojit ladicí program ke každé části systému.
- Mnoho služeb by nemělo být pozastaveno. Připojení ladicího programu často způsobuje selhání časového výpadku.
- Problémy se ne vždy předpokládají. Protokolování a trasování jsou určeny pro nízké režie, takže programy mohou být vždy záznam v případě, že dojde k problému.

## <a name="net-core-apis"></a>Základní rozhraní API .NET

### <a name="print-style-apis"></a>Tisknout nastavení API stylu

V <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> a třídy poskytují podobné tiskové styl API vhodné pro protokolování.

Volba, které rozhraní API stylu tisku má být používáno, je na vás. Hlavní rozdíly jsou:

- <xref:System.Console?displayProperty=nameWithType>
  - Vždy povolena a vždy zapisuje do konzoly.
  - Užitečné pro informace, které zákazník může potřebovat vidět ve verzi.
  - Protože je to nejjednodušší přístup, často se používá pro dočasné ladění ad-hoc. Tento ladicí kód je často nikdy vrácena se změnami do správy zdrojového kódu.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Povoleno pouze `TRACE` v případě, že je definován.
  - Zapíše do <xref:System.Diagnostics.Trace.Listeners>připojeného <xref:System.Diagnostics.DefaultTraceListener>, ve výchozím nastavení .
  - Toto rozhraní API použijte při vytváření protokolů, které budou povoleny ve většině sestavení.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Povoleno pouze `DEBUG` v případě, že je definován.
  - Zapíše do připojeného ladicího programu.
  - Na `*nix` zápisy stderr, pokud `COMPlus_DebugWriteToStdErr` je nastavena.
  - Toto rozhraní API použijte při vytváření protokolů, které budou povoleny pouze v sestaveních ladění.

### <a name="logging-events"></a>Protokolování událostí

Následující api jsou více orientované na události. Spíše než protokolování jednoduchých řetězců protokolují objekty událostí.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource je primární rozhraní API pro trasování jádra .NET.
  - K dispozici ve všech verzích .NET Standard.
  - Umožňuje pouze trasování serializovatelných objektů.
  - Zapíše připojené [posluchače událostí](xref:System.Diagnostics.Tracing.EventListener).
  - .NET Core poskytuje posluchače pro:
    - .NET Core EventPipe na všech platformách
    - [Trasování událostí pro Windows (ETW)](/windows/win32/etw/event-tracing-portal)
    - [LTTng trasovací rámec pro Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Součástí rozhraní .NET Core a jako [balíček NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pro rozhraní .NET Framework.
  - Umožňuje v průběhu procesu trasování neserializovatelných objektů.
  - Obsahuje most, který umožňuje zápis vybraných polí protokolovaných objektů do . <xref:System.Diagnostics.Tracing.EventSource>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Poskytuje definitivní způsob, jak identifikovat zprávy protokolu vyplývající z určité aktivity nebo transakce. Tento objekt lze použít ke korelaci protokolů mezi různými službami.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Pouze pro Windows.
  - Zapisuje zprávy do protokolu událostí systému Windows.
  - Správci systému očekávají, že se v protokolu událostí systému Windows zobrazí závažné chybové zprávy aplikace.

## <a name="ilogger-and-logging-frameworks"></a>ILogger a protokolování rámců

Nízkoúrovňová api nemusí být tou správnou volbou pro vaše potřeby protokolování. Možná budete chtít zvážit protokolování rámce.

Rozhraní <xref:Microsoft.Extensions.Logging.ILogger> bylo použito k vytvoření společného rozhraní protokolování, kde lze vložit úhozy kláves prostřednictvím vkládání závislostí.

Například, aby vám umožní učinit nejlepší `ASP.NET` volbou pro vaši aplikaci nabízí podporu pro výběr vestavěných a jiných výrobců rámců:

- [ASP.NET vestavěné poskytovatele protokolování](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET poskytovatelé protokolování třetích stran](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Protokolování souvisejících odkazů

- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Postupy: Přidání příkazů trasování do kódu aplikace](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET protokolování](/aspnet/core/fundamentals/logging) poskytuje přehled technik protokolování, které podporuje.

- [Interpolace řetězce Jazyka C#](../../csharp/language-reference/tokens/interpolated.md) může zjednodušit psaní kódu protokolování.

- Vlastnost <xref:System.Exception.Message?displayProperty=nameWithType> je užitečná pro protokolování výjimek.

- Třída <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> může být užitečné poskytnout informace zásobníku v protokolech.

## <a name="performance-considerations"></a>Otázky výkonu

Formátování řetězců může trvat znatelné čas zpracování procesoru.

V aplikacích kritických pro výkon doporučujeme:

- Vyhněte se hodně protokolování, když nikdo neposlouchá. Vyhněte se vytváření nákladné protokolování zpráv kontrolou, zda je protokolování povoleno jako první.
- Zaznaužte jen to, co je užitečné.
- Odložte ozdobné formátování do fáze analýzy.
