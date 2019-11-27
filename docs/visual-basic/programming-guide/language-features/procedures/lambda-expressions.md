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
ms.openlocfilehash: f3f963167e1b3633cc5fe6e1f435e374cd272cce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345979"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda – výrazy (Visual Basic)

*Výraz lambda* je funkce nebo podrutina bez názvu, který lze použít všude, kde je delegát platný. Výrazy lambda mohou být funkce nebo podprocesy a mohou být jednořádkové nebo víceřádkové. Můžete předat hodnoty z aktuálního oboru do výrazu lambda.

> [!NOTE]
> Příkaz `RemoveHandler` je výjimka. Do parametru Delegate `RemoveHandler`nelze předat výraz lambda.

Lambda výrazy vytvoříte pomocí klíčového slova `Function` nebo `Sub` stejným způsobem jako při vytváření standardní funkce nebo podrutiny. Výrazy lambda jsou však zahrnuty v příkazu.

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

- Výrazy lambda nemůžou mít modifikátory, jako je `Overloads` nebo `Overrides`.

- Jednořádkové funkce lambda nepoužívají klauzuli `As` k určení návratového typu. Místo toho je typ odvozen z hodnoty, na kterou je text výrazu lambda vyhodnocen. Například pokud je tělo výrazu lambda `cust.City = "London"`, je jeho návratový typ `Boolean`.

- Ve víceřádkových lambda funkcích můžete buď zadat návratový typ pomocí klauzule `As`, nebo vynechat klauzuli `As`, aby se návratový typ odvodil. Pokud je u víceřádkové funkce lambda vynechána klauzule `As`, návratový typ je odvozený jako dominantní typ ze všech příkazů `Return` ve víceřádkové funkci lambda. *Dominantní typ* je jedinečný typ, na který se mohou rozšířit všechny ostatní typy. Pokud tento jedinečný typ nelze určit, dominantní typ je jedinečný typ, který mohou být pro všechny ostatní typy v poli zúženy. Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object`. V takovém případě, pokud je `Option Strict` nastaveno na `On`, dojde k chybě kompilátoru.

     Například pokud výrazy dodané do příkazu `Return` obsahují hodnoty typu `Integer`, `Long`a `Double`, výsledné pole je typu `Double`. `Integer` i `Long` rozšířit na `Double` a pouze `Double`. Proto je `Double` dominantní typ. Další informace najdete v tématu [rozšiřování a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Tělo funkce s jednou řádkou musí být výraz, který vrací hodnotu, nikoli příkaz. Pro jednořádkové funkce není k dispozici žádný příkaz `Return`. Hodnota vrácená funkcí single-line je hodnota výrazu v těle funkce.

- Tělo jednořádkového podprocesu musí být jednořádkový příkaz.

- Jednořádkové funkce a podprogramy neobsahují příkaz `End Function` ani `End Sub`.

- Můžete zadat datový typ parametru výrazu lambda pomocí klíčového slova `As`, nebo datový typ parametru lze odvodit. Buď musí mít všechny parametry zadané datové typy, nebo musí být všechny odvoditelné.

- parametry `Optional` a `Paramarray` nejsou povoleny.

- Obecné parametry nejsou povolené.

## <a name="async-lambdas"></a>Asynchronní lambdy

Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../../../visual-basic/language-reference/modifiers/async.md) a [await](../../../../visual-basic/language-reference/operators/await-operator.md) . Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.

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

Můžete přidat stejnou obslužnou rutinu události pomocí asynchronní lambda v [příkazu AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Chcete-li přidat tuto obslužnou rutinu, přidejte modifikátor `Async` před seznam parametrů lambda, jak ukazuje následující příklad.

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

Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Kontext

Výraz lambda sdílí svůj kontext s oborem, ve kterém je definován. Má stejná přístupová práva jako jakýkoli kód napsaný v nadřazeném oboru. To zahrnuje přístup k proměnným členů, funkcím a předparametrům, `Me`a parametrům a lokálním proměnným v nadřazeném oboru.

Přístup k lokálním proměnným a parametrům v rámci nadřazeného oboru může přesáhnout dobu života tohoto oboru. Dokud nebude delegát odkazující na výraz lambda dostupný pro uvolňování paměti, bude zachován přístup k proměnným v původním prostředí. V následujícím příkladu je proměnná `target` místní pro `makeTheGame`, metoda, ve které je definován výraz lambda `playTheGame`. Všimněte si, že vrácený výraz lambda přiřazený `takeAGuess` v `Main`má stále přístup k místní proměnné `target`.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Následující příklad ukazuje široké spektrum přístupových práv vnořeného výrazu lambda. Když je vrácený výraz lambda proveden z `Main` jako `aDel`, přistupuje k těmto prvkům:

- Pole třídy, ve které je definováno: `aField`

- Vlastnost třídy, ve které je definována: `aProp`

- Parametr metody `functionWithNestedLambda`, ve kterém je definován: `level1`

- Místní proměnná `functionWithNestedLambda`: `localVar`

- Parametr výrazu lambda, ve kterém je vnořený: `level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Převod na typ delegáta

Výraz lambda lze implicitně převést na kompatibilní typ delegáta. Informace o obecných požadavcích na kompatibilitu naleznete v tématu [odlehčený převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Například následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající signaturu delegáta.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající signaturu delegáta.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Pokud přiřadíte výrazy lambda delegátům nebo je předáte jako argumenty procedurám, můžete zadat názvy parametrů, ale vynechat jejich datové typy, aby bylo možné typy přenášet z delegáta.

## <a name="examples"></a>Příklady

- Následující příklad definuje výraz lambda, který vrací `True`, pokud má argument null přiřazenou hodnotu a `False`, pokud je jeho hodnota `Nothing`.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Následující příklad definuje výraz lambda, který vrátí index posledního prvku v poli.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Postupy: Předání procedur jinému postupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Postupy: Vytvoření výrazu lambda](./how-to-create-a-lambda-expression.md)
- [Volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
