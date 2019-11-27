---
title: Funkční transformace XML
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 7e029fd562ae3f221a8aaef40f332a1e3fa896eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353428"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Funkční transformace XML (Visual Basic)
Toto téma popisuje přístup čistě funkční transformace pro úpravu dokumentů XML a kontrastuje ho s procedurálním přístupem.  
  
## <a name="modifying-an-xml-document"></a>Úprava dokumentu XML  
 Jedna z nejběžnějších úloh pro programátory XML je transformace XML z jednoho obrazce na druhý. Tvar dokumentu XML je struktura dokumentu, která obsahuje následující:  
  
- Hierarchie vyjádřená dokumentem.  
  
- Názvy elementů a atributů.  
  
- Datové typy prvků a atributů.  
  
 Obecně platí, že nejúčinnější přístup k transformaci XML z jednoho tvaru na druhý je výsledkem čistě funkční transformace. V tomto přístupu je primární programátorský úkol vytvořit transformaci, která se aplikuje na celý dokument XML (nebo na jeden nebo více striktně definovaných uzlů). Funkční transformace je pravděpodobně nejsnadnější na kód (po tom, co programátor je obeznámen s přístupem), poskytuje nejvíc udržovatelný kód a je často kompaktnější než alternativní přístupy.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkční transformační technologie XML  
 Společnost Microsoft nabízí dvě funkční transformační technologie pro použití v dokumentech XML: XSLT a LINQ to XML. XSLT je podporován ve spravovaném oboru názvů <xref:System.Xml.Xsl> a v nativní implementaci jazyka COM služby MSXML. I když je XSLT robustní technologie pro manipulaci s dokumenty XML, vyžaduje odbornost ve specializované doméně, konkrétně v jazyce XSLT a jeho podpůrných rozhraních API.  
  
 LINQ to XML poskytuje nástroje potřebné pro kód čistě funkční transformace v rámci C# kódu nebo Visual Basic. Mnohé z příkladů v dokumentaci LINQ to XML například využívají čistě funkční přístup. V tomto kurzu taky [: manipulace s obsahem v WordprocessingML dokumentu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) , používáme LINQ to XML ve funkčním přístupu k manipulaci s informacemi v dokumentu Microsoft Wordu.  
  
 Podrobnější porovnání LINQ to XML s dalšími technologiemi Microsoft XML najdete v tématu [LINQ to XML vs. další technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT je doporučeným nástrojem pro transformace orientované na dokument, pokud zdrojový dokument má nepravidelnou strukturu. LINQ to XML však může také provádět transformace orientované na dokument. Další informace najdete v tématu [Postupy: použití poznámek k transformaci LINQ to XMLch stromů ve stylu XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Viz také:

- [Úvod do čistě funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [LINQ to XML vs. další technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
