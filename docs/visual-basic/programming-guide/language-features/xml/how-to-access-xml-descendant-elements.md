---
title: 'Postupy: Přístup k následnickým elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 6d41844b540631df96740ce56818c125cf85e928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Postupy: Přístup k následnickým elementům XML (Visual Basic)
Tento příklad ukazuje, jak používat vlastnost osy nástupce pro přístup k všech elementů XML, které jsou obsažené v elementu XML, které mají zadaný název. Konkrétně používá `Value` vlastnost, která má získat hodnotu první prvek v kolekci, která `name` vrátí vlastnost Následnické osy. `name` Vlastnost osy nástupce získá všechny elementy s názvem `name` , jsou součástí `contacts` objektu. Tento příklad také používá `phone` vlastnost osy nástupce přístup všech potomků s názvem `phone` , jsou součástí `contacts` objektu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System.Xml.Linq> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [Vlastnost osy nástupce XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [Vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Přístup XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
