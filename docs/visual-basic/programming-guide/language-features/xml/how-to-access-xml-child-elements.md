---
title: 'Postupy: Přístup k podřízeným elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: af5ea809cb0777b16230f20e133764dd5f1f86d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332344"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Postupy: Přístup k podřízeným elementům XML (Visual Basic)
This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element. In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns. The `name` child axis property gets all child elements named `phone` in the `contact` object. This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 This example requires:  
  
- A reference to the <xref:System.Xml.Linq> namespace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Vlastnost osy podřízeného XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
