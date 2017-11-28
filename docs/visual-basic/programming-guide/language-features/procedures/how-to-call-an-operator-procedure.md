---
title: "Postupy: Volání procedury operátora (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abff0a81ebcdacb59b69d0c307bb4aa219906c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Postupy: Volání procedury operátora (Visual Basic)
Symbol operátoru ve výrazu můžete volání procedury operátora. V případě operátora převodu, zavoláte [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) převést hodnotu z jednoho datového typu.  
  
 Procedury operátoru není volána explicitně. Stačí použít operátor nebo `CType` funkce v příkazu přiřazení nebo výraz, stejně jako běžně použít operátor. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]provede volání procedury operátora.  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
### <a name="to-call-an-operator-procedure"></a>K volání procedury operátora  
  
1.  Symbol operátoru používejte ve výrazu běžným způsobem.  
  
2.  Ujistěte se, že datové typy operandy jsou vhodné pro operátor a ve správném pořadí.  
  
3.  Operátor přispívá k hodnotu výrazu podle očekávání.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>K volání procedury operátora převodu  
  
1.  Použití `CType` uvnitř výrazu.  
  
2.  Ujistěte se, že datové typy operandy jsou vhodné pro převod a ve správném pořadí.  
  
3.  `CType`volání procedury operátora převodu a vrátí převedenou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě <xref:System.TimeSpan> struktury, přidá je dohromady a výsledek je uložen ve třetí <xref:System.TimeSpan> struktura. <xref:System.TimeSpan> Struktura definuje postup operátor přetížení několik standardní operátory.  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Protože <xref:System.TimeSpan> přetížení standardní `+` operátor, předchozí příklad volání procedury operátora při výpočtu hodnotu `combinedSpan`.  
  
 Příklad volání procedury operátora konverzace, naleznete v části [postupy: použití třídy, že definuje operátory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít.  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: definice operátora](./how-to-define-an-operator.md)  
 [Postupy: definice operátora převodu](./how-to-define-a-conversion-operator.md)  
 [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Rozšíření](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Zužující](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
