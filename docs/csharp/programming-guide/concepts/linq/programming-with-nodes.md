---
title: Programování s uzly (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 05c2e95fe97effda7b537a7ac2d8f5780f4e212b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168311"
---
# <a name="programming-with-nodes-c"></a>Programování s uzly (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovatel sestavy, často potřebují psát programy, které pracují na jemnější úrovni rozlišovací schopnosti než prvky a atributy. Často je třeba pracovat na úrovni uzlu, manipulace s textovými uzly, pokyny pro zpracování a komentáře. Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti o uzlu  
 Existuje celá řada podrobností o programování, které programátor pracující na úrovni uzlu by měl vědět.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadřazená vlastnost podřízených uzlů XDocument je nastavena na hodnotu Null.  
 Vlastnost <xref:System.Xml.Linq.XObject.Parent%2A> obsahuje nadřazený <xref:System.Xml.Linq.XElement>uzel , nikoli nadřazený uzel. Podřízené uzly <xref:System.Xml.Linq.XElement>nemají nadřazenou položku <xref:System.Xml.Linq.XDocument> . Jejich nadřazený <xref:System.Xml.Linq.XObject.Parent%2A> je dokument, takže vlastnost pro tyto uzly je nastavena na hodnotu null.  
  
 Následující příklad ukazuje toto:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Sousední textové uzly jsou možné  
 V řadě programovacích modelů XML jsou sousední textové uzly vždy sloučeny. To se někdy nazývá normalizace textových uzlů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nenormalizuje textové uzly. Pokud přidáte dva textové uzly do stejného prvku, bude výsledkem sousední textové uzly. Pokud však přidáte obsah určený jako řetězec, nikoli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jako uzel, <xref:System.Xml.Linq.XText> může řetězec sloučit s sousedním textovým uzlem.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Prázdné textové uzly jsou možné  
 V některých programovacích modelech XML je zaručeno, že textové uzly neobsahují prázdný řetězec. Důvodem je, že takový textový uzel nemá žádný vliv na serializaci XML. Ze stejného důvodu, že sousední textové uzly jsou možné, pokud odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel ovlivňuje serializaci  
 Pokud prvek obsahuje pouze podřízený textový uzel, který je prázdný, je `<Child></Child>`serializován s syntaxí dlouhé značky: . Pokud prvek neobsahuje žádné podřízené uzly, je serializován `<Child />`s syntaxí krátké značky: .  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Obory názvů jsou atributy ve stromu LINQ do stromu XML  
 I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy. V aplikaci jsou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]však <xref:System.Xml.Linq.XAttribute> obory názvů uloženy jako objekty ve stromu XML. Pokud iterát prostřednictvím atributy pro prvek, který obsahuje deklaraci oboru názvů, zobrazí se deklarace oboru názvů jako jedna z položek ve vrácené kolekci.  
  
 Vlastnost <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> označuje, zda je atribut deklarací oboru názvů.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevracejí podřízený prázdné místo xdocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje podřízené textové uzly <xref:System.Xml.Linq.XDocument>, pokud textové uzly obsahují pouze prázdné znaky. Objektový model XPath však neobsahuje prázdné místo jako podřízené uzly dokumentu, takže <xref:System.Xml.Linq.XDocument> při <xref:System.Xml.Linq.XContainer.Nodes%2A> iterace prostřednictvím podřízených objektů pomocí osy budou vráceny prázdné textové uzly. Však při iterace prostřednictvím <xref:System.Xml.Linq.XDocument> podřízených pomocí metody osy XPath, prázdné textové uzly nebudou vráceny.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Objekty XDeclaration nejsou uzly  
 Při itetu prostřednictvím podřízených <xref:System.Xml.Linq.XDocument>uzlů , neuvidíte objekt deklarace XML. Je vlastnostdokumentu, nikoli podřízený uzel.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  