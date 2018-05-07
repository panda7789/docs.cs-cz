---
title: Vlastnost osy atributu XML (Visual Basic)
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
ms.openlocfilehash: 3e02fd2ddc3928bdd2e9741737fc31fb2b16901c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Vlastnost osy atributu XML (Visual Basic)
Poskytuje přístup k hodnotě atributu pro <xref:System.Xml.Linq.XElement> objektu nebo na prvním elementem v kolekci <xref:System.Xml.Linq.XElement> objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Součásti  
 `object`  
 Požadováno. <xref:System.Xml.Linq.XElement> Objektu nebo kolekci <xref:System.Xml.Linq.XElement> objekty.  
  
 .@  
 Požadováno. Označuje začátek vlastnost osy atributu.  
  
 <  
 Volitelné. Označuje začátek název atributu, když `attribute` není platný identifikátor v jazyce Visual Basic.  
  
 `attribute`  
 Požadováno. Název atributu pro přístup k ve formátu [`prefix`:]`name`.  
  
|Část|Popis|  
|----------|-----------------|  
|`prefix`|Volitelné. Předpona oboru názvů XML pro atribut. Musí být globální obor názvů XML definovány se `Imports` příkaz.|  
|`name`|Požadováno. Local – atribut názvu. V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Volitelné. Označuje konec název atributu, když `attribute` není platný identifikátor v jazyce Visual Basic.  
  
## <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje hodnotu `attribute`. Pokud název neexistuje, `Nothing` je vrácen.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu podle názvu z <xref:System.Xml.Linq.XElement> objekt nebo z první prvek v kolekci <xref:System.Xml.Linq.XElement> objekty. Můžete načíst hodnotu atributu podle názvu nebo přidat nový atribut pro element tak, že zadáte nový název předchází @ identifikátor.  
  
 Když odkazujete na atribut XML pomocí @ identifikátoru, je vrácena hodnota atributu jako řetězec a není nutné explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.  
  
 Pravidla pojmenování pro atributy XML se liší od pravidla pojmenování pro identifikátory jazyka Visual Basic. Pro přístup k atribut XML, který má název, který není platný identifikátor jazyka Visual Basic, uzavřete název v lomených závorkách (\< a >).  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Název v vlastnost osy atributu můžete použít pouze XML – předpony oboru názvů deklarovat globálně pomocí `Imports` příkaz. Nemůže používat lokálně deklarované v rámci elementu XML – literály XML – předpony oboru názvů. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce elementů XML, které jsou s názvem `phone`.  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořte atributy pro element XML i deklarativně, v rámci kódu XML a dynamicky přidáním atribut na instanci <xref:System.Xml.Linq.XElement> objektu. `type` Atribut je vytvořen deklarativně a `owner` atribut se vytváří dynamicky.  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá syntaxi lomená závorka k získání hodnoty atributu XML s názvem `number-type`, což není platný identifikátor v jazyce Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: work`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel s kvalifikovaný název "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
