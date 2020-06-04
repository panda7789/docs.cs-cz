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
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408429"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Vlastnost osy atributu XML (Visual Basic)
Poskytuje přístup k hodnotě atributu pro <xref:System.Xml.Linq.XElement> objekt nebo na první prvek kolekce <xref:System.Xml.Linq.XElement> objektů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Součásti  
 `object`  
 Povinná hodnota. <xref:System.Xml.Linq.XElement>Objekt nebo kolekce <xref:System.Xml.Linq.XElement> objektů.  
  
 .@  
 Povinná hodnota. Označuje začátek Vlastnosti osy atributu.  
  
 <  
 Nepovinný parametr. Označuje začátek názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.  
  
 `attribute`  
 Povinná hodnota. Název atributu, pro který má být přístup, z formuláře [ `prefix` :] `name` .  
  
|Část|Description|  
|----------|-----------------|  
|`prefix`|Nepovinný parametr. Předpona oboru názvů XML pro atribut Musí být globální obor názvů XML definovaný `Imports` příkazem.|  
|`name`|Povinná hodnota. Název místního atributu Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Nepovinný parametr. Označuje konec názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.  
  
## <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje hodnotu `attribute` . Pokud název atributu neexistuje, `Nothing` je vrácen.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu podle názvu z <xref:System.Xml.Linq.XElement> objektu nebo z prvního prvku v kolekci <xref:System.Xml.Linq.XElement> objektů. Můžete načíst hodnotu atributu podle názvu nebo přidat nový atribut k elementu zadáním nového názvu předchází identifikátor @.  
  
 Když odkazujete na atribut XML pomocí @ identifikátor, vrátí se hodnota atributu jako řetězec a nemusíte explicitně zadávat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.  
  
 Pravidla pro pojmenování atributů XML se liší od pravidel pro pojmenování Visual Basicch identifikátorů. Chcete-li získat přístup k atributu XML, který má název, který není platným identifikátorem Visual Basic, uveďte název do lomených závorek ( \< and > ).  
  
## <a name="xml-namespaces"></a>XML – obory názvů  
 Název ve vlastnosti osa atributu může používat pouze předpony oboru názvů XML deklarované globálně pomocí `Imports` příkazu. Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce elementů XML s názvem `phone` .  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Tento kód zobrazí následující text:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit atributy pro element XML deklarativně, jako součást XML a dynamicky přidáním atributu do instance <xref:System.Xml.Linq.XElement> objektu. `type`Atribut je vytvořen deklarativně a `owner` atribut je vytvořen dynamicky.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá syntaxi lomené závorky k získání hodnoty atributu XML s názvem `number-type` , který není platným identifikátorem v Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: work`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem " `ns:name` ".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](index.md)
- [Literály XML](../xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
