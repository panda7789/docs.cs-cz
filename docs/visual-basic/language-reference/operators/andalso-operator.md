---
title: AndAlso – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371931"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso – operátor (Visual Basic)
Provede krátkodobé rozvodu logického spojení na dvou výrazech.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`result`|Povinná hodnota. Libovolný `Boolean` výraz. Výsledkem je `Boolean` výsledek porovnání dvou výrazů.|  
|`expression1`|Povinná hodnota. Libovolný `Boolean` výraz.|  
|`expression2`|Povinná hodnota. Libovolný `Boolean` výraz.|  
  
## <a name="remarks"></a>Poznámky  
 Logická operace je označována jako *krátká* , pokud zkompilovaný kód může obejít vyhodnocení jednoho výrazu v závislosti na výsledku jiného výrazu. Pokud výsledek prvního vyhodnoceného výrazu určí konečný výsledek operace, není nutné vyhodnotit druhý výraz, protože nemůže změnit konečný výsledek. Krátkodobé okruhy mohou zvýšit výkon, pokud je výraz obcházení složitý, nebo pokud zahrnuje volání procedur.  
  
 Pokud se oba výrazy vyhodnotí jako `True` , `result` je `True` . Následující tabulka ukazuje, jak `result` je určena.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nehodnoceno)|`False`|  
  
## <a name="data-types"></a>Typy dat  
 `AndAlso`Operátor je definován pouze pro [datový typ Boolean](../data-types/boolean-data-type.md). Visual Basic každou operand podle potřeby převede `Boolean` před vyhodnocením výrazu. Pokud přiřadíte výsledek číselnému typu, Visual Basic jej převede z `Boolean` na tento typ, který `False` se změní `0` a `True` bude se jednat o `-1` .
Další informace naleznete v tématu [převody logických typů](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Přetížení  
 [Operátor and](and-operator.md) a operátor s hodnotou [false](isfalse-operator.md) mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, je-li operand typu této třídy nebo struktury. Přetížení operátorů `And` a `IsFalse` ovlivňuje chování `AndAlso` operátoru. Pokud váš kód používá `AndAlso` třídu nebo strukturu, která je přetížena `And` a, ujistěte se, že `IsFalse` rozumíte jejich předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `AndAlso` operátor k provedení logického spojení se dvěma výrazy. Výsledkem je `Boolean` hodnota, která představuje, zda je úplný výraz JOIN pravdivý. Pokud je první výraz `False` , druhý není vyhodnocen.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Předchozí příklad vytvoří výsledky `True` , a v `False` `False` uvedeném pořadí. Při výpočtu není `secondCheck` druhý výraz vyhodnocen, protože první je již `False` . Nicméně druhý výraz je vyhodnocen při výpočtu `thirdCheck` .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Function` proceduru, která vyhledává danou hodnotu mezi prvky pole. Pokud je pole prázdné nebo pokud byla překročena délka pole, `While` příkaz netestuje prvek pole proti hledané hodnotě.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Viz také

- [Logické/bitové operátory (Visual Basic)](logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [And – operátor](and-operator.md)
- [IsFalse – operátor](isfalse-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
