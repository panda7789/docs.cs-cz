---
title: OrElse – operátor
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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401404"
---
# <a name="orelse-operator-visual-basic"></a>OrElse – operátor (Visual Basic)
Provádí krátkodobé rozvodu zahrnující logickou disjunkci dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Libovolný `Boolean` výraz.  
  
 `expression1`  
 Povinná hodnota. Libovolný `Boolean` výraz.  
  
 `expression2`  
 Povinná hodnota. Libovolný `Boolean` výraz.  
  
## <a name="remarks"></a>Poznámky  
 Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu. Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek. Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.  
  
 Pokud se oba výrazy vyhodnotí jako `True` , `result` je `True` . Následující tabulka ukazuje, jak `result` je určena.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nehodnoceno)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Typy dat  
 `OrElse`Operátor je definován pouze pro [datový typ Boolean](../data-types/boolean-data-type.md). Visual Basic každou operand podle potřeby převede `Boolean` před vyhodnocením výrazu. Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ, který `False` se změní `0` a `True` bude se jednat o `-1` .
Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Přetížení  
 [Operátor OR](or-operator.md) a operátor " [true](istrue-operator.md) " mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury. Přetížení operátorů `Or` a `IsTrue` ovlivňuje chování `OrElse` operátoru. Pokud váš kód používá `OrElse` třídu nebo strukturu, která je přetížena `Or` a, ujistěte se, že `IsTrue` rozumíte jejich předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `OrElse` operátor k provedení logické disjunkce dvou výrazů. Výsledkem je `Boolean` hodnota, která představuje, zda je jeden z obou výrazů pravdivý. Pokud je první výraz `True` , druhý není vyhodnocen.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Předchozí příklad vytvoří výsledky `True` , `True` a `False` v uvedeném pořadí. Při výpočtu není `firstCheck` druhý výraz vyhodnocen, protože první je již `True` . Nicméně druhý výraz je vyhodnocen při výpočtu `secondCheck` .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `If` příkaz... `Then` obsahující dvě volání procedur. Pokud se první volání vrátí `True` , druhá procedura není volána. To může vést k neočekávaným výsledkům, pokud druhý postup provádí důležité úkoly, které by měly být vždy provedeny při spuštění této části kódu.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Viz také

- [Logické/bitové operátory (Visual Basic)](logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Or – operátor](or-operator.md)
- [IsTrue – operátor](istrue-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
