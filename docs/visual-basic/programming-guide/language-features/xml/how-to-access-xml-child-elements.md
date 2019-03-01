---
title: 'Postupy: Přístup k podřízeným elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 874c7490e451d64bf50e25934ea43a9b928ddab9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980552"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Postupy: Přístup k podřízeným elementům XML (Visual Basic)
Tento příklad ukazuje, jak používat podřízený – vlastnost osy pro přístup k všechny podřízené prvky XML, které mají zadaný název v elementu jazyka XML. Konkrétně se použije <xref:System.Xml.Linq.XElement.Value%2A> vlastnost k získání hodnoty prvního prvku v kolekci, která `name` vrátí vlastnost podřízené osy. `name` – Vlastnost podřízené osy získá všechny podřízené prvky s názvem `phone` v `contact` objektu. Tento příklad také používá `phone` – vlastnost podřízené osy pro přístup k všechny podřízené prvky s názvem `phone` , které jsou součástí `contact` objektu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System.Xml.Linq> oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Vlastnost osy podřízeného XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
