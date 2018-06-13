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
ms.openlocfilehash: 2b1226f51143b912f85e94146948091891376e49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589916"
---
# <a name="managed-threading"></a>Dělení na spravovaná vlákna
Zda vyvíjíte pro počítače s jeden procesor nebo několik, má vaše aplikace poskytují nejvíce přizpůsobivý interakci s uživatelem, i když aplikaci právě provádí jinou práci. Používání více vláken, která je jedním z nejúčinnějších způsobů, jak udržovat aplikace reaguje na uživatele a současně proveďte využití procesoru v mezi nebo i během událostí uživatele. Při této části jsou popsány základní koncepty dělení na vlákna, se zaměřuje na spravovaná vlákna koncepty a pomocí spravovaného dělení na vlákna.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vícevláknové programování je výrazně jednodušší s <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nové souběžných kolekce tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na konceptu úkolů, nikoli vláken. Další informace najdete v tématu [paralelní programování](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)  
 Poskytuje přehled spravovaného dělení na vlákna a popisuje použití více vláken.  
  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
 Vysvětluje, jak vytvořit a spuštění, pozastavení, obnovení a zrušení vláken.  
  
 [Doporučené postupy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Popisuje úrovně synchronizace, jak se vyhnout blokování a konflikty časování, jedním procesorem a počítačů s více procesory a další vláken problémy.  
  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 Popisuje spravované třídy, které můžete použít k synchronizaci aktivity vláken a data objektů získat přístup v různých vláknech a poskytuje přehled podprocesy z fondu podprocesů.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading>  
 Obsahuje třídy pro použití a synchronizace spravovaných vláken.  
  
 <xref:System.Collections.Concurrent>  
 Obsahuje třídy kolekce, které jsou bezpečné pro použití s více vlákny.  
  
 <xref:System.Threading.Tasks>  
 Obsahuje třídy pro vytváření a plánování úloh souběžné zpracování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje přehled aplikační domény a jejich použití Common Language Infrastructure.  
  
 [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.  
  
 [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Poskytuje přehled vzoru doporučené pro asynchronní programování v rozhraní .NET.  
  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Vysvětluje, jak volat metody pro přístup z více vláken pomocí integrovaných funkcí delegáti z fondu podprocesů.  
  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 Popisuje paralelní programování knihoven, které zjednodušují používání více vláken v aplikacích.  
  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Popisuje systému pro spuštění dotazů paralelně, abyste mohli využívat více procesorů.
