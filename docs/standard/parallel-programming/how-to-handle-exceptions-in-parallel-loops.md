---
title: 'Postupy: Zpracování výjimek v paralelních smyčkách'
description: Naučte se zpracovávat výjimky v paralelních smyčkách v .NET. Podívejte se na příklad, jak zabalit všechny výjimky ze smyčky v System. AggregateException.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 61c22d6e82282f8aeb54818c813d4489e3bc9641
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768973"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Postupy: Zpracování výjimek v paralelních smyčkách
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Přetížení a nemají <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> žádný zvláštní mechanismus pro zpracování výjimek, které mohou být vyvolány. V tomto ohledu se podobají regulárním `for` `foreach` cyklům a smyčkám ( `For` a `For Each` v Visual Basic); Neošetřená výjimka způsobí, že se smyčka ukončí ihned po dokončení všech aktuálně spuštěných iterací.
  
 Když přidáte vlastní logiku zpracování výjimek do paralelních smyček, zpracujte případ, ve kterém mohou být podobné výjimky vyvolány na více vláknech současně, a případ, ve kterém výjimka vyvolaná v jednom vlákně způsobí vyvolání jiné výjimky v jiném vlákně. Oba případy můžete zpracovat tak, že zabalíte všechny výjimky ze smyčky v <xref:System.AggregateException?displayProperty=nameWithType> . Následující příklad ukazuje jeden možný přístup.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v následujícím příkladu. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou zachyceny všechny výjimky a poté zabaleny do, <xref:System.AggregateException?displayProperty=nameWithType> který je vyvolána. Volající může rozhodnout, jaké výjimky se mají zpracovat.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)
