---
title: Funkční transformace XML (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: f6702a29d79aa66cc5cb11c9a889861398d46ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322546"
---
# <a name="functional-transformation-of-xml-c"></a>Funkční transformace XML (C#)
Toto téma popisuje čistý funkční transformace přístup k úpravě XML – dokumenty a liší se od procedurální přístup.  
  
## <a name="modifying-an-xml-document"></a>Úpravy dokumentu XML  
 Jeden z nejčastějších úloh pro programátory XML je převod XML z jednoho obrazce do jiného. Obrazec, dokumentu XML je strukturu dokumentu, který zahrnuje následující:  
  
-   Hierarchie vyjádřená dokumentu.  
  
-   Název elementu a atributu.  
  
-   Datové typy elementů a atributů.  
  
 Obecně platí co nejúčinnější způsob převod XML z jednoho obrazce do jiného je, že čistý funkční transformace. Úlohu primární programátory tohoto přístupu je vytvoření transformace, které se použije celý dokument XML (nebo jeden nebo více uzlů výhradně definované). Funkční transformaci je pravděpodobně nejsnadnější kód (po obeznámeni s přístupem programátory), poskytuje nejvíc udržovatelného kódu a je často více než alternativní přístupy compact.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkční Transformational technologií XML  
 Společnost Microsoft nabízí dva funkční transformace technologie pro použití na dokumenty XML: XSLT a technologie LINQ to XML. XSLT je podporována v <xref:System.Xml.Xsl> spravovat obor názvů a nativní implementace COM MSXML. I když XSLT je robustní technologie pro manipulaci s dokumenty XML, vyžaduje znalosti v specializované domény, a to jazyka XSLT a jeho podpůrné rozhraní API.  
  
 Technologie LINQ to XML poskytuje nástroje potřebné k čisté funkční transformace kód výrazovou a výkonné způsobem, v rámci kódu C# nebo Visual Basic. Například mnoho tyto příklady v LINQ dokumentace XML pomocí čistý funkční přístup. Také v [kurz: manipulace s obsahu v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurzu používáme technologie LINQ to XML v rámci funkční přístupu k manipulaci s informace v dokumentu Microsoft Wordu.  
  
 Obsáhlejší porovnání technologie LINQ to XML s jinými technologiemi Microsoft XML najdete v tématu [technologie LINQ to XML vs. Další technologie XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT je doporučeným nástrojem pro závislé na dokumentech transformace při zdrojový dokument má nestandardní strukturu. Technologie LINQ to XML však můžete také provést na střed dokumentu transformací. Další informace najdete v tématu [postupy: použití poznámky transformace technologie LINQ to XML stromy v XSLT stylu (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [Technologie LINQ to XML versus jiné technologie XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
