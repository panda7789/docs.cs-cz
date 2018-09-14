---
title: Function – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609927"
---
# <a name="function-expression-visual-basic"></a>Function – výraz (Visual Basic)
Deklaruje parametry a kód, které definují výraz lambda funkce.  
  
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
|`parameterlist`|Volitelné. Seznam místní názvy proměnných, které představují parametry tohoto postupu. Závorky musí být k dispozici i v případě, že je seznam prázdný. Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Požadováno. Jeden výraz. Typ výrazu je návratový typ funkce.|  
|`statements`|Požadováno. Seznam příkazů, který vrací hodnotu s použitím `Return` příkazu. (Viz [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).) Typ hodnoty vrácené je návratový typ funkce.|  
  
## <a name="remarks"></a>Poznámky  
 A *výraz lambda* je funkce bez názvu, který vypočítává a vrací hodnotu. Výraz lambda můžete použít kdekoli můžete použít typ delegáta, s výjimkou jako argument `RemoveHandler`. Další informace o delegátech a použití výrazů lambda s delegáty, naleznete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda se podobá u standardní funkci. Rozdíly jsou následující:  
  
-   Výraz lambda nemá název.  
  
-   Výrazy lambda nemůžou mít modifikátory, jako například `Overloads` nebo `Overrides`.  
  
-   Výrazy lambda se nepoužívá `As` klauzule k určení návratového typu funkce. Místo toho typ je odvozen z hodnotu, která se vyhodnotí jako hlavní část výrazu lambda jednořádkového nebo návratovou hodnotu víceřádkového výrazu lambda výrazu. Například, pokud je hlavní část výrazu lambda jednořádkového `Where cust.City = "London"`, je její typ vrácené hodnoty `Boolean`.  
  
-   Výraz, ne příkaz musí být tělo tohoto výrazu lambda jednořádkového. Text se může skládat z volání proceduru function, ale ne voláním procedury sub.  
  
-   Buď všechny parametry musí mít zadaný datové typy nebo všechny musí být odvozený.  
  
-   Volitelné a Paramarray parametry nejsou povoleny.  
  
-   Obecné parametry nejsou povoleny.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují dva způsoby, jak vytvořit jednoduchý lambda výrazy. První použití `Dim` k poskytnutí názvu pro funkci. Pro volání funkce, předáte hodnotu parametru.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Příklad  
 Můžete také deklarovat a spustit funkci ve stejnou dobu.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Příklad  
 Tady je příklad výraz lambda, který zvýší její argument a vrátí hodnotu. Příklad ukazuje obě jedním řádkem a víceřádkového výrazu lambda syntaxe výrazu pro funkci. Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Příklad  
 Výrazy lambda tvoří základ mnoho operátorů dotazu v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]a můžete explicitně použít v dotazech založených na volání metody. Následující příklad ukazuje typickou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, za nímž následuje překladu dotazu do formátu metody.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Další informace o metodách dotazu naleznete v tématu [dotazy](../../../visual-basic/language-reference/queries/index.md). Další informace o standardních operátorů pro dotazování, naleznete v tématu [přehled standardních operátorů dotazu](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Porovnání hodnot](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Logické výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)  
 [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
