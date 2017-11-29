---
title: "Funkční transformace XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69cd09a017ab7fbf9fc56a6724abb4cc15b3e1cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Funkční transformace XML (Visual Basic)
Toto téma popisuje čistý funkční transformace přístup k úpravě XML – dokumenty a liší se od procedurální přístup.  
  
## <a name="modifying-an-xml-document"></a>Úpravy dokumentu XML  
 Jeden z nejčastějších úloh pro programátory XML je převod XML z jednoho obrazce do jiného. Obrazec, dokumentu XML je strukturu dokumentu, který zahrnuje následující:  
  
-   Hierarchie vyjádřená dokumentu.  
  
-   Název elementu a atributu.  
  
-   Datové typy elementů a atributů.  
  
 Obecně platí co nejúčinnější způsob převod XML z jednoho obrazce do jiného je, že čistý funkční transformace. Úlohu primární programátory tohoto přístupu je vytvoření transformace, které se použije celý dokument XML (nebo jeden nebo více uzlů výhradně definované). Funkční transformaci je pravděpodobně nejsnadnější kód (po obeznámeni s přístupem programátory), poskytuje nejvíc udržovatelného kódu a je často více než alternativní přístupy compact.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkční Transformational technologií XML  
 Společnost Microsoft nabízí dva funkční transformace technologie pro použití na dokumenty XML: XSLT a technologie LINQ to XML. XSLT je podporována v <xref:System.Xml.Xsl> spravovat obor názvů a nativní implementace COM MSXML. I když XSLT je robustní technologie pro manipulaci s dokumenty XML, vyžaduje znalosti v specializované domény, a to jazyka XSLT a jeho podpůrné rozhraní API.  
  
 Technologie LINQ to XML poskytuje nástroje potřebné k čisté funkční transformace kód výrazovou a výkonné způsobem, v rámci kódu C# nebo Visual Basic. Například mnoho tyto příklady v LINQ dokumentace XML pomocí čistý funkční přístup. Také v [kurz: manipulace s obsahu v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurzu používáme technologie LINQ to XML v rámci funkční přístupu k manipulaci s informace v dokumentu Microsoft Wordu.  
  
 Obsáhlejší porovnání technologie LINQ to XML s jinými technologiemi Microsoft XML najdete v tématu [technologie LINQ to XML vs. Další technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT je doporučeným nástrojem pro závislé na dokumentech transformace při zdrojový dokument má nestandardní strukturu. Technologie LINQ to XML však můžete také provést na střed dokumentu transformací. Další informace najdete v tématu [postupy: použití poznámky transformace technologie LINQ to XML stromy v XSLT stylu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Technologie LINQ to XML vs. Další technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)  
 [Technologie LINQ to XML vs. Další technologie XML](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
