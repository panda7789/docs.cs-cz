---
title: Literál XML CDATA
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349437"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literál XML CDATA (Visual Basic)
Literál představující objekt <xref:System.Xml.Linq.XCData>.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Součásti  
 `<![CDATA[`  
 Požadováno. Označuje začátek oddílu CDATA XML.  
  
 `content`  
 Požadováno. Textový obsah, který se má zobrazit v oddílu CDATA XML  
  
 `]]>`  
 Požadováno. Označuje konec oddílu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XCData>.  
  
## <a name="remarks"></a>Poznámky  
 Oddíly XML CDATA obsahují nezpracovaný text, který by měl být zahrnut, ale ne analyzován, s XML, který jej obsahuje. Oddíl CDATA XML může obsahovat libovolný text. To zahrnuje vyhrazené znaky XML. Oddíl CDATA XML končí sekvencí "]] >". To zahrnuje následující body:  
  
- V literálu CDATA XML nelze použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem CDATA XML.  
  
- Oddíly XML CDATA nemohou být vnořené, protože `content` nesmí obsahovat hodnotu "]] >".  
  
 Můžete přiřadit literál CDATA XML proměnné nebo jej zahrnout do literálu elementu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků, ale nepoužívá znaky pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál XML CDATA na volání konstruktoru <xref:System.Xml.Linq.XCData.%23ctor%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří oddíl CDATA, který obsahuje text "může obsahovat literál \<> značky XML.  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XCData>
- [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
