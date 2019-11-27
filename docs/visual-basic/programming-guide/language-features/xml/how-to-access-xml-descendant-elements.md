---
title: 'Postupy: Přístup k následnickým elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 63a094c3c2b20736f0ef6589c76d53b7cc96b29a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332317"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Postupy: Přístup k následnickým elementům XML (Visual Basic)
Tento příklad ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v elementu XML. Konkrétně používá vlastnost `Value` k získání hodnoty prvního prvku v kolekci, kterou vrací vlastnost osy `name` následníka. Vlastnost osy `name` následníka získá všechny prvky pojmenované `name`, které jsou obsaženy v objektu `contacts`. Tento příklad také používá vlastnost `phone` následníka pro přístup ke všem následníkům s názvem `phone`, které jsou obsaženy v objektu `contacts`.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na obor názvů <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Vlastnost osy nástupce XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Přístup k XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
