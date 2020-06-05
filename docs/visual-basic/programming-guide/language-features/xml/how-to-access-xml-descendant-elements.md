---
title: 'Postupy: Přístup k následnickým elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 03c403aa3c187b0b9d2006104eccaa1f9cd8aec5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392633"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Postupy: Přístup k následnickým elementům XML (Visual Basic)
Tento příklad ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v elementu XML. Konkrétně používá `Value` vlastnost k získání hodnoty prvního prvku v kolekci, kterou `name` vrací vlastnost osy následníka. `name`Vlastnost osy následníka získá všechny prvky s názvem `name` , které jsou obsaženy v `contacts` objektu. Tento příklad také používá `phone` vlastnost následníka pro přístup ke všem následníkům s názvem `phone` , které jsou obsaženy v `contacts` objektu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Tento příklad vyžaduje:  
  
- Odkaz na <xref:System.Xml.Linq> obor názvů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Vlastnost osy nástupce XML](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [Vlastnost hodnoty XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Přístup ke XML v jazyce Visual Basic](accessing-xml.md)
- [XML](index.md)
