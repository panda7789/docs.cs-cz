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
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="19c94-103">Protokolování a trasování jádra .NET</span><span class="sxs-lookup"><span data-stu-id="19c94-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="19c94-104">Protokolování a trasování jsou opravdu dva názvy pro stejnou techniku.</span><span class="sxs-lookup"><span data-stu-id="19c94-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="19c94-105">Jednoduchá technika se používá od prvních dnů počítačů.</span><span class="sxs-lookup"><span data-stu-id="19c94-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="19c94-106">Jednoduše zahrnuje instrumentace aplikace pro zápis výstupu, který má být spotřebován později.</span><span class="sxs-lookup"><span data-stu-id="19c94-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="19c94-107">Důvody pro použití protokolování a trasování</span><span class="sxs-lookup"><span data-stu-id="19c94-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="19c94-108">Tato jednoduchá technika je překvapivě silná.</span><span class="sxs-lookup"><span data-stu-id="19c94-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="19c94-109">Lze jej použít v situacích, kdy ladicí program selže:</span><span class="sxs-lookup"><span data-stu-id="19c94-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="19c94-110">Problémy vyskytující se v průběhu dlouhé časové období, může být obtížné ladit s tradiční ladicí program.</span><span class="sxs-lookup"><span data-stu-id="19c94-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="19c94-111">Protokoly umožňují podrobnou posmrtnou kontrolu zahrnující dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="19c94-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="19c94-112">Naproti tomu ladicí programy jsou omezeny na analýzu v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="19c94-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="19c94-113">Vícevláknové aplikace a distribuované aplikace jsou často obtížné ladit.</span><span class="sxs-lookup"><span data-stu-id="19c94-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="19c94-114">Připojení ladicího programu má tendenci měnit chování.</span><span class="sxs-lookup"><span data-stu-id="19c94-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="19c94-115">Podrobné protokoly lze analyzovat podle potřeby pochopit složité systémy.</span><span class="sxs-lookup"><span data-stu-id="19c94-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="19c94-116">Problémy v distribuovaných aplikacích mohou vzniknout z komplexní interakce mezi mnoha součástmi a nemusí být rozumné připojit ladicí program ke každé části systému.</span><span class="sxs-lookup"><span data-stu-id="19c94-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="19c94-117">Mnoho služeb by nemělo být pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="19c94-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="19c94-118">Připojení ladicího programu často způsobuje selhání časového výpadku.</span><span class="sxs-lookup"><span data-stu-id="19c94-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="19c94-119">Problémy se ne vždy předpokládají.</span><span class="sxs-lookup"><span data-stu-id="19c94-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="19c94-120">Protokolování a trasování jsou určeny pro nízké režie, takže programy mohou být vždy záznam v případě, že dojde k problému.</span><span class="sxs-lookup"><span data-stu-id="19c94-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="19c94-121">Základní rozhraní API .NET</span><span class="sxs-lookup"><span data-stu-id="19c94-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="19c94-122">Tisknout nastavení API stylu</span><span class="sxs-lookup"><span data-stu-id="19c94-122">Print style APIs</span></span>

<span data-ttu-id="19c94-123">V <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> a třídy poskytují podobné tiskové styl API vhodné pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="19c94-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="19c94-124">Volba, které rozhraní API stylu tisku má být používáno, je na vás.</span><span class="sxs-lookup"><span data-stu-id="19c94-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="19c94-125">Hlavní rozdíly jsou:</span><span class="sxs-lookup"><span data-stu-id="19c94-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-126">Vždy povolena a vždy zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="19c94-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="19c94-127">Užitečné pro informace, které zákazník může potřebovat vidět ve verzi.</span><span class="sxs-lookup"><span data-stu-id="19c94-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="19c94-128">Protože je to nejjednodušší přístup, často se používá pro dočasné ladění ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="19c94-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="19c94-129">Tento ladicí kód je často nikdy vrácena se změnami do správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="19c94-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-130">Povoleno pouze `TRACE` v případě, že je definován.</span><span class="sxs-lookup"><span data-stu-id="19c94-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="19c94-131">Zapíše do <xref:System.Diagnostics.Trace.Listeners>připojeného <xref:System.Diagnostics.DefaultTraceListener>, ve výchozím nastavení .</span><span class="sxs-lookup"><span data-stu-id="19c94-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="19c94-132">Toto rozhraní API použijte při vytváření protokolů, které budou povoleny ve většině sestavení.</span><span class="sxs-lookup"><span data-stu-id="19c94-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-133">Povoleno pouze `DEBUG` v případě, že je definován.</span><span class="sxs-lookup"><span data-stu-id="19c94-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="19c94-134">Zapíše do připojeného ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="19c94-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="19c94-135">Na `*nix` zápisy stderr, pokud `COMPlus_DebugWriteToStdErr` je nastavena.</span><span class="sxs-lookup"><span data-stu-id="19c94-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="19c94-136">Toto rozhraní API použijte při vytváření protokolů, které budou povoleny pouze v sestaveních ladění.</span><span class="sxs-lookup"><span data-stu-id="19c94-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="19c94-137">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="19c94-137">Logging events</span></span>

