---
title: Přehled třídy XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: 7fbe1cc484ea3482bc455c161783bd7a4513d0bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783614"
---
# <a name="xelement-class-overview-visual-basic"></a>Přehled třídy XElement (Visual Basic)
<xref:System.Xml.Linq.XElement> Třídy je jedním ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje XML element. Tato třída slouží k vytváření prvků; Změňte obsah elementu; Přidání, změna nebo odstranění podřízené elementy; přidat atributy pro element. nebo serializace obsah prvek v textové podobě. Můžete také spolupracovat s jinými třídami v <xref:System.Xml?displayProperty=nameWithType>, jako například <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funkce XElement  
 Toto téma popisuje funkce poskytované službou <xref:System.Xml.Linq.XElement> třídy.  
  
### <a name="constructing-xml-trees"></a>Vytváření stromů XML  
 Můžete sestavit stromů XML v celou řadu způsobů, včetně následujících:  
  
- Můžete vytvořit stromu XML v kódu. Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
- Můžete analyzovat soubor XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textové soubory nebo webovou adresu (URL). Další informace najdete v tématu [analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
- Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu. Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Pokud máte modul, který může zapisovat obsah tak, aby <xref:System.Xml.XmlWriter>, můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu pro vytvoření zapisovač, předat modul pro zápis do modulu a pak použít obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromu XML.  
  
 Nejběžnější způsob, jak vytvořit stromu XML je však následujícím způsobem:  
  
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
  
 Zahrnuje jiného velmi běžná technika pro vytvoření stromu XML pomocí výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu k naplnění stromu XML, jak je znázorněno v následujícím příkladu:  
  
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
 Může serializovat stromu XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.  
  
 Další informace najdete v tématu [serializace stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Načítání dat XML pomocí metody osy  
 Načíst atributy, podřízené prvky, následnickým elementům a nadřazených elementů můžete použít metody osy. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy pracovat na metody osy a poskytují několik pružnější a výkonnější způsobů, jak procházet a zpracování stromu XML.  
  
 Další informace najdete v tématu [osy LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Dotazování na stromy XML  
 Můžete napsat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahují data z stromu XML.  
  
 Další informace najdete v tématu [dotazování na stromy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Změna stromů XML  
 Můžete upravovat prvek v celou řadu způsobů, včetně změny jeho obsahu nebo atributů. Můžete také odebrat element ze svého nadřazeného objektu.  
  
 Další informace najdete v tématu [změna stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
