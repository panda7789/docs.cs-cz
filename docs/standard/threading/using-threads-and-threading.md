---
title: Použití vláken a dělení na vlákna
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4fd57de4c6e65c3c82d0dc71bcaf84d668f28bf
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864226"
---
# <a name="using-threads-and-threading"></a>Použití vláken a dělení na vlákna

Pomocí rozhraní .NET můžete psát aplikace, které provést více operací ve stejnou dobu. Operace má potenciál pojme jiné operace můžete spustit v samostatných vláknech, tento proces se označuje jako *multithreading* nebo *zdarma dělení na vlákna*.  
  
Aplikace, které využívají multithreading je rychlejší reakce na uživatele, protože uživatelské rozhraní zůstane aktivní, spouštět úlohy náročné na procesor v samostatných vláknech. Multithreading je také užitečné při vytváření škálovatelných aplikací, protože přidáte vlákna zatížení stoupá.

> [!NOTE]
> Pokud potřebujete větší kontrolu nad chováním aplikace vlákna, můžete spravovat vlákna sami. Nicméně od verze rozhraní .NET Framework 4, vícevláknové programování je výrazně usnadněna díky <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md), nové souběžných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na koncepci úkoly spíše než vlákna. Další informace najdete v tématu [paralelního programování](../parallel-programming/index.md) a [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Postupy: vytvoření a spuštění nového vlákna

Vytvořit nové vlákno tak, že vytvoříte novou instanci třídy <xref:System.Threading.Thread?displayProperty=nameWithType> třídy a poskytnutí názvu metody, která je třeba spustit v novém vláknu konstruktoru. Chcete-li spustit vytvořeného vlákna, zavolejte <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody. Další informace a příklady najdete v tématu [vytváření vláken a předávání dat při spuštění](creating-threads-and-passing-data-at-start-time.md) článku a <xref:System.Threading.Thread> reference k rozhraní API.

## <a name="how-to-stop-a-thread"></a>Postupy: zastavení vlákna

Chcete-li ukončit provádění vlákna, použijte <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody. Tato metoda vyvolá <xref:System.Threading.ThreadAbortException> ve vlákně, na kterém je vyvolána. Další informace najdete v tématu [zničení vláken](destroying-threads.md).

Od verze rozhraní .NET Framework 4, můžete použít <xref:System.Threading.CancellationToken?displayProperty=nameWithType> kooperativně zrušit vlákno. Další informace najdete v tématu [spolupráce při rušení vláken](canceling-threads-cooperatively.md).

Použití <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda aby volající vlákno, počkejte ukončení vlákna, na kterém je metoda vyvolána.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Postupy: pozastavení nebo přerušení vlákna

Můžete použít <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metody pozastaví aktuální vlákno pro určenou dobu. Blokovaná vlákna můžete přerušit voláním <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody. Další informace najdete v tématu [pozastavení a přerušení vlákna](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Vlastnosti vlákna

Následující tabulka uvádí některé z <xref:System.Threading.Thread> vlastnosti:  
  
|Vlastnost|Popis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Vrátí `true` Pokud vlákno byla spuštěna a nebylo dosud byl korektně ukončen nebo bylo přerušeno.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Získá nebo nastaví logickou hodnotu, která označuje, zda je podproces vlákna na pozadí. Vlákna na pozadí jsou podobné vláken v popředí, ale vlákno na pozadí nezabrání proces zastavení. Jakmile všechna vlákna na popředí, které patří k procesu zastavený, modul common language runtime ukončí proces voláním <xref:System.Threading.Thread.Abort%2A> metoda na pozadí podprocesů, které jsou stále aktivní. Další informace najdete v tématu [popředí a pozadí podprocesů](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Získá nebo nastaví název vlákna. Nejčastěji používá ke zjišťování jednotlivá vlákna při ladění.|  
|<xref:System.Threading.Thread.Priority%2A>|Získá nebo nastaví <xref:System.Threading.ThreadPriority> hodnotu, která se používá v operačním systému k určení priority plánování vláken. Další informace najdete v tématu [plánování vláken](scheduling-threads.md) a <xref:System.Threading.ThreadPriority> odkaz.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Získá <xref:System.Threading.ThreadState> hodnotu obsahující aktuální stavy vlákna.|  

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread?displayProperty=nameWithType>  
- [Vlákna a dělení na vlákna](threads-and-threading.md)  
- [Paralelní programování](../parallel-programming/index.md)  
