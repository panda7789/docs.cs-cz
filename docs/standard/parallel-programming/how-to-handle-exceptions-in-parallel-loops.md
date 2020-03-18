---
title: 'Postupy: Zpracování výjimek v paralelních smyčkách'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453010"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Postupy: Zpracování výjimek v paralelních smyčkách
A <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> přetížení nemají žádný zvláštní mechanismus pro zpracování výjimek, které mohou být vyvolány. V tomto ohledu se `for` `foreach` podobají`For` `For Each` pravidelné a smyčky ( a v jazyce Visual Basic); neošetřená výjimka způsobí, že smyčka bude ukončena, jakmile dokončí všechny aktuálně spuštěné iterace.
  
 Přidáte-li vlastní logiku zpracování výjimek do paralelnísmyčky, zpracování případu, ve kterém podobné výjimky mohou být vyvolány na více vláken současně a v případě, ve kterém výjimka vyvolána na jednom vlákně způsobí, že další výjimku vyvolat na jiném Vlákno. Oba případy můžete zpracovat zabalením všech <xref:System.AggregateException?displayProperty=nameWithType>výjimek ze smyčky v . Následující příklad ukazuje jeden možný přístup.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladu níže. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou všechny výjimky zachyceny a poté zabaleny do <xref:System.AggregateException?displayProperty=nameWithType> který je vyvolána. Volající může rozhodnout, které výjimky zpracovat.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
