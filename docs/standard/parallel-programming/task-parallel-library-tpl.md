---
title: Task Parallel Library (TPL)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 74a6fc20e95e11bfdbec617742f304a940f3e769
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507556"
---
# <a name="task-parallel-library-tpl"></a>Task Parallel Library (TPL)
Task Parallel Library (TPL) je sada veřejných typů a rozhraní API v oborech názvů <xref:System.Threading?displayProperty=nameWithType> a <xref:System.Threading.Tasks?displayProperty=nameWithType> . Účelem TPL je, aby byli vývojáři produktivnější díky zjednodušení procesu přidávání paralelismu a souběžného zpracování do aplikací. TPL nastavuje stupeň souběžnosti dynamicky, aby byly co nejefektivněji využity všechny procesory, které jsou k dispozici. Kromě toho TPL zpracovává rozdělení práce, plánování vláken na <xref:System.Threading.ThreadPool>, podporu zrušení, správu stavu a další podrobnosti nízké úrovně. Pomocí TPL můžete maximalizovat výkon kódu a zaměřit se na práci, pro kterou je aplikace navržena.  
  
 Počínaje .NET Framework 4 je TPL upřednostňovaným způsobem, jak psát vícevláknový a paralelní kód. Ne všechny kódy jsou však vhodné pro paralelizaci – pokud například smyčka provádí pouze malé množství práce při každé iteraci nebo není použita pro více iterací, potom může režie paralelního zpracování způsobit pomalejší práci s kódem. Paralelizace, stejně jako všechny kódy s více vlákny, dodává provádění programu na složitosti. Ačkoli TPL zjednodušuje scénáře s více vlákny, doporučujeme mít základní znalost koncepce práce s vlákny, například uzamčení, zablokování a konflikty časování, abyste mohli TPL používat efektivně.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-|-|  
|[Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Popisuje, jak vytvořit paralelní `for` smyčky `foreach` a smyčky (`For` a `For Each` v Visual Basic).|  
|[Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Popisuje, jak vytvářet a spouštět úlohy implicitně pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> nebo explicitně pomocí <xref:System.Threading.Tasks.Task> objektů přímo.|  
|[Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|Popisuje způsob použití součásti toku dat v knihovně TPL Dataflow Library pro zpracování více operací, které musí komunikovat mezi sebou, nebo zpracování dat, jakmile budou k dispozici.|  
|[Použití TPL s dalšími asynchronními vzory](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|Popisuje způsob použití TPL s dalšími asynchronními vzory v rozhraní .NET|  
|[Potenciální nástrahy datového a funkčního paralelismu](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Popisuje některé běžné nástrahy a způsob, jak se jim vyhnout.|  
|[Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)|Popisuje, jak dosáhnout datového paralelismu s dotazy LINQ.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Uzel nejvyšší úrovně pro paralelní programování .NET.|  
  
## <a name="see-also"></a>Viz také

- [Ukázky pro paralelní programování s rozhraním .NET Core & .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
