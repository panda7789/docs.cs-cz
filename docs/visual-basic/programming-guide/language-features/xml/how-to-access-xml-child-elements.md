---
title: 'Postupy: Přístup k podřízeným elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 32bdb1ba476a954bdad1f23c3ecc6129c90ccaac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347179"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Postupy: Přístup k podřízeným elementům XML (Visual Basic)
Tento příklad ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML. Konkrétně používá vlastnost <xref:System.Xml.Linq.XElement.Value%2A> k získání hodnoty prvního prvku v kolekci, kterou vrací vlastnost `name` podřízená osa. Vlastnost `name` podřízená osa získá všechny podřízené elementy s názvem `phone` v objektu `contact`. Tento příklad také používá vlastnost `phone` podřízená osa pro přístup ke všem podřízeným prvkům s názvem `phone`, které jsou obsaženy v objektu `contact`.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na obor názvů <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Vlastnost osy podřízeného XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Přístup k XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
