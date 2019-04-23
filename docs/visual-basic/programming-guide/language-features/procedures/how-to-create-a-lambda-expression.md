---
title: 'Postupy: Vytvoření výrazu Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344543"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Postupy: Vytvoření výrazu Lambda (Visual Basic)
A *výraz lambda* je funkce nebo podprogramu, který nemá název. Výraz lambda je možné bez ohledu na typ delegáta je platný.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Vytvořit funkci výraz lambda jednořádkového  
  
1. V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:  
  
     `Dim add1 =`   `Function`  
  
2. V závorkách přímo po `Function`, zadejte parametry funkce. Všimněte si, že nezadáte název po `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Následující seznam parametrů zadejte jeden výraz jako tělo funkce. Výraz je vyhodnocen jako hodnota je hodnota vrácená funkcí. Je velmi riskantní používat `As` klauzule k určení návratového typu.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Můžete pro volání výrazu lambda předáním celočíselný argument.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Případně stejného výsledku lze dosáhnout v následujícím příkladu:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Chcete-li vytvořit výraz lambda jednořádkového podprogram  
  
1. V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Sub`  
  
2. V závorkách přímo po `Sub`, typ parametrů volanému podprogramu. Všimněte si, že nezadáte název po `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Následující seznam parametrů zadejte jako text podprogramu jeden příkaz.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Můžete pro volání výrazu lambda předáním jako argument řetězec.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>K vytvoření víceřádkového výrazu lambda výraz funkce  
  
1. V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Function`  
  
2. V závorkách přímo po `Function`, zadejte parametry funkce. Všimněte si, že nezadáte název po `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Stiskněte klávesu ENTER. `End Function` Je automaticky přidán příkaz.  
  
4. V těle funkce přidejte následující kód k vytvoření výrazu a vrátí hodnotu. Je velmi riskantní používat `As` klauzule k určení návratového typu.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Můžete pro volání výrazu lambda předáním celočíselný argument.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>K vytvoření víceřádkového výrazu lambda výraz podprogram  
  
1. V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:  
  
     `Dim add1 =`   `Sub`  
  
2. V závorkách přímo po `Sub`, typ parametrů volanému podprogramu. Všimněte si, že nezadáte název po `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Stiskněte klávesu ENTER. `End Sub` Je automaticky přidán příkaz.  
  
4. V těle funkce přidejte následující kód pro spuštění při vyvolání podprogramu.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Můžete pro volání výrazu lambda předáním jako argument řetězec.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Příklad  
 Běžné použití výrazů lambda je definice funkce, které lze předat jako argument pro parametr, jehož typ je `Delegate`. V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> metoda vrátí pole z procesů spuštěných na místním počítači. <xref:System.Linq.Enumerable.Where%2A> Metodu z <xref:System.Linq.Enumerable> vyžaduje třídu `Boolean` jako svůj argument. Výraz lambda v příkladu se používá pro tento účel. Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Předchozí příklad je ekvivalentní následující kód, který je napsán v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxi:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Enumerable>
- [Výrazy lambda](./lambda-expressions.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
