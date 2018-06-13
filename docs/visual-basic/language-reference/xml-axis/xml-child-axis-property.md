---
title: Vlastnost osy podřízeného souboru XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 1407a3315d8971895b70893af9d85c8bb428c3be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603857"
---
# <a name="xml-child-axis-property-visual-basic"></a>Vlastnost osy podřízeného souboru XML (Visual Basic)
Poskytuje přístup k podřízené objekty daného jednu z následujících: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.<child>  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Požadováno. <xref:System.Xml.Linq.XElement> Objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.|  
|.<|Požadováno. Označuje začátek vlastnost osy podřízeného.|  
|`child`|Požadováno. Název podřízené uzly pro přístup k ve formátu [`prefix``:`]`name`.<br /><br /> -   `Prefix` -Volitelné. Předpona oboru názvů XML pro podřízený uzel. Musí být globální obor názvů XML definovány se `Imports` příkaz.<br />-   `Name` -Vyžaduje. Název místní podřízený uzel. V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Požadováno. Označuje konec vlastnost osy podřízeného.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce <xref:System.Xml.Linq.XElement> objekty.  
  
## <a name="remarks"></a>Poznámky  
 Můžete vlastnost osy podřízeného souboru XML pro přístup k podřízené uzly podle názvu z <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty. Použít soubor XML `Value` vlastnost pro přístup k hodnotě první podřízený uzel v vrácená kolekce. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Visual Basic – kompilátor převede vlastnosti osy podřízeného volání <xref:System.Xml.Linq.XContainer.Elements%2A> metoda.  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Název v vlastnost osy podřízeného můžete použít pouze XML – předpony oboru názvů globálně deklarovat s `Imports` příkaz. Nemůže používat lokálně deklarované v rámci elementu XML – literály XML – předpony oboru názvů. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat přístup k podřízené uzly s názvem `phone` z `contact` objektu.  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat přístup k podřízené uzly s názvem `phone` z kolekce vrácené `contact` vlastnost podřízené osy `contacts` objektu.  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel s kvalifikovaný název `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
