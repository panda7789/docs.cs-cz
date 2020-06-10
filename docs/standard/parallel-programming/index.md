---
title: Paralelní programování v .NET
description: Přečtěte si o paralelním programování v .NET. K zjednodušení vývoje v rozhraní .NET použijte modul runtime .NET, typy knihovny tříd a diagnostické nástroje.
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 02087cf58720388c64d8aba5424db0b54828219a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661962"
---
# <a name="parallel-programming-in-net"></a>Paralelní programování v .NET

Mnoho osobních počítačů a pracovních stanic má několik jader procesoru, které umožňují spouštět více vláken současně. Chcete-li využít výhod hardwaru, můžete paralelizovat svůj kód pro distribuci práce mezi více procesorů.

V minulosti paralelizace vyžadovala nízkoúrovňovou manipulaci s vlákny a zámky. Visual Studio a .NET Framework zvyšují podporu paralelního programování tím, že poskytuje modul runtime, typy knihovny tříd a diagnostické nástroje. Tyto funkce, které byly představeny s .NET Framework 4, zjednodušují paralelní vývoj. V přirozeném idiom můžete napsat efektivní, jemně odstupňovaný a škálovatelný paralelní kód, aniž byste museli pracovat přímo s vlákny nebo s fondem vláken.

Následující obrázek poskytuje podrobný přehled architektury paralelního programování v .NET Framework:

![Architektura paralelního programování .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Související témata

|Technologie|Popis|
|----------------|-----------------|
|[Task Parallel Library (TPL)](task-parallel-library-tpl.md)|Poskytuje dokumentaci pro <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídu, která obsahuje paralelní verze `For` a `ForEach` smyčky, a také pro <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídu, která představuje preferovaný způsob, jak vyjádřit asynchronní operace.|
|[Paralelní LINQ (PLINQ)](introduction-to-plinq.md)|Paralelní implementace LINQ to Objects, která v mnoha scénářích výrazně zvyšuje výkon.|
|[Datové struktury pro paralelní programování](data-structures-for-parallel-programming.md)|Obsahuje odkazy na dokumentaci pro třídy kolekce bezpečné pro přístup z více vláken, typy zjednodušené synchronizace a typy pro opožděnou inicializaci.|
|[Paralelní Diagnostické nástroje](parallel-diagnostic-tools.md)|Obsahuje odkazy na dokumentaci pro okna ladicího programu sady Visual Studio pro úlohy a paralelní zásobníky a pro [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).|
|[Vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md)|Popisuje, jak pracují rozdělovače a jak nakonfigurovat výchozí rozdělovače nebo vytvořit nový rozdělovač.|
|[Plánovače úloh](xref:System.Threading.Tasks.TaskScheduler)|Popisuje, jak pracují plánovače a jak lze nakonfigurovat výchozí plánovače.|
|[Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)|Poskytuje stručný přehled výrazů lambda v jazyce C# a Visual Basic a ukazuje způsob jejich použití v PLINQ a Task Parallel Library.|
|[Pro další čtení](for-further-reading-parallel-programming.md)|Obsahuje odkazy na Další informace a ukázkové prostředky pro paralelní programování v rozhraní .NET.|

## <a name="see-also"></a>Viz také

- [Asynchronní přehled](../async.md)
- [Spravované podprocesy](../threading/index.md)
