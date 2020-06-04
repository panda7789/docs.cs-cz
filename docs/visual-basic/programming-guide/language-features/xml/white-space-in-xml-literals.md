---
title: Prázdné znaky v literálech XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: b3caf7ac052f3fed3fe5427da0cc96bbdd955ea6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360472"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Prázdné znaky v literálech XML (Visual Basic)
Kompilátor Visual Basic při vytváření objektu zahrnuje pouze významné prázdné znaky z literálu XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Nevýznamné prázdné znaky nejsou začleněny.  
  
## <a name="significant-and-insignificant-white-space"></a>Významné a nevýznamné prázdné znaky  
 Prázdné znaky v literálech XML jsou významné pouze v třech oblastech:  
  
- Pokud jsou v hodnotě atributu.  
  
- Pokud jsou součástí textového obsahu elementu a text obsahuje také jiné znaky.  
  
- Když jsou ve vloženém výrazu pro textový obsah elementu.  
  
 V opačném případě kompilátor zpracovává prázdné znaky jako nevýznamný a nezahrnuje pak v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu pro literál.  
  
 Chcete-li zahrnout do literálu XML nevýznamné prázdné znaky, použijte vložený výraz, který obsahuje řetězcový literál s prázdným znakem.  
  
> [!NOTE]
> Pokud se `xml:space` atribut objeví v literálu elementu XML, kompilátor Visual Basic obsahuje atribut v <xref:System.Xml.Linq.XElement> objektu, ale přidáním tohoto atributu se nezmění způsob, jakým kompilátor zpracovává prázdné znaky.  
  
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
  
## <a name="see-also"></a>Viz také

- [Vytvoření XML v jazyce Visual Basic](creating-xml.md)
