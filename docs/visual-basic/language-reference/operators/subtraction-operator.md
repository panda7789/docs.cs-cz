---
title: '- – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: eb34b34986613f36b624c43c04f98390ffba4fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965856"
---
# <a name="--operator-visual-basic"></a>- – operátor (Visual Basic)
Vrátí rozdíl mezi dvěma číselnými výrazy nebo zápornou hodnotu číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinný parametr. Libovolný číselný výraz.  
  
 `expression2`  
 Povinné, pokud `–` operátor nevypočítá zápornou hodnotu. Libovolný číselný výraz.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je rozdíl mezi `expression1` hodnotami a `expression2`, nebo `expression1`s hodnotou negace.  
  
 Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a. `expression2` Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy. To zahrnuje typy unsigned a float-Point a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 V prvním použití zobrazeném v syntaxi uvedené dříve `–` je operátor *binární* aritmetický operátor odčítání pro rozdíl mezi dvěma číselnými výrazy.  
  
 Ve druhém použití zobrazeném v syntaxi, která `–` byla dříve uvedena, je operátor *unární* operátor negace pro zápornou hodnotu výrazu. V tomto smyslu se negace skládá z opačného znaménka `expression1` , aby byl výsledek kladný, pokud `expression1` je záporné.  
  
 Pokud se některý výraz vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), `–` operátor ho považuje za nulu.  
  
> [!NOTE]
> Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `–` Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `–` operátor k výpočtu a vrácení rozdílu mezi dvěma čísly a pak pro negaci čísla.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Po provedení těchto příkazů `binaryResult` obsahuje 124,45 a `unaryResult` obsahuje – 334,90.  
  
## <a name="see-also"></a>Viz také:

- [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
