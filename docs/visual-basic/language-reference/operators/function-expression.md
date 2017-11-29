---
title: "Function – výraz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a>Function – výraz (Visual Basic)
Deklaruje, parametry a kód, který definovat výraz lambda funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`parameterlist`|Volitelné. Seznam místní názvy proměnných, které představují parametry tohoto postupu. Závorkách musí být k dispozici i v případě, že seznam je prázdný. V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Požadováno. Jeden výraz. Typ výrazu je návratový typ funkce.|  
|`statements`|Požadováno. Seznam příkazů, která vrátí hodnotu pomocí `Return` příkaz. (Viz [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).) Typ hodnoty vrácené je návratový typ funkce.|  
  
## <a name="remarks"></a>Poznámky  
 A *výrazu lambda* je funkce, bez název, který vypočítá a vrátí hodnotu. Výraz lambda lze použít kdekoli můžete použít typem delegáta, s výjimkou jako argument pro `RemoveHandler`. Další informace o Delegáti a použití výrazů lambda s delegáti najdete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda podobá se standardní funkce. Rozdíly jsou následující:  
  
-   Výraz lambda nemá název.  
  
-   Lambda – výrazy nemůže mít modifikátory, jako například `Overloads` nebo `Overrides`.  
  
-   Lambda – výrazy nepoužívejte `As` klauzule k určení návratový typ funkce. Místo toho je typ odvodit z hodnotu, která vyhodnotí jako text výrazu lambda jeden řádek, nebo vrací hodnotu výrazu lambda víceřádkový. Například, pokud je text výrazu lambda jeden řádek `Where cust.City = "London"`, je její návratový typ `Boolean`.  
  
-   Tělo výrazu lambda jeden řádek musí být výraz není příkaz. Text se může skládat z volání procedury funkce, ale není volání procedury sub.  
  
-   Buď všechny parametry musí mít zadán odvodit datové typy nebo všechny.  
  
-   Volitelné a Paramarray parametry nejsou povoleny.  
  
-   Obecné parametry nejsou povoleny.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují dva způsoby, jak vytvořit jednoduché lambda – výrazy. První používá `Dim` k zadání názvu pro tuto funkci. Pro volání funkce, můžete odeslat hodnotu pro parametr.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Příklad  
 Alternativně můžete deklarovat a spusťte funkci ve stejnou dobu.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Příklad  
 Tady je příklad, který zvýší jeho argumentů a vrátí hodnotu výrazu lambda. Příklad ukazuje, jak jeden řádek a víceřádkový syntaxe výrazu lambda pro funkci. Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Příklad  
 Lambda – výrazy tvoří základ řadu operátory dotazu v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]a je možné explicitně v dotazech na základě metod. Následující příklad ukazuje typické [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, za nímž následuje překlad dotazu do formátu metoda.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Další informace o metody dotazů najdete v tématu [dotazy](../../../visual-basic/language-reference/queries/queries.md). Další informace o standardních operátorů dotazu najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
## <a name="see-also"></a>Viz také  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Lambda – výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Porovnání hodnot](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Logické výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Pokud operátor](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
