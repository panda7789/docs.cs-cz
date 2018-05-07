---
title: Přehled třídy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 49b3b81276a598d003efa98337dd945576d802ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xelement-class-overview-c"></a>Přehled třídy XElement (C#)
<xref:System.Xml.Linq.XElement> Třída je jedné ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje element, XML. Tuto třídu můžete použít k vytváření prvků; Změňte obsah elementu; přidat, změnit nebo odstranit podřízené elementy; Přidání atributů do elementu; nebo serializovat obsah elementu v textové podobě. Také můžete spolupracovat s jiné třídy v <xref:System.Xml?displayProperty=nameWithType>, jako například <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funkce XElement  
 Toto téma popisuje funkce poskytované službou <xref:System.Xml.Linq.XElement> třídy.  
  
### <a name="constructing-xml-trees"></a>Vytváření stromů XML  
 Můžete vytvořit stromy XML v mnoha různými způsoby, včetně následujících:  
  
-   Můžete vytvořit strom XML v kódu. Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
-   Můžete analyzovat soubor XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textové soubory nebo webovou adresu (URL). Další informace najdete v tématu [analýze XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).  
  
-   Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu. Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
-   Pokud máte modul, který může zapisovat obsah tak, aby <xref:System.Xml.XmlWriter>, můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu pro vytvoření zapisovač, zapisovač předat modul a potom používat obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromové struktuře XML.  
  
 Však většiny běžných způsob, jak vytvořit strom XML je následující:  
  
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
  
 Jiné velmi běžné technika pro vytvoření strom XML, která využívá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz k naplnění strom XML, jak je znázorněno v následujícím příkladu:  
  
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
  
### <a name="serializing-xml-trees"></a>Serializace XML stromů  
 Může serializovat XML stromu <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.  
  
 Další informace najdete v tématu [serializace XML stromů (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Načítání dat XML pomocí metody osy  
 Metody osy můžete načíst atributy, podřízené elementy, následnickým elementům a nadřazenými prvky. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy na ose metody pracovat a zadejte několik způsobů pružnější a výkonnější procházení a zpracovat strom XML.  
  
 Další informace najdete v tématu [technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Dotazování stromy XML  
 Můžete napsat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahovat data z strom XML.  
  
 Další informace najdete v tématu [dotazování stromy XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Úprava stromy XML  
 Element v mnoha různými způsoby, včetně změny jeho obsah nebo atributy, můžete upravit. Můžete také odebrat element z jeho nadřazený objekt.  
  
 Další informace najdete v tématu [úpravy stromů XML (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML přehled programování (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
