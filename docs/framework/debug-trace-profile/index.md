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
ms.openlocfilehash: ff2be73b2cea563066f70ea2fe6d53840f718e75
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855280"
---
# <a name="debugging-tracing-and-profiling"></a>Ladění, trasování a profilace
Pro ladění aplikace rozhraní .NET Framework, musí být nakonfigurováno kompilátoru a modulu runtime prostředí umožňující ladicího programu pro připojení k aplikaci a k vytvoření symboly a řádku mapy, pokud je to možné, aplikace a její odpovídající Microsoft intermediate Language (MSIL). Poté, co byl ladit spravované aplikace, můžete profilaci pro zvýšení výkonu. Profilace vyhodnocuje a popisuje, řádky zdrojového kódu, které generují kód nejčastěji prováděnou a kolik času je trvá je spouštět.  
  
 Aplikace rozhraní .NET framework jsou jednoduše ladit pomocí sady Visual Studio, která zpracovává řadu podrobnosti o konfiguraci. Pokud není nainstalována aplikace Visual Studio, můžete prozkoumat a zlepšit výkon aplikací využívajících rozhraní .NET Framework pomocí tříd ladění v rozhraní .NET Framework <xref:System.Diagnostics> oboru názvů. Tento obor názvů obsahuje <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, a <xref:System.Diagnostics.TraceSource> třídy pro sledování spuštění toku a <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, a <xref:System.Diagnostics.PerformanceCounter> třídy pro profilování kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povolení JIT – ladění Attach](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 Ukazuje, jak nakonfigurovat registr JIT připojit ladicí modul k aplikaci .NET Framework.  
  
 [Usnadnění ladění obrázku](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 Ukazuje, jak vypnout sledování JIT na a optimalizace pro usnadnění sestavení pro ladění.  
  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 Popisuje, jak monitorovat aplikace během jejího běhu a jak k instrumentaci a jak dobře zobrazit provádí, nebo jestli se něco nepovedlo.  
  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 Popisuje asistentů spravovaného ladění (mda), které ladíte pomůcek, které fungují ve spojení s modul CLR (CLR), která poskytují informace o stavu modulu runtime.  
  
 [Rozšíření ladění pomocí atributů zobrazení ladicího programu](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 Popisuje, jak může vývojář typu určit co, že typ bude vypadat podobně jako když se objeví v ladicí program.  
  
 [Čítače výkonu](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 Popisuje čítače, které můžete použít ke sledování výkonu aplikace.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění aplikací ASP.NET a AJAX](https://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 Obsahuje požadavky a pokyny, jak ladit aplikaci technologie ASP.NET při vývoji nebo po nasazení.  
  
 [Průvodce vývojem](../../../docs/framework/development-guide.md)  
 Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.
