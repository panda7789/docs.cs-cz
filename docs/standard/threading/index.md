---
title: Dělení na spravovaná vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: c5ca102dc98e50067d39d2f0c51a6ff75e342e9f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588655"
---
# <a name="managed-threading"></a>Dělení na spravovaná vlákna
Bez ohledu na to, zda vyvíjíte pro počítače s jedním nebo několika procesory, chcete, aby aplikace poskytovala nejcitlivější interakci s uživatelem, a to i v případě, že aplikace aktuálně provádí jinou práci. Použití více vláken provádění je jedním z nejvýkonnějších způsobů, jak udržet aplikaci reagovat na uživatele a zároveň využít procesor u nebo dokonce během událostí uživatele. Zatímco tato část představuje základní koncepty zřetězení, zaměřuje se na spravované koncepty vláken a použití spravovaného podprocesu.  
  
> [!NOTE]
> Počínaje rozhraním .NET Framework 4 je programování s více <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> vlákny značně zjednodušeno pomocí tříd a, Paralelní <xref:System.Collections.Concurrent?displayProperty=nameWithType> [LINQ (PLINQ),](../../../docs/standard/parallel-programming/introduction-to-plinq.md)nové třídy souběžné kolekce v oboru názvů a nový programovací model, který je založen na konceptu úloh spíše než zřetěze. Další informace naleznete [v tématu Paralelní programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)  
 Obsahuje přehled spravovaného podprocesu a popisuje, kdy použít více vláken.  
  
 [Použití vláken a zřetězení](../../../docs/standard/threading/using-threads-and-threading.md)  
 Vysvětluje, jak vytvořit, spustit, pozastavit, obnovit a přerušit podprocesy.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje úrovně synchronizace, jak se vyhnout zablokování a sporáky a další problémy podprocesem.  
  
 [Objekty a prvky zřetězení](../../../docs/standard/threading/threading-objects-and-features.md)  
 Popisuje spravované třídy, které můžete použít k synchronizaci aktivit vláken a dat objektů, ke které se přistupuje v různých vláknech, a poskytuje přehled vláken fondu vláken.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading>  
 Obsahuje třídy pro použití a synchronizaci spravovaných vláken.  
  
 <xref:System.Collections.Concurrent>  
 Obsahuje třídy kolekce, které jsou bezpečné pro použití s více vlákny.  
  
 <xref:System.Threading.Tasks>  
 Obsahuje třídy pro vytváření a plánování souběžných úloh zpracování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Obsahuje přehled aplikačních domén a jejich použití společnou jazykovou infrastrukturou.  
  
 [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.  
  
 [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Obsahuje přehled doporučeného vzoru pro asynchronní programování v rozhraní .NET.  
  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Vysvětluje, jak volat metody ve vláknech fondu vláken pomocí integrovaných funkcí delegátů.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje paralelní programovací knihovny, které zjednodušují použití více vláken v aplikacích.  
  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
 Popisuje systém pro paralelní spouštění dotazů, aby bylo možné využívat více procesorů.
