---
title: Dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137933"
---
# <a name="managed-threading"></a>Dělení na spravovaná vlákna
Bez ohledu na to, zda vyvíjíte pro počítače s jedním nebo několika procesory, chcete, aby vaše aplikace poskytovala co nejrychlejší interakci s uživatelem, a to i v případě, že aplikace právě provádí jinou práci. Použití několika podprocesů provádění je jedním z nejúčinnějších způsobů, jak zajistit, aby aplikace reagovala na uživatele a zároveň používala procesor v rámci událostí uživatele nebo dokonce i během nich. V této části se seznámíte se základními koncepcemi dělení na vlákna, zaměřuje se na koncepty spravovaného vlákna a pomocí spravovaného vlákna.  
  
> [!NOTE]
> Počínaje .NET Framework 4 je vícevláknové programování výrazně zjednodušené s třídami <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nové třídy souběžných kolekcí v oboru názvů <xref:System.Collections.Concurrent?displayProperty=nameWithType> a nový programovací model, který je na základě konceptu úkolů, nikoli vláken. Další informace najdete v tématu [paralelní programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)  
 Poskytuje přehled spravovaného zřetězení a popisuje, kdy použít více vláken.  
  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
 Vysvětluje, jak vytvořit, spustit, pozastavit, obnovit a přerušit vlákna.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje úrovně synchronizace, jak zabránit zablokování a konfliktům časování a dalším problémům s vlákny.  
  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 Popisuje spravované třídy, které lze použít k synchronizaci aktivit vláken a dat objektů, ke kterým přistupovalo v různých vláknech, a poskytuje přehled vláken fondu vláken.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading>  
 Obsahuje třídy pro použití a synchronizaci spravovaných vláken.  
  
 <xref:System.Collections.Concurrent>  
 Obsahuje třídy kolekcí, které jsou bezpečné pro použití s více vlákny.  
  
 <xref:System.Threading.Tasks>  
 Obsahuje třídy pro vytváření a plánování souběžných úloh zpracování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje přehled aplikačních domén a jejich použití Common Language Infrastructure.  
  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.  
  
 [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Poskytuje přehled o doporučeném vzoru pro asynchronní programování v rozhraní .NET.  
  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Vysvětluje, jak volat metody v vláknech fondu vláken pomocí integrovaných funkcí delegátů.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje knihovny paralelního programování, které zjednodušují použití více vláken v aplikacích.  
  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Popisuje systém pro souběžné spouštění dotazů, aby bylo možné využít více procesorů.
