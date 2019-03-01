---
title: 'Postupy: Přístup k Následnickým elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 1edbbc052bbf319d91f1f944451312e7d67594ca
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973857"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Postupy: Přístup k Následnickým elementům XML (Visual Basic)
Tento příklad ukazuje, jak používat vlastnost Následnické osy pro přístup k všech elementů XML, které jsou obsaženy v rámci elementu XML, které mají zadaný název. Konkrétně se použije `Value` vlastnost k získání hodnoty prvního prvku v kolekci, která `name` vrátí vlastnost Následnické osy. `name` Vlastnost Následnické osy získá všechny prvky s názvem `name` , které jsou součástí `contacts` objektu. Tento příklad také používá `phone` vlastnost Následnické osy pro přístup k všech potomků s názvem `phone` , které jsou součástí `contacts` objektu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System.Xml.Linq> oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Vlastnost osy nástupce XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
