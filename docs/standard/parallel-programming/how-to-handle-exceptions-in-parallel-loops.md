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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ba240d71287be91bd0b4b40a2cb69f6e2808d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Postupy: Zpracování výjimek v paralelních smyčkách
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> přetížení nemají žádný zvláštní mechanismus zpracování výjimek, které mohou být vyvolány. V tomto ohledu se podobají normálním `for` a `foreach` smyčky (`For` a `For Each` v jazyce Visual Basic); k neošetřené výjimce způsobí, že smyčky ukončit okamžitě.  
  
 Když přidáte vlastní logiku zpracování výjimek a paralelní smyčky, zpracovávat tento případ, ve kterém může být podobné výjimky vyvolány ve více vláknech souběžně a tento případ, ve kterém výjimce na jedno vlákno způsobí, že jiné na jiném vyvolání výjimky přístup z více vláken. Obou případech může zpracovávat všechny výjimky z smyčky v zabalení <xref:System.AggregateException?displayProperty=nameWithType>. Následující příklad ukazuje jeden možný přístup.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, který je znázorněn v následujícím příkladu. Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou všechny výjimky zachycení a pak uzavřen do <xref:System.AggregateException?displayProperty=nameWithType> která je vyvolána. Volající můžete rozhodnout, které výjimky zpracovat.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
