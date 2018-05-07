---
title: '&lt;&lt; Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: bdec015309526aeac2499bc7b459b6ccab6f1e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt; Operátor (Visual Basic)
Provede aritmetický levém posun bitový.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Integrální číselná hodnota. Výsledek s posunem vzoru bit. Typ dat je stejný jako u `pattern`.  
  
 `pattern`  
 Požadováno. Integrální číselný výraz. Bitový posunutí. Datový typ musí být typ integrální (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz. Počet bitů se posunou vzoru bit. Datový typ musí být `Integer` nebo rozšířit do `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci. V aritmetické posunutí doleva jsou zahozeny bits zapuštěno mimo rozsah datového typu výsledek a pozice bit vacated na pravé straně nastaveny na nulu.  
  
 Pokud chcete zabránit posunutí ve více bits, než mohou být uloženy výsledek, Visual Basic zakrývá hodnotu `amount` s maskou velikost, která odpovídá datový typ `pattern`. Binární a z těchto hodnot se používá pro velikost shift. Velikost masek jsou následující:  
  
|Datový typ `pattern`|Velikost maska (decimální):|Velikost maska (hexadecimální)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|15|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`. Pokud `amount` je záporná, je jako hodnotu bez znaménka a maskovat s maskou správnou velikost.  
  
 Aritmetické posuny nikdy generování výjimek přetečení.  
  
> [!NOTE]
>  `<<` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `<<` operátor provést aritmetické zbývajících posuny na celočíselné hodnoty. Výsledek má vždy stejnou datový typ, který se zapuštěno výrazu.  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `result1` je 192 (0000 0000 1100 0000).  
  
-   `result2` je 3072 (0000 1100 0000 0000).  
  
-   `result3` je-32 768 (1000 0000-0000 0000).  
  
-   `result4` je 384 (0000 0001 1000 0000).  
  
-   `result5` je 0 (posunuté 15 místa vlevo).  
  
 Velikost posunutí pro `result4` počítá se jako 17 a 15, který se rovná 1.  
  
## <a name="see-also"></a>Viz také  
 [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<<= – operátor](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
