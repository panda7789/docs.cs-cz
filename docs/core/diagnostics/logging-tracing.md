---
title: Protokolování a trasování – .NET Core
description: Úvod do protokolování a trasování .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 46e64a7f60b88c26ceef9ac817be885bfa180c8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926353"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="f08bd-103">Protokolování a trasování .NET Core</span><span class="sxs-lookup"><span data-stu-id="f08bd-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="f08bd-104">Protokolování a trasování jsou ve skutečnosti dva názvy pro stejnou techniku.</span><span class="sxs-lookup"><span data-stu-id="f08bd-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="f08bd-105">Od počátečních dní počítačů se použila jednoduchá technika.</span><span class="sxs-lookup"><span data-stu-id="f08bd-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="f08bd-106">Jednoduše zahrnuje instrumentaci aplikace pro zápis výstupu, který se má spotřebovat později.</span><span class="sxs-lookup"><span data-stu-id="f08bd-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="f08bd-107">Důvody pro použití protokolování a trasování</span><span class="sxs-lookup"><span data-stu-id="f08bd-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="f08bd-108">Tato jednoduchá technika je překvapivě výkonná.</span><span class="sxs-lookup"><span data-stu-id="f08bd-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="f08bd-109">Dá se použít v situacích, kdy dojde k chybě ladicího programu:</span><span class="sxs-lookup"><span data-stu-id="f08bd-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="f08bd-110">Problémy, ke kterým dochází v dlouhých časových obdobích, mohou být obtížné ladit pomocí tradičního ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f08bd-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="f08bd-111">Protokoly umožňují podrobnou kontrolu po dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="f08bd-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="f08bd-112">Naproti tomu ladicí programy jsou omezené na analýzu v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="f08bd-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="f08bd-113">Aplikace s více vlákny a distribuované aplikace jsou často obtížné ladit.</span><span class="sxs-lookup"><span data-stu-id="f08bd-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="f08bd-114">Připojení ladicího programu je v úmyslu změnit chování.</span><span class="sxs-lookup"><span data-stu-id="f08bd-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="f08bd-115">Podrobné protokoly je možné analyzovat podle potřeby pro pochopení složitých systémů.</span><span class="sxs-lookup"><span data-stu-id="f08bd-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="f08bd-116">Problémy v distribuovaných aplikacích mohou vzniknout ze složitých interakcí mezi mnoha komponentami a nemusí být vhodné připojit ladicí program ke každé části systému.</span><span class="sxs-lookup"><span data-stu-id="f08bd-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="f08bd-117">Mnoho služeb by nemělo být zastaveno.</span><span class="sxs-lookup"><span data-stu-id="f08bd-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="f08bd-118">Připojení ladicího programu často způsobuje chyby s časovým limitem.</span><span class="sxs-lookup"><span data-stu-id="f08bd-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="f08bd-119">Problémy nejsou vždycky předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="f08bd-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="f08bd-120">Protokolování a trasování jsou navržené pro nízkou režii, takže programy můžou vždy nahrávat v případě, že dojde k problému.</span><span class="sxs-lookup"><span data-stu-id="f08bd-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="f08bd-121">Rozhraní API .NET Core</span><span class="sxs-lookup"><span data-stu-id="f08bd-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="f08bd-122">Styly tisku – rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f08bd-122">Print style APIs</span></span>

<span data-ttu-id="f08bd-123">Třídy <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType> a<xref:System.Diagnostics.Debug?displayProperty=nameWithType> obsahují podobné rozhraní API stylu tisku, které je vhodné pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="f08bd-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="f08bd-124">Volba stylu tiskového rozhraní API, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="f08bd-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="f08bd-125">Hlavní rozdíly:</span><span class="sxs-lookup"><span data-stu-id="f08bd-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-126">Vždy zapnuto a vždy zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f08bd-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="f08bd-127">Užitečné pro informace, které může zákazník potřebovat k zobrazení ve vydané verzi.</span><span class="sxs-lookup"><span data-stu-id="f08bd-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="f08bd-128">Vzhledem k tomu, že se jedná o nejjednodušší přístup, často se používá pro dočasné ladění ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="f08bd-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="f08bd-129">Tento kód ladění často nikdy není vrácen se změnami do správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f08bd-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-130">Povoleno pouze v `TRACE` případě, že je definován.</span><span class="sxs-lookup"><span data-stu-id="f08bd-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="f08bd-131"><xref:System.Diagnostics.Trace.Listeners> Ve<xref:System.Diagnostics.DefaultTraceListener>výchozím nastavení zapisuje do přílohy.</span><span class="sxs-lookup"><span data-stu-id="f08bd-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="f08bd-132">Použijte toto rozhraní API při vytváření protokolů, které budou povolené ve většině sestavení.</span><span class="sxs-lookup"><span data-stu-id="f08bd-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-133">Povoleno pouze v `DEBUG` případě, že je definován.</span><span class="sxs-lookup"><span data-stu-id="f08bd-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="f08bd-134">Zapisuje do připojeného ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f08bd-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="f08bd-135">`*nix` Pokud`COMPlus_DebugWriteToStdErr` je nastaveno, při zápisu do stderr.</span><span class="sxs-lookup"><span data-stu-id="f08bd-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="f08bd-136">Použijte toto rozhraní API při vytváření protokolů, které budou povoleny pouze v sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="f08bd-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="f08bd-137">Události protokolování</span><span class="sxs-lookup"><span data-stu-id="f08bd-137">Logging events</span></span>

