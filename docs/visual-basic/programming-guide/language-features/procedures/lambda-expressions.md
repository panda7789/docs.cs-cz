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
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406700"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda – výrazy (Visual Basic)

*Výraz lambda* je funkce nebo podrutina bez názvu, který lze použít všude, kde je delegát platný. Výrazy lambda mohou být funkce nebo podprocesy a mohou být jednořádkové nebo víceřádkové. Můžete předat hodnoty z aktuálního oboru do výrazu lambda.

> [!NOTE]
> `RemoveHandler`Příkaz je výjimka. Do parametru Delegate v nelze předat výraz lambda `RemoveHandler` .

Výrazy lambda lze vytvořit pomocí `Function` `Sub` klíčového slova or, stejně jako při vytváření standardní funkce nebo podprocesu. Výrazy lambda jsou však zahrnuty v příkazu.

Následující příklad je výraz lambda, který zvyšuje svůj argument a vrací hodnotu. V příkladu se zobrazí jak jednoduchá čára, tak víceřádková syntaxe výrazu lambda pro funkci.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

Následující příklad je výraz lambda, který zapisuje hodnotu do konzoly. V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro podprogram.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Všimněte si, že v předchozích příkladech jsou výrazy lambda přiřazeny názvu proměnné. Vždy, když odkazujete na proměnnou, vyvoláte výraz lambda. Můžete také deklarovat a vyvolat výraz lambda ve stejnou dobu, jak je znázorněno v následujícím příkladu.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Výraz lambda lze vrátit jako hodnotu volání funkce (jak je uvedeno v příkladu v [kontextu](#context) dále v tomto tématu), nebo předaný jako argument parametru, který přebírá typ delegáta, jak je znázorněno v následujícím příkladu.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda

Syntaxe výrazu lambda se podobá funkci standardní funkce nebo dílčí rutiny. Rozdíly jsou následující:

- Výraz lambda nemá název.

- Výrazy lambda nemůžou mít modifikátory, například `Overloads` nebo `Overrides` .

- Jednořádkové funkce lambda nepoužívají `As` klauzuli k určení návratového typu. Místo toho je typ odvozen z hodnoty, na kterou je text výrazu lambda vyhodnocen. Například, pokud je tělo výrazu lambda `cust.City = "London"` , je jeho návratový typ `Boolean` .

- Ve víceřádkových lambda funkcích můžete buď zadat návratový typ pomocí `As` klauzule, nebo vynechat `As` klauzuli tak, aby byl návratový typ odvozený. Je-li `As` pro víceřádkovou funkci lambda vynechána klauzule, návratový typ je odvozen jako dominantní typ ze všech `Return` příkazů ve víceřádkové funkci lambda. *Dominantní typ* je jedinečný typ, na který se mohou rozšířit všechny ostatní typy. Pokud tento jedinečný typ nelze určit, dominantní typ je jedinečný typ, který mohou být pro všechny ostatní typy v poli zúženy. Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object` . V takovém případě, pokud `Option Strict` je nastaveno na `On` , dojde k chybě kompilátoru.

     Například pokud výrazy dodané do `Return` příkazu obsahují hodnoty typu `Integer` , `Long` , a `Double` výsledné pole je typu `Double` . `Integer`A `Long` Rozšiřte je i na `Double` `Double` . Proto `Double` je dominantní typ. Další informace najdete v tématu [rozšiřování a zúžení převodů](../data-types/widening-and-narrowing-conversions.md).

- Tělo funkce s jednou řádkou musí být výraz, který vrací hodnotu, nikoli příkaz. `Return`Pro vložené funkce neexistuje žádný příkaz. Hodnota vrácená funkcí single-line je hodnota výrazu v těle funkce.

- Tělo jednořádkového podprocesu musí být jednořádkový příkaz.

- Jednořádkové funkce a podrutiny nezahrnují `End Function` `End Sub` příkaz or.

- Můžete zadat datový typ parametru výrazu lambda pomocí `As` klíčového slova, nebo datový typ parametru lze odvodit. Buď musí mít všechny parametry zadané datové typy, nebo musí být všechny odvoditelné.

- `Optional``Paramarray`parametry a nejsou povolené.

- Obecné parametry nejsou povolené.

## <a name="async-lambdas"></a>Asynchronní lambdy

Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../../language-reference/modifiers/async.md) a [await](../../../language-reference/operators/await-operator.md) . Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync` .

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

Můžete přidat stejnou obslužnou rutinu události pomocí asynchronní lambda v [příkazu AddHandler](../../../language-reference/statements/addhandler-statement.md). Chcete-li přidat tuto obslužnou rutinu, přidejte `Async` Modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.

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

Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../concepts/async/index.md).

## <a name="context"></a>Kontext

Výraz lambda sdílí svůj kontext s oborem, ve kterém je definován. Má stejná přístupová práva jako jakýkoli kód napsaný v nadřazeném oboru. To zahrnuje přístup k proměnným členů, funkcím, `Me` parametrům a parametrům a místním proměnným v nadřazeném oboru.

Přístup k lokálním proměnným a parametrům v rámci nadřazeného oboru může přesáhnout dobu života tohoto oboru. Dokud nebude delegát odkazující na výraz lambda dostupný pro uvolňování paměti, bude zachován přístup k proměnným v původním prostředí. V následujícím příkladu `target` je proměnná lokální pro `makeTheGame` , metodu, ve které `playTheGame` je definován výraz lambda. Všimněte si, že vrácený výraz lambda přiřazený `takeAGuess` v v `Main` má stále přístup k místní proměnné `target` .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Následující příklad ukazuje široké spektrum přístupových práv vnořeného výrazu lambda. Když je vrácený výraz lambda proveden z `Main` as `aDel` , přistupuje k těmto prvkům:

- Pole třídy, ve které je definováno:`aField`

- Vlastnost třídy, ve které je definována:`aProp`

- Parametr metody `functionWithNestedLambda` , ve které je definována:`level1`

- Místní proměnná `functionWithNestedLambda` :`localVar`

- Parametr výrazu lambda, ve kterém je vnořený:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Převod na typ delegáta

Výraz lambda lze implicitně převést na kompatibilní typ delegáta. Informace o obecných požadavcích na kompatibilitu naleznete v tématu [odlehčený převod delegáta](../delegates/relaxed-delegate-conversion.md). Například následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající signaturu delegáta.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající signaturu delegáta.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Pokud přiřadíte výrazy lambda delegátům nebo je předáte jako argumenty procedurám, můžete zadat názvy parametrů, ale vynechat jejich datové typy, aby bylo možné typy přenášet z delegáta.

## <a name="examples"></a>Příklady

- Následující příklad definuje výraz lambda, který se vrátí, `True` Pokud argument typu hodnoty Nullable má přiřazenou hodnotu, a `False` Pokud je jeho hodnota `Nothing` .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Následující příklad definuje výraz lambda, který vrátí index posledního prvku v poli.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Představení technologie LINQ v jazyce Visual Basic](../linq/introduction-to-linq.md)
- [Delegáti](../delegates/index.md)
- [Function – příkaz](../../../language-reference/statements/function-statement.md)
- [Sub – příkaz](../../../language-reference/statements/sub-statement.md)
- [Typy hodnot s možnou hodnotou null](../data-types/nullable-value-types.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Postupy: Vytvoření výrazu lambda](./how-to-create-a-lambda-expression.md)
- [Volný převod delegáta](../delegates/relaxed-delegate-conversion.md)
