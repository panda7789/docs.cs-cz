---
title: "&lt;&lt;Operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56cfb227f7e5c68de802c1f2cfb842a770f65ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;Operátor (Visual Basic)
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
  
|Datový typ`pattern`|Velikost maska (decimální):|Velikost maska (hexadecimální)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`. Pokud `amount` je záporná, je jako hodnotu bez znaménka a maskovat s maskou správnou velikost.  
  
 Aritmetické posuny nikdy generování výjimek přetečení.  
  
> [!NOTE]
>  `<<` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `<<` operátor provést aritmetické zbývajících posuny na celočíselné hodnoty. Výsledek má vždy stejnou datový typ, který se zapuštěno výrazu.  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `result1`je 192 (0000 0000 1100 0000).  
  
-   `result2`je 3072 (0000 1100 0000 0000).  
  
-   `result3`je-32 768 (1000 0000-0000 0000).  
  
-   `result4`je 384 (0000 0001 1000 0000).  
  
-   `result5`je 0 (posunuté 15 místa vlevo).  
  
 Velikost posunutí pro `result4` počítá se jako 17 a 15, který se rovná 1.  
  
## <a name="see-also"></a>Viz také  
 [Operátory bitového posunutí](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<< = – operátor](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
