---
title: Vlastnost osy atributu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352675"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Vlastnost osy atributu XML (Visual Basic)
Poskytuje přístup k hodnotě atributu pro objekt <xref:System.Xml.Linq.XElement> nebo k prvnímu prvku kolekce objektů <xref:System.Xml.Linq.XElement>.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Součásti  
 `object`  
 Požadováno. Objekt <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XElement>.  
  
 .@  
 Požadováno. Označuje začátek Vlastnosti osy atributu.  
  
 <  
 Volitelná. Označuje začátek názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.  
  
 `attribute`  
 Požadováno. Název atributu, pro který má být přístup, z formuláře [`prefix`:]`name`.  
  
|Částí|Popis|  
|----------|-----------------|  
|`prefix`|Volitelná. Předpona oboru názvů XML pro atribut Musí být globální obor názvů XML definovaný pomocí příkazu `Imports`.|  
|`name`|Požadováno. Název místního atributu Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Volitelná. Označuje konec názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.  
  
## <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje hodnotu `attribute`. Pokud název atributu neexistuje, `Nothing` se vrátí.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu podle názvu z objektu <xref:System.Xml.Linq.XElement> nebo z prvního prvku kolekce objektů <xref:System.Xml.Linq.XElement>. Můžete načíst hodnotu atributu podle názvu nebo přidat nový atribut k elementu zadáním nového názvu předchází identifikátor @.  
  
 Když odkazujete na atribut XML pomocí @ identifikátor, vrátí se hodnota atributu jako řetězec a nemusíte explicitně určovat vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>.  
  
 Pravidla pro pojmenování atributů XML se liší od pravidel pro pojmenování Visual Basicch identifikátorů. Chcete-li získat přístup k atributu XML, který má název, který není platným identifikátorem Visual Basic, zadejte název do lomených závorek (\< a >).  
  
## <a name="xml-namespaces"></a>XML – obory názvů  
 Název ve vlastnosti osy atributu může používat pouze předpony oboru názvů XML deklarované globálně pomocí příkazu `Imports`. Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce prvků XML s názvem `phone`.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Tento kód zobrazí následující text:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit atributy pro element XML deklarativně, jako součást XML a dynamicky přidáním atributu do instance objektu <xref:System.Xml.Linq.XElement>. Atribut `type` se vytvoří deklarativně a dynamicky se vytvoří atribut `owner`.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá syntaxi lomené závorky k získání hodnoty atributu XML s názvem `number-type`, což není platný identifikátor v Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: work`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
