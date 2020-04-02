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
ms.openlocfilehash: 5ccddfb01d6b173900dfffc465292c7812626ddc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587991"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Postupy: Zpracování výjimek v dotazu PLINQ

První příklad v tomto tématu <xref:System.AggregateException?displayProperty=nameWithType> ukazuje, jak zpracovat, které mohou být vyvolány z dotazu PLINQ při spuštění. Druhý příklad ukazuje, jak umístit try-catch bloky v rámci delegátů, co nejblíže k kde bude vyvolána výjimka. Tímto způsobem můžete zachytit, jakmile k nim dojde a případně pokračovat v provádění dotazu. Pokud jsou povoleny výjimky bubliny zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek po vyvolání výjimky.

V některých případech, kdy PLINQ přejde zpět na sekvenční spuštění a dojde k výjimce, může být výjimka šířena přímo a není zabalena do . <xref:System.AggregateException> Také <xref:System.Threading.ThreadAbortException>s jsou vždy šířeny přímo.

> [!NOTE]
> Pokud je povolena možnost "Pouze můj kód", Visual Studio se přeruší na řádku, který vyvolá výjimku a zobrazí chybovou zprávu s textem "výjimka není zpracována uživatelským kódem". Tato chyba je neškodná. Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.
>
> Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak umístit try-catch bloky kolem kódu, <xref:System.AggregateException?displayProperty=nameWithType>který spustí dotaz zachytit všechny s, které jsou vyvolány.

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

V tomto příkladu dotaz nemůže pokračovat po vyvolání výjimky. V době, kdy kód aplikace zachytí výjimku, PLINQ již zastavil dotaz na všechna vlákna.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak umístit blok try-catch v delegátovi, aby bylo možné zachytit výjimku a pokračovat v provádění dotazu.

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

- Chcete-li zkompilovat a spustit tyto příklady, zkopírujte je do příkladu ukázky dat PLINQ a volání metody z Main.

## <a name="robust-programming"></a>Robustní programování

Nezachycujte výjimku, pokud nevíte, jak ji zpracovat, abyste nepoškodili stav programu.

## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
