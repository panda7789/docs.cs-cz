---
title: AndAlso – operátor (Visual Basic)
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
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608312"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso – operátor (Visual Basic)
Provede zkrácenou logickou konjunkci dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`result`|Povinný parametr. Žádné `Boolean` výrazu. Výsledkem je, `Boolean` výsledku porovnání řetězců dvou výrazů.|  
|`expression1`|Povinný parametr. Žádné `Boolean` výrazu.|  
|`expression2`|Povinný parametr. Žádné `Boolean` výrazu.|  
  
## <a name="remarks"></a>Poznámky  
 Logické operace se říká, že *zkrácenou* Pokud zkompilovaný kód může obejít vyhodnocení výrazů v závislosti na výsledek jiný výraz. Pokud výsledek první výraz vyhodnotí Určuje konečný výsledek operace, není nutné k vyhodnocení, druhý výraz, protože jej nelze změnit na konečný výsledek. Krátký cyklus může zlepšit výkon, pokud jednorázovým přihlášením výrazu je komplexní nebo zahrnuje volání procedur.  
  
 Pokud mají oba výrazy `True`, `result` je `True`. Následující tabulka ukazuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nevyhodnoceno)|`False`|  
  
## <a name="data-types"></a>Datové typy  
 `AndAlso` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic převede operandem tak, aby `Boolean` a provádí operaci, která je zcela v `Boolean`. Pokud přiřadíte číselného typu výsledku, ho z Visual Basic převede `Boolean` k danému typu. To by mohla vést k neočekávanému chování. Například `5 AndAlso 12` výsledkem `–1` při převodu na `Integer`.  
  
## <a name="overloading"></a>Přetížení  
 [Operátoru](../../../visual-basic/language-reference/operators/and-operator.md) a [IsFalse operátor](../../../visual-basic/language-reference/operators/isfalse-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ, který třídy nebo struktury. Přetížení `And` a `IsFalse` operátory má vliv na chování `AndAlso` operátor. Pokud váš kód používá `AndAlso` v třídě nebo struktuře, která přetížení `And` a `IsFalse`, je nutné pochopit jejich Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `AndAlso` operátor logickou konjunkci dvou výrazů. Výsledkem je `Boolean` , která udává, zda conjoined celý výraz hodnotu true. Pokud je první výraz `False`, druhý se už nevyhodnocuje.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Předchozí příklad vytváří výsledky `True`, `False`, a `False`v uvedeném pořadí. Při výpočtu `secondCheck`, druhý výraz není vyhodnocen, protože první je již `False`. Nicméně, druhý výraz je vyhodnocen při výpočtu `thirdCheck`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Function` proceduru, která hledá pro danou hodnotu mezi prvky pole. Pokud je pole prázdné, nebo pokud byla překročena délka pole, `While` příkaz netestuje na prvek pole s hodnotou vyhledávání.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor And](../../../visual-basic/language-reference/operators/and-operator.md)
- [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
