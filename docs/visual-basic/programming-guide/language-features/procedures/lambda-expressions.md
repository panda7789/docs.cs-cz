---
title: Lambda – výrazy
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249666"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda – výrazy (Visual Basic)

Výraz *lambda* je funkce nebo podprogram bez názvu, který lze použít všude tam, kde je platný delegát. Lambda výrazy mohou být funkce nebo podprogramy a může být jednořádkové nebo víceřádkové. Hodnoty z aktuálního oboru můžete předat výrazu lambda.

> [!NOTE]
> Příkaz `RemoveHandler` je výjimkou. Výraz lambda nelze předat pro parametr `RemoveHandler`delegáta aplikace .

Výrazy lambda vytvoříte `Function` pomocí `Sub` klíčového slova nebo, stejně jako vytvoříte standardní funkci nebo podprogram. Však lambda výrazy jsou zahrnuty v příkazu.

Následující příklad je lambda výraz, který zintenzivňuje jeho argument a vrátí hodnotu. Příklad ukazuje jednořádkovou i víceřádkovou syntaxi výrazu lambda pro funkci.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

Následující příklad je lambda výraz, který zapisuje hodnotu do konzoly. Příklad ukazuje jednořádkovou i víceřádkovou syntaxi výrazu lambda pro podprogram.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Všimněte si, že v předchozích příkladech lambda výrazy jsou přiřazeny k názvu proměnné. Vždy, když odkazujete na proměnnou, vyvoláte výraz lambda. Můžete také deklarovat a vyvolat výraz lambda současně, jak je znázorněno v následujícím příkladu.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Výraz lambda může být vrácen jako hodnota volání funkce (jak je znázorněno v příkladu v části [Kontext](#context) dále v tomto tématu) nebo předán jako argument parametru, který přebírá typ delegáta, jak je znázorněno v následujícím příkladu.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda

Syntaxe výrazu lambda se podobá standardní funkci nebo podprogramu. Rozdíly jsou následující:

- Výraz lambda nemá název.

- Lambda výrazy nemohou mít modifikátory, například `Overloads` nebo `Overrides`.

- Jednořádkové funkce lambda nepoužívají `As` klauzuli k označení návratového typu. Místo toho je typ odvozen z hodnoty, kterou tělo výrazu lambda vyhodnotí. Například pokud je `cust.City = "London"`tělo výrazu lambda , `Boolean`jeho návratový typ je .

- Ve víceřádkové funkce lambda můžete buď určit návratový typ pomocí `As` klauzule, nebo vynechat `As` klauzuli tak, aby byl odvozen návratový typ. Pokud `As` je klauzule vynechána pro víceřádkovou funkci lambda, návratový typ je `Return` odvozen jako dominantní typ ze všech příkazů ve funkci lambda více řádků. *Dominantní typ* je jedinečný typ, který všechny ostatní typy lze rozšířit. Pokud tento jedinečný typ nelze určit, dominantní typ je jedinečný typ, který všechny ostatní typy v poli lze zúžit. Pokud nelze určit ani jeden z těchto jedinečných typů, dominantní typ je `Object`. V tomto případě, `Option Strict` pokud `On`je nastavena na , dojde k chybě kompilátoru.

     Pokud například výrazy zadané `Return` do příkazu `Integer`obsahují `Long`hodnoty `Double`typu , a , `Double`výsledné pole je typu . Oba `Integer` `Long` a `Double` rozšířit `Double`na a pouze . Proto `Double` je dominantní typ. Další informace naleznete v [tématu Rozšíření a zúžení převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Tělo jednořádkové funkce musí být výraz, který vrací hodnotu, nikoli příkaz. Neexistuje žádný `Return` příkaz pro jednořádkové funkce. Hodnota vrácená jednořádkovou funkcí je hodnota výrazu v těle funkce.

- Tělo jednořádkové podprogramu musí být jednořádkové prohlášení.

- Jednořádkové funkce a podprogramy `End Function` neobsahují `End Sub` příkaz nebo.

- Můžete určit datový typ parametru výrazu lambda pomocí klíčového `As` slova nebo lze odvodit datový typ parametru. Všechny parametry musí mít zadané datové typy nebo všechny musí být odvozeny.

- `Optional`a `Paramarray` parametry nejsou povoleny.

- Obecné parametry nejsou povoleny.

## <a name="async-lambdas"></a>Asynchronní lambdy

Můžete snadno vytvořit lambda výrazy a příkazy, které zahrnují asynchronní zpracování pomocí klíčová slova [Async](../../../../visual-basic/language-reference/modifiers/async.md) a [Await Operator.](../../../../visual-basic/language-reference/operators/await-operator.md) Například následující příklad windows forms obsahuje obslužnou rutinu události, `ExampleMethodAsync`která volá a čeká na asynchronní metodu .

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Můžete přidat stejnou obslužnou rutinu události pomocí asynchronní lambda v [AddHandler prohlášení](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Chcete-li přidat tuto `Async` obslužnou rutinu, přidejte modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Další informace o vytváření a používání asynchronních metod naleznete [v tématu Asynchronní programování s async a Await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Kontext

Výraz lambda sdílí svůj kontext s oborem, ve kterém je definován. Má stejná přístupová práva jako jakýkoli kód napsaný v obsahujícím oboru. To zahrnuje přístup k členským proměnným, `Me`funkcím a subs , a parametrům a místním proměnným v obsahujícím oboru.

Přístup k místním proměnným a parametrům v obsahujícím oboru může přesáhnout dobu životnosti tohoto oboru. Tak dlouho, dokud delegát odkazující na výraz lambda není k dispozici pro uvolňování paměti, přístup k proměnným v původním prostředí je zachována. V následujícím příkladu `target` je `makeTheGame`proměnná local to , metoda, ve které je definován výraz `playTheGame` lambda. Všimněte si, že vrácený `takeAGuess` výraz `Main`lambda přiřazený `target`v , má stále přístup k místní proměnné .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Následující příklad ukazuje širokou škálu přístupových práv vnořeného výrazu lambda. Při vrácené lambda výraz `Main` je `aDel`spuštěn z as , přistupuje k těmto prvkům:

- Pole třídy, ve které je definováno:`aField`

- Vlastnost třídy, ve které je definována:`aProp`

- Parametr metody `functionWithNestedLambda`, ve kterém je definován:`level1`

- Místní proměnná `functionWithNestedLambda`:`localVar`

- Parametr výrazu lambda, ve kterém je vnořen:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Převod na typ delegáta

Výraz lambda lze implicitně převést na kompatibilní typ delegáta. Informace o obecných požadavcích na kompatibilitu naleznete v [tématu Uvolněný převod delegátů](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Například následující příklad kódu ukazuje výraz lambda, který `Func(Of Integer, Boolean)` implicitně převádí nebo odpovídající podpis delegáta.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Následující příklad kódu ukazuje výraz lambda, který `Sub(Of Double, String, Double)` implicitně převádí nebo odpovídající podpis delegáta.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Při přiřazení lambda výrazy delegátům nebo předat jako argumenty procedur, můžete zadat názvy parametrů, ale vynechat jejich datové typy, nechat typy převzaty z delegáta.

## <a name="examples"></a>Příklady

- Následující příklad definuje výraz lambda, `True` který vrátí, pokud argument typu hodnoty `False` s možnou hodnotou s možnou hodnotou má přiřazenou hodnotu a pokud je `Nothing`jeho hodnota .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Následující příklad definuje výraz lambda, který vrací index posledního prvku v poli.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Představení technologie LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegáty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Postupy: Vytvoření výrazu lambda](./how-to-create-a-lambda-expression.md)
- [Volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
