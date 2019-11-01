---
title: Ladění, trasování a profilace
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e9438ed2c1cd82bb4d89ff082545021b2d543e
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195352"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="39e14-102">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="39e14-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="39e14-103">Chcete-li ladit aplikaci .NET Framework, musí být kompilátor a prostředí modulu runtime nakonfigurovány tak, aby umožňovaly ladicímu programu připojit se k aplikaci a aby bylo možné vytvořit symboly a mapy řádků, pokud je to možné, pro aplikaci a její odpovídající Microsoft Intermediate jazyk (MSIL).</span><span class="sxs-lookup"><span data-stu-id="39e14-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="39e14-104">Po ladění spravované aplikace se dá profilovat, aby se zvýšil výkon.</span><span class="sxs-lookup"><span data-stu-id="39e14-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="39e14-105">Profilování vyhodnocuje a popisuje řádky zdrojového kódu, které generují nejčastěji spouštěný kód, a dobu, po kterou je potřeba je spustit.</span><span class="sxs-lookup"><span data-stu-id="39e14-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="39e14-106">Aplikace .NET Framework lze snadno ladit pomocí sady Visual Studio, která zpracovává mnoho podrobností o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="39e14-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="39e14-107">Pokud není nainstalována aplikace Visual Studio, můžete kontrolovat a zlepšovat výkon aplikací .NET Framework pomocí tříd ladění v oboru názvů .NET Framework <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="39e14-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="39e14-108">Tento obor názvů obsahuje třídy <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>a <xref:System.Diagnostics.TraceSource> pro trasování toku spouštění a třídy <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>a <xref:System.Diagnostics.PerformanceCounter> pro kód profilace.</span><span class="sxs-lookup"><span data-stu-id="39e14-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39e14-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="39e14-109">In This Section</span></span>  
 [<span data-ttu-id="39e14-110">Povolení JIT – ladění Attach</span><span class="sxs-lookup"><span data-stu-id="39e14-110">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="39e14-111">Ukazuje, jak nakonfigurovat registr pro JIT – připojit ladicí stroj k aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39e14-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="39e14-112">Usnadnění ladění obrázku</span><span class="sxs-lookup"><span data-stu-id="39e14-112">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="39e14-113">Ukazuje, jak zapnout a optimalizovat sledování JIT, aby bylo sestavení snazší ladit.</span><span class="sxs-lookup"><span data-stu-id="39e14-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="39e14-114">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="39e14-114">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="39e14-115">Popisuje, jak monitorovat provádění aplikace, když je spuštěná, a jak ji instrumentovat, aby zobrazila, jak dobře funguje, nebo jestli se něco pokazilo.</span><span class="sxs-lookup"><span data-stu-id="39e14-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="39e14-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="39e14-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="39e14-117">Popisuje pomocníky spravovaného ladění (MDA), které jsou v kombinaci s modulem CLR (Common Language Runtime) k dispozici informace o stavu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="39e14-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="39e14-118">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="39e14-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="39e14-119">Popisuje, jak může vývojář typu určit, jaký typ bude vypadat, jako by byl zobrazen v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="39e14-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="39e14-120">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="39e14-120">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="39e14-121">Popisuje čítače, které lze použít ke sledování výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="39e14-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="39e14-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="39e14-122">Related Sections</span></span>  
 [<span data-ttu-id="39e14-123">Ladění aplikací ASP.NET nebo ASP.NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39e14-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="39e14-124">Poskytuje předpoklady a pokyny pro ladění aplikace ASP.NET během vývoje nebo po nasazení.</span><span class="sxs-lookup"><span data-stu-id="39e14-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="39e14-125">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="39e14-125">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="39e14-126">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="39e14-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
