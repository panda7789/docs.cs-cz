---
title: Paralelní programování v .NET
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b5426f5af9cd6ca919d8da0de0acfed76a2e63
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970386"
---
# <a name="parallel-programming-in-net"></a>Paralelní programování v .NET

Mnoho osobních počítačů a pracovních stanic má více jader procesoru, které umožňují více vláken současně. Abyste mohli využívat hardware, můžete kód k rozložení práce mezi více procesorů paralelizovat.

V minulosti paralelizace vyžadovala nízkoúrovňovou manipulaci s vlákny a zámky. Visual Studio a rozhraní .NET Framework rozšiřují podporu pro paralelní programování poskytnutím modul runtime, typy v knihovně tříd a diagnostické nástroje. Tyto funkce, které byly představeny s nástrojem rozhraní .NET Framework 4, zjednodušují vývoj paralelních aplikací. Můžete napsat efektivní, jemně odstupňovaný a škálovatelný paralelní kód v přirozeném stylu bez nutnosti pracovat přímo s vlákny nebo s fondem vláken.

Následující obrázek poskytuje podrobný přehled architektury paralelního programování v rozhraní .NET Framework:

![Architektura paralelní programování .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Související témata

|Technologie|Popis|
|----------------|-----------------|
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje dokumentaci pro <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídu, která zahrnuje paralelní verze `For` a `ForEach` smyčky a také pro <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídu, která představuje preferovaný způsob, jak vyjádřit asynchronní operace.|
|[Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Paralelní implementace LINQ to Objects, která v mnoha scénářích výrazně zvyšuje výkon.|
|[Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Obsahuje odkazy na dokumentaci pro třídy kolekce bezpečné pro přístup z více vláken, typy zjednodušené synchronizace a typy pro opožděnou inicializaci.|
|[Paralelní diagnostické nástroje](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Poskytuje odkazy na dokumentaci oken ladicího programu sady Visual Studio pro úkoly a Paralelní zásobníky a pro [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).|
|[Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Popisuje, jak pracují rozdělovače a jak nakonfigurovat výchozí rozdělovače nebo vytvořit nový rozdělovač.|
|[Plánovače úloh](xref:System.Threading.Tasks.TaskScheduler)|Popisuje, jak pracují plánovače a jak lze nakonfigurovat výchozí plánovače.|
|[Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Poskytuje stručný přehled výrazů lambda v jazyce C# a Visual Basic a ukazuje způsob jejich použití v PLINQ a Task Parallel Library.|
|[Pro další čtení](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Obsahuje odkazy na další informace a zdroje ukázek pro paralelní programování v rozhraní .NET.|

## <a name="see-also"></a>Viz také:

- [Přehled asynchronních](../async.md)
- [Dělení na spravovaná vlákna](../threading/index.md)
