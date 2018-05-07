---
title: Programování s uzly (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 871755ef0293513f07c60b1d5735c47692163b78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="programming-with-nodes-visual-basic"></a>Programování s uzly (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Vývojáři, kteří potřebují často psát programy, jako je například editoru XML, transformace systému nebo Autor sestavy je potřeba psát programy, které fungují na jemnějšího úrovni členitosti než elementů a atributů. Často potřebují k práci na úrovni uzlu, manipulace s textové uzly, pokyny pro zpracování a komentáře. Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti o uzlu  
 Existuje několik podrobností programování, které programátorem práce na úrovni uzlu měli vědět.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadřazené vlastnost z podřízené uzly z XDocument je nastaven na hodnotu Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazený <xref:System.Xml.Linq.XElement>, není nadřazený uzel. Uzly podřízené <xref:System.Xml.Linq.XDocument> mít žádný nadřazený <xref:System.Xml.Linq.XElement>. Jejich nadřazená položka dokumentu, proto <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro uzly, je nastavena na hodnotu null.  
  
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
 Počet programovací modely XML jsou vždy sloučit uzly okolního textu. To se někdy nazývá normalizaci textové uzly. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Normalizuje není textové uzly. Pokud přidáte dva textové uzly stejného elementu, bude výsledkem uzly okolního textu. Ale pokud přidáte obsah zadán jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučení řetězec s do okolního textu uzlu.  
  
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
  
### <a name="empty-text-nodes-are-possible"></a>Prázdný textové uzly jsou možné  
 V některých programovacích modelů XML je zaručeno textové uzly nebude obsahovat prázdný řetězec. Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML. Však ze stejného důvodu, které jsou uzly okolního textu možné, pokud odeberte text ze textový uzel podle nastavení její hodnoty na prázdný řetězec, uzel text nebudou odstraněna.  
  
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
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel ovlivňuje serializace  
 Pokud element obsahuje pouze textový uzel podřízené, který je prázdný, je serializovat s příznakem syntaxe dlouho značek: `<Child></Child>`. Pokud element obsahuje jakkoli žádné podřízené uzly, je serializovat s příznakem syntaxe krátké značek: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Atributy v technologii LINQ to XML stromu jsou obory názvů  
 I když deklarace oboru názvů mít identické syntaxe atributy, v některých programovací rozhraní, například XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy. Ale v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML. Pokud iteraci atributy elementu, který obsahuje deklaraci oboru názvů, zobrazí se deklaraci oboru názvů jako jedna z položek v vrácená kolekce.  
  
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
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevrátí podřízené prázdné místo XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahovat jenom prázdný znak. Ale objektový model XPath nezahrnuje mezer jako podřízené uzly dokumentu, tak při procházení podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen mezer textové uzly. Ale když iteraci podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí metody XPath osy, nejsou k dispozici mezer textové uzly.  
  
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
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Objekty XDeclaration nejsou uzly  
 Při procházení podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML. Jde o vlastnost dokumentu, není podřízeným uzlem ho.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
