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
ms.openlocfilehash: 8526f632b7e54c03bd16c3af70375179cd7cf277
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724470"
---
# <a name="--operator-visual-basic"></a>- – operátor (Visual Basic)
Vrátí rozdíl dvou numerických výrazů nebo zápornou hodnotu číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
 `expression2`  
 Vyžaduje se, pokud `–` operátor je výpočet zápornou hodnotu. Jakýkoli číselný výraz.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je rozdíl mezi `expression1` a `expression2`, nebo hodnotu negovaným čítačem `expression1`.  
  
 Datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`. Viz "Celočíselné aritmetiky" tabulky v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy. Jedná se o typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 V prvním využití je znázorněno v syntaxi uvedenému výše `–` operátor je *binární* operátor aritmetické odčítání pro rozdíl dvou numerických výrazů.  
  
 V druhém využití je znázorněno v syntaxi uvedenému výše `–` operátor je *unární* operátor negace záporné hodnoty výrazu. V tomto smyslu negaci se skládá z vrácení znaménko `expression1` tak, aby, výsledek je kladný Pokud `expression1` je záporný.  
  
 Pokud je výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md), `–` operátor zpracovává jako nula.  
  
> [!NOTE]
>  `–` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `–` operátor vypočítá a vrátí rozdíl dvou čísel a který se má negovat číslo.  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Po spuštění těchto příkazů `binaryResult` obsahuje 124.45 a `unaryResult` obsahuje –334.90.  
  
## <a name="see-also"></a>Viz také:
- [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
