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
---
# <a name="debugging-tracing-and-profiling"></a>Ladění, trasování a profilace
K ladění aplikací rozhraní .NET Framework, je nutné nakonfigurovat kompilátoru a prostředí runtime umožňující ladicí program pro připojení k aplikaci a k vytvoření symboly a řádku mapy, pokud je to možné, aplikace a jeho odpovídající společnosti Microsoft zprostředkující jazyk (MSIL). Po spravované aplikace byla ladit, může být profilovaným pro zvýšení výkonu. Profilace vyhodnotí a popisuje řádky zdrojového kódu, které generování nejčastěji spuštění kódu a kolik času ho trvá k jejich vyřízení.  
  
 .NET framework – aplikace se snadno ladí pomocí sady Visual Studio, která zpracovává mnoho podrobností konfigurace. Pokud není nainstalované sady Visual Studio, můžete zkontrolovat a zlepšit výkon aplikací rozhraní .NET Framework pomocí třídy ladění v rozhraní .NET Framework <xref:System.Diagnostics> oboru názvů. Tento obor názvů obsahuje <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, a <xref:System.Diagnostics.TraceSource> třídy pro trasování provádění toku a <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, a <xref:System.Diagnostics.PerformanceCounter> třídy pro profilace kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povolení JIT – ladění Attach](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 Ukazuje, jak nakonfigurovat registr JIT – připojené ladění modulu k aplikaci .NET Framework.  
  
 [Usnadnění ladění obrázku](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 Ukazuje, jak vypnout sledování JIT na a optimalizace pro snazší ladění sestavení.  
  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 Popisuje, jak monitorovat aplikace, když je spuštěná a jak zobrazit, jak dobře instrumentovat provádí nebo zda něco nepovede.  
  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 Popisuje spravované ladění Pomocníci (mda), které jsou ladění pomůcek, které spolupracují se modul CLR (CLR) k poskytování informací o stav modulu runtime.  
  
 [Rozšíření ladění pomocí atributů zobrazení ladicího programu](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 Popisuje, jak může vývojář typu určit co, typ bude vypadat, který se zobrazí v ladicí program.  
  
 [Čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 Popisuje čítače, které můžete použít ke sledování výkonu aplikace.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění aplikací ASP.NET a AJAX](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 Poskytuje požadavky a pokyny k ladění aplikace ASP.NET během vývoje nebo po nasazení.  
  
 [Průvodce vývojem](../../../docs/framework/development-guide.md)  
 Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.
