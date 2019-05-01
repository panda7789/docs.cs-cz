---
title: Dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6447cd37e4718093acfb3a0e2db053c13a027d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015137"
---
# <a name="managed-threading"></a>Dělení na spravovaná vlákna
Ať už vyvíjíte pro počítače s jedním procesorem nebo několik, má aplikace poskytují největší responzivní interakci s uživatelem, i v případě, že aplikace je aktuálně provádění jiné práce. Použití více vláken, která je jedním z nejúčinnějších způsobů, jak udržovat vaše aplikace reagovat na uživatele a ujistěte se, v době, využívání procesoru mezi nebo i během událostí uživatele. Zatímco tato část představuje základní koncepce práce s vlákny, zaměřuje se na spravované koncepce práce s vlákny a použití dělení na spravovaná vlákna.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vícevláknové programování je výrazně usnadněna díky <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nové souběžných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na koncepci úkoly spíše než vlákna. Další informace najdete v tématu [paralelního programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)  
 Obsahuje základní informace o správě vláken a popisuje použití více vláken.  
  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
 Vysvětluje, jak vytvořit a spuštění, pozastavení, obnovení a přerušení vlákna.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Tento článek popisuje úrovně synchronizace, jak se vyhnout zablokování a konflikty časování a dalších dělení na vlákna problémy.  
  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 Popisuje spravované třídy, které lze použít k synchronizaci aktivity vláken a datové objekty přístupné v různých vláknech a najdete zde přehled vláken fondu vláken.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading>  
 Obsahuje třídy pro použití a synchronizaci spravovaných vláken.  
  
 <xref:System.Collections.Concurrent>  
 Obsahuje třídy kolekcí, které jsou bezpečné pro použití s více vlákny.  
  
 <xref:System.Threading.Tasks>  
 Obsahuje třídy pro vytváření a plánování úloh souběžné zpracování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje přehled domén aplikací a jejich použití Common Language Infrastructure.  
  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.  
  
 [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Poskytuje přehled o doporučený model pro asynchronní programování v rozhraní .NET.  
  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Vysvětluje, jak volat metody ve vlákně fondu vláken pomocí integrované funkce delegátů.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje paralelní programování knihoven, které zjednodušují používání více vláken v aplikacích.  
  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Popisuje systém pro spouštění dotazů paralelně, abyste mohli využívat více procesorů.
