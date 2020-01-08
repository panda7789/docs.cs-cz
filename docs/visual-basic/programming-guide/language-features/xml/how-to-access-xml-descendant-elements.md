---
title: 'Postupy: Přístup k následnickým elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347159"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Postupy: Přístup k následnickým elementům XML (Visual Basic)
Tento příklad ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v elementu XML. Konkrétně používá vlastnost `Value` k získání hodnoty prvního prvku v kolekci, kterou vrací vlastnost osy `name` následníka. Vlastnost osy `name` následníka získá všechny prvky pojmenované `name`, které jsou obsaženy v objektu `contacts`. Tento příklad také používá vlastnost `phone` následníka pro přístup ke všem následníkům s názvem `phone`, které jsou obsaženy v objektu `contacts`.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na obor názvů <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Vlastnost osy nástupce XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Přístup k XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