<span data-ttu-id="f08bd-138">Následující rozhraní API jsou podrobněji orientované na události.</span><span class="sxs-lookup"><span data-stu-id="f08bd-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="f08bd-139">Místo protokolování jednoduchých řetězců, které protokolují objekty událostí.</span><span class="sxs-lookup"><span data-stu-id="f08bd-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-140">EventSource je primární rozhraní API pro trasování kořenového rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f08bd-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="f08bd-141">K dispozici ve všech verzích .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f08bd-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="f08bd-142">Povoluje pouze trasování serializovatelných objektů.</span><span class="sxs-lookup"><span data-stu-id="f08bd-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="f08bd-143">Zapisuje do připojených [posluchačů událostí](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="f08bd-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="f08bd-144">.NET Core poskytuje naslouchací procesy pro:</span><span class="sxs-lookup"><span data-stu-id="f08bd-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="f08bd-145">EventPipe .NET Core na všech platformách</span><span class="sxs-lookup"><span data-stu-id="f08bd-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="f08bd-146">Trasování událostí pro Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="f08bd-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="f08bd-147">Rozhraní trasování LTTng pro Linux</span><span class="sxs-lookup"><span data-stu-id="f08bd-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-148">Je součástí .NET Core a jako [balíček NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pro .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f08bd-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="f08bd-149">Umožňuje vnitroprocesové trasování objektů, které nejsou serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="f08bd-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="f08bd-150">Obsahuje most umožňující zápis vybraných polí protokolovaných objektů do <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="f08bd-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-151">Poskytuje Konečný způsob, jak identifikovat zprávy protokolu vyplývající z konkrétní aktivity nebo transakce.</span><span class="sxs-lookup"><span data-stu-id="f08bd-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="f08bd-152">Tento objekt lze použít ke korelaci protokolů napříč různými službami.</span><span class="sxs-lookup"><span data-stu-id="f08bd-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="f08bd-153">Pouze Windows.</span><span class="sxs-lookup"><span data-stu-id="f08bd-153">Windows only.</span></span>
  - <span data-ttu-id="f08bd-154">Zapisuje zprávy do protokolu událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f08bd-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="f08bd-155">Správci systému očekávají závažné chybové zprávy aplikací, které se mají zobrazit v protokolu událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f08bd-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="f08bd-156">ILogger a protokolovací rozhraní</span><span class="sxs-lookup"><span data-stu-id="f08bd-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="f08bd-157">Rozhraní API na nízké úrovni nemusí být správná volba pro vaše potřeby přihlašování.</span><span class="sxs-lookup"><span data-stu-id="f08bd-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="f08bd-158">Možná budete chtít zvážit protokolovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f08bd-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="f08bd-159"><xref:Microsoft.Extensions.Logging.ILogger> Rozhraní bylo použito k vytvoření společného protokolovacího rozhraní, ve kterém lze vkládat protokolovací nástroje pomocí injektáže závislosti.</span><span class="sxs-lookup"><span data-stu-id="f08bd-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="f08bd-160">Chcete-li například umožnit, aby vaše aplikace `ASP.NET` nejlépe vystavila podporu pro výběr integrovaných a platforem třetích stran:</span><span class="sxs-lookup"><span data-stu-id="f08bd-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="f08bd-161">ASP.NET integrovaná zprostředkovatelé protokolování</span><span class="sxs-lookup"><span data-stu-id="f08bd-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="f08bd-162">ASP.NET zprostředkovatelé protokolování třetích stran</span><span class="sxs-lookup"><span data-stu-id="f08bd-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="f08bd-163">Protokolování souvisejících odkazů</span><span class="sxs-lookup"><span data-stu-id="f08bd-163">Logging related references</span></span>

- [<span data-ttu-id="f08bd-164">Postupy: Podmíněně kompilovat pomocí trasování a ladění</span><span class="sxs-lookup"><span data-stu-id="f08bd-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="f08bd-165">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="f08bd-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="f08bd-166">[Protokolování ASP.NET](/aspnet/core/fundamentals/logging) poskytuje přehled postupů protokolování, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="f08bd-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="f08bd-167">Interpolace řetězců může zjednodušit zápis kódu protokolování. [ C# ](../../csharp/language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="f08bd-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="f08bd-168"><xref:System.Exception.Message?displayProperty=nameWithType> Vlastnost je užitečná pro protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f08bd-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="f08bd-169"><xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> Třída může být užitečná pro poskytování informací o zásobníku v protokolech.</span><span class="sxs-lookup"><span data-stu-id="f08bd-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="f08bd-170">Důležité informace o výkonu</span><span class="sxs-lookup"><span data-stu-id="f08bd-170">Performance considerations</span></span>

<span data-ttu-id="f08bd-171">Formátování řetězce může trvat znatelné doby zpracování procesoru.</span><span class="sxs-lookup"><span data-stu-id="f08bd-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="f08bd-172">V důležitých aplikacích pro výkon doporučujeme:</span><span class="sxs-lookup"><span data-stu-id="f08bd-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="f08bd-173">Vyhněte se velkým množstvím protokolování, když nikdo nenaslouchá.</span><span class="sxs-lookup"><span data-stu-id="f08bd-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="f08bd-174">Vyhněte se vytváření drahých zpráv protokolování, a to tak, že zkontrolujete, jestli je povolené protokolování.</span><span class="sxs-lookup"><span data-stu-id="f08bd-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="f08bd-175">Protokolujte, co je užitečné.</span><span class="sxs-lookup"><span data-stu-id="f08bd-175">Only log what's useful.</span></span>
- <span data-ttu-id="f08bd-176">Odložit ozdobný formátování do fáze analýzy.</span><span class="sxs-lookup"><span data-stu-id="f08bd-176">Defer fancy formatting to the analysis stage.</span></span>
