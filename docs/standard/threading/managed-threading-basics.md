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
ms.openlocfilehash: bec769043ab630b37609bed12302ceff5b90474a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139233"
---
# <a name="managed-threading-basics"></a>Základy spravovaného podprocesu

Prvních pět témat této části je navrženo tak, aby vám pomohla určit, kdy použít spravované podprocesy, a vysvětlit některé základní funkce. Informace o třídách, které poskytují další funkce, naleznete v [tématu Objekty zřetězení a prvky](../../../docs/standard/threading/threading-objects-and-features.md) a [Přehled primitivnísynchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Ostatní témata v této části pokrývají pokročilá témata, včetně interakce spravovaného podprocesu s operačním systémem Windows.  
  
> [!NOTE]
> V rozhraní .NET Framework 4 poskytují paralelní knihovna úloh a PLINQ rozhraní API pro paralelismus úloh a dat v programech s více vlákny. Další informace naleznete [v tématu Paralelní programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu

 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 Popisuje výhody a nevýhody více vláken a popisuje scénáře, ve kterých můžete vytvořit vlákna nebo použít vlákna fondu vláken.  
  
 [Výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Popisuje chování neošetřených výjimek ve vláknech pro různé verze rozhraní .NET Framework, zejména v situacích, ve kterých mají za následek ukončení aplikace.  
  
 [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Popisuje strategie pro synchronizaci dat ve třídách, které budou použity s více vlákny.  
  
 [Vlákna v popředí a v pozadí](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Vysvětluje rozdíly mezi popředí a podprocesů na pozadí.  
  
 [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Popisuje vztah mezi spravovaným a nespravovaným podprocesem, uvádí spravované ekvivalenty pro rozhraní API pro podprocesy systému Windows a popisuje interakci komoda a spravovaných vláken.  
  
 [Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Popisuje mechanismy úložiště relativní k vláknu.  
  
## <a name="reference"></a>Referenční informace

 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro třídu **Thread,** která představuje spravované vlákno, zda pochází z nespravovaného kódu nebo byla vytvořena ve spravované aplikaci.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Poskytuje bezpečný způsob implementace multithreading ve spojení s objekty uživatelského rozhraní.  
  
## <a name="related-sections"></a>Související oddíly

 [Přehled základních synchronizačních zařízení](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Popisuje spravované třídy používané k synchronizaci aktivit více vláken.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje běžné problémy s multithreading a strategie pro předcházení problémům.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje paralelní knihovnu úloh a PLINQ, které výrazně zjednodušují práci při vytváření asynchronních a vícevláknových aplikací rozhraní .NET Framework.
