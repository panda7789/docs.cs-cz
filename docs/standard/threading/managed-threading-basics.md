---
title: "Základy dělení na spravovaná vlákna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
  
 [Synchronizace dat pro Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Popisuje strategie pro synchronizaci dat v třídy, které se použije s více vlákny.  
  
 [Stavy spravovaných vláken](../../../docs/standard/threading/managed-thread-states.md)  
 Popisuje stavy základní vláken a vysvětluje, jak zjistit, zda je spuštěn vlákna.  
  
 [Na popředí a vlákna na pozadí](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Vysvětluje rozdíly mezi vlákna na popředí a na pozadí.  
  
 [Spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Popisuje vztah mezi spravovaná a nespravovaná vlákna, jsou uvedené spravované ekvivalenty pro dělení na vlákna rozhraní API systému Windows a popisuje interakci Apartment COM a spravovaných vláknech.  
  
 [Thread.Suspend, uvolnění paměti a bezpečné body](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 Popisuje kolekci pozastavení a uvolňování paměti přístup z více vláken.  
  
 [Úložiště Thread Local: Statická pole relativní vůči vláknu a datové sloty ve vztahu](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
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
  
 [Dělení na spravovaná vlákna osvědčené postupy](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje časté problémy s více vláken a strategie pro vyhnout se tak problémům.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje Task Parallel Library a PLINQ, které výrazně usnadňuje práci při vytváření asynchronní a vícevláknových aplikací rozhraní .NET Framework.
