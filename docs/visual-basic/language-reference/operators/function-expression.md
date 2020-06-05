---
title: Function – výraz
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371178"
---
# <a name="function-expression-visual-basic"></a>Function – výraz (Visual Basic)
Deklaruje parametry a kód, které definují výraz lambda funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`parameterlist`|Nepovinný parametr. Seznam místních názvů proměnných, které reprezentují parametry tohoto postupu. Závorky musí být přítomny i v případě, že je seznam prázdný. Viz [seznam parametrů](../statements/parameter-list.md).|  
|`expression`|Povinná hodnota. Jeden výraz. Typ výrazu je návratový typ funkce.|  
|`statements`|Povinná hodnota. Seznam příkazů, které vrací hodnotu pomocí `Return` příkazu. (Viz [návratový příkaz](../statements/return-statement.md).) Typ vrácené hodnoty je návratový typ funkce.|  
  
## <a name="remarks"></a>Poznámky  
 *Výraz lambda* je funkce bez názvu, který počítá a vrací hodnotu. Můžete použít výraz lambda kdekoli, kde můžete použít typ delegáta, s výjimkou argumentu pro `RemoveHandler` . Další informace o delegátech a použití výrazů lambda s delegáty naleznete v tématu [příkaz Delegate](../statements/delegate-statement.md) a [odlehčený převod delegáta](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda se podobá funkci standardní funkce. Rozdíly jsou následující:  
  
- Výraz lambda nemá název.  
  
- Výrazy lambda nemůžou mít modifikátory, například `Overloads` nebo `Overrides` .  
  
- Výrazy lambda nepoužívají `As` klauzuli k určení návratového typu funkce. Místo toho je typ odvozen z hodnoty, na kterou se tělo jednořádkového výrazu lambda vyhodnocuje, nebo návratovou hodnotu víceřádkového výrazu lambda. Například pokud tělo víceřádkového výrazu lambda je `Where cust.City = "London"` , jeho návratový typ je `Boolean` .  
  
- Tělo výrazu lambda s jedním řádkem musí být výraz, nikoli příkaz. Tělo může být tvořeno voláním procedury funkce, ale nikoli voláním procedury Sub.  
  
- Buď musí mít všechny parametry zadané datové typy, nebo musí být všechny odvoditelné.  
  
- Nepovinné parametry a parametry ParamArray nejsou povoleny.  
  
- Obecné parametry nejsou povolené.  
  
## <a name="example"></a>Příklad  
 Následující příklady znázorňují dva způsoby, jak vytvořit jednoduché výrazy lambda. První používá `Dim` k zadání názvu funkce. Chcete-li zavolat funkci, odešlete hodnotu parametru.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Alternativně můžete deklarovat a spustit funkci ve stejnou dobu.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následuje příklad výrazu lambda, který zvyšuje svůj argument a vrací hodnotu. V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro funkci. Další příklady naleznete v tématu [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  
 Výrazy lambda jsou základem mnoha operátorů dotazu v jazyce LINQ (Language-Integrated Query) a lze je použít explicitně v dotazech založených na metodách. Následující příklad ukazuje typický dotaz LINQ následovaný překladem dotazu do formátu metody.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Další informace o metodách dotazů naleznete v tématu [dotazy](../queries/index.md). Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorů dotazů](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Function – příkaz](../statements/function-statement.md)
- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
- [Porovnání hodnot](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Logické výrazy](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If – operátor](if-operator.md)
- [Volný převod delegáta](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
