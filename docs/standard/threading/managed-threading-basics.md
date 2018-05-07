---
title: Základy dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fa91bb22de6492815f79bfd50e1fefc800c6047
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="managed-threading-basics"></a>Základy dělení na spravovaná vlákna
Prvních pět témata v této části jsou navrženy pro vám pomohou určit, kdy používat spravovaného dělení na vlákna a vysvětlit některé základní funkce. Informace o třídy, které poskytují další funkce, najdete v části [dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md) a [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Zbývající témata v této části titulní rozšířené témata, včetně interakci spravovaného dělení na vlákna s operačním systémem Windows.  
  
> [!NOTE]
>  V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Task Parallel Library a PLINQ poskytují rozhraní API pro úlohy a datový paralelismus v vícevláknových programů. Další informace najdete v tématu [paralelní programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 Popisuje výhody a nevýhody více vláken a popisuje scénáře, ve kterých může vytvořit vláken nebo použít podprocesy z fondu podprocesů.  
  
 [Výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Popisuje chování neošetřenými výjimkami v vláken pro různé verze rozhraní .NET Framework, zejména situace, ve které vedou ukončení aplikace.  
  
 [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Popisuje strategie pro synchronizaci dat v třídy, které se použije s více vlákny.  
  
 [Stavy spravovaných vláken](../../../docs/standard/threading/managed-thread-states.md)  
 Popisuje stavy základní vláken a vysvětluje, jak zjistit, zda je spuštěn vlákna.  
  
 [Vlákna v popředí a v pozadí](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Vysvětluje rozdíly mezi vlákna na popředí a na pozadí.  
  
 [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Popisuje vztah mezi spravovaná a nespravovaná vlákna, jsou uvedené spravované ekvivalenty pro dělení na vlákna rozhraní API systému Windows a popisuje interakci Apartment COM a spravovaných vláknech.  
  
 [Thread.Suspend, uvolňování paměti a bezpečné body](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 Popisuje kolekci pozastavení a uvolňování paměti přístup z více vláken.  
  
 [Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Popisuje mechanismy relativní vůči vláknu úložiště.  
  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Popisuje, jak asynchronní nebo dlouhotrvající synchronní operace se může týkat pomocí tokenu zrušení.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro **vlákno** třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Poskytuje bezpečný způsob, jak implementovat více vláken ve spojení s objekty uživatelského rozhraní.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Popisuje spravované třídy, které jsou použity k synchronizaci aktivity z více vláken.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje časté problémy s více vláken a strategie pro vyhnout se tak problémům.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje Task Parallel Library a PLINQ, které výrazně usnadňuje práci při vytváření asynchronní a vícevláknových aplikací rozhraní .NET Framework.
