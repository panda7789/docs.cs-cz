---
title: Task Parallel Library (TPL)
description: Prozkoumejte knihovnu Task Parallel Library (TPL), sadu veřejných typů a rozhraní API pro zjednodušení procesu přidávání paralelismu & souběžnosti do aplikací v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 42768d99e7f3a15751ccf4c980edb9373666d49f
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768598"
---
# <a name="task-parallel-library-tpl"></a>Task Parallel Library (TPL)
Task Parallel Library (TPL) je sada veřejných typů a rozhraní API v <xref:System.Threading?displayProperty=nameWithType> <xref:System.Threading.Tasks?displayProperty=nameWithType> oborech názvů a. Účelem TPL je, aby byli vývojáři produktivnější díky zjednodušení procesu přidávání paralelismu a souběžného zpracování do aplikací. TPL nastavuje stupeň souběžnosti dynamicky, aby byly co nejefektivněji využity všechny procesory, které jsou k dispozici. Kromě toho TPL zpracovává rozdělení práce, plánování vláken na <xref:System.Threading.ThreadPool> , podporu zrušení, správu stavu a další podrobnosti nízké úrovně. Pomocí TPL můžete maximalizovat výkon kódu a zaměřit se na práci, pro kterou je aplikace navržena.  
  
 Počínaje .NET Framework 4 je TPL upřednostňovaným způsobem, jak psát vícevláknový a paralelní kód. Ne všechny kódy jsou však vhodné pro paralelizaci – pokud například smyčka provádí pouze malé množství práce při každé iteraci nebo není použita pro více iterací, potom může režie paralelního zpracování způsobit pomalejší práci s kódem. Paralelizace, stejně jako všechny kódy s více vlákny, dodává provádění programu na složitosti. Ačkoli TPL zjednodušuje scénáře s více vlákny, doporučujeme mít základní znalost koncepce práce s vlákny, například uzamčení, zablokování a konflikty časování, abyste mohli TPL používat efektivně.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-|-|  
|[Datový paralelismus](data-parallelism-task-parallel-library.md)|Popisuje, jak vytvořit paralelní `for` `foreach` smyčky a smyčky ( `For` a `For Each` v Visual Basic).|  
|[Asynchronní programování založené na úlohách](task-based-asynchronous-programming.md)|Popisuje, jak vytvářet a spouštět úlohy implicitně pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> nebo explicitně pomocí <xref:System.Threading.Tasks.Task> objektů přímo.|  
|[Tok dat](dataflow-task-parallel-library.md)|Popisuje způsob použití součásti toku dat v knihovně TPL Dataflow Library pro zpracování více operací, které musí komunikovat mezi sebou, nebo zpracování dat, jakmile budou k dispozici.|  
|[Použití TPL s dalšími asynchronními vzory](using-tpl-with-other-asynchronous-patterns.md)|Popisuje způsob použití TPL s dalšími asynchronními vzory v rozhraní .NET|  
|[Potenciální nástrahy datového a funkčního paralelismu](potential-pitfalls-in-data-and-task-parallelism.md)|Popisuje některé běžné nástrahy a způsob, jak se jim vyhnout.|  
|[Paralelní LINQ (PLINQ)](introduction-to-plinq.md)|Popisuje, jak dosáhnout datového paralelismu s dotazy LINQ.|  
|[Paralelní programování](index.md)|Uzel nejvyšší úrovně pro paralelní programování .NET.|  
  
## <a name="see-also"></a>Viz také

- [Ukázky pro paralelní programování s rozhraním .NET Core & .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
