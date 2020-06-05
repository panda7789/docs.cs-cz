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
ms.openlocfilehash: fa2bc5417b8b917ff48502a5bd0a4daa21fab67e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388566"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Postupy: Volání procedury operátora (Visual Basic)
Proceduru operátoru zavoláte pomocí symbolu operátoru ve výrazu. V případě operátoru převodu zavoláte [funkci CType](../../../language-reference/functions/ctype-function.md) pro převod hodnoty z jednoho datového typu na jiný.  
  
 Explicitně Nevolejte procedury operátora. Stačí použít operátor nebo `CType` funkci v příkazu přiřazení nebo výrazu stejným způsobem, jakým obvykle používáte operátor. Visual Basic provede volání procedury operátoru.  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
### <a name="to-call-an-operator-procedure"></a>Volání procedury operátoru  
  
1. Používejte symbol operátoru ve výrazu běžným způsobem.  
  
2. Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.  
  
3. Operátor přispívá k hodnotě výrazu podle očekávání.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Volání procedury operátora převodu  
  
1. Použijte `CType` uvnitř výrazu.  
  
2. Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.  
  
3. `CType`volá proceduru operátora převodu a vrátí převedenou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě <xref:System.TimeSpan> struktury, přidá je dohromady a uloží výsledek do třetí <xref:System.TimeSpan> struktury. <xref:System.TimeSpan>Struktura definuje procedury operátoru pro přetížení několika standardních operátorů.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Vzhledem k tomu <xref:System.TimeSpan> , že přetěžuje `+` operátor Standard, předchozí příklad volá proceduru operátoru při výpočtu hodnoty `combinedSpan` .  
  
 Příklad volání procedury operátoru konverzace naleznete v tématu [How to: Use a Class definující operátory](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.  
  
## <a name="see-also"></a>Viz také

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)
- [Operator – příkaz](../../../language-reference/statements/operator-statement.md)
- [Rozšíření](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../data-types/widening-and-narrowing-conversions.md)
