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
ms.openlocfilehash: 46614ad43e7be72c8396f47ba7f5d02185f62827
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837088"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Postupy: Volání procedury operátora (Visual Basic)
Volání procedury operátora pomocí symbol operátoru ve výrazu. V případě operátor převodu, volání [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) převést hodnotu z jednoho datového typu na jiný.  
  
 Procedury operátoru není explicitně volat. Stačí použít operátor, nebo `CType` funkce v příkazu přiřazení nebo výraz, stejně jako obvykle použijete operátor. Visual Basic je volání procedury operátora.  
  
 Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.  
  
### <a name="to-call-an-operator-procedure"></a>Volání procedury operátora  
  
1.  Použijte symbol operátoru ve výrazu běžným způsobem.  
  
2.  Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.  
  
3.  Operátor, který přispívá k hodnotu výrazu podle očekávání.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Volání procedury operátora převodu  
  
1.  Použití `CType` uvnitř výrazu.  
  
2.  Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.  
  
3.  `CType` volání procedury operátora převodu a vrátí převedenou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva <xref:System.TimeSpan> struktury, přidá je dohromady a výsledek je uložen na třetí <xref:System.TimeSpan> struktury. <xref:System.TimeSpan> Struktury definuje procedury operátoru přetížení několik standardních operátorů.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Protože <xref:System.TimeSpan> přetížení standardní `+` operátor v předchozím příkladu volání procedury operátora při výpočtu hodnoty `combinedSpan`.  
  
 Příklad volání procedury operátora konverzace, naleznete v tématu [jak: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třídy nebo struktury, které používáte definuje operátor, který chcete použít.  
  
## <a name="see-also"></a>Viz také:

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definovat operátor](./how-to-define-an-operator.md)
- [Postupy: Definice operátora převodu](./how-to-define-a-conversion-operator.md)
- [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
