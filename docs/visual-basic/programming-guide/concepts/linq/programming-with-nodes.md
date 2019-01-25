---
title: Programování s uzly (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 1cd9792905c1816094d9bbd12e0648c5a4d7c4f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527403"
---
# <a name="programming-with-nodes-visual-basic"></a>Programování s uzly (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vývojářům, kteří potřebují psát programy, jako je například XML editor, systém transformace nebo Autor sestavy často potřeba psát programy, které fungují na jemnější úrovni členitosti než elementů a atributů. Často potřebují pracovat na úrovni uzlu manipulace s uzly text, instrukce ke zpracování a komentáře. Toto téma obsahuje podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti o uzlu  
 Existuje mnoho detailů programování, které byste měli mít programátor funguje na úrovni uzlu.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadřazená vlastnost z podřízené uzly z XDocument nastaven na hodnotu Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazené <xref:System.Xml.Linq.XElement>, není nadřazený uzel. Podřízené uzly <xref:System.Xml.Linq.XDocument> mít žádný nadřazený objekt <xref:System.Xml.Linq.XElement>. Jejich nadřazené je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> pro ty uzly, je hodnota nastavena na hodnotu null.  
  
 Následující příklad ukazuje toto:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Sousední textové uzly jsou možné  
 V řadě programovacích modelů XML jsou vždy sloučeny sousední textové uzly. To se někdy nazývá normalizace textové uzly. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] není normalizovat textové uzly. Pokud chcete přidat dva textové uzly stejného elementu, jinak dojde sousední textové uzly. Ale pokud chcete přidat obsah určený jako řetězce, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučit řetězec s sousední textový uzel.  
  
 Následující příklad ukazuje toto:  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Co jsou prázdné textové uzly  
 V některých programovací modely jazyka XML je zaručeno textové uzly nesmí obsahovat prázdný řetězec. Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML. Ale ze stejného důvodu, které jsou uzly okolního textu možná, pokud odeberete text z textového uzlu tak, že nastavíte její hodnotu na prázdný řetězec, samotný uzel text se neodstraní.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel má vliv na serializace  
 Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhé značek: `<Child></Child>`. Pokud element obsahuje podřízené uzly jakýmkoli způsobem, je serializované pomocí syntaxe krátký značek: `<Child />`.  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Obory názvů jsou atributy v technologii LINQ to XML stromu  
 I když deklarace oboru názvů mají stejné syntaxi atributů, v některých rozhraních programování, jako je například XSLT a výraz XPath, deklarace oboru názvů nejsou považovány za atributy. Nicméně v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML. Pokud iteraci atributy pro element, který obsahuje deklarace oboru názvů, uvidíte jako jednu z položek v kolekci vrácené deklarace oboru názvů.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost určuje, zda je atribut deklarace oboru názvů.  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevrátí podřízené prázdné znaky z XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahující jenom prázdné znaky. Však XPath objektový model neobsahuje mezery jako podřízené uzly dokumentu, tak při iteraci podřízených položek <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen text uzly prázdné místo. Ale při iteraci podřízených položek <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath, nebude vrácena textové uzly prázdné místo.  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration objekty nejsou uzly  
 Při iteraci podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML. Je to vlastnost dokumentu a jeho není podřízený uzel.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Viz také:
- [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
