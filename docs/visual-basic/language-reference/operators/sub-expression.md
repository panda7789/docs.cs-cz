---
title: Sub – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 5e8c66f4f2b21a890b8c61e6fc642ce276df6f60
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966720"
---
# <a name="sub-expression-visual-basic"></a>Sub – výraz (Visual Basic)
Deklaruje parametry a kód, které definují výrazu lambda podprogram.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`parameterlist`|Volitelné. Seznam místní názvy proměnných, které představují parametry procesu. Závorky musí být k dispozici i v případě, že je seznam prázdný. Další informace najdete v tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Povinný parametr. Jeden příkaz.|  
|`statements`|Povinný parametr. Seznam příkazů.|  
  
## <a name="remarks"></a>Poznámky  
 A *výraz lambda* je podprogram, který nemá název a, který se spustí jeden nebo více příkazů. Výraz lambda můžete použít kdekoli, můžete použít typ delegáta, s výjimkou jako argument `RemoveHandler`. Další informace o delegátech a použití výrazů lambda s delegáty, naleznete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda  
 Syntaxe výrazu lambda se podobá u standardní podprogram. Rozdíly jsou následující:  
  
-   Výraz lambda nemá název.  
  
-   Výraz lambda nemůže mít modifikátor, jako například `Overloads` nebo `Overrides`.  
  
-   Příkaz, není výraz musí být tělo tohoto výrazu lambda jednořádkového. Text se může skládat z volání procedury sub, ale není volání funkce procedury.  
  
-   Výraz lambda musí být buď všechny parametry zadána, že datové typy nebo všechny parametry musí být odvozený.  
  
-   Volitelné a `ParamArray` parametry nejsou povoleny ve výrazech lambda.  
  
-   Obecné parametry nejsou povoleny ve výrazech lambda.  
  
## <a name="example"></a>Příklad  
 Následuje příklad výrazu lambda, která hodnotu zapíše do konzoly. Příklad ukazuje obě jedním řádkem a víceřádkového výrazu lambda výraz syntaxe podprogram. Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
