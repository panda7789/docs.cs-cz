---
title: Programování s uzly
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 9c64c348f5d26172f26593b927e6bc24baf365bf
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794400"
---
# <a name="programming-with-nodes-visual-basic"></a>Programování s uzly (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovač sestav, často potřebují psát programy, které fungují na jemnější úrovni členitosti než prvky a atributy. Často potřebují pracovat na úrovni uzlu, manipulaci s textovými uzly, pokyny pro zpracování a komentáře. Toto téma poskytuje některé podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti uzlu  
 Existuje řada podrobných informací o programování, které by programátor pracující na úrovni uzlu měl znát.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Vlastnost Parent podřízených uzlů XDocument je nastavena na hodnotu null.  
 <xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazenou položku <xref:System.Xml.Linq.XElement>, ne nadřazený uzel. Podřízené uzly <xref:System.Xml.Linq.XDocument> nemají žádnou nadřazenou <xref:System.Xml.Linq.XElement>položku. Jejich nadřazeným prvkem je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro tyto uzly je nastavena na hodnotu null.  
  
 Následující příklad ukazuje toto:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Jsou možné sousední uzly textu.  
 V řadě programovacích modelů XML jsou sousední textové uzly vždycky sloučeny. To se někdy označuje jako normalizace textových uzlů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nenormalizuje textové uzly. Pokud přidáte dva textové uzly do stejného elementu, bude výsledkem sousedících textových uzlů. Pokud však přidáte obsah zadaný jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzel, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může řetězec sloučit s sousedícím textovým uzlem.  
  
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
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Jsou možné prázdné textové uzly.  
 V některých programovacích modelech XML je zaručeno, že textové uzly nebudou obsahovat prázdný řetězec. Důvodem je, že takový textový uzel nemá žádný vliv na serializaci kódu XML. Z toho důvodu, že když odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn, ze stejného důvodu, že je možné použít sousední textové uzly.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel ovlivňuje serializaci.  
 Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhých značek: `<Child></Child>`. Pokud element neobsahuje žádné podřízené uzly, je serializován s syntaxí krátké značky: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Obory názvů jsou atributy ve stromu LINQ to XML.  
 I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oborů názvů nejsou považovány za atributy. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]rozhraní se však obory názvů ukládají <xref:System.Xml.Linq.XAttribute> jako objekty ve stromu XML. Pokud iterete pomocí atributů pro prvek, který obsahuje deklaraci oboru názvů, uvidíte deklaraci oboru názvů jako jednu z položek ve vrácené kolekci.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost označuje, zda je atribut deklarací oboru názvů.  
  
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
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevracejí podřízené prázdné znaky XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje podřízených textových uzlů v <xref:System.Xml.Linq.XDocument>, pokud textové uzly obsahují pouze prázdné znaky. Model objektu XPath ale neobsahuje prázdné znaky jako podřízené uzly dokumentu, takže při iteraci mezi podřízenými prvky <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy se vrátí textové uzly s prázdným znakem. Při iteraci po podřízených objektech <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath však nebudou textové uzly prázdné místo vráceny.  
  
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
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Objekty XDeclaration nejsou uzly.  
 Při iteraci mezi podřízenými uzly objektu <xref:System.Xml.Linq.XDocument>, se nezobrazí objekt deklarace XML. Jedná se o vlastnost dokumentu, nikoli o podřízený uzel.  
  
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

- [Rozšířené programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
