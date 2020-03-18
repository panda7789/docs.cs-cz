---
title: Použití vláken a dělení na vlákna
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 1d487edff2cdc2e63f81963bfaa1f68a06e5b36e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75936847"
---
# <a name="using-threads-and-threading"></a>Použití vláken a dělení na vlákna

Pomocí rozhraní .NET můžete psát aplikace, které provádějí více operací současně. Operace s potenciálem pozdržet další operace lze provést v samostatných vláknech, což je proces známý jako *multithreading* nebo *free threading*.  
  
Aplikace, které používají vícevláknové práce, lépe reagují na vstup uživatele, protože uživatelské rozhraní zůstává aktivní, protože úlohy náročné na procesor se provádějí v samostatných vláknech. Multithreading je také užitečné při vytváření škálovatelných aplikací, protože můžete přidat vlákna jako zvyšuje zatížení.

> [!NOTE]
> Pokud potřebujete větší kontrolu nad chováním vláken aplikace, můžete spravovat vlákna sami. Počínaje rozhraním .NET Framework 4 je však programování s <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> více <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> vlákny značně zjednodušeno pomocí tříd a, Paralelní <xref:System.Collections.Concurrent?displayProperty=nameWithType> [LINQ (PLINQ),](../parallel-programming/parallel-linq-plinq.md)nové třídy souběžné kolekce v oboru názvů a nový programovací model, který je založen na konceptu úloh y spíše než na vláknech. Další informace naleznete [v tématu Paralelní programování](../parallel-programming/index.md) a paralelní [knihovna úloh (TPL).](../parallel-programming/task-parallel-library-tpl.md)

## <a name="how-to-create-and-start-a-new-thread"></a>Postup: Vytvoření a spuštění nového vlákna

Vytvoříte nové vlákno vytvořením nové <xref:System.Threading.Thread?displayProperty=nameWithType> instance třídy a zadáním názvu metody, kterou chcete spustit v novém vlákně konstruktoru. Chcete-li spustit vytvořené <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> vlákno, zavolejte metodu. Další informace a příklady naleznete [v tématu vytváření vláken a předávání dat v článku čas zahájení](creating-threads-and-passing-data-at-start-time.md) a odkaz na <xref:System.Threading.Thread> rozhraní API.

## <a name="how-to-stop-a-thread"></a>Postup: Zastavení vlákna

Chcete-li ukončit provádění podprocesu, použijte <xref:System.Threading.CancellationToken?displayProperty=nameWithType>. Poskytuje jednotný způsob, jak zastavit vlákna kooperativně. Další informace naleznete [v tématu Zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md).

Někdy není možné zastavit vlákno kooperativně, protože spustí kód třetí strany, který není určen pro kooperativní zrušení. V takovém případě můžete chtít ukončit jeho provádění násilně. Chcete-li ukončit provádění podprocesu násilně, v <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> rozhraní .NET Framework můžete použít metodu. Tato metoda <xref:System.Threading.ThreadAbortException> vyvolá na vlákno, na kterém je vyvolána. Další informace naleznete v [tématu Zničení vláken](destroying-threads.md). Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> není podporována v .NET Core. Pokud potřebujete ukončit provádění kódu třetí strany násilně v .NET Core, spusťte jej v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.

Není <xref:System.Threading.CancellationToken?displayProperty=nameWithType> k dispozici před rozhraním .NET Framework 4. Chcete-li zastavit vlákno ve starších verzích rozhraní .NET Framework, měli byste implementovat kooperativní zrušení ručně pomocí technik synchronizace vláken. Můžete například vytvořit nestálé logické `shouldStop` pole a použít ho k vyžádání kódu provedeného vláknem k zastavení. Další informace naleznete [v tématu](../../csharp/language-reference/keywords/volatile.md) <xref:System.Threading.Volatile?displayProperty=nameWithType>volatile v c# reference a .

Pomocí <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody můžete volající vlákno čekat na ukončení podprocesu, který je zastaven.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Postup: Pozastavení nebo přerušení vlákna

Metoda slouží <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> k pozastavení aktuálního vlákna po určitou dobu. Blokované vlákno můžete přerušit <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> voláním metody. Další informace naleznete [v tématu Pozastavení a přerušení podprocesů](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Vlastnosti vlákna

V následující tabulce jsou <xref:System.Threading.Thread> uvedeny některé vlastnosti:  
  
|Vlastnost|Popis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Vrátí, `true` pokud vlákno bylo spuštěno a ještě nebylo ukončeno normálně nebo přerušeno.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Získá nebo nastaví logickou hodnotu, která označuje, pokud vlákno je vlákno na pozadí. Vlákna na pozadí jsou jako vlákna na popředí, ale vlákno na pozadí nebrání zastavení procesu. Jakmile jsou zastavena všechna vlákna v popředí, která patří do procesu, <xref:System.Threading.Thread.Abort%2A> běžný jazyk runtime ukončí proces voláním metody na vláknech na pozadí, které jsou stále naživu. Další informace naleznete [v tématu Popředí a vlákna na pozadí](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Získá nebo nastaví název vlákna. Nejčastěji se používá ke zjištění jednotlivých podprocesů při ladění.|  
|<xref:System.Threading.Thread.Priority%2A>|Získá nebo <xref:System.Threading.ThreadPriority> nastaví hodnotu, která se používá v operačním systému k upřednostnění plánování podprocesů. Další informace naleznete v [tématu Plánování vláken](scheduling-threads.md) a <xref:System.Threading.ThreadPriority> odkaz.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Získá <xref:System.Threading.ThreadState> hodnotu obsahující aktuální stavy vlákna.|  

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Paralelní programování](../parallel-programming/index.md)
