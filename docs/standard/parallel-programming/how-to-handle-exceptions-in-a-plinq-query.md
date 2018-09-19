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
ms.openlocfilehash: 40b98e01d6c34fb01a1f508f2ea52309f2f7938b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989518"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Postupy: Zpracování výjimek v dotazu PLINQ
První příklad v tomto tématu ukazuje, jak zpracovat <xref:System.AggregateException?displayProperty=nameWithType> , které mohou být vyvolány z dotazu PLINQ při provádění. Druhý příklad ukazuje, jak vložit bloků try-catch v rámci delegáty, co nejblíže k kde bude vyvolána výjimka. Tímto způsobem může zachytit je co nejdříve, dojde k a případně pokračovat provádění dotazu. Pokud je výjimkám umožněn pokračovala zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.  
  
 V některých případech při PLINQ spadne zpět na sekvenční provádění a dojde k výjimce, výjimky může být rozšířena přímo a nejsou zabaleny v <xref:System.AggregateException>. Navíc <xref:System.Threading.ThreadAbortException>s nerozšíří vždy přímo.  
  
> [!NOTE]
>  Pokud je povoleno "Jen můj kód", Visual Studio na řádce, která výjimku a zobrazí chybovou zprávu, že "výjimka není ošetřena v uživatelském kódu." Tato chyba je neškodná. Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech. Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
>   
>  V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vložit bloků try-catch kolem kód, který provede daný dotaz k zachycení všech <xref:System.AggregateException?displayProperty=nameWithType>, které jsou vyvolány.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 V tomto příkladu dotaz nemůže pokračovat po vyvolání výjimky. Podle času kódu aplikace zachytí výjimku PLINQ již zastavil dotaz na všech vláknech.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vložit blok try-catch v delegátovi, aby bylo možné zachytit výjimku a pokračujte v provádění dotazu.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Kompilace a spuštění tyto příklady, zkopírujte je do příklad ukázková Data pro PLINQ a zavolejte metodu z hlavní.  
  
## <a name="robust-programming"></a>Robustní programování  
 Nezachycujte výjimky, pokud si nejste jisti, jak ji zpracovat tak, aby nedošlo k poškození stavu programu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>  
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
