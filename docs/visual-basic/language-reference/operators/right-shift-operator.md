---
title: "&gt;&gt;Operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;Operátor (Visual Basic)
Provede aritmetický správné posun bitový.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Integrální číselná hodnota. Výsledek s posunem vzoru bit. Typ dat je stejný jako u `pattern`.  
  
 `pattern`  
 Požadováno. Integrální číselný výraz. Bitový posunutí. Datový typ musí být typ integrální (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz. Počet bitů se posunou vzoru bit. Datový typ musí být `Integer` nebo rozšířit do `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci. V aritmetické posunutí doprava bits zapuštěno nad rámec nejvíce vpravo bit pozice se zahodí a bit krajní levé (symbol) rozšířena do pozice bit vacated na levé straně. To znamená, že pokud `pattern` má zápornou hodnotu vacated pozic jsou nastavené na jednu; jinak jsou nastaveny na nulu.  
  
 Všimněte si, že datové typy `Byte`, `UShort`, `UInteger`, a `ULong` jsou bez znaménka, proto neexistuje žádný přihlašovací bit rozšíření. Pokud `pattern` je všechny nepodepsané typu, vacated pozic jsou vždy nastavená na hodnotu nula.  
  
 Aby se zabránilo ve více bits, než mohou být uloženy výsledek s posunem, Visual Basic zakrývá hodnotu `amount` s maskou velikost odpovídající datový typ `pattern`. Binární a z těchto hodnot se používá pro velikost shift. Velikost masek jsou následující:  
  
|Datový typ`pattern`|Velikost maska (decimální):|Velikost maska (hexadecimální)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`. Pokud `amount` je záporná, je jako hodnotu bez znaménka a maskovat s maskou správnou velikost.  
  
 Aritmetické posuny nikdy generování výjimek přetečení.  
  
## <a name="overloading"></a>Přetížení  
 `>>` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `>>` operátor provést aritmetické posuny doprava na celočíselné hodnoty. Výsledek má vždy stejnou datový typ, který se zapuštěno výrazu.  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `result1`je 2560 (0000 1010 0000 0000).  
  
-   `result2`je 160 (0000 0000 1010 0000).  
  
-   `result3`je 2 (0000 0000-0000 0010).  
  
-   `result4`je 640 (0000 0010 1000 0000).  
  
-   `result5`je 0 (posunuté 15 místech vpravo).  
  
 Velikost posunutí pro `result4` počítá se jako 18 a 15, který se rovná 2.  
  
 Následující příklad ukazuje aritmetické posuny na zápornou hodnotu.  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `negresult1`je -512 (1111 1110 0000 0000).  
  
-   `negresult2`je -1 (verze přihlašovací rozšířena).  
  
## <a name="see-also"></a>Viz také  
 [Operátory bitového posunutí](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [>> = – operátor](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
