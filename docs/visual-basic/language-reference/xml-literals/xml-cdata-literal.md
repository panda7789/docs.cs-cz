---
title: Literál XML CDATA (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 248f3cf31f686de3af2ea06012aa4a6d4f3f29fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942921"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literál XML CDATA (Visual Basic)
Literál představující <xref:System.Xml.Linq.XCData> objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Součásti  
 `<![CDATA[`  
 Povinný parametr. Označuje začátek oddílu CDATA XML.  
  
 `content`  
 Povinný parametr. Textový obsah, který se má zobrazit v oddílu CDATA XML  
  
 `]]>`  
 Povinný parametr. Označuje konec oddílu.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XCData> Objekt.  
  
## <a name="remarks"></a>Poznámky  
 Oddíly XML CDATA obsahují nezpracovaný text, který by měl být zahrnut, ale ne analyzován, s XML, který jej obsahuje. Oddíl CDATA XML může obsahovat libovolný text. To zahrnuje vyhrazené znaky XML. Oddíl CDATA XML končí sekvencí "]] >". To zahrnuje následující body:  
  
- V literálu CDATA XML nelze použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem CDATA XML.  
  
- Oddíly XML CDATA nemůžou být vnořené, `content` protože nesmí obsahovat hodnotu "]] >".  
  
 Můžete přiřadit literál CDATA XML proměnné nebo jej zahrnout do literálu elementu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků, ale nepoužívá znaky pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál XML CDATA na volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří oddíl CDATA, který obsahuje text "může obsahovat literál \<XML > značek".  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XCData>
- [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
