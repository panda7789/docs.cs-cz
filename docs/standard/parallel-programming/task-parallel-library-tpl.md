---
title: Task Parallel Library (TPL)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1c261928981399722373d826bcc60726ec3f8ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="task-parallel-library-tpl"></a>Task Parallel Library (TPL)
Task Parallel Library (TPL) je sada veřejné typy a rozhraní API v <xref:System.Threading?displayProperty=nameWithType> a <xref:System.Threading.Tasks?displayProperty=nameWithType> obory názvů. Účelem TPL je, aby byli vývojáři produktivnější díky zjednodušení procesu přidávání paralelismu a souběžného zpracování do aplikací. TPL nastavuje stupeň souběžnosti dynamicky, aby byly co nejefektivněji využity všechny procesory, které jsou k dispozici. Kromě toho TPL zpracovává dělení práce, plánování vláken na <xref:System.Threading.ThreadPool>, podporu zrušení, Správa stavu a další nízké úrovně podrobnosti. Pomocí TPL můžete maximalizovat výkon kódu a zaměřit se na práci, pro kterou je aplikace navržena.  
  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], TPL je upřednostňovaný způsob, jak napsat kód s více vlákny a paralelní. Ne všechny kódy jsou však vhodné pro paralelizaci – pokud například smyčka provádí pouze malé množství práce při každé iteraci nebo není použita pro více iterací, potom může režie paralelního zpracování způsobit pomalejší práci s kódem. Paralelizace, stejně jako všechny kódy s více vlákny, dodává provádění programu na složitosti. Ačkoli TPL zjednodušuje scénáře s více vlákny, doporučujeme mít základní znalost koncepce práce s vlákny, například uzamčení, zablokování a konflikty časování, abyste mohli TPL používat efektivně.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-|-|  
|[Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Popisuje postup vytvoření paralelní `for` a `foreach` smyčky (`For` a `For Each` v jazyce Visual Basic).|  
|[Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Popisuje, jak vytvořit a spustit úlohy implicitně pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> nebo explicitně pomocí <xref:System.Threading.Tasks.Task> objekty přímo.|  
|[Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|Popisuje způsob použití součásti toku dat v knihovně TPL Dataflow Library pro zpracování více operací, které musí komunikovat mezi sebou, nebo zpracování dat, jakmile budou k dispozici.|  
|[Použití TPL s dalšími asynchronními vzory](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|Popisuje způsob použití TPL s dalšími asynchronními vzory v rozhraní .NET|  
|[Potenciální nástrahy datového a funkčního paralelismu](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Popisuje některé běžné nástrahy a způsob, jak se jim vyhnout.|  
|[Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Popisuje, jak dosáhnout datového paralelismu s dotazy LINQ.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Uzel nejvyšší úrovně pro paralelní programování .NET.|  
  
## <a name="see-also"></a>Viz také  
 [Ukázky pro paralelní programování s rozhraním .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
