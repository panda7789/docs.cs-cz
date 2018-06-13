---
title: Programování s uzly (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 060f487e6e92c2ca42a685cc03afbe438106b839
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335416"
---
# <a name="programming-with-nodes-c"></a>Programování s uzly (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Vývojáři, kteří potřebují často psát programy, jako je například editoru XML, transformace systému nebo Autor sestavy je potřeba psát programy, které fungují na jemnějšího úrovni členitosti než elementů a atributů. Často potřebují k práci na úrovni uzlu, manipulace s textové uzly, pokyny pro zpracování a komentáře. Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.  
  
## <a name="node-details"></a>Podrobnosti o uzlu  
 Existuje několik podrobností programování, které programátorem práce na úrovni uzlu měli vědět.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadřazené vlastnost z podřízené uzly z XDocument je nastaven na hodnotu Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazený <xref:System.Xml.Linq.XElement>, není nadřazený uzel. Uzly podřízené <xref:System.Xml.Linq.XDocument> mít žádný nadřazený <xref:System.Xml.Linq.XElement>. Jejich nadřazená položka dokumentu, proto <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro uzly, je nastavena na hodnotu null.  
  
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
 Počet programovací modely XML jsou vždy sloučit uzly okolního textu. To se někdy nazývá normalizaci textové uzly. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Normalizuje není textové uzly. Pokud přidáte dva textové uzly stejného elementu, bude výsledkem uzly okolního textu. Ale pokud přidáte obsah zadán jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučení řetězec s do okolního textu uzlu.  
  
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
  
### <a name="empty-text-nodes-are-possible"></a>Prázdný textové uzly jsou možné  
 V některých programovacích modelů XML je zaručeno textové uzly nebude obsahovat prázdný řetězec. Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML. Však ze stejného důvodu, které jsou uzly okolního textu možné, pokud odeberte text ze textový uzel podle nastavení její hodnoty na prázdný řetězec, uzel text nebudou odstraněna.  
  
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
  
### <a name="an-empty-text-node-impacts-serialization"></a>Prázdný textový uzel ovlivňuje serializace  
 Pokud element obsahuje pouze textový uzel podřízené, který je prázdný, je serializovat s příznakem syntaxe dlouho značek: `<Child></Child>`. Pokud element obsahuje jakkoli žádné podřízené uzly, je serializovat s příznakem syntaxe krátké značek: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Atributy v technologii LINQ to XML stromu jsou obory názvů  
 I když deklarace oboru názvů mít identické syntaxe atributy, v některých programovací rozhraní, například XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy. Ale v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML. Pokud iteraci atributy elementu, který obsahuje deklaraci oboru názvů, zobrazí se deklaraci oboru názvů jako jedna z položek v vrácená kolekce.  
  
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
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osy XPath nevrátí podřízené prázdné místo XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahovat jenom prázdný znak. Ale objektový model XPath nezahrnuje mezer jako podřízené uzly dokumentu, tak při procházení podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen prázdný textové uzly. Ale když iteraci podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí metody XPath osy, nejsou k dispozici prázdný textové uzly.  
  
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
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Objekty XDeclaration nejsou uzly  
 Při procházení podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML. Jde o vlastnost dokumentu, není podřízeným uzlem ho.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
