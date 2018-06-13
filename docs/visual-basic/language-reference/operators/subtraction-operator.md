---
title: '- Operátor (Visual Basic)'
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
ms.openlocfilehash: 4df8eb3844ed20fd24ca375f77cea46b9c6cee37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604312"
---
# <a name="--operator-visual-basic"></a>- – operátor (Visual Basic)
Vrátí rozdíl mezi dvou numerických výrazů nebo zápornou hodnotu číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Požadováno. Jakýkoli číselný výraz.  
  
 `expression2`  
 Vyžaduje, pokud `–` operátor je výpočet zápornou hodnotu. Jakýkoli číselný výraz.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je rozdíl mezi `expression1` a `expression2`, nebo posunut hodnotu `expression1`.  
  
 Datový typ výsledků je vhodné pro datové typy číselného typu `expression1` a `expression2`. Podívejte se na tabulky "Celočíselné aritmetiky" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy. To zahrnuje typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 V prvním použití zobrazí v syntaxi výše uvedený `–` operátor je *binární* operátor odčítání aritmetické pro rozdíl mezi dvou numerických výrazů.  
  
 Druhý využití znázorněno v syntaxi výše uvedený `–` operátor je *unární* operátor negace pro zápornou hodnotu výrazu. V tomto smyslu negace se skládá z Prohodit znaménko `expression1` tak, aby výsledkem je kladné Pokud `expression1` záporné.  
  
 Pokud výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md), `–` operátor se považuje za nula.  
  
> [!NOTE]
>  `–` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor. v takových třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `–` operátor vypočítat a vrátí rozdíl dvou čísel a pak negate číslo.  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Po provedení těchto příkazech `binaryResult` obsahuje 124.45 a `unaryResult` obsahuje –334.90.  
  
## <a name="see-also"></a>Viz také  
 [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
