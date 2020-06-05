---
title: 'Postupy: Vložení výrazů do literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 59ba03be6e132203523427d3b7af5a163b6f05ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392311"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Postupy: Vložení výrazů do literálů XML (Visual Basic)
Můžete zkombinovat literály XML s vloženými výrazy a vytvořit dokument XML, fragment nebo prvek, který obsahuje obsah vytvořený v době běhu. Následující příklady ukazují, jak použít vložené výrazy k naplnění obsahu prvku, atributů a názvů elementů za běhu.  
  
 Syntaxe vloženého výrazu je `<%=` `exp` `%>` , což je stejná syntaxe, kterou používá ASP.NET. Další informace najdete v tématu [vložené výrazy v XML](embedded-expressions-in-xml.md).  
  
 Můžete také použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API k vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektů. Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Vložení textu jako obsahu elementu  
  
- Následující příklad ukazuje, jak vložit text, který je obsažen v `contactName` proměnné mezi otevírací a zavírací prvky názvu.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Vložení textu jako hodnoty atributu  
  
- Následující příklad ukazuje, jak vložit text obsažený v `phoneType` proměnné jako hodnotu `type` atributu.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Vložení textu pro název elementu  
  
- Následující příklad ukazuje, jak vložit text obsažený v `elementName` proměnné jako název elementu.  
  
     Při vytváření prvků pomocí této techniky je nutné je uzavřít se \</> značkou.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytváření literálů XML](how-to-create-xml-literals.md)
- [Vložené výrazy v XML](embedded-expressions-in-xml.md)
- [Vytvoření XML v jazyce Visual Basic](creating-xml.md)
- [XML](index.md)
