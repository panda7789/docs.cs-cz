---
title: Vlastnost osy podřízeného souboru XML
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
ms.openlocfilehash: 728c17cd2ed8661e0a5f1f2b8e929059713a1edf
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545115"
---
# <a name="xml-child-axis-property-visual-basic"></a>Vlastnost osy podřízeného souboru XML (Visual Basic)
Poskytuje přístup k podřízeným položkám jedné z následujících: objekt <xref:System.Xml.Linq.XElement>, objekt <xref:System.Xml.Linq.XDocument>, kolekci objektů <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XDocument>.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Požadováno. Objekt <xref:System.Xml.Linq.XElement>, objekt <xref:System.Xml.Linq.XDocument>, kolekce objektů <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XDocument>.|  
|.<|Požadováno. Označuje začátek podřízené vlastnosti osy.|  
|`child`|Požadováno. Název podřízených uzlů, pro které má být přístup z formuláře `[prefix:]name`.<br /><br /> -   `Prefix` – volitelné. Předpona oboru názvů XML pro podřízený uzel. Musí být globální obor názvů XML definovaný pomocí příkazu `Imports`.<br />`Name` -   – povinné. Název místního podřízeného uzlu. Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Požadováno. Označuje konec podřízené vlastnosti osy.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce objektů <xref:System.Xml.Linq.XElement>.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost podřízené osy XML můžete použít pro přístup k podřízeným uzlům podle názvu z objektu <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> nebo z kolekce objektů <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>. Pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci použijte vlastnost `Value` XML. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Kompilátor Visual Basic převede vlastnosti podřízené osy na volání metody <xref:System.Xml.Linq.XContainer.Elements%2A>.  
  
## <a name="xml-namespaces"></a>XML – obory názvů  
 Název v podřízené vlastnosti osy může používat pouze předpony oboru názvů XML deklarované globálně s příkazem `Imports`. Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přistupovat k podřízeným uzlům s názvem `phone` z objektu `contact`.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Tento kód zobrazí následující text:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat přístup k podřízeným uzlům s názvem `phone` z kolekce vrácené vlastností `contact` podřízená osa objektu `contacts`.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Tento kód zobrazí následující text:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Tento kód zobrazí následující text:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
