---
title: Přehled třídy XElement
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: 2e5a1e161345df39ff5c006f751fb293cad60510
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636663"
---
# <a name="xelement-class-overview-visual-basic"></a>Přehled třídy XElement (Visual Basic)
Třída <xref:System.Xml.Linq.XElement> je jednou ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Představuje XML element. Tuto třídu můžete použít k vytváření elementů. změnit obsah elementu; Přidání, změna nebo odstranění podřízených elementů; přidejte atributy k elementu; nebo serializovat obsah elementu v textovém formuláři. Můžete také vzájemně spolupracovat s jinými třídami v <xref:System.Xml?displayProperty=nameWithType>, jako jsou <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>a <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funkce XElement  
 Toto téma popisuje funkce poskytované třídou <xref:System.Xml.Linq.XElement>.  
  
### <a name="constructing-xml-trees"></a>Sestavování stromů XML  
 Stromy XML můžete vytvářet různými způsoby, včetně následujících:  
  
- V kódu můžete vytvořit strom XML. Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
- Můžete analyzovat XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textových souborů nebo webové adresy (URL). Další informace najdete v tématu [Analýza XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
- K naplnění stromu můžete použít <xref:System.Xml.XmlReader>. Další informace najdete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Pokud máte modul, který může zapisovat obsah do <xref:System.Xml.XmlWriter>, můžete pomocí metody <xref:System.Xml.Linq.XContainer.CreateWriter%2A> vytvořit zapisovač, předat zapisovači modulu a potom použít obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromu XML.  
  
 Nejběžnější způsob vytvoření stromu XML je však následující:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Další velmi obvyklá technika pro vytváření stromu XML zahrnuje použití výsledků dotazu LINQ k naplnění stromu XML, jak je znázorněno v následujícím příkladu:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
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
  
### <a name="serializing-xml-trees"></a>Serializace stromů XML  
 Strom XML lze serializovat do <xref:System.IO.File>, <xref:System.IO.TextWriter>nebo <xref:System.Xml.XmlWriter>.  
  
 Další informace naleznete v tématu [serializace stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Načítání dat XML přes metody osy  
 Můžete použít metody osy k načtení atributů, podřízených prvků, následníků a nadřazených prvků. Dotazy LINQ pracují na metodách osy a poskytují několik flexibilních a výkonných způsobů navigace ve stromu XML a zpracování.  
  
 Další informace najdete v tématu [LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Dotazování na stromy XML  
 Můžete zapisovat dotazy LINQ, které extrahují data ze stromu XML.  
  
 Další informace najdete v tématu [dotazování na stromy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Úprava stromů XML  
 Prvek můžete upravit různými způsoby, včetně změny jeho obsahu nebo atributů. Můžete také odebrat prvek z jeho nadřazeného prvku.  
  
 Další informace najdete v tématu [Úprava stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
