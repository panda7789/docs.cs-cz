---
title: 'Postupy: Vložení výrazů do literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332930"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Postupy: Vložení výrazů do literálů XML (Visual Basic)
Můžete zkombinovat literály XML s vloženými výrazy a vytvořit dokument XML, fragment nebo prvek, který obsahuje obsah vytvořený v době běhu. Následující příklady ukazují, jak použít vložené výrazy k naplnění obsahu prvku, atributů a názvů elementů za běhu.  
  
 Syntaxe vloženého výrazu je `<%=` `exp` `%>`, což je stejná syntaxe, kterou používá ASP.NET. Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 K vytváření objektů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete použít taky rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API. Další informace najdete v tématu <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Vložení textu jako obsahu elementu  
  
- Následující příklad ukazuje, jak vložit text, který je obsažen v proměnné `contactName` mezi prvky pro otevření a zavření názvu.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Vložení textu jako hodnoty atributu  
  
- Následující příklad ukazuje, jak vložit text, který je obsažen v proměnné `phoneType` jako hodnota atributu `type`.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Vložení textu pro název elementu  
  
- Následující příklad ukazuje, jak vložit text, který je obsažen v proměnné `elementName` jako název elementu.  
  
     Při vytváření prvků pomocí této techniky je nutné je zavřít pomocí značky \</>.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření literálů XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [Vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Vytváření XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
