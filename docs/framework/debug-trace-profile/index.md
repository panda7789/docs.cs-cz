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
# <a name="debugging-tracing-and-profiling"></a>Ladění, trasování a profilace
Chcete-li ladit aplikaci .NET Framework, musí být kompilátor a prostředí modulu runtime nakonfigurovány tak, aby umožňovaly ladicímu programu připojit se k aplikaci a vytvořit symboly a mapy řádků, pokud je to možné, pro aplikaci a odpovídající jazyk MSIL (Microsoft Intermediate Language). Po ladění spravované aplikace se dá profilovat, aby se zvýšil výkon. Profilování vyhodnocuje a popisuje řádky zdrojového kódu, které generují nejčastěji spouštěný kód, a dobu, po kterou je potřeba je spustit.  
  
 Aplikace .NET Framework lze snadno ladit pomocí sady Visual Studio, která zpracovává mnoho podrobností o konfiguraci. Pokud není nainstalována aplikace Visual Studio, můžete kontrolovat a zlepšovat výkon aplikací .NET Framework pomocí tříd ladění v <xref:System.Diagnostics> oboru názvů .NET Framework. Tento obor názvů obsahuje <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> třídy, a <xref:System.Diagnostics.TraceSource> pro sledování toku spouštění a <xref:System.Diagnostics.Process> <xref:System.Diagnostics.EventLog> třídy, a <xref:System.Diagnostics.PerformanceCounter> pro kód profilace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povolení JIT – ladění Attach](enabling-jit-attach-debugging.md)  
 Ukazuje, jak nakonfigurovat registr pro JIT – připojit ladicí stroj k aplikaci .NET Framework.  
  
 [Usnadnění ladění image](making-an-image-easier-to-debug.md)  
 Ukazuje, jak zapnout a optimalizovat sledování JIT, aby bylo sestavení snazší ladit.  
  
 [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)  
 Popisuje, jak monitorovat provádění aplikace, když je spuštěná, a jak ji instrumentovat, aby zobrazila, jak dobře funguje, nebo jestli se něco pokazilo.  
  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)  
 Popisuje pomocníky spravovaného ladění (MDA), které jsou v kombinaci s modulem CLR (Common Language Runtime) k dispozici informace o stavu modulu runtime.  
  
 [Rozšíření ladění pomocí atributů zobrazení ladicího programu](enhancing-debugging-with-the-debugger-display-attributes.md)  
 Popisuje, jak může vývojář typu určit, jaký typ bude vypadat, jako by byl zobrazen v ladicím programu.  
  
 [Čítače výkonu](performance-counters.md)  
 Popisuje čítače, které lze použít ke sledování výkonu aplikace.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění aplikací ASP.NET nebo ASP.NET Core v sadě Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 Poskytuje předpoklady a pokyny pro ladění aplikace ASP.NET během vývoje nebo po nasazení.  
  
 [Průvodce vývojem](../development-guide.md)  
 Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.
