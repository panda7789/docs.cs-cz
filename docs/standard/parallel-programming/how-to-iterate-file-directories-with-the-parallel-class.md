---
title: "Postupy: Procházení adresářů se soubory pomocí paralelní třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ddcc19ea37735dd08e801f4fd9e314398ccc44a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Postupy: Procházení adresářů se soubory pomocí paralelní třídy
V mnoha případech je iterace souboru operací, kterou lze snadno paralelizovat. Téma [postupy: procházení adresářů se soubory pomocí PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) ukazuje nejjednodušší způsob, jak to provést pro mnoho scénářů. Jakmile se však musí kód vypořádat s mnoha typy výjimek, mohou se při přístupu k systému souborů objevit komplikace. Následující příklad znázorňuje jeden ze způsobů řešení problému. Pro procházení všech souborů a složek v zadaném adresáři používá iteraci založenou na zásobníku a umožňuje kódu zachytit a zpracovat různé výjimky. Způsob zpracování výjimek záleží samozřejmě na vás.  
  
## <a name="example"></a>Příklad  
 Následující příklad prochází adresář sekvenčně, soubory však zpracovává paralelně. Toto je pravděpodobně nejlepší řešení, pokud máte velký poměr souborů na adresář. Je také možné provést paralelní zpracování iterace adresáře a k jednotlivým souborům přistupovat sekvenčně. Paralelní zpracování obou smyček není pravděpodobně efektivní, dokud není výslovně použito počítače s velkým počtem procesorů. Jako ve všech případech je však třeba důkladně otestovat celou aplikaci a určit nejlepší přístup.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 V tomto příkladu se vstupně-výstupní operace souboru provádějí synchronně. Při používání velkých souborů nebo pomalého připojení k síti může být vhodnější přistupovat k souborům asynchronně. Pomocí paralelní iterace lze kombinovat asynchronní vstupně-výstupní techniky. Další informace najdete v tématu [TPL a tradiční rozhraní .NET Framework asynchronní programování](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Pro zachování celkového počtu zpracovaných souborů je v příkladu použita místní proměnná `fileCount`. Vzhledem k tomu, že k proměnné může přistupovat souběžně více úkolů, je přístup k této proměnné synchronizován voláním metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>.  
  
 Pamatujte, že pokud je výjimka vyvolána v hlavním vlákně, mohou vlákna, která byla spouštěna metodou <xref:System.Threading.Tasks.Parallel.ForEach%2A>, být spuštěna i nadále. Tato vlákna lze zastavit nastavením proměnné typu Boolean v obslužných rutinách události a ověřením hodnoty v jednotlivých iteracích paralelní smyčky. Označuje-li hodnota vyvolání výjimky, je třeba pro zastavení nebo přerušení smyčky použít proměnnou <xref:System.Threading.Tasks.ParallelLoopState>. Další informace najdete v tématu [postupy: zastavení nebo přerušení smyčky Parallel.For](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
