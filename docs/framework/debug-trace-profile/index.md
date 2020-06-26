---
title: Ladění, trasování a profilace
description: Přečtěte si o ladění, trasování a profilaci v rozhraní .NET. Viz články, které se týkají ladění JIT (just-in-time), trasování a instrumentace aplikací a dalších.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 745f16652c02e3409e7fa7a48beacbf7e777e924
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415976"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="5979c-104">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="5979c-104">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="5979c-105">Chcete-li ladit aplikaci .NET Framework, musí být kompilátor a prostředí modulu runtime nakonfigurovány tak, aby umožňovaly ladicímu programu připojit se k aplikaci a vytvořit symboly a mapy řádků, pokud je to možné, pro aplikaci a odpovídající jazyk MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="5979c-105">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="5979c-106">Po ladění spravované aplikace se dá profilovat, aby se zvýšil výkon.</span><span class="sxs-lookup"><span data-stu-id="5979c-106">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="5979c-107">Profilování vyhodnocuje a popisuje řádky zdrojového kódu, které generují nejčastěji spouštěný kód, a dobu, po kterou je potřeba je spustit.</span><span class="sxs-lookup"><span data-stu-id="5979c-107">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="5979c-108">Aplikace .NET Framework lze snadno ladit pomocí sady Visual Studio, která zpracovává mnoho podrobností o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5979c-108">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="5979c-109">Pokud není nainstalována aplikace Visual Studio, můžete kontrolovat a zlepšovat výkon aplikací .NET Framework pomocí tříd ladění v <xref:System.Diagnostics> oboru názvů .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5979c-109">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="5979c-110">Tento obor názvů obsahuje <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> třídy, a <xref:System.Diagnostics.TraceSource> pro sledování toku spouštění a <xref:System.Diagnostics.Process> <xref:System.Diagnostics.EventLog> třídy, a <xref:System.Diagnostics.PerformanceCounter> pro kód profilace.</span><span class="sxs-lookup"><span data-stu-id="5979c-110">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5979c-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5979c-111">In This Section</span></span>  
 [<span data-ttu-id="5979c-112">Povolení JIT – ladění Attach</span><span class="sxs-lookup"><span data-stu-id="5979c-112">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="5979c-113">Ukazuje, jak nakonfigurovat registr pro JIT – připojit ladicí stroj k aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5979c-113">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="5979c-114">Usnadnění ladění image</span><span class="sxs-lookup"><span data-stu-id="5979c-114">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="5979c-115">Ukazuje, jak zapnout a optimalizovat sledování JIT, aby bylo sestavení snazší ladit.</span><span class="sxs-lookup"><span data-stu-id="5979c-115">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="5979c-116">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="5979c-116">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="5979c-117">Popisuje, jak monitorovat provádění aplikace, když je spuštěná, a jak ji instrumentovat, aby zobrazila, jak dobře funguje, nebo jestli se něco pokazilo.</span><span class="sxs-lookup"><span data-stu-id="5979c-117">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="5979c-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5979c-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="5979c-119">Popisuje pomocníky spravovaného ladění (MDA), které jsou v kombinaci s modulem CLR (Common Language Runtime) k dispozici informace o stavu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5979c-119">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="5979c-120">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="5979c-120">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="5979c-121">Popisuje, jak může vývojář typu určit, jaký typ bude vypadat, jako by byl zobrazen v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="5979c-121">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="5979c-122">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="5979c-122">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="5979c-123">Popisuje čítače, které lze použít ke sledování výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5979c-123">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5979c-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5979c-124">Related Sections</span></span>  
 [<span data-ttu-id="5979c-125">Ladění aplikací ASP.NET nebo ASP.NET Core v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5979c-125">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="5979c-126">Poskytuje předpoklady a pokyny pro ladění aplikace ASP.NET během vývoje nebo po nasazení.</span><span class="sxs-lookup"><span data-stu-id="5979c-126">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="5979c-127">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="5979c-127">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="5979c-128">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="5979c-128">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
