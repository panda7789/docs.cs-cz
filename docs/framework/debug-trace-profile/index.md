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
ms.openlocfilehash: 481360f731297e1c287c969e6524c68e0c9c0b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386467"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="ac57e-102">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="ac57e-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="ac57e-103">K ladění aplikací rozhraní .NET Framework, je nutné nakonfigurovat kompilátoru a prostředí runtime umožňující ladicí program pro připojení k aplikaci a k vytvoření symboly a řádku mapy, pokud je to možné, aplikace a jeho odpovídající společnosti Microsoft zprostředkující jazyk (MSIL).</span><span class="sxs-lookup"><span data-stu-id="ac57e-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="ac57e-104">Po spravované aplikace byla ladit, může být profilovaným pro zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="ac57e-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="ac57e-105">Profilace vyhodnotí a popisuje řádky zdrojového kódu, které generování nejčastěji spuštění kódu a kolik času ho trvá k jejich vyřízení.</span><span class="sxs-lookup"><span data-stu-id="ac57e-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="ac57e-106">.NET framework – aplikace se snadno ladí pomocí sady Visual Studio, která zpracovává mnoho podrobností konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ac57e-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="ac57e-107">Pokud není nainstalované sady Visual Studio, můžete zkontrolovat a zlepšit výkon aplikací rozhraní .NET Framework pomocí třídy ladění v rozhraní .NET Framework <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ac57e-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="ac57e-108">Tento obor názvů obsahuje <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, a <xref:System.Diagnostics.TraceSource> třídy pro trasování provádění toku a <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, a <xref:System.Diagnostics.PerformanceCounter> třídy pro profilace kódu.</span><span class="sxs-lookup"><span data-stu-id="ac57e-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac57e-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ac57e-109">In This Section</span></span>  
 [<span data-ttu-id="ac57e-110">Povolení JIT – ladění Attach</span><span class="sxs-lookup"><span data-stu-id="ac57e-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="ac57e-111">Ukazuje, jak nakonfigurovat registr JIT – připojené ladění modulu k aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac57e-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="ac57e-112">Usnadnění ladění obrázku</span><span class="sxs-lookup"><span data-stu-id="ac57e-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="ac57e-113">Ukazuje, jak vypnout sledování JIT na a optimalizace pro snazší ladění sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac57e-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="ac57e-114">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="ac57e-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="ac57e-115">Popisuje, jak monitorovat aplikace, když je spuštěná a jak zobrazit, jak dobře instrumentovat provádí nebo zda něco nepovede.</span><span class="sxs-lookup"><span data-stu-id="ac57e-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="ac57e-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ac57e-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="ac57e-117">Popisuje spravované ladění Pomocníci (mda), které jsou ladění pomůcek, které spolupracují se modul CLR (CLR) k poskytování informací o stav modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ac57e-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="ac57e-118">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="ac57e-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="ac57e-119">Popisuje, jak může vývojář typu určit co, typ bude vypadat, který se zobrazí v ladicí program.</span><span class="sxs-lookup"><span data-stu-id="ac57e-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="ac57e-120">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="ac57e-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="ac57e-121">Popisuje čítače, které můžete použít ke sledování výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ac57e-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac57e-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ac57e-122">Related Sections</span></span>  
 [<span data-ttu-id="ac57e-123">Ladění aplikací ASP.NET a AJAX</span><span class="sxs-lookup"><span data-stu-id="ac57e-123">Debugging ASP.NET and AJAX Applications</span></span>](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 <span data-ttu-id="ac57e-124">Poskytuje požadavky a pokyny k ladění aplikace ASP.NET během vývoje nebo po nasazení.</span><span class="sxs-lookup"><span data-stu-id="ac57e-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="ac57e-125">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="ac57e-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="ac57e-126">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="ac57e-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
