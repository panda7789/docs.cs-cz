---
title: "Výrazy Lambda (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69ac88d295420277e99058d0f80a5ae1c2ce2e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-visual-basic"></a>Výrazy Lambda (Visual Basic)
A *výrazu lambda* je funkce nebo podprogramu bez názvu, který lze použít bez ohledu na delegáta je platný. Výrazy lambda může být funkce nebo subrutiny a může být jeden nebo více řádků. Můžete předat hodnoty z aktuálního oboru do výrazu lambda.  
  
> [!NOTE]
>  `RemoveHandler` Příkaz je výjimku. Nelze předat výrazu lambda v pro parametr delegáta `RemoveHandler`.  
  
 Lambda – výrazy vytvoříte pomocí `Function` nebo `Sub` – klíčové slovo, stejně jako můžete vytvořit standardní funkce nebo podprogramu. Lambda – výrazy jsou však součástí příkazu.  
  
 V následujícím příkladu je výraz lambda, který zvýší jeho argumentů a vrátí hodnotu. Příklad ukazuje, jak jednom řádku a víceřádkový syntaxe výrazu lambda pro funkci.  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 V následujícím příkladu je výraz lambda, která hodnotu zapíše do konzoly. Příklad ukazuje, jak jednom řádku a víceřádkový syntaxe výrazu lambda pro podprogramu.  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 Všimněte si, že v předchozích příkladech jsou výrazy lambda přiřazené k název proměnné. Vždy, když odkazujete na proměnnou, můžete vyvolat výrazu lambda. Můžete také deklarovat a vyvolání výrazu lambda ve stejnou dobu, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Výraz lambda může být vrácen jako hodnota z volání funkce (jak je znázorněno v příkladu v [kontextu](#context) později v tomto tématu), nebo předaná jako argument parametr, který přebírá typem delegáta, jak je znázorněno v následující Příklad.  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda podobá se standardní funkce nebo podprogramu. Rozdíly jsou následující:  
  
-   Výraz lambda nemá název.  
  
-   Lambda – výrazy nemůže mít modifikátory, jako například `Overloads` nebo `Overrides`.  
  
-   Jeden řádek lambda funkce nepoužívají `As` klauzule k určení návratový typ. Místo toho je typ odvodit z hodnotu, která vyhodnotí jako text výrazu lambda. Například, pokud je text výrazu lambda `cust.City = "London"`, je její návratový typ `Boolean`.  
  
-   V Víceřádkový lambda funkce, můžete buď zadat návratový typ pomocí `As` klauzuli, nebo vynechejte `As` klauzule tak, že je návratový typ odvodit. Když `As` klauzule je zadán pro funkci Víceřádkový lambda, je jako typ dominantní ze všech odvodit návratový typ `Return` příkazy ve funkci Víceřádkový lambda. *Dominantní typ* je jedinečný typ, který všechny ostatní typy můžete rozšířit do. Pokud tento typ jedinečného nelze určit, dominantní typ je jedinečný typ, který k můžete zúžit všechny ostatní typy v poli. Pokud žádná z těchto jedinečný se dá určit, že dominantní typ je `Object`. V takovém případě pokud `Option Strict` je nastaven na `On`, dojde k chybě kompilátoru.  
  
     Například, pokud zadané výrazy `Return` příkaz obsahovat hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`. Obě `Integer` a `Long` rozšíří do `Double` pouze a `Double`. Proto `Double` dominantní typu. Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   Tělo funkce jeden řádek musí být výraz, který vrátí hodnotu, nikoli příkaz. Neexistuje žádné `Return` údajů pro funkce jeden řádek. Hodnota vrácená funkcí jeden řádek je hodnota výrazu v těle funkce.  
  
-   Tělo podprogramu jeden řádek musí být příkaz jeden řádek.  
  
-   Jeden řádek funkce a subrutiny nezahrnují `End Function` nebo `End Sub` příkaz.  
  
-   Datový typ parametru výrazu lambda můžete zadat pomocí `As` lze odvodit – klíčové slovo nebo datový typ parametru. Buď všechny parametry musí mít zadán odvodit datové typy nebo všechny.  
  
-   `Optional`a `Paramarray` parametry nejsou povoleny.  
  
-   Obecné parametry nejsou povoleny.  
  
## <a name="async-lambdas"></a>Asynchronní lambdy  
 Můžete snadno vytvořit lambda – výrazy a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) a [Await – operátor](../../../../visual-basic/language-reference/operators/await-operator.md) klíčová slova. Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a čeká použití asynchronní metody `ExampleMethodAsync`.  
  
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
  
 Stejné obslužné rutiny události můžete přidat pomocí asynchronní lambda v [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Chcete-li přidat Tato obslužná rutina, přidejte `Async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.  
  
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
  
 Další informace o tom, jak vytvořit a použít asynchronní metody najdete v tématu [asynchronní programování s Async a Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
##  <a name="context"></a>Kontext  
 Výraz lambda sdílí jeho kontext k oboru, ve kterém je definovaný. Má stejné oprávnění jako jakékoli kód napsaný v oboru obsahujícího. Poskytuje přístup k členské proměnné, funkce a předplatných, `Me`a parametry a místní proměnné v oboru obsahujícího.  
  
 Přístup k místní proměnné a parametry v oboru obsahujícího můžete rozšířit nad rámec doba platnosti tohoto oboru. Dokud není k dispozici pro uvolňování paměti s delegátem, která odkazuje na výraz lambda, přístup k proměnným v původní prostředí se zachová. V následujícím příkladu, proměnné `target` je místní pro `makeTheGame`, metoda, ve kterém výrazu lambda `playTheGame` je definována. Všimněte si, že výraz lambda vrácený přiřazené `takeAGuess` v `Main`, stále má přístup k místní proměnné `target`.  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 Následující příklad ukazuje širokou škálu přístupová práva výrazu vnořené lambda. Provedení výrazu lambda vrácená z `Main` jako `aDel`, přistupuje k tyto prvky:  
  
-   Pole třídy, ve kterém je definovaný:`aField`  
  
-   Vlastnosti třídy, ve kterém je definovaný:`aProp`  
  
-   Parametr metody `functionWithNestedLambda`, ve kterém je definována:`level1`  
  
-   Místní proměnná `functionWithNestedLambda`:`localVar`  
  
-   Parametr výrazu lambda, ve kterém jsou vnořeny:`level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>Převádění na typ delegáta  
 Výraz lambda může implicitně převést na typ kompatibilní delegáta. Informace o obecné požadavky na kompatibilitu najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Například následující příklad kódu ukazuje výrazu lambda, která se implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající podpisu delegáta.  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 Následující příklad kódu ukazuje výrazu lambda, která se implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající podpisu delegáta.  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 Když výrazy lambda přiřadit delegáty nebo je předat jako argumenty procedury, můžete zadat názvy parametrů, ale vynechejte jejich datové typy, když necháte typy provedou z delegáta.  
  
## <a name="examples"></a>Příklady  
  
-   V následujícím příkladu definuje výraz lambda, který vrací `True` Pokud má argument s možnou hodnotou Null přiřazenou hodnotu, a `False` Pokud je jeho hodnota `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   V následujícím příkladu definuje výraz lambda, který vrátí index posledním elementem pole.  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Postupy: předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Postupy: vytvoření výrazu Lambda](./how-to-create-a-lambda-expression.md)  
 [Volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
