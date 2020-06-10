---
title: Použití vláken a dělení na vlákna
description: Seznamte se s používáním vláken a vláken v .NET, abyste mohli psát aplikace pro provádění mnoha operací ve stejnou dobu (multithreading).
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: c092994818c9105a555acaf63ceba4b8e99bcada
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663028"
---
# <a name="using-threads-and-threading"></a>Použití vláken a dělení na vlákna

Pomocí technologie .NET můžete psát aplikace, které provádějí více operací současně. Operace s potenciálním provozem jiných operací se můžou spouštět v samostatných vláknech, *což je proces* , který se označuje jako *vícevláknové nebo volné podprocesy*.  
  
Aplikace, které používají multithreading, mají větší reakci na uživatelský vstup, protože uživatelské rozhraní zůstává aktivní jako úlohy náročné na procesory spouštěné v samostatných vláknech. Multithreading je také užitečné při vytváření škálovatelných aplikací, protože je možné přidat vlákna při zvýšení zatížení.

> [!NOTE]
> Pokud potřebujete větší kontrolu nad chováním vláken aplikace, můžete spravovat vlákna sami. Počínaje .NET Framework 4 ale vícevláknové programování je výrazně zjednodušeno pomocí <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tříd a, [Paralelní LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), nové souběžné třídy kolekce v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů a nového programovacího modelu, který je založen na konceptu úkolů, nikoli na vláknech. Další informace naleznete v tématu [paralelní programování](../parallel-programming/index.md) a [Task PARALLEL Library (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Postupy: vytvoření a spuštění nového vlákna

Vytvoříte nové vlákno vytvořením nové instance <xref:System.Threading.Thread?displayProperty=nameWithType> třídy a zadáním názvu metody, kterou chcete spustit v novém vlákně konstruktoru. Chcete-li spustit vytvořené vlákno, zavolejte <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metodu. Další informace a příklady najdete v článku [vytváření vláken a předávání dat v čase spuštění](creating-threads-and-passing-data-at-start-time.md) a <xref:System.Threading.Thread> Reference k rozhraní API.

## <a name="how-to-stop-a-thread"></a>Postupy: zastavení vlákna

Chcete-li ukončit provádění vlákna, použijte <xref:System.Threading.CancellationToken?displayProperty=nameWithType> . Nabízí jednotný způsob, jak v družstvě zastavit vlákna. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md).

V některých případech není možné vlákno zastavovat spolupracuje, protože spouští kód třetí strany, který není navržen pro kooperativní zrušení. V takovém případě může být vhodné ukončit provádění jeho vynuceně. Chcete-li ukončit provádění vlákna vynuceně, v .NET Framework můžete použít <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodu. Tato metoda vyvolává <xref:System.Threading.ThreadAbortException> ve vlákně, ve kterém je vyvolána. Další informace naleznete v tématu [zničení vláken](destroying-threads.md). <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda není v rozhraní .NET Core podporována. Pokud potřebujete ukončit provádění kódu třetí strany vynuceně v .NET Core, spusťte ho v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

<xref:System.Threading.CancellationToken?displayProperty=nameWithType>Není k dispozici před .NET Framework 4. Chcete-li zastavit vlákno ve starších verzích .NET Framework, měli byste implementovat kooperativní zrušení ručně pomocí technik synchronizace vláken. Můžete například vytvořit pole volatile Boolean `shouldStop` a použít ho k vyžádání kódu spuštěného vláknem k zastavení. Další informace naleznete v tématu [volatile](../../csharp/language-reference/keywords/volatile.md) v jazyce C# Reference a <xref:System.Threading.Volatile?displayProperty=nameWithType> .

Použijte <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metodu, aby volající vlákno čekalo na ukončení zastaveného vlákna.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Postupy: pozastavení nebo přerušení vlákna

Použijte <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metodu pro pozastavení aktuálního vlákna po zadanou dobu. Blokované vlákno lze přerušit voláním <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody. Další informace najdete v tématu [pozastavení a přerušení vláken](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Vlastnosti vlákna

Následující tabulka uvádí některé z <xref:System.Threading.Thread> vlastností:  
  
|Vlastnost|Popis|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Vrátí, `true` zda bylo vlákno spuštěno a dosud nebylo ukončeno normální nebo přerušeno.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Získá nebo nastaví logickou hodnotu, která označuje, zda se jedná o vlákno na pozadí. Vlákna na pozadí jsou jako vlákna na popředí, ale vlákno na pozadí nezabrání procesu v jeho zastavení. Po zastavení všech vláken na popředí, která patří do procesu, ukončí modul CLR (Common Language Runtime) proces voláním <xref:System.Threading.Thread.Abort%2A> metody na vláknech na pozadí, které jsou stále aktivní. Další informace naleznete v tématu [vlákna v popředí a na pozadí](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Získá nebo nastaví název vlákna. Nejčastěji se používá ke zjišťování jednotlivých vláken při ladění.|  
|<xref:System.Threading.Thread.Priority%2A>|Získá nebo nastaví <xref:System.Threading.ThreadPriority> hodnotu, která je používána operačním systémem k určení priorit plánování vláken. Další informace naleznete v tématu [plánování vláken](scheduling-threads.md) a <xref:System.Threading.ThreadPriority> reference.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Získá <xref:System.Threading.ThreadState> hodnotu obsahující aktuální stavy vlákna.|  

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Paralelní programování](../parallel-programming/index.md)
