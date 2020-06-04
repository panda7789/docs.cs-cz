---
title: Funkční transformace XML
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: b82030f5763f24feca5b50a5dd84283943ba9bcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398445"
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
 Společnost Microsoft nabízí dvě funkční transformační technologie pro použití v dokumentech XML: XSLT a LINQ to XML. XSLT je podporován ve <xref:System.Xml.Xsl> spravovaném oboru názvů a v nativní implementaci modelu COM v rámci služby MSXML. I když je XSLT robustní technologie pro manipulaci s dokumenty XML, vyžaduje odbornost ve specializované doméně, konkrétně v jazyce XSLT a jeho podpůrných rozhraních API.  
  
 LINQ to XML poskytuje nástroje potřebné pro kódování čistě funkčních transformací v rámci kódu C# nebo Visual Basic. Mnohé z příkladů v dokumentaci LINQ to XML například využívají čistě funkční přístup. V tomto kurzu taky [: manipulace s obsahem v WordprocessingML dokumentu (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) , používáme LINQ to XML ve funkčním přístupu k manipulaci s informacemi v dokumentu Microsoft Wordu.  
  
 Podrobnější porovnání LINQ to XML s dalšími technologiemi Microsoft XML najdete v tématu [LINQ to XML vs. další technologie XML](linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT je doporučeným nástrojem pro transformace orientované na dokument, pokud zdrojový dokument má nepravidelnou strukturu. LINQ to XML však může také provádět transformace orientované na dokument. Další informace najdete v tématu [Postupy: použití poznámek k transformaci LINQ to XMLch stromů ve stylu XSLT (Visual Basic)](how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Viz také

- [Úvod do čistě funkční transformace (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [Technologie LINQ to XML vs. jiné technologie XML](linq-to-xml-vs-other-xml-technologies.md)
