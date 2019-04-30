---
title: 'Postupy: Procházení adresářů se soubory pomocí paralelní třídy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1ec270159430434adc074f1fa6ca92ec3c4a455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781209"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Postupy: Procházení adresářů se soubory pomocí paralelní třídy
V mnoha případech je iterace souboru operací, kterou lze snadno paralelizovat. Téma [jak: Procházení adresářů se soubory pomocí jazyka PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) ukazuje nejjednodušší způsob, jak tuto úlohu proveďte pro řadu scénářů. Jakmile se však musí kód vypořádat s mnoha typy výjimek, mohou se při přístupu k systému souborů objevit komplikace. Následující příklad znázorňuje jeden ze způsobů řešení problému. Pro procházení všech souborů a složek v zadaném adresáři používá iteraci založenou na zásobníku a umožňuje kódu zachytit a zpracovat různé výjimky. Způsob zpracování výjimek záleží samozřejmě na vás.  
  
## <a name="example"></a>Příklad  
 Následující příklad prochází adresář sekvenčně, soubory však zpracovává paralelně. Toto je pravděpodobně nejlepší řešení, pokud máte velký poměr souborů na adresář. Je také možné provést paralelní zpracování iterace adresáře a k jednotlivým souborům přistupovat sekvenčně. Paralelní zpracování obou smyček není pravděpodobně efektivní, dokud není výslovně použito počítače s velkým počtem procesorů. Jako ve všech případech je však třeba důkladně otestovat celou aplikaci a určit nejlepší přístup.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 V tomto příkladu se vstupně-výstupní operace souboru provádějí synchronně. Při používání velkých souborů nebo pomalého připojení k síti může být vhodnější přistupovat k souborům asynchronně. Pomocí paralelní iterace lze kombinovat asynchronní vstupně-výstupní techniky. Další informace najdete v tématu [TPL a tradiční rozhraní .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Pro zachování celkového počtu zpracovaných souborů je v příkladu použita místní proměnná `fileCount`. Vzhledem k tomu, že k proměnné může přistupovat souběžně více úkolů, je přístup k této proměnné synchronizován voláním metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>.  
  
 Pamatujte, že pokud je výjimka vyvolána v hlavním vlákně, mohou vlákna, která byla spouštěna metodou <xref:System.Threading.Tasks.Parallel.ForEach%2A>, být spuštěna i nadále. Tato vlákna lze zastavit nastavením proměnné typu Boolean v obslužných rutinách události a ověřením hodnoty v jednotlivých iteracích paralelní smyčky. Označuje-li hodnota vyvolání výjimky, je třeba pro zastavení nebo přerušení smyčky použít proměnnou <xref:System.Threading.Tasks.ParallelLoopState>. Další informace najdete v tématu [jak: Zastavení nebo přerušení smyčky Parallel.For](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
