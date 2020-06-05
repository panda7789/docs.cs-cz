---
title: 'Postupy: Přístup k podřízeným elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392815"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Postupy: Přístup k podřízeným elementům XML (Visual Basic)
Tento příklad ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML. Konkrétně používá <xref:System.Xml.Linq.XElement.Value%2A> vlastnost k získání hodnoty prvního prvku v kolekci, kterou `name` vrací vlastnost podřízené osy. `name`Vlastnost podřízené osy získá všechny podřízené elementy s názvem `phone` v `contact` objektu. Tento příklad také používá `phone` vlastnost podřízené osy pro přístup ke všem podřízeným prvkům s názvem `phone` , které jsou obsaženy v `contact` objektu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Tento příklad vyžaduje:  
  
- Odkaz na <xref:System.Xml.Linq> obor názvů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Vlastnost osy podřízeného XML](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost hodnoty XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Přístup ke XML v jazyce Visual Basic](accessing-xml.md)
- [XML](index.md)
