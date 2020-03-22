---
title: Programování s uzly
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: b2c9022cb57cf122af47bbe6d1a7fe2b4d41327c
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266960"
---
# <a name="programming-with-nodes-visual-basic"></a>Programování pomocí uzlů (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovatel sestavy, často potřebují psát programy, které pracují na jemnější úrovni rozlišovací schopnosti než prvky a atributy. Často je třeba pracovat na úrovni uzlu, manipulace s textovými uzly, pokyny pro zpracování a komentáře. Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti o uzlu  
 Existuje celá řada podrobností o programování, které programátor pracující na úrovni uzlu by měl vědět.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadřazená vlastnost podřízených uzlů XDocument je nastavena na hodnotu Null.  
 Vlastnost <xref:System.Xml.Linq.XObject.Parent%2A> obsahuje nadřazený <xref:System.Xml.Linq.XElement>uzel , nikoli nadřazený uzel. Podřízené uzly <xref:System.Xml.Linq.XElement>nemají nadřazenou položku <xref:System.Xml.Linq.XDocument> . Jejich nadřazený <xref:System.Xml.Linq.XObject.Parent%2A> je dokument, takže vlastnost pro tyto uzly je nastavena na hodnotu null.  
  
 Následující příklad ukazuje toto:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Sousední textové uzly jsou možné  
 V řadě programovacích modelů XML jsou sousední textové uzly vždy sloučeny. To se někdy nazývá normalizace textových uzlů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nenormalizuje textové uzly. Pokud přidáte dva textové uzly do stejného prvku, bude výsledkem sousední textové uzly. Pokud však přidáte obsah určený jako řetězec, nikoli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jako uzel, <xref:System.Xml.Linq.XText> může řetězec sloučit s sousedním textovým uzlem.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Prázdné textové uzly jsou možné  
 V některých programovacích modelech XML je zaručeno, že textové uzly neobsahují prázdný řetězec. Důvodem je, že takový textový uzel nemá žádný vliv na serializaci XML. Ze stejného důvodu, že sousední textové uzly jsou možné, pokud odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel ovlivňuje serializaci  
 Pokud prvek obsahuje pouze podřízený textový uzel, který je prázdný, je `<Child></Child>`serializován s syntaxí dlouhé značky: . Pokud prvek neobsahuje žádné podřízené uzly, je serializován `<Child />`s syntaxí krátké značky: .  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Obory názvů jsou atributy ve stromu LINQ do stromu XML  
 I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy. V aplikaci jsou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]však <xref:System.Xml.Linq.XAttribute> obory názvů uloženy jako objekty ve stromu XML. Pokud iterát prostřednictvím atributy pro prvek, který obsahuje deklaraci oboru názvů, zobrazí se deklarace oboru názvů jako jedna z položek ve vrácené kolekci.  
  
 Vlastnost <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> označuje, zda je atribut deklarací oboru názvů.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevracejí podřízený prázdné místo xdocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje podřízené textové uzly <xref:System.Xml.Linq.XDocument>, pokud textové uzly obsahují pouze prázdné znaky. Objektový model XPath však neobsahuje prázdné znaky jako podřízené uzly dokumentu, takže <xref:System.Xml.Linq.XDocument> při <xref:System.Xml.Linq.XContainer.Nodes%2A> iterace prostřednictvím podřízených objektů pomocí osy budou vráceny uzly prázdného místa. Však při iterace prostřednictvím <xref:System.Xml.Linq.XDocument> podřízených pomocí metody osy XPath, prázdné místo textové uzly nebudou vráceny.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Objekty XDeclaration nejsou uzly  
 Při itetu prostřednictvím podřízených <xref:System.Xml.Linq.XDocument>uzlů , neuvidíte objekt deklarace XML. Je vlastnostdokumentu, nikoli podřízený uzel.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Viz také

- [Rozšířené linq na xml programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
