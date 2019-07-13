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
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860145"
---
# <a name="orelse-operator-visual-basic"></a>OrElse – operátor (Visual Basic)
Provede zkrácenou inkluzivní logickou disjunkci dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `Boolean` výrazu.  
  
 `expression1`  
 Povinný parametr. Žádné `Boolean` výrazu.  
  
 `expression2`  
 Povinný parametr. Žádné `Boolean` výrazu.  
  
## <a name="remarks"></a>Poznámky  
 Logické operace se říká, že *zkrácenou* Pokud zkompilovaný kód může obejít vyhodnocení výrazů v závislosti na výsledek jiný výraz. Pokud výsledek první výraz vyhodnotí Určuje konečný výsledek operace, není nutné k vyhodnocení, druhý výraz, protože jej nelze změnit na konečný výsledek. Krátký cyklus může zlepšit výkon, pokud jednorázovým přihlášením výrazu je komplexní nebo zahrnuje volání procedur.  
  
 Pokud mají jednoho nebo obou výrazech `True`, `result` je `True`. Následující tabulka ukazuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nevyhodnoceno)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Datové typy  
 `OrElse` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic převede operandem tak, aby `Boolean` před vyhodnocením výrazu. Pokud přiřadíte číselného typu výsledku, ho z Visual Basic převede `Boolean` k danému typu tak, aby `False` stane `0` a `True` stane `-1`.
Další informace najdete v tématu [logická převody typu](../data-types/boolean-data-type.md#type-conversions)
  
## <a name="overloading"></a>Přetížení  
 [Nebo operátor](../../../visual-basic/language-reference/operators/or-operator.md) a [IsTrue operátor](../../../visual-basic/language-reference/operators/istrue-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ této třídy nebo struktury. Přetížení `Or` a `IsTrue` operátory má vliv na chování `OrElse` operátor. Pokud váš kód používá `OrElse` v třídě nebo struktuře, která přetížení `Or` a `IsTrue`, je nutné pochopit jejich Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `OrElse` operátor provádět logické disjunkce dvou výrazů. Výsledkem je `Boolean` hodnotu, která udává, zda je splněna jedna ze dvou výrazů. Pokud je první výraz `True`, druhý se už nevyhodnocuje.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Předchozí příklad vytváří výsledky `True`, `True`, a `False` v uvedeném pořadí. Při výpočtu `firstCheck`, druhý výraz není vyhodnocen, protože první je již `True`. Nicméně, druhý výraz je vyhodnocen při výpočtu `secondCheck`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `If`... `Then` příkazu, který obsahuje dvě volání procedur. Pokud první volání vrátí `True`, druhý postup není volána. Pokud se druhý postup provádí důležité úkoly, které mají být provedeny vždy při spuštění této části kódu, může vést k neočekávaným výsledkům.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor Or](../../../visual-basic/language-reference/operators/or-operator.md)
- [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
