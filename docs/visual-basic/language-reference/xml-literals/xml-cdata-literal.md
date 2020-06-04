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
ms.openlocfilehash: b9cc830d27625f192d8f5e059bd3783d05d8ba3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400225"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literál XML CDATA (Visual Basic)
Literál představující <xref:System.Xml.Linq.XCData> objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Součásti  
 `<![CDATA[`  
 Povinná hodnota. Označuje začátek oddílu CDATA XML.  
  
 `content`  
 Povinná hodnota. Textový obsah, který se má zobrazit v oddílu CDATA XML  
  
 `]]>`  
 Povinná hodnota. Označuje konec oddílu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XCData>.  
  
## <a name="remarks"></a>Poznámky  
 Oddíly XML CDATA obsahují nezpracovaný text, který by měl být zahrnut, ale ne analyzován, s XML, který jej obsahuje. Oddíl CDATA XML může obsahovat libovolný text. To zahrnuje vyhrazené znaky XML. Oddíl CDATA XML končí sekvencí "]] >". To zahrnuje následující body:  
  
- V literálu CDATA XML nelze použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem CDATA XML.  
  
- Oddíly XML CDATA nemůžou být vnořené, protože `content` nesmí obsahovat hodnotu "]] >".  
  
 Můžete přiřadit literál CDATA XML proměnné nebo jej zahrnout do literálu elementu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků, ale nepoužívá znaky pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál XML CDATA na volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří oddíl CDATA obsahující text "může obsahovat literální \<XML> značky".  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XCData>
- [Literál XML elementu](xml-element-literal.md)
- [Literály XML](index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
