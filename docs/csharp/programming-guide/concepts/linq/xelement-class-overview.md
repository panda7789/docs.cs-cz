---
title: Přehled třídy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 815b7b6523afe7106fcdcbe242d667c5ad6aa56e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487016"
---
# <a name="xelement-class-overview-c"></a>Přehled třídy XElement (C#)
<xref:System.Xml.Linq.XElement> Třídy je jedním ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje XML element. Tato třída slouží k vytváření prvků; Změňte obsah elementu; Přidání, změna nebo odstranění podřízené elementy; přidat atributy pro element. nebo serializace obsah prvek v textové podobě. Můžete také spolupracovat s jinými třídami v <xref:System.Xml?displayProperty=nameWithType>, jako například <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
Toto téma popisuje funkce poskytované službou <xref:System.Xml.Linq.XElement> třídy.  
  
## <a name="constructing-xml-trees"></a>Vytváření stromů XML  
 Můžete sestavit stromů XML v celou řadu způsobů, včetně následujících:  
  
- Můžete vytvořit stromu XML v kódu. Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).  
  
- Můžete analyzovat soubor XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textové soubory nebo webovou adresu (URL). Další informace najdete v tématu [analýza kódu XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md).  
  
- Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu. Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Pokud máte modul, který může zapisovat obsah tak, aby <xref:System.Xml.XmlWriter>, můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu pro vytvoření zapisovač, předat modul pro zápis do modulu a pak použít obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromu XML.  
  
 Nejběžnější způsob, jak vytvořit stromu XML je však následujícím způsobem:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Zahrnuje jiného velmi běžná technika pro vytvoření stromu XML pomocí výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu k naplnění stromu XML, jak je znázorněno v následujícím příkladu:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a>Serializace stromů XML  
 Může serializovat stromu XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.  
  
 Další informace najdete v tématu [serializace stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Načítání dat XML pomocí metody osy  
 Načíst atributy, podřízené prvky, následnickým elementům a nadřazených elementů můžete použít metody osy. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy pracovat na metody osy a poskytují několik pružnější a výkonnější způsobů, jak procházet a zpracování stromu XML.  
  
 Další informace najdete v tématu [osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>Dotazování na stromy XML  
 Můžete napsat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahují data z stromu XML.  
  
 Další informace najdete v tématu [dotazování na stromy XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>Změna stromů XML  
 Můžete upravovat prvek v celou řadu způsobů, včetně změny jeho obsahu nebo atributů. Můžete také odebrat element ze svého nadřazeného objektu.  
  
 Další informace najdete v tématu [změna stromů XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to XML programování (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
