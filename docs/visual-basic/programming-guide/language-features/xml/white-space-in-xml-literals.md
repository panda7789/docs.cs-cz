---
title: Prázdné znaky v literálech XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335998"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Prázdné znaky v literálech XML (Visual Basic)
Kompilátor Visual Basic při vytváření objektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v podnikové síti obsahuje pouze významné znaky mezer z literálu XML. Nevýznamné prázdné znaky nejsou začleněny.  
  
## <a name="significant-and-insignificant-white-space"></a>Významné a nevýznamné prázdné znaky  
 Prázdné znaky v literálech XML jsou významné pouze v třech oblastech:  
  
- Pokud jsou v hodnotě atributu.  
  
- Pokud jsou součástí textového obsahu elementu a text obsahuje také jiné znaky.  
  
- Když jsou ve vloženém výrazu pro textový obsah elementu.  
  
 V opačném případě kompilátor zpracovává prázdné znaky jako nevýznamný a nezahrnuje potom do objektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pro literál.  
  
 Chcete-li zahrnout do literálu XML nevýznamné prázdné znaky, použijte vložený výraz, který obsahuje řetězcový literál s prázdným znakem.  
  
> [!NOTE]
> Pokud se atribut `xml:space` nachází v literálu elementu XML, kompilátor Visual Basic obsahuje atribut v objektu <xref:System.Xml.Linq.XElement>, ale přidání tohoto atributu nemění způsob, jakým kompilátor zpracovává prázdné znaky.  
  
## <a name="examples"></a>Příklady  
 Následující příklad obsahuje dva elementy XML, vnější a vnitřní. Oba elementy obsahují prázdné znaky v textovém obsahu. Prázdné znaky vnějšího prvku jsou nevýznamné, protože obsahují pouze prázdné znaky a XML element. Prázdné znaky v vnitřním prvku jsou významné, protože obsahují prázdné znaky a text.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Při spuštění tento kód zobrazí následující text.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Viz také:

- [Vytváření XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
