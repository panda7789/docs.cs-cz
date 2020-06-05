---
title: 'Postupy: Vytvoření výrazu lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 7affc84fa501ba98bdfa93835f0b0e381580b9bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388384"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Postupy: Vytvoření výrazu lambda (Visual Basic)
*Výraz lambda* je funkce nebo podprogram, který nemá název. Výraz lambda lze použít všude, kde je typ delegáta platný.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Vytvoření jednořádkové funkce výrazu lambda na jednom řádku  
  
1. V jakékoli situaci, kdy může být použit typ delegáta, zadejte klíčové slovo `Function` , jak je uvedeno v následujícím příkladu:  
  
     `Dim add1 =`   `Function`  
  
2. V závorkách přímo za `Function` Zadejte parametry funkce. Všimněte si, že neurčíte název po `Function` .  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Po seznamu parametrů zadejte jako tělo funkce jeden výraz. Hodnota, na kterou se výraz vyhodnocuje, je hodnota vrácená funkcí. `As`K určení návratového typu nepoužíváte klauzuli.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Výraz lambda zavoláte předáním celočíselného argumentu.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Stejný výsledek lze také provést pomocí následujícího příkladu:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Vytvoření dílčí rutiny lambda výrazu na jednom řádku  
  
1. V jakékoli situaci, kdy lze použít typ delegáta, zadejte klíčové slovo `Sub` , jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Sub`  
  
2. V závorkách přímo po `Sub` Zadejte parametry subrutiny. Všimněte si, že neurčíte název po `Sub` .  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Po seznamu parametrů zadejte jeden příkaz jako tělo dílčí rutiny.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Výraz lambda zavoláte předáním argumentu řetězce.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Vytvoření víceřádkové funkce výrazu lambda  
  
1. V jakékoli situaci, kdy lze použít typ delegáta, zadejte klíčové slovo `Function` , jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Function`  
  
2. V závorkách přímo za `Function` Zadejte parametry funkce. Všimněte si, že neurčíte název po `Function` .  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Stiskněte ENTER. `End Function`Příkaz se přidá automaticky.  
  
4. V těle funkce přidejte následující kód, který vytvoří výraz a vrátí hodnotu. `As`K určení návratového typu nepoužíváte klauzuli.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Výraz lambda zavoláte předáním celočíselného argumentu.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Vytvoření víceřádkové subrutiny výrazu lambda  
  
1. V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Sub` , jak je znázorněno v následujícím příkladu:  
  
     `Dim add1 =`   `Sub`  
  
2. V závorkách přímo po `Sub` Zadejte parametry subrutiny. Všimněte si, že neurčíte název po `Sub` .  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Stiskněte ENTER. `End Sub`Příkaz se přidá automaticky.  
  
4. V těle funkce přidejte následující kód, který se spustí při vyvolání podrutiny.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Výraz lambda zavoláte předáním argumentu řetězce.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Příklad  
 Běžné použití výrazů lambda je definovat funkci, která může být předána jako argument pro parametr, jehož typ je `Delegate` . V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> Metoda vrátí pole procesů spuštěných v místním počítači. <xref:System.Linq.Enumerable.Where%2A>Metoda z <xref:System.Linq.Enumerable> třídy vyžaduje `Boolean` delegáta jako svůj argument. Výraz lambda v příkladu se používá pro tento účel. Vrátí se `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList` .  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Předchozí příklad je ekvivalentní následujícímu kódu, který je napsán v syntaxi LINQ (Language-Integrated Query):  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- [Výrazy lambda](./lambda-expressions.md)
- [Function – příkaz](../../../language-reference/statements/function-statement.md)
- [Sub – příkaz](../../../language-reference/statements/sub-statement.md)
- [Delegáti](../delegates/index.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate – příkaz](../../../language-reference/statements/delegate-statement.md)
- [Představení technologie LINQ v jazyce Visual Basic](../linq/introduction-to-linq.md)
