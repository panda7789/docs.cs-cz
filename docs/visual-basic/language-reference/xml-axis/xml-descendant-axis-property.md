---
title: Vlastnost osy nástupce XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 02bb87235efbdef8a5474fec9799757f75877876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Vlastnost osy nástupce XML (Visual Basic)
Poskytuje přístup k následníky následující: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>Součásti  
 `object`  
 Požadováno. <xref:System.Xml.Linq.XElement> Objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.  
  
 ...<  
 Požadováno. Označuje začátek vlastnost Následnické osy.  
  
 `descendant`  
 Požadováno. Název podřízených uzlů pro přístup k ve formátu [`prefix``:`]`name`.  
  
|Část|Popis|  
|----------|-----------------|  
|`prefix`|Volitelné. Předpona oboru názvů XML pro podřízený uzel. Musí být globální obor názvů XML, který je definován pomocí `Imports` příkaz.|  
|`name`|Požadováno. Místní název následné uzlu. V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Požadováno. Označuje konec vlastnost Následnické osy.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce <xref:System.Xml.Linq.XElement> objekty.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít vlastnost osy nástupce XML pro přístup k následnickým uzly podle názvu z <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty. Použít soubor XML `Value` vlastnost pro přístup k hodnotě první podřízený uzel v vrácená kolekce. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Visual Basic – kompilátor převede vlastnosti osy nástupce volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metoda.  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Název v vlastnost osy nástupce můžete použít pouze obory názvů XML globálně deklarovat s `Imports` příkaz. Obory názvů XML lokálně deklarované v rámci elementu XML – literály nemůže používat. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat přístup k hodnotě první podřízený uzel s názvem `name` a hodnoty všechny následné uzlech s názvem `phone` z `contacts` objektu.  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k hodnotě první podřízený uzel s kvalifikovaný název `ns:name`.  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
