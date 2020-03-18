---
title: Paralelní programování v .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: ae129ef0cb2b331c1eb0220282f21fec6f6fb77d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134148"
---
# <a name="parallel-programming-in-net"></a>Paralelní programování v .NET

Mnoho osobních počítačů a pracovních stanic má více jader procesoru, které umožňují současné spouštění více vláken. Chcete-li využít výhod hardwaru, můžete paralelizovat kód distribuovat práci mezi více procesorů.

V minulosti paralelizace vyžadovala nízkoúrovňovou manipulaci s vlákny a zámky. Visual Studio a rozhraní .NET Framework zvyšují podporu paralelního programování tím, že poskytují runtime, typy knihovny tříd a diagnostické nástroje. Tyto funkce, které byly zavedeny s rozhraním .NET Framework 4, zjednodušují paralelní vývoj. Můžete psát efektivní, jemně odstupňovaný a škálovatelný paralelní kód v přirozeném idiomu, aniž byste museli pracovat přímo s vlákny nebo fondem vláken.

Následující obrázek poskytuje přehled na vysoké úrovni architektury paralelního programování v rozhraní .NET Framework:

![Architektura paralelního programování rozhraní .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Související témata

|Technologie|Popis|
|----------------|-----------------|
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje dokumentaci <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> pro třídu, která `For` `ForEach` zahrnuje paralelní verze a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> smyčky a také pro třídu, která představuje upřednostňovaný způsob vyjádření asynchronních operací.|
|[Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Paralelní implementace LINQ to Objects, která v mnoha scénářích výrazně zvyšuje výkon.|
|[Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Obsahuje odkazy na dokumentaci pro třídy kolekce bezpečné pro přístup z více vláken, typy zjednodušené synchronizace a typy pro opožděnou inicializaci.|
|[Paralelní diagnostické nástroje](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Obsahuje odkazy na dokumentaci pro okna ladicího programu sady VisualStudio pro úlohy a paralelní zásobníky a pro [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).|
|[Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Popisuje, jak pracují rozdělovače a jak nakonfigurovat výchozí rozdělovače nebo vytvořit nový rozdělovač.|
|[Plánovače úloh](xref:System.Threading.Tasks.TaskScheduler)|Popisuje, jak pracují plánovače a jak lze nakonfigurovat výchozí plánovače.|
|[Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Poskytuje stručný přehled výrazů lambda v jazyce C# a Visual Basic a ukazuje způsob jejich použití v PLINQ a Task Parallel Library.|
|[Pro další čtení](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Obsahuje odkazy na další informace a ukázkové prostředky pro paralelní programování v rozhraní .NET.|

## <a name="see-also"></a>Viz také

- [Přehled asynchronizací](../async.md)
- [Dělení na spravovaná vlákna](../threading/index.md)
