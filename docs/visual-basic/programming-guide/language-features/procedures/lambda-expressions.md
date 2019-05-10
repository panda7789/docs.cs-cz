---
title: Lambda – výrazy (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 5e59b0284ad1c05c16c33d520bc4c223e6ddace1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623259"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda – výrazy (Visual Basic)
A *výraz lambda* je funkce nebo podprogramu bez názvu, který lze použít bez ohledu na to delegát je platný. Výrazy lambda může být funkce nebo podprogramy a může být jeden nebo více řádků. Můžete předat hodnoty z aktuálního oboru pro výraz lambda.  
  
> [!NOTE]
>  `RemoveHandler` Příkaz je výjimku. Nelze předat výraz lambda v parametru delegáta `RemoveHandler`.  
  
 Vytvoříte pomocí výrazů lambda `Function` nebo `Sub` – klíčové slovo, podobně jako můžete vytvořit standardní funkce nebo podprogramu. Výrazy lambda jsou však zahrnuty v příkazu.  
  
 V následujícím příkladu je výraz lambda, který zvýší její argument a vrátí hodnotu. Příklad ukazuje obě lambda jednořádkového a více řádky syntaxe výrazu pro funkci.  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 V následujícím příkladu je výraz lambda, který zapíše hodnoty do konzoly. Příklad ukazuje obě jedním řádkem a víceřádkového výrazu lambda výraz syntaxe podprogram.  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 Všimněte si, že v předchozích příkladech jsou lambda výrazy přiřazeny k názvu proměnné. Pokaždé, když odkazujete na proměnnou, vyvolání lambda výrazu. Můžete také deklarovat a volat lambda výraz ve stejnou dobu, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 Výraz lambda může být vrácen jako hodnotu volání funkce (jak je znázorněno v příkladu [kontextu](#context) později v tomto tématu), nebo předaný jako argument pro parametr, který přijímá typ delegáta, jak je znázorněno v následujícím Příklad.  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda se podobá standardní funkce nebo podprogram. Rozdíly jsou následující:  
  
- Výraz lambda nemá název.  
  
- Výrazy lambda nemůžou mít modifikátory, jako například `Overloads` nebo `Overrides`.  
  
- Funkce lambda jednořádkového nepoužívejte `As` klauzule k určení návratového typu. Místo toho typ je odvozen z hodnotu, která se vyhodnotí jako hlavní část výrazu lambda. Například pokud tělo výrazu lambda je `cust.City = "London"`, je její typ vrácené hodnoty `Boolean`.  
  
- Ve funkcích víceřádkového výrazu lambda, můžete zadat typ vrácené hodnoty pomocí `As` klauzuli, nebo vynechejte `As` klauzule tak, aby návratový typ je odvozen. Když `As` klauzule vynecháte víceřádkového výrazu lambda funkce, návratový typ je odvozen dominantní typ ze všech `Return` příkazy ve funkci víceřádkového výrazu lambda. *Dominantní typ* je jedinečný typ, který lze rozšířit všechny ostatní typy na. Pokud nelze určit tento jedinečný typ, dominantní typ je jedinečný typ, který můžete zúžit všechny typy jako pole k. Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object`. V takovém případě pokud `Option Strict` je nastavena na `On`, dojde k chybě kompilátoru.  
  
     Například, pokud zadaný výraz pro `Return` příkaz obsahovat hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`. Obě `Integer` a `Long` rozšířit na `Double` a pouze `Double`. Proto `Double` dominantní typ je. Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
- Výraz, který vrací hodnotu, ne příkaz, musí být tělo funkce jedním řádkem. Neexistuje žádná `Return` příkaz pro funkce jedním řádkem. Hodnota vrácená funkcí jedním řádkem je hodnota výrazu v těle funkce.  
  
- Jednořádkového příkazu musí být tělo tohoto podprogram jedním řádkem.  
  
- Jedním řádkem funkce a podprogramy nezahrnují `End Function` nebo `End Sub` příkazu.  
  
- Datový typ parametru výrazu lambda můžete určit pomocí `As` jde odvodit – klíčové slovo nebo datový typ parametru. Buď všechny parametry musí mít zadaný datové typy nebo všechny musí být odvozený.  
  
- `Optional` a `Paramarray` parametry nejsou povoleny.  
  
- Obecné parametry nejsou povoleny.  
  
## <a name="async-lambdas"></a>Asynchronní lambdy  
 Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) a [operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md) klíčová slova. Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.  
  
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
  
 Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy v [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Chcete-li přidat tuto obslužnou rutinu, přidejte `Async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.  
  
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
  
 Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
## <a name="context"></a> Kontext  
 Výraz lambda sdílí jeho kontextu oboru, ve kterém je definována. Má stejná přístupová práva jako libovolný kód napsaný v rozsah. Jedná se o přístup k proměnné členů, funkcí a typu Sub, `Me`a parametrů a lokálních proměnných v nadřazeného oboru.  
  
 Přístup k místní proměnné a parametry v rozsah můžete rozšířit nad rámec doby života tohoto oboru. Dokud delegát, který odkazuje na výraz lambda není k dispozici pro uvolňování paměti, přístup k proměnným v původní prostředí se zachová. V následujícím příkladu proměnná `target` je lokální vzhledem k `makeTheGame`, metody, ve které výraz lambda `playTheGame` je definována. Všimněte si, že vrácený výraz lambda, přiřazená `takeAGuess` v `Main`, má stále přístup k místní proměnné `target`.  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 Následující příklad ukazuje širokou škálu přístupová práva vnořený výraz lambda. Při spouštění vrácený výraz lambda se z `Main` jako `aDel`, přistupuje k tyto prvky:  
  
- Pole třídy, ve kterém je definována: `aField`  
  
- Vlastnost třídy, ve kterém je definována: `aProp`  
  
- Parametr metody `functionWithNestedLambda`, ve kterém je definována: `level1`  
  
- Místní proměnná `functionWithNestedLambda`: `localVar`  
  
- Parametr lambda výrazu, ve kterém je vnořená: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>Převádění na typ delegáta  
 Výraz lambda lze implicitně převést na typ delegáta kompatibilní. Informace o požadavcích na obecné kompatibility najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Například následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající signatura delegáta.  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 Následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající signatura delegáta.  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 Při přiřazení výrazy lambda na delegáty nebo předávat jako argumenty na postupy, můžete zadat názvy parametrů, ale vynechejte jejich datové typy, kde typy vytvářena z delegáta.  
  
## <a name="examples"></a>Příklady  
  
- Následující příklad definuje výraz lambda, který vrátí `True` Pokud s možnou hodnotou Null argument má přiřazenou hodnotu, a `False` pokud její hodnota je `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- Následující příklad definuje výraz lambda, který vrátí index posledního prvku v poli.  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy hodnot s povolenou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Postupy: Vytvoření výrazu Lambda](./how-to-create-a-lambda-expression.md)
- [Volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
