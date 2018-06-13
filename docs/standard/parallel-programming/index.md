---
title: Paralelní programování v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea32ee89e20a1716b988a219dce221edec7c8917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582220"
---
# <a name="parallel-programming-in-net"></a>Paralelní programování v .NET

Mnoho osobní počítače a pracovní stanice mají několik jader procesoru, které umožňují více vláken současně. V blízké budoucnosti se očekává, že počítače budou mít mnohem více jader. V rámci využití výhod dostupného hardwaru lze kód paralelizovat a distribuovat tak práci mezi více procesorů. V minulosti paralelizace vyžadovala nízkoúrovňovou manipulaci s vlákny a zámky. Visual Studio 2010 a rozhraní .NET Framework 4 rozšiřují podporu pro paralelní programování poskytnutím nový modul runtime, nových typů knihovny tříd a nové diagnostické nástroje. Tyto funkce zjednodušují vývoj paralelních aplikací tak, aby bylo možné psát účinný, jemně odstupňovaný a škálovatelný paralelní kód v přirozeném stylu bez nutnosti pracovat přímo s vlákny nebo s fondem vláken. Následující obrázek poskytuje podrobný přehled architektury paralelní programování v rozhraní .NET Framework 4.
  
 ![Paralelní programování architektura .NET](./media/tpl-architecture.png "TPL_Architecture")  
  
## <a name="related-topics"></a>Související témata  
  
|Technologie|Popis|  
|----------------|-----------------|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje dokumentaci <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídy, která zahrnuje paralelní verze `For` a `ForEach` smyčky a také pro <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, která představuje upřednostňovaný způsob, jak vyjádřit asynchronní operace.|  
|[Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Paralelní implementace LINQ to Objects, která v mnoha scénářích výrazně zvyšuje výkon.|  
|[Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Obsahuje odkazy na dokumentaci pro třídy kolekce bezpečné pro přístup z více vláken, typy zjednodušené synchronizace a typy pro opožděnou inicializaci.|  
|[Paralelní diagnostické nástroje](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Obsahuje odkazy na dokumentaci k sadě Visual Studio ladicího programu pro úlohy a Paralelní zásobníky a [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer), která zahrnuje sadu zobrazení [!INCLUDE[vsprvsts](../../../includes/vsprvsts-md.md)] profileru, který slouží k ladění a optimalizaci výkon paralelního kódu.|  
|[Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Popisuje, jak pracují rozdělovače a jak nakonfigurovat výchozí rozdělovače nebo vytvořit nový rozdělovač.|  
|[Plánovače úloh](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Popisuje, jak pracují plánovače a jak lze nakonfigurovat výchozí plánovače.|  
|[Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Poskytuje stručný přehled výrazů lambda v jazyce C# a Visual Basic a ukazuje způsob jejich použití v PLINQ a Task Parallel Library.|  
|[Pro další čtení](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Obsahuje odkazy na další informace a ukázkové prostředky pro paralelní programování v rozhraní .NET.|  

## <a name="see-also"></a>Viz také  
 [Async – přehled](../async.md)  
 [Dělení na spravovaná vlákna](../threading/index.md)  
