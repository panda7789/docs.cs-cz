---
title: Funkční transformace XML (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 83ecd97f9319027dc50f346abf7a9888b5c23862
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75336799"
---
# <a name="functional-transformation-of-xml-c"></a>Funkční transformace XML (C#)
Toto téma popisuje čistě funkční transformační přístup k úpravám dokumentů XML a kontrastuje s procedurálním přístupem.  
  
## <a name="modifying-an-xml-document"></a>Úprava dokumentu XML  
 Jedním z nejběžnějších úkolů programátora XML je transformace XML z jednoho obrazce do druhého. Obrazec dokumentu XML je struktura dokumentu, která zahrnuje následující:  
  
- Hierarchie vyjádřená dokumentem.  
  
- Názvy prvků a atributů.  
  
- Datové typy prvků a atributů.  
  
 Obecně platí, že nejúčinnější přístup k transformaci XML z jednoho tvaru do druhého je čistě funkční transformace. V tomto přístupu je primárním programátorem vytvořit transformaci, která se použije na celý dokument XML (nebo na jeden nebo více přesně definovaných uzlů). Funkční transformace je pravděpodobně nejjednodušší kód (poté, co programátor je obeznámen s přístupem), dává nejvíce udržovatelný kód a je často kompaktnější než alternativní přístupy.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkční transformační technologie XML  
 Společnost Microsoft nabízí dvě technologie funkční transformace pro použití v dokumentech XML: XSLT a LINQ na XML. XSLT je podporován <xref:System.Xml.Xsl> ve spravovaném oboru názvů a v nativní implementaci com msxml. Ačkoli XSLT je robustní technologie pro manipulaci s dokumenty XML, vyžaduje odborné znalosti ve specializované doméně, a to jazyk XSLT a jeho podpůrné rozhraní API.  
  
 LINQ na XML poskytuje nástroje potřebné ke kódování čistě funkční transformace expresivním a výkonným způsobem, v rámci kódu Jazyka C# nebo Visual Basic. Například mnoho příkladů v dokumentaci LINQ xml použít čistě funkční přístup. Také v [kurzu: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) používáme LINQ na XML ve funkčním přístupu k manipulaci s informacemi v dokumentu aplikace Microsoft Word.  
  
 Podrobnější porovnání linq s XML s jinými technologiemi Microsoft XML naleznete v tématu [LINQ to XML vs. Other XML Technologies](./linq-to-xml-vs-other-xml-technologies.md).  
  
XSLT je doporučený nástroj pro transformace zaměřené na dokumenty, pokud má zdrojový dokument nepravidelnou strukturu. Linq na XML však můžete také provádět transformace zaměřené na dokumenty. Další informace naleznete v tématu [Použití anotací k transformaci LINQ na stromy XML ve stylu XSLT (C#).](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)
  
## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
- [LINQ na XML vs. jiné technologie XML](./linq-to-xml-vs-other-xml-technologies.md)
