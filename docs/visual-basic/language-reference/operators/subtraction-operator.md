---
title: '- Operátor'
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
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348226"
---
# <a name="--operator-visual-basic"></a>- – operátor (Visual Basic)
Vrátí rozdíl mezi dvěma číselnými výrazy nebo zápornou hodnotu číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
expression1 – expression2
```
  
nebo

```vb  
–expression1  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Požadováno. Libovolný číselný výraz.  
  
 `expression2`  
 Povinné, pokud operátor `–` nevypočítá zápornou hodnotu. Libovolný číselný výraz.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je rozdíl mezi `expression1` a `expression2`nebo hodnotou negace `expression1`.  
  
 Výsledný datový typ je číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy. To zahrnuje typy bez znaménka a typy s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 V prvním použití zobrazeném v syntaxi uvedené dříve je operátor `–` *binární* aritmetický operátor odčítání pro rozdíl mezi dvěma číselnými výrazy.  
  
 Ve druhém použití zobrazeném v syntaxi uvedené dříve je operátor `–` *unární* operátor negace pro zápornou hodnotu výrazu. V tomto smyslu se negace skládá z opačného znaménka `expression1` tak, že výsledek je kladný, pokud `expression1` záporné.  
  
 Pokud se některý výraz vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), operátor `–` považuje za nulu.  
  
> [!NOTE]
> Operátor `–` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `–` k výpočtu a vrácení rozdílu mezi dvěma čísly a pak pro negaci čísla.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Po provedení těchto příkazů `binaryResult` obsahuje 124,45 a `unaryResult` obsahuje – 334,90.  
  
## <a name="see-also"></a>Viz také:

- [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
