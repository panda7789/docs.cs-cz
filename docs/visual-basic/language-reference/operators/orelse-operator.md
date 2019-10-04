---
title: OrElse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835235"
---
# <a name="orelse-operator-visual-basic"></a>OrElse – operátor (Visual Basic)
Provádí krátkodobé rozvodu zahrnující logickou disjunkci dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Libovolný výraz `Boolean`.  
  
 `expression1`  
 Požadováno. Libovolný výraz `Boolean`.  
  
 `expression2`  
 Požadováno. Libovolný výraz `Boolean`.  
  
## <a name="remarks"></a>Poznámky  
 Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu. Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek. Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.  
  
 Pokud se jeden nebo oba výrazy vyhodnotí jako `True`, `result` je `True`. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nehodnoceno)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Datové typy  
 Operátor `OrElse` je definován pouze pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic převede každý operand podle potřeby, aby `Boolean` před vyhodnocením výrazu. Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ tak, aby `False` se staly `0` a `True` se `-1`.
Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Přetížení  
 [Operátor OR](../../../visual-basic/language-reference/operators/or-operator.md) a operátor " [true](../../../visual-basic/language-reference/operators/istrue-operator.md) " mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury. Přetížení operátorů `Or` a `IsTrue` má vliv na chování operátoru `OrElse`. Pokud váš kód používá `OrElse` u třídy nebo struktury, která přetěžuje `Or` a `IsTrue`, ujistěte se, že rozumíte jejich předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `OrElse` k provedení logické disjunkce dvou výrazů. Výsledkem je hodnota @no__t 0, která představuje, zda jsou oba výrazy pravdivé. Pokud je první výraz `True`, druhý se nevyhodnotí.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Předchozí příklad vytvoří výsledky `True`, `True` a @no__t – 2. Při výpočtu `firstCheck` není druhý výraz vyhodnocen, protože první je již `True`. Nicméně druhý výraz je vyhodnocen při výpočtu `secondCheck`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje příkaz `If`... `Then` obsahující dvě volání procedur. Pokud první volání vrátí `True`, druhá procedura není volána. To může vést k neočekávaným výsledkům, pokud druhý postup provádí důležité úkoly, které by měly být vždy provedeny při spuštění této části kódu.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor Or](../../../visual-basic/language-reference/operators/or-operator.md)
- [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
