---
title: 'Postupy: Volání procedury operátora (Visual Basic)'
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
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Postupy: Volání procedury operátora (Visual Basic)
Symbol operátoru ve výrazu můžete volání procedury operátora. V případě operátora převodu, zavoláte [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) převést hodnotu z jednoho datového typu.  
  
 Procedury operátoru není volána explicitně. Stačí použít operátor nebo `CType` funkce v příkazu přiřazení nebo výraz, stejně jako běžně použít operátor. Visual Basic umožňuje volání procedury operátora.  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
### <a name="to-call-an-operator-procedure"></a>K volání procedury operátora  
  
1.  Symbol operátoru používejte ve výrazu běžným způsobem.  
  
2.  Ujistěte se, že datové typy operandy jsou vhodné pro operátor a ve správném pořadí.  
  
3.  Operátor přispívá k hodnotu výrazu podle očekávání.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>K volání procedury operátora převodu  
  
1.  Použití `CType` uvnitř výrazu.  
  
2.  Ujistěte se, že datové typy operandy jsou vhodné pro převod a ve správném pořadí.  
  
3.  `CType` volání procedury operátora převodu a vrátí převedenou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě <xref:System.TimeSpan> struktury, přidá je dohromady a výsledek je uložen ve třetí <xref:System.TimeSpan> struktura. <xref:System.TimeSpan> Struktura definuje postup operátor přetížení několik standardní operátory.  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Protože <xref:System.TimeSpan> přetížení standardní `+` operátor, předchozí příklad volání procedury operátora při výpočtu hodnotu `combinedSpan`.  
  
 Příklad volání procedury operátora konverzace, naleznete v části [postupy: použití třídy, že definuje operátory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít.  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: Definice operátoru](./how-to-define-an-operator.md)  
 [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)  
 [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
