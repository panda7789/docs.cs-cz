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
ms.openlocfilehash: a7a93608d14bcbec316228b59467b23e9247e043
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828798"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Vlastnost osy atributu XML (Visual Basic)
Poskytuje přístup k hodnotě atributu pro <xref:System.Xml.Linq.XElement> objekt nebo na první prvek v kolekci <xref:System.Xml.Linq.XElement> objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Součásti  
 `object`  
 Povinný parametr. <xref:System.Xml.Linq.XElement> Objektu nebo kolekci <xref:System.Xml.Linq.XElement> objekty.  
  
 .@  
 Povinný parametr. Označuje začátek vlastnost osy atributu.  
  
 <  
 Volitelné. Označuje začátek název atributu při `attribute` není platný identifikátor v jazyce Visual Basic.  
  
 `attribute`  
 Povinný parametr. Název atributu pro přístup k ve tvaru [`prefix`:]`name`.  
  
|Část|Popis|  
|----------|-----------------|  
|`prefix`|Volitelné. Předpona oboru názvů XML pro atribut. Musí se definovat globální obor názvů XML `Imports` příkazu.|  
|`name`|Povinný parametr. Local – atribut názvu. Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Volitelné. Označuje konec názvu atributu při `attribute` není platný identifikátor v jazyce Visual Basic.  
  
## <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje hodnotu `attribute`. Pokud název neexistuje, `Nothing` je vrácena.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu prostřednictvím jeho názvu <xref:System.Xml.Linq.XElement> objektu nebo z první prvek v kolekci <xref:System.Xml.Linq.XElement> objekty. Hodnotu atributu načíst podle názvu nebo přidat nový atribut na prvek tak, že zadáte nový název, před kterými @ identifikátor.  
  
 Když budete odkazovat na atribut XML s použitím @ identifikátor, vrátí se hodnota atributu jako řetězec a není potřeba explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.  
  
 Pravidla pojmenování atributů XML se liší od pravidla pojmenování identifikátorů jazyka Visual Basic. Pro přístup k atributu XML, který má název, který není platným identifikátorem jazyka Visual Basic, uzavřete název v ostrých závorek (\< a >).  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Název ve vlastnosti osy atribut lze použít pouze předpon oboru názvů XML globálně deklarovaná příkazem using `Imports` příkazu. Místně deklarované v rámci elementu literály XML předpon názvového prostoru XML nemůže používat. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce elementů XML, které jsou pojmenovány `phone`.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Tento kód zobrazí následující text:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit atributy pro element XML i deklarativně, jako součást XML a dynamicky tak, že přidáte atribut k instanci <xref:System.Xml.Linq.XElement> objektu. `type` Atributu je vytvořen pomocí deklarace a `owner` atribut se vytváří dynamicky.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá syntaxi ostré závorky k získání hodnoty atributu XML s názvem `number-type`, což není platný identifikátor v jazyce Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: work`  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel s kvalifikovaným názvem "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
