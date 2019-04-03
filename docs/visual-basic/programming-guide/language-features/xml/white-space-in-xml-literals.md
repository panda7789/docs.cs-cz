---
title: Prázdné znaky v literálech XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 08be345557d10a528aa03234883eba1b3a31beaa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832749"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Prázdné znaky v literálech XML (Visual Basic)
Kompilátor jazyka Visual Basic zahrnuje pouze znaky významných mezer literál XML při vytváření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu. Neplatné prázdné znaky nejsou zahrnuty.  
  
## <a name="significant-and-insignificant-white-space"></a>Prázdné místo důležité a nevýznamné  
 Prázdné znaky v literálech XML jsou významné v pouze tři oblasti:  
  
-   Když jsou v hodnotě atributu.  
  
-   Když jsou součástí obsahu prvku textu a text také obsahuje jiné znaky.  
  
-   Když jsou v vložený výraz pro textový obsah elementu.  
  
 V opačném případě kompilátor považuje za prázdné znaky neplatné a potom nezahrnuje v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt pro literál.  
  
 Zahrnout nevýznamné prázdný znak literálu XML, použijte vložený výraz, který obsahuje řetězcový literál s prázdné znaky.  
  
> [!NOTE]
>  Pokud `xml:space` atributu se zobrazí v elementu XML literál, kompilátor jazyka Visual Basic obsahuje atribut v <xref:System.Xml.Linq.XElement> objektu, ale přidat tento atribut nedojde ke změně způsobu, jakým kompilátor zpracovává prázdné znaky.  
  
## <a name="examples"></a>Příklady  
 Následující příklad obsahuje dva elementy XML, vnitřní a vnější. Oba prvky obsahovat prázdné znaky ve svém textového obsahu. Prázdné znaky na vnější element je neplatné, protože obsahuje pouze prázdné znaky a platný element XML. Prázdný znak ve vnitřní element je důležité, protože obsahuje prázdné znaky a text.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Při spuštění, tento kód zobrazí následující text.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
