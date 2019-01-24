---
title: ^ – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 2fb52a57a9d96f93c31ab1419e81e7f05967f831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659711"
---
# <a name="-operator-visual-basic"></a>^ – operátor (Visual Basic)
Umocní jedno číslo na mocninu vyjádřenou druhým číslem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Součásti  
 `number`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
 `exponent`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je `number` umocněné na sílu `exponent`, vždy jako `Double` hodnotu.  
  
## <a name="supported-types"></a>Podporované typy  
 `Double`. Jakýkoli jiný typ operandy jsou převedeny na `Double`.  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic vždy provádí umocnění v [datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 Hodnota `exponent` může být zlomkové záporné nebo obojí.  
  
 Při provádění více než jeden umocnění v jednom výrazu `^` operátor je vyhodnocovány, jak je zjištěna zleva doprava.  
  
> [!NOTE]
>  `^` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `^` operátor se má zvýšit číslo mocninu exponent. Výsledkem je první operand umocněné na druhou.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 Předchozí příklad vytváří následující výsledky:  
  
 `exp1` je nastavena na 4 (spolehlivosti 2).  
  
 `exp2` je nastaven na 19683 (umocněnou, 3 pak tuto hodnotu na třetí).  
  
 `exp3` je nastaven na-125 (-5 umocněnou).  
  
 `exp4` je nastaven na 625 (čtvrtá exponentem -5).  
  
 `exp5` je nastavena na 2 (uživatel root datové krychle 8).  
  
 `exp6` je nastaven na 0,5 (1.0 dělený kořenové datové krychle 8).  
  
 Všimněte si důležitost závorky ve výrazech v předchozím příkladu. Z důvodu *priorita operátorů*, Visual Basic se obvykle provádí `^` i unární operátor před všechny ostatní `–` operátor. Pokud `exp4` a `exp6` měl vypočtena bez závorek by mít vyprodukoval následující výsledky:  
  
 `exp4 = -5 ^ 4` se vypočítá jako – (5 a čtvrtý výkon), které způsobovaly-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0` se vypočítá jako (8 – 1 napájení nebo 0,125) 3.0, což by vytvořilo 0.041666666666666666666666666666667 dělený.  
  
## <a name="see-also"></a>Viz také:
- [^= – operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