<span data-ttu-id="19c94-138">Následující api jsou více orientované na události.</span><span class="sxs-lookup"><span data-stu-id="19c94-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="19c94-139">Spíše než protokolování jednoduchých řetězců protokolují objekty událostí.</span><span class="sxs-lookup"><span data-stu-id="19c94-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-140">EventSource je primární rozhraní API pro trasování jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="19c94-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="19c94-141">K dispozici ve všech verzích .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="19c94-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="19c94-142">Umožňuje pouze trasování serializovatelných objektů.</span><span class="sxs-lookup"><span data-stu-id="19c94-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="19c94-143">Zapíše připojené [posluchače událostí](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="19c94-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="19c94-144">.NET Core poskytuje posluchače pro:</span><span class="sxs-lookup"><span data-stu-id="19c94-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="19c94-145">.NET Core EventPipe na všech platformách</span><span class="sxs-lookup"><span data-stu-id="19c94-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="19c94-146">Trasování událostí pro Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="19c94-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="19c94-147">LTTng trasovací rámec pro Linux</span><span class="sxs-lookup"><span data-stu-id="19c94-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-148">Součástí rozhraní .NET Core a jako [balíček NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19c94-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="19c94-149">Umožňuje v průběhu procesu trasování neserializovatelných objektů.</span><span class="sxs-lookup"><span data-stu-id="19c94-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="19c94-150">Obsahuje most, který umožňuje zápis vybraných polí protokolovaných objektů do . <xref:System.Diagnostics.Tracing.EventSource></span><span class="sxs-lookup"><span data-stu-id="19c94-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-151">Poskytuje definitivní způsob, jak identifikovat zprávy protokolu vyplývající z určité aktivity nebo transakce.</span><span class="sxs-lookup"><span data-stu-id="19c94-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="19c94-152">Tento objekt lze použít ke korelaci protokolů mezi různými službami.</span><span class="sxs-lookup"><span data-stu-id="19c94-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="19c94-153">Pouze pro Windows.</span><span class="sxs-lookup"><span data-stu-id="19c94-153">Windows only.</span></span>
  - <span data-ttu-id="19c94-154">Zapisuje zprávy do protokolu událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="19c94-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="19c94-155">Správci systému očekávají, že se v protokolu událostí systému Windows zobrazí závažné chybové zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c94-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="19c94-156">ILogger a protokolování rámců</span><span class="sxs-lookup"><span data-stu-id="19c94-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="19c94-157">Nízkoúrovňová api nemusí být tou správnou volbou pro vaše potřeby protokolování.</span><span class="sxs-lookup"><span data-stu-id="19c94-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="19c94-158">Možná budete chtít zvážit protokolování rámce.</span><span class="sxs-lookup"><span data-stu-id="19c94-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="19c94-159">Rozhraní <xref:Microsoft.Extensions.Logging.ILogger> bylo použito k vytvoření společného rozhraní protokolování, kde lze vložit úhozy kláves prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="19c94-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="19c94-160">Například, aby vám umožní učinit nejlepší `ASP.NET` volbou pro vaši aplikaci nabízí podporu pro výběr vestavěných a jiných výrobců rámců:</span><span class="sxs-lookup"><span data-stu-id="19c94-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="19c94-161">ASP.NET vestavěné poskytovatele protokolování</span><span class="sxs-lookup"><span data-stu-id="19c94-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="19c94-162">ASP.NET poskytovatelé protokolování třetích stran</span><span class="sxs-lookup"><span data-stu-id="19c94-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="19c94-163">Protokolování souvisejících odkazů</span><span class="sxs-lookup"><span data-stu-id="19c94-163">Logging related references</span></span>

- [<span data-ttu-id="19c94-164">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="19c94-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="19c94-165">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="19c94-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="19c94-166">[ASP.NET protokolování](/aspnet/core/fundamentals/logging) poskytuje přehled technik protokolování, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="19c94-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="19c94-167">[Interpolace řetězce Jazyka C#](../../csharp/language-reference/tokens/interpolated.md) může zjednodušit psaní kódu protokolování.</span><span class="sxs-lookup"><span data-stu-id="19c94-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="19c94-168">Vlastnost <xref:System.Exception.Message?displayProperty=nameWithType> je užitečná pro protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="19c94-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="19c94-169">Třída <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> může být užitečné poskytnout informace zásobníku v protokolech.</span><span class="sxs-lookup"><span data-stu-id="19c94-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="19c94-170">Otázky výkonu</span><span class="sxs-lookup"><span data-stu-id="19c94-170">Performance considerations</span></span>

<span data-ttu-id="19c94-171">Formátování řetězců může trvat znatelné čas zpracování procesoru.</span><span class="sxs-lookup"><span data-stu-id="19c94-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="19c94-172">V aplikacích kritických pro výkon doporučujeme:</span><span class="sxs-lookup"><span data-stu-id="19c94-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="19c94-173">Vyhněte se hodně protokolování, když nikdo neposlouchá.</span><span class="sxs-lookup"><span data-stu-id="19c94-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="19c94-174">Vyhněte se vytváření nákladné protokolování zpráv kontrolou, zda je protokolování povoleno jako první.</span><span class="sxs-lookup"><span data-stu-id="19c94-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="19c94-175">Zaznaužte jen to, co je užitečné.</span><span class="sxs-lookup"><span data-stu-id="19c94-175">Only log what's useful.</span></span>
- <span data-ttu-id="19c94-176">Odložte ozdobné formátování do fáze analýzy.</span><span class="sxs-lookup"><span data-stu-id="19c94-176">Defer fancy formatting to the analysis stage.</span></span>
