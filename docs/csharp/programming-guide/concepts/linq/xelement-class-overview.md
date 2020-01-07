---
title: XElement – Přehled třídyC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: d77c725b3c786b8a8fa2b0eeab4bc4b30f298218
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635467"
---
# <a name="xelement-class-overview-c"></a>XElement – Přehled třídyC#()
Třída <xref:System.Xml.Linq.XElement> je jednou ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Představuje XML element. Tuto třídu můžete použít k vytváření elementů. změnit obsah elementu; Přidání, změna nebo odstranění podřízených elementů; přidejte atributy k elementu; nebo serializovat obsah elementu v textovém formuláři. Můžete také vzájemně spolupracovat s jinými třídami v <xref:System.Xml?displayProperty=nameWithType>, jako jsou <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>a <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
Toto téma popisuje funkce poskytované třídou <xref:System.Xml.Linq.XElement>.  
  
## <a name="constructing-xml-trees"></a>Sestavování stromů XML  
 Stromy XML můžete vytvářet různými způsoby, včetně následujících:  
  
- V kódu můžete vytvořit strom XML. Další informace naleznete v tématu [CREATING XML TreesC#()](./linq-to-xml-overview.md).  
  
- Můžete analyzovat XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textových souborů nebo webové adresy (URL). Další informace najdete v tématu [Analýza XML (C#)](./how-to-parse-a-string.md).  
  
- K naplnění stromu můžete použít <xref:System.Xml.XmlReader>. Další informace najdete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Pokud máte modul, který může zapisovat obsah do <xref:System.Xml.XmlWriter>, můžete pomocí metody <xref:System.Xml.Linq.XContainer.CreateWriter%2A> vytvořit zapisovač, předat zapisovači modulu a potom použít obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromu XML.  
  
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
  
 Další velmi obvyklá technika pro vytváření stromu XML zahrnuje použití výsledků dotazu LINQ k naplnění stromu XML, jak je znázorněno v následujícím příkladu:  
  
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
 Strom XML lze serializovat do <xref:System.IO.File>, <xref:System.IO.TextWriter>nebo <xref:System.Xml.XmlWriter>.  
  
 Další informace naleznete v tématu [serializace stromů XML (C#)](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Načítání dat XML přes metody osy  
 Můžete použít metody osy k načtení atributů, podřízených prvků, následníků a nadřazených prvků. Dotazy LINQ pracují na metodách osy a poskytují několik flexibilních a výkonných způsobů navigace ve stromu XML a zpracování.  
  
 Další informace najdete v tématu [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>Dotazování na stromy XML  
 Můžete zapisovat dotazy LINQ, které extrahují data ze stromu XML.  
  
 Další informace najdete v tématu [dotazování na stromy XMLC#()](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>Úprava stromů XML  
 Prvek můžete upravit různými způsoby, včetně změny jeho obsahu nebo atributů. Můžete také odebrat prvek z jeho nadřazeného prvku.  
  
 Další informace najdete v tématu [Úprava stromů XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled programování LINQ to XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
