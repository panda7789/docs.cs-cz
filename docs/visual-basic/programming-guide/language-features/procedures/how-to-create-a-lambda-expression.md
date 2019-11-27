---
title: 'Postupy: Vytvoření výrazu lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: bb0bdb3c10a7df2ca954fbdb9382a25bf805068d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349744"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Postupy: Vytvoření výrazu lambda (Visual Basic)
*Výraz lambda* je funkce nebo podprogram, který nemá název. Výraz lambda lze použít všude, kde je typ delegáta platný.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Vytvoření jednořádkové funkce výrazu lambda na jednom řádku  
  
1. V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:  
  
     `Dim add1 =`   `Function`  
  
2. V závorkách přímo po `Function`zadejte parametry funkce. Všimněte si, že po `Function`neurčíte název.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Po seznamu parametrů zadejte jako tělo funkce jeden výraz. Hodnota, na kterou se výraz vyhodnocuje, je hodnota vrácená funkcí. K určení návratového typu nepoužíváte klauzuli `As`.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Výraz lambda zavoláte předáním celočíselného argumentu.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Stejný výsledek lze také provést pomocí následujícího příkladu:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Vytvoření dílčí rutiny lambda výrazu na jednom řádku  
  
1. V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Sub`  
  
2. V závorkách přímo po `Sub`zadejte parametry subrutiny. Všimněte si, že po `Sub`neurčíte název.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Po seznamu parametrů zadejte jeden příkaz jako tělo dílčí rutiny.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Výraz lambda zavoláte předáním argumentu řetězce.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Vytvoření víceřádkové funkce výrazu lambda  
  
1. V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Function`  
  
2. V závorkách přímo po `Function`zadejte parametry funkce. Všimněte si, že po `Function`neurčíte název.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Stiskněte klávesu ENTER. Příkaz `End Function` je automaticky přidán.  
  
4. V těle funkce přidejte následující kód, který vytvoří výraz a vrátí hodnotu. K určení návratového typu nepoužíváte klauzuli `As`.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Výraz lambda zavoláte předáním celočíselného argumentu.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Vytvoření víceřádkové subrutiny výrazu lambda  
  
1. V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:  
  
     `Dim add1 =`   `Sub`  
  
2. V závorkách přímo po `Sub`zadejte parametry subrutiny. Všimněte si, že po `Sub`neurčíte název.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Stiskněte klávesu ENTER. Příkaz `End Sub` je automaticky přidán.  
  
4. V těle funkce přidejte následující kód, který se spustí při vyvolání podrutiny.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Výraz lambda zavoláte předáním argumentu řetězce.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Příklad  
 Běžné použití výrazů lambda je definovat funkci, která může být předána jako argument pro parametr, jehož typ je `Delegate`. V následujícím příkladu metoda <xref:System.Diagnostics.Process.GetProcesses%2A> vrátí pole procesů spuštěných v místním počítači. Metoda <xref:System.Linq.Enumerable.Where%2A> z <xref:System.Linq.Enumerable> třídy vyžaduje jako argument delegáta `Boolean`. Výraz lambda v příkladu se používá pro tento účel. Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Předchozí příklad je ekvivalentní následujícímu kódu, který je napsán v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxe:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Enumerable>
- [Výrazy lambda](./lambda-expressions.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Postupy: Předání procedur jinému postupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
