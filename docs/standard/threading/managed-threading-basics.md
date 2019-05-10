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
ms.openlocfilehash: b352c35a327ed4736a1f41816d3f15c1a0f559f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644824"
---
# <a name="managed-threading-basics"></a>Dělení na spravovaná vlákna základy

Prvních pět témata v této části jsou navržené tak, která vám pomůže určit, kdy použití dělení na spravovaná vlákna a vysvětlit jim některé základní funkce. Informace o třídách, které poskytují další funkce, najdete v části [funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md) a [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Zbývající témata v této části pokrývají Pokročilá témata, včetně interakcí správě vláken s operačním systémem Windows.  
  
> [!NOTE]
>  V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Task Parallel Library a PLINQ poskytují rozhraní API pro paralelismus úloh a dat ve vícevláknových aplikacích. Další informace najdete v tématu [paralelního programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu

 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 Tento článek popisuje, jaké výhody a nevýhody více vláken a popisuje scénáře, ve kterých může vytvářet vlákna nebo pomocí vláken fondu vláken.  
  
 [Výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Popisuje chování neošetřené výjimky ve vláknech pro různé verze rozhraní .NET Framework, zejména situace, ve které se za následek ukončení aplikace.  
  
 [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Popisuje strategie pro synchronizaci dat ve třídách, které se použijí s více vlákny.  
  
 [Vlákna v popředí a v pozadí](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Vysvětluje rozdíly mezi vlákna v popředí a pozadí.  
  
 [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Tento článek popisuje vztah mezi spravovaná a nespravovaná vlákna, jsou uvedené spravované ekvivalenty pro dělení na vlákna rozhraní API Windows a popisuje interakce Apartment modelu COM a spravovaná vlákna.  
  
 [Úložiště Thread Local: Statická pole relativní vůči vláknu a datové sloty ve vztahu](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Popisuje relativní vůči vláknu úložiště mechanismy.  
  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Popisuje, jak asynchronní nebo dlouhotrvající synchronní operace se může týkat pomocí tokenu zrušení.  
  
## <a name="reference"></a>Odkaz

 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro **vlákno** třídu, která představuje spravované vlákno, ať už pochází z nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Poskytuje bezpečný způsob, jak implementovat multithreadingu ve spojení s objektů uživatelského rozhraní.  
  
## <a name="related-sections"></a>Související oddíly

 [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Popisuje spravované třídy používané pro synchronizaci činností více vláken.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje běžné problémy s multithreading a strategie, jak se vyhnout problémům.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje Task Parallel Library a PLINQ, které značně zjednodušují vytváření asynchronní a vícevláknové aplikace rozhraní .NET Framework.
