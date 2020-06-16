---
title: Základy dělení na spravovaná vlákna
description: Viz odkazy na další články spravovaného vlákna, které pokrývají témata, například výjimky, synchronizaci dat, popředí & vlákny na pozadí, místní úložiště a další.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769090"
---
# <a name="managed-threading-basics"></a>Základy spravovaného zřetězení

Prvních pět témat této části vám pomůže určit, kdy použít spravované zřetězení a vysvětlit některé základní funkce. Informace o třídách, které poskytují další funkce, naleznete v tématu [vlákna objektů a funkcí](threading-objects-and-features.md) a [Přehled základních synchronizací](overview-of-synchronization-primitives.md).  
  
 Zbývající témata v této části se týkají pokročilých témat, včetně interakce spravovaného vlákna s operačním systémem Windows.  
  
> [!NOTE]
> V .NET Framework 4 poskytuje Task Parallel Library a PLINQ rozhraní API pro paralelismus Task a data v programech s více vlákny. Další informace najdete v tématu [paralelní programování](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V této části

 [Vlákna a dělení na vlákna](threads-and-threading.md)  
 Popisuje výhody a nevýhody více vláken a popisuje scénáře, ve kterých je možné vytvářet vlákna nebo používat vlákna fondu vláken.  
  
 [Výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md)  
 Popisuje chování neošetřených výjimek v vláknech pro různé verze .NET Framework, zejména v situacích, kdy mají za následek ukončení aplikace.  
  
 [Synchronizace dat pro vícevláknové zpracování](synchronizing-data-for-multithreading.md)  
 Popisuje strategie pro synchronizaci dat ve třídách, které budou použity s více vlákny.  
  
 [Vlákna v popředí a v pozadí](foreground-and-background-threads.md)  
 Vysvětluje rozdíly mezi vlákny v popředí a na pozadí.  
  
 [Dělení na spravovaná a nespravovaná vlákna ve Windows](managed-and-unmanaged-threading-in-windows.md)  
 Popisuje vztah mezi spravovaným a nespravovaným vláknem, uvádí spravované ekvivalenty pro rozhraní API pro dělení na vlákna systému Windows a popisuje interakci objektů COM a spravovaných vláken.  
  
 [Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Popisuje mechanismy úložiště související s vlákny.  
  
## <a name="reference"></a>Referenční informace

 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro třídu **vlákna** , která představuje spravované vlákno, bez ohledu na to, zda pochází z nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Poskytuje bezpečný způsob implementace multithreading ve spojení s objekty uživatelského rozhraní.  
  
## <a name="related-sections"></a>Související oddíly

 [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)  
 Popisuje spravované třídy, které slouží k synchronizaci aktivit více vláken.  
  
 [Doporučené postupy dělení na spravovaná vlákna](managed-threading-best-practices.md)  
 Popisuje běžné problémy s více vlákny a strategiemi pro předcházení problémů.  
  
 [Paralelní programování](../parallel-programming/index.md)  
 Popisuje úlohu Parallel Library and PLINQ, která významně zjednodušuje práci při vytváření asynchronních a vícevláknových .NET Framework aplikací.
