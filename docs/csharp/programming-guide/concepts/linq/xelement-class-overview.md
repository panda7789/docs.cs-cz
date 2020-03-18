---
title: Přehled třídy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167891"
---
# <a name="xelement-class-overview-c"></a>Přehled třídy XElement (C#)
Třída <xref:System.Xml.Linq.XElement> je jednou ze základních [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]tříd v . Představuje element XML. Tuto třídu můžete použít k vytvoření prvků; změnit obsah prvku; přidání, změna nebo odstranění podřízených prvků; přidat atributy k prvku; nebo serializovat obsah prvku v textové podobě. Můžete také spolupracovat s jinými třídami <xref:System.Xml?displayProperty=nameWithType>v , například <xref:System.Xml.XmlReader>v , <xref:System.Xml.XmlWriter>a <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
Toto téma popisuje funkce poskytované <xref:System.Xml.Linq.XElement> třídou.  
  
## <a name="constructing-xml-trees"></a>Vytváření stromů XML  
 Stromy XML můžete vytvářet různými způsoby, včetně následujících:  
  
- Můžete vytvořit strom XML v kódu. Další informace naleznete [v tématu Creating XML Trees (C#)](./linq-to-xml-overview.md).  
  
- Xml můžete analyzovat z různých zdrojů, včetně textových <xref:System.IO.TextReader>souborů nebo webové adresy (URL). Další informace naleznete [v tématu Analýza XML (C#)](./how-to-parse-a-string.md).  
  
- Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu. Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Pokud máte modul, který může <xref:System.Xml.XmlWriter>psát obsah do <xref:System.Xml.Linq.XContainer.CreateWriter%2A> , můžete použít metodu k vytvoření zapisovače, předat <xref:System.Xml.XmlWriter> zapisovatele do modulu a potom použít obsah, který je zapsán do stromu XML.  
  
 Nejběžnější způsob vytvoření stromu XML je však následující:  
  
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
  
 Další velmi běžná technika pro vytvoření stromu XML zahrnuje použití výsledků dotazu LINQ k naplnění stromu XML, jak je znázorněno v následujícím příkladu:  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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
 Strom XML můžete serializovat do <xref:System.IO.File>, <xref:System.IO.TextWriter>a <xref:System.Xml.XmlWriter>nebo .  
  
 Další informace naleznete [v tématu Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Načítání dat XML pomocí metod osy  
 Metody osy můžete použít k načtení atributů, podřízených prvků, potomků prvků a prvků nadřazených prvků. Linq dotazy pracují na metodách osy a poskytují několik flexibilních a účinných způsobů procházení a zpracování stromu XML.  
  
 Další informace naleznete v tématu [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>Dotazování na stromy XML  
 Můžete psát dotazy LINQ, které extrahují data ze stromu XML.  
  
 Další informace naleznete v [tématu Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>Úprava mezistromy XML  
 Prvek můžete upravit různými způsoby, včetně změny jeho obsahu nebo atributů. Můžete také odebrat prvek z jeho nadřazeného prvku.  
  
 Další informace naleznete [v tématu Úprava stromů XML (LINQ na XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
