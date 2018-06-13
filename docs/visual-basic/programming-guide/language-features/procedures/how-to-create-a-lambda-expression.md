---
title: 'Postupy: Vytvoření výrazu lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653543"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Postupy: Vytvoření výrazu lambda (Visual Basic)
A *výrazu lambda* je funkce nebo podprogramu, který nemá název. Výraz lambda lze použít bez ohledu na typ delegáta je platný.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Chcete-li vytvořit funkci výrazu lambda jeden řádek  
  
1.  V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:  
  
     `Dim add1 =`   `Function`  
  
2.  V závorkách přímo po `Function`, zadejte parametry funkce. Všimněte si, že nezadáte název po `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Následující seznam parametrů zadejte jako text funkce jeden výraz. Hodnota, která je výsledkem výrazu je hodnota vráceným funkcí. Nepoužívejte `As` klauzule zadat návratový typ.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Můžete pro volání výrazu lambda předávání v argument celé číslo.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Alternativně stejného výsledku se dosahuje prostřednictvím v následujícím příkladu:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Chcete-li vytvořit podprogramu výrazu lambda jeden řádek  
  
1.  V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Sub`  
  
2.  V závorkách přímo po `Sub`, parametry podprogramu typu. Všimněte si, že nezadáte název po `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Následující seznam parametrů zadejte jako text podprogramu jeden příkaz.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Můžete pro volání výrazu lambda předávání v argument řetězce.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Chcete-li vytvořit výraz funkce Víceřádkový lambda  
  
1.  V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.  
  
     `Dim add1 =`   `Function`  
  
2.  V závorkách přímo po `Function`, zadejte parametry funkce. Všimněte si, že nezadáte název po `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Stiskněte klávesu ENTER. `End Function` Je automaticky přidán příkaz.  
  
4.  V hlavní funkce přidejte následující kód k vytvoření výrazu a vrátí hodnotu. Nepoužívejte `As` klauzule zadat návratový typ.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Můžete pro volání výrazu lambda předávání v argument celé číslo.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Chcete-li vytvořit výraz podprogramu Víceřádkový lambda  
  
1.  V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:  
  
     `Dim add1 =`   `Sub`  
  
2.  V závorkách přímo po `Sub`, parametry podprogramu typu. Všimněte si, že nezadáte název po `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Stiskněte klávesu ENTER. `End Sub` Je automaticky přidán příkaz.  
  
4.  V hlavní funkce přidejte následující kód provést při vyvolání podprogramu.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Můžete pro volání výrazu lambda předávání v argument řetězce.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Příklad  
 Běžné použití výrazů lambda je určit funkce, které lze předat ve jako argument pro parametr s jiným typem `Delegate`. V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> metoda vrátí pole procesů spuštěných v místním počítači. <xref:System.Linq.Enumerable.Where%2A> Metoda z <xref:System.Linq.Enumerable> vyžaduje třídy `Boolean` delegovat jako její argument. Výraz lambda v příkladu se používá k tomuto účelu. Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty, které jsou vybrány v `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 Předchozí příklad je ekvivalentní následující kód, který je napsána v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxe:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable>  
 [Výrazy lambda](./lambda-expressions.md)  
 [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Postupy: předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
