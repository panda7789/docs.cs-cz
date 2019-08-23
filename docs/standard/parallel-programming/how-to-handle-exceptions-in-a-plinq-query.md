---
title: 'Postupy: Zpracování výjimek v dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 416ed968d9fe2b7149c90fb6d1fa37547db735dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962514"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Postupy: Zpracování výjimek v dotazu PLINQ
První příklad v tomto tématu ukazuje <xref:System.AggregateException?displayProperty=nameWithType> , jak zpracovat, která může být vyvolána z dotazu PLINQ při jeho spuštění. Druhý příklad ukazuje, jak umístit bloky try-catch v rámci delegátů co nejblíže k, kde bude vyvolána výjimka. Tímto způsobem je můžete zachytit ihned po jejich výskytu a případně pokračovat v provádění dotazů. Pokud jsou výjimky povoleny k bublinám zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.  
  
 V některých případech, pokud se PLINQ vrátí zpět k sekvenčnímu provedení a dojde k výjimce, výjimka může být šířena přímo a není zabalena <xref:System.AggregateException>do. <xref:System.Threading.ThreadAbortException>Navíc se vždy šíří přímo.  
  
> [!NOTE]
> Když je povolená možnost Pouze můj kód, Visual Studio se na řádku, který vyvolá výjimku, přeruší a zobrazí se chybová zpráva s informacemi o tom, že výjimka není zpracována uživatelským kódem. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.  
>   
>  Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak umístit bloky try-catch kolem kódu, který spouští dotaz k zachycení všech <xref:System.AggregateException?displayProperty=nameWithType>vyvolaných s.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 V tomto příkladu nemůže dotaz pokračovat, i když je vyvolána výjimka. V době, kdy kód aplikace zachytí výjimku, PLINQ již zastavil dotaz na všech vláknech.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak umístit blok try-catch do delegáta pro zajištění, že je možné zachytit výjimku a pokračovat v provádění dotazu.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Chcete-li tyto příklady zkompilovat a spustit, zkopírujte je do ukázkového příkladu dat PLINQ a zavolejte metodu z Main.  
  
## <a name="robust-programming"></a>Robustní programování  
 Nezachyťte výjimku, Pokud nevíte, jak ji zpracovat, abyste nepoškodili stav programu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
