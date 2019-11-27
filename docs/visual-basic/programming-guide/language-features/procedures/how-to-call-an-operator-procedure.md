---
title: 'Postupy: Volání procedury operátora'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340248"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Postupy: Volání procedury operátora (Visual Basic)
Proceduru operátoru zavoláte pomocí symbolu operátoru ve výrazu. V případě operátoru převodu zavoláte [funkci CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pro převod hodnoty z jednoho datového typu na jiný.  
  
 Explicitně Nevolejte procedury operátora. Stačí použít operátor nebo funkci `CType` v příkazu přiřazení nebo výrazu stejným způsobem, jakým obvykle používáte operátor. Visual Basic provede volání procedury operátoru.  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
### <a name="to-call-an-operator-procedure"></a>Volání procedury operátoru  
  
1. Používejte symbol operátoru ve výrazu běžným způsobem.  
  
2. Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.  
  
3. Operátor přispívá k hodnotě výrazu podle očekávání.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Volání procedury operátora převodu  
  
1. Použijte `CType` uvnitř výrazu.  
  
2. Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.  
  
3. `CType` volá proceduru operátora převodu a vrátí převedenou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě struktury <xref:System.TimeSpan>, přidá je dohromady a uloží výsledek do třetí <xref:System.TimeSpan> struktury. Struktura <xref:System.TimeSpan> definuje procedury operátoru pro přetížení několika standardních operátorů.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Vzhledem k tomu, že <xref:System.TimeSpan> přetěžuje standardní operátor `+`, předchozí příklad volá proceduru operátoru při výpočtu hodnoty `combinedSpan`.  
  
 Příklad volání procedury operátoru konverzace naleznete v tématu [How to: Use a Class definující operátory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.  
  
## <a name="see-also"></a>Viz také:

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)
- [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
