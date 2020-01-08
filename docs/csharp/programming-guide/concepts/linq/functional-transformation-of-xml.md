---
title: Funkční transformace jazyka XML (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 83ecd97f9319027dc50f346abf7a9888b5c23862
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336799"
---
# <a name="functional-transformation-of-xml-c"></a>Funkční transformace jazyka XML (C#)
Toto téma popisuje přístup čistě funkční transformace pro úpravu dokumentů XML a kontrastuje ho s procedurálním přístupem.  
  
## <a name="modifying-an-xml-document"></a>Úprava dokumentu XML  
 Jedna z nejběžnějších úloh pro programátory XML je transformace XML z jednoho obrazce na druhý. Tvar dokumentu XML je struktura dokumentu, která obsahuje následující:  
  
- Hierarchie vyjádřená dokumentem.  
  
- Názvy elementů a atributů.  
  
- Datové typy prvků a atributů.  
  
 Obecně platí, že nejúčinnější přístup k transformaci XML z jednoho tvaru na druhý je výsledkem čistě funkční transformace. V tomto přístupu je primární programátorský úkol vytvořit transformaci, která se aplikuje na celý dokument XML (nebo na jeden nebo více striktně definovaných uzlů). Funkční transformace je pravděpodobně nejsnadnější na kód (po tom, co programátor je obeznámen s přístupem), poskytuje nejvíc udržovatelný kód a je často kompaktnější než alternativní přístupy.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkční transformační technologie XML  
 Společnost Microsoft nabízí dvě funkční transformační technologie pro použití v dokumentech XML: XSLT a LINQ to XML. XSLT je podporován ve spravovaném oboru názvů <xref:System.Xml.Xsl> a v nativní implementaci jazyka COM služby MSXML. I když je XSLT robustní technologie pro manipulaci s dokumenty XML, vyžaduje odbornost ve specializované doméně, konkrétně v jazyce XSLT a jeho podpůrných rozhraních API.  
  
 LINQ to XML poskytuje nástroje potřebné pro kód čistě funkční transformace v rámci C# kódu nebo Visual Basic. Mnohé z příkladů v dokumentaci LINQ to XML například využívají čistě funkční přístup. V tomto kurzu taky [: manipulace s obsahem v WordprocessingML dokumentu (C#)](./shape-of-wordprocessingml-documents.md) , používáme LINQ to XML ve funkčním přístupu k manipulaci s informacemi v dokumentu Microsoft Wordu.  
  
 Podrobnější porovnání LINQ to XML s dalšími technologiemi Microsoft XML najdete v tématu [LINQ to XML vs. další technologie XML](./linq-to-xml-vs-other-xml-technologies.md).  
  
XSLT je doporučeným nástrojem pro transformace orientované na dokument, pokud zdrojový dokument má nepravidelnou strukturu. LINQ to XML však může také provádět transformace orientované na dokument. Další informace najdete v tématu [Jak používat poznámky k transformaci LINQ to XMLch stromů ve stylu XSLT (C#)](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).
  
## <a name="see-also"></a>Viz také:

- [Úvod do čistě funkční transformace (C#)](./introduction-to-pure-functional-transformations.md)
- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
- [LINQ to XML vs. další technologie XML](./linq-to-xml-vs-other-xml-technologies.md)
