---
title: Vlastnost osy podřízeného XML
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
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400263"
---
# <a name="xml-child-axis-property-visual-basic"></a>Vlastnost osy podřízeného souboru XML (Visual Basic)
Poskytuje přístup k podřízeným položkám jednoho z následujících objektů: <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`object`|Povinná hodnota. <xref:System.Xml.Linq.XElement>Objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.|  
|. <|Povinná hodnota. Označuje začátek podřízené vlastnosti osy.|  
|`child`|Povinná hodnota. Název podřízených uzlů, pro které má být přístup, ve formuláři `[prefix:]name` .<br /><br /> -   `Prefix`Volitelné. Předpona oboru názvů XML pro podřízený uzel. Musí být globální obor názvů XML definovaný `Imports` příkazem.<br />-   `Name`Požadovanou. Název místního podřízeného uzlu. Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Povinná hodnota. Označuje konec podřízené vlastnosti osy.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce objektů <xref:System.Xml.Linq.XElement>.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít vlastnost podřízené osy XML pro přístup k podřízeným uzlům podle názvu z <xref:System.Xml.Linq.XElement> objektu nebo nebo <xref:System.Xml.Linq.XDocument> z kolekce <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objektů nebo. Použijte vlastnost XML `Value` pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci. Další informace najdete v tématu [vlastnost hodnoty XML](xml-value-property.md).  
  
 Kompilátor Visual Basic převede vlastnosti podřízené osy na volání <xref:System.Xml.Linq.XContainer.Elements%2A> metody.  
  
## <a name="xml-namespaces"></a>XML – obory názvů  
 Název v podřízené vlastnosti osy může používat pouze předpony oboru názvů XML deklarované globálně s `Imports` příkazem. Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přistupovat k podřízeným uzlům s názvem `phone` z `contact` objektu.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Tento kód zobrazí následující text:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přistupovat k podřízeným uzlům, které jsou pojmenovány `phone` z kolekce vrácené `contact` vlastností podřízené osy `contacts` objektu.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Tento kód zobrazí následující text:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem `ns:name` .  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Tento kód zobrazí následující text:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](index.md)
- [Literály XML](../xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
