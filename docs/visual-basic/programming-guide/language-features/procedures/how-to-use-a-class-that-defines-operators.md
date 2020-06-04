---
title: 'Postupy: Použití třídy, která definuje operátory.'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414347"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Postupy: Použití třídy, která definuje operátory (Visual Basic).
Pokud používáte třídu nebo strukturu, která definuje své vlastní operátory, můžete k těmto operátorům přistupovat z Visual Basic.  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad přistupuje ke struktuře SQL <xref:System.Data.SqlTypes.SqlString> , která definuje operátory převodu ([funkce CType](../../../language-reference/functions/ctype-function.md)) v obou směrech mezi řetězcem SQL a řetězcem Visual Basic. Použijte `CType(` *řetězcový výraz SQL* `String)` pro převod řetězce SQL na řetězec Visual Basic a řetězcový `CType(` *výraz Visual Basic* <xref:System.Data.SqlTypes.SqlString> `)` pro převod v druhém směru.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>Struktura definuje operátor převodu ([funkce CType](../../../language-reference/functions/ctype-function.md)) z `String` na <xref:System.Data.SqlTypes.SqlString> a druhý z <xref:System.Data.SqlTypes.SqlString> na `String` . Příkaz, který přiřadí `title` k `jobTitle` použití prvního operátoru a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání funkce používá sekundu.  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít. Nepředpokládají, že třída nebo struktura definovala každý operátor, který je k dispozici pro přetížení. Seznam dostupných operátorů naleznete v tématu [příkaz operator](../../../language-reference/statements/operator-statement.md).  
  
 Zahrňte příslušný `Imports` příkaz pro řetězec SQL na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes> ).  
  
 Projekt musí mít odkazy na System. data a System. XML.  
  
## <a name="see-also"></a>Viz také

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)
- [Rozšíření](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../data-types/widening-and-narrowing-conversions.md)
