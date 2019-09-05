---
title: Programování s použitím uzlůC#()
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8c4c858cbc1fad4041c2e5ce62ca8a01dd1cfb2c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253150"
---
# <a name="programming-with-nodes-c"></a>Programování s použitím uzlůC#()
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovač sestav, často potřebují psát programy, které fungují na jemnější úrovni členitosti než prvky a atributy. Často potřebují pracovat na úrovni uzlu, manipulaci s textovými uzly, pokyny pro zpracování a komentáře. Toto téma poskytuje některé podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti uzlu  
 Existuje řada podrobných informací o programování, které by programátor pracující na úrovni uzlu měl znát.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Vlastnost Parent podřízených uzlů XDocument je nastavena na hodnotu null.  
 Vlastnost obsahuje nadřazenou položku <xref:System.Xml.Linq.XElement>, ne nadřazený uzel. <xref:System.Xml.Linq.XObject.Parent%2A> Podřízené uzly <xref:System.Xml.Linq.XDocument> nemají žádnou nadřazenou <xref:System.Xml.Linq.XElement>položku. Jejich nadřazeným prvkem je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro tyto uzly je nastavena na hodnotu null.  
  
 Následující příklad ukazuje toto:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Jsou možné sousední uzly textu.  
 V řadě programovacích modelů XML jsou sousední textové uzly vždycky sloučeny. To se někdy označuje jako normalizace textových uzlů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nenormalizuje textové uzly. Pokud přidáte dva textové uzly do stejného elementu, bude výsledkem sousedících textových uzlů. Pokud však přidáte obsah zadaný jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzel, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může řetězec sloučit s sousedícím textovým uzlem.  
  
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
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Jsou možné prázdné textové uzly.  
 V některých programovacích modelech XML je zaručeno, že textové uzly nebudou obsahovat prázdný řetězec. Důvodem je, že takový textový uzel nemá žádný vliv na serializaci kódu XML. Z toho důvodu, že když odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn, ze stejného důvodu, že je možné použít sousední textové uzly.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel ovlivňuje serializaci.  
 Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhých značek: `<Child></Child>`. Pokud element neobsahuje žádné podřízené uzly, je serializován s syntaxí krátké značky: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Obory názvů jsou atributy ve stromu LINQ to XML.  
 I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oborů názvů nejsou považovány za atributy. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]rozhraní se však obory názvů ukládají <xref:System.Xml.Linq.XAttribute> jako objekty ve stromu XML. Pokud iterete pomocí atributů pro prvek, který obsahuje deklaraci oboru názvů, uvidíte deklaraci oboru názvů jako jednu z položek ve vrácené kolekci.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost označuje, zda je atribut deklarací oboru názvů.  
  
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
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevracejí podřízené prázdné znaky XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje podřízených textových uzlů <xref:System.Xml.Linq.XDocument>v, pokud textové uzly obsahují pouze prázdné znaky. Model objektu XPath ale neobsahuje prázdné znaky jako podřízené uzly dokumentu, takže při iteraci mezi podřízenými prvky <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> pomocí osy se vrátí textové uzly bílého prostoru. Při iteraci mezi podřízenými objekty <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath ale prázdné textové uzly nebudou vráceny.  
  
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
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Objekty XDeclaration nejsou uzly.  
 Při iteraci mezi podřízenými uzly <xref:System.Xml.Linq.XDocument>objektu, se nezobrazí objekt deklarace XML. Jedná se o vlastnost dokumentu, nikoli o podřízený uzel.  
  
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
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  