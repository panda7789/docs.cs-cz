---
title: Programování s uzly (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 0924d7b1d25a33635cc5140ca32622658b10fa0e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681920"
---
# <a name="programming-with-nodes-c"></a>Programování s uzly (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vývojářům, kteří potřebují psát programy, jako je například XML editor, systém transformace nebo Autor sestavy často potřeba psát programy, které fungují na jemnější úrovni členitosti než elementů a atributů. Často potřebují pracovat na úrovni uzlu manipulace s uzly text, instrukce ke zpracování a komentáře. Toto téma obsahuje podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti o uzlu  
 Existuje mnoho detailů programování, které byste měli mít programátor funguje na úrovni uzlu.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadřazená vlastnost z podřízené uzly z XDocument nastaven na hodnotu Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazené <xref:System.Xml.Linq.XElement>, není nadřazený uzel. Podřízené uzly <xref:System.Xml.Linq.XDocument> mít žádný nadřazený objekt <xref:System.Xml.Linq.XElement>. Jejich nadřazené je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> pro ty uzly, je hodnota nastavena na hodnotu null.  
  
 Následující příklad ukazuje toto:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Sousední textové uzly jsou možné  
 V řadě programovacích modelů XML jsou vždy sloučeny sousední textové uzly. To se někdy nazývá normalizace textové uzly. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] není normalizovat textové uzly. Pokud chcete přidat dva textové uzly stejného elementu, jinak dojde sousední textové uzly. Ale pokud chcete přidat obsah určený jako řetězce, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučit řetězec s sousední textový uzel.  
  
 Následující příklad ukazuje toto:  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Co jsou prázdné textové uzly  
 V některých programovací modely jazyka XML je zaručeno textové uzly nesmí obsahovat prázdný řetězec. Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML. Ale ze stejného důvodu, které jsou uzly okolního textu možná, pokud odeberete text z textového uzlu tak, že nastavíte její hodnotu na prázdný řetězec, samotný uzel text se neodstraní.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel má vliv na serializace  
 Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhé značek: `<Child></Child>`. Pokud element obsahuje podřízené uzly jakýmkoli způsobem, je serializované pomocí syntaxe krátký značek: `<Child />`.  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Obory názvů jsou atributy v technologii LINQ to XML stromu  
 I když deklarace oboru názvů mají stejné syntaxi atributů, v některých rozhraních programování, jako je například XSLT a výraz XPath, deklarace oboru názvů nejsou považovány za atributy. Nicméně v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML. Pokud iteraci atributy pro element, který obsahuje deklarace oboru názvů, uvidíte jako jednu z položek v kolekci vrácené deklarace oboru názvů.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost určuje, zda je atribut deklarace oboru názvů.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevrátí podřízené prázdné znaky z XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahující jenom prázdné znaky. Však XPath objektový model neobsahuje mezery jako podřízené uzly dokumentu, tak při iteraci podřízených položek <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen text prázdné znaky uzly. Ale při iteraci podřízených položek <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath, nebude vrácena uzly text prázdné místo.  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());   
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration objekty nejsou uzly  
 Při iteraci podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML. Je to vlastnost dokumentu a jeho není podřízený uzel.  
  
```csharp  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Viz také:

- [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
