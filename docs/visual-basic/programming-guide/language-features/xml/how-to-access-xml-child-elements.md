---
title: 'Postupy: Přístup k podřízeným elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 92ecea2c2e6e117add37b30498f5fb34adfeac6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626651"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Postupy: Přístup k podřízeným elementům XML (Visual Basic)
Tento příklad ukazuje, jak používat podřízený – vlastnost osy pro přístup k všechny podřízené prvky XML, které mají zadaný název v elementu jazyka XML. Konkrétně se použije <xref:System.Xml.Linq.XElement.Value%2A> vlastnost k získání hodnoty prvního prvku v kolekci, která `name` vrátí vlastnost podřízené osy. `name` – Vlastnost podřízené osy získá všechny podřízené prvky s názvem `phone` v `contact` objektu. Tento příklad také používá `phone` – vlastnost podřízené osy pro přístup k všechny podřízené prvky s názvem `phone` , které jsou součástí `contact` objektu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System.Xml.Linq> oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Vlastnost osy podřízeného XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
