---
title: Programování s uzly (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 92ec8445123a8b685bd6ea134aca0b792cab6d2d
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="a19e6-102">Programování s uzly (C#)</span><span class="sxs-lookup"><span data-stu-id="a19e6-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a19e6-103"> Vývojáři, kteří potřebují často psát programy, jako je například editoru XML, transformace systému nebo Autor sestavy je potřeba psát programy, které fungují na jemnějšího úrovni členitosti než elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="a19e6-103"> developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="a19e6-104">Často potřebují k práci na úrovni uzlu, manipulace s textové uzly, pokyny pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="a19e6-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="a19e6-105">Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="a19e6-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="a19e6-106">Podrobnosti o uzlu</span><span class="sxs-lookup"><span data-stu-id="a19e6-106">Node Details</span></span>  
 <span data-ttu-id="a19e6-107">Existuje několik podrobností programování, které programátorem práce na úrovni uzlu měli vědět.</span><span class="sxs-lookup"><span data-stu-id="a19e6-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="a19e6-108">Nadřazené vlastnost z podřízené uzly z XDocument je nastaven na hodnotu Null</span><span class="sxs-lookup"><span data-stu-id="a19e6-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="a19e6-109"><xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazený <xref:System.Xml.Linq.XElement>, není nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="a19e6-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="a19e6-110">Uzly podřízené <xref:System.Xml.Linq.XDocument> mít žádný nadřazený <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a19e6-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="a19e6-111">Jejich nadřazená položka dokumentu, proto <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro uzly, je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a19e6-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="a19e6-112">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="a19e6-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="a19e6-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="a19e6-114">Sousední textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="a19e6-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="a19e6-115">Počet programovací modely XML jsou vždy sloučit uzly okolního textu.</span><span class="sxs-lookup"><span data-stu-id="a19e6-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="a19e6-116">To se někdy nazývá normalizaci textové uzly.</span><span class="sxs-lookup"><span data-stu-id="a19e6-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a19e6-117"> Normalizuje není textové uzly.</span><span class="sxs-lookup"><span data-stu-id="a19e6-117"> does not normalize text nodes.</span></span> <span data-ttu-id="a19e6-118">Pokud přidáte dva textové uzly stejného elementu, bude výsledkem uzly okolního textu.</span><span class="sxs-lookup"><span data-stu-id="a19e6-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="a19e6-119">Ale pokud přidáte obsah zadán jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučení řetězec s do okolního textu uzlu.</span><span class="sxs-lookup"><span data-stu-id="a19e6-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="a19e6-120">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="a19e6-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="a19e6-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="a19e6-122">Prázdný textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="a19e6-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="a19e6-123">V některých programovacích modelů XML je zaručeno textové uzly nebude obsahovat prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a19e6-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="a19e6-124">Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML.</span><span class="sxs-lookup"><span data-stu-id="a19e6-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="a19e6-125">Však ze stejného důvodu, které jsou uzly okolního textu možné, pokud odeberte text ze textový uzel podle nastavení její hodnoty na prázdný řetězec, uzel text nebudou odstraněna.</span><span class="sxs-lookup"><span data-stu-id="a19e6-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="a19e6-126">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="a19e6-127">Prázdný textový uzel ovlivňuje serializace</span><span class="sxs-lookup"><span data-stu-id="a19e6-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="a19e6-128">Pokud element obsahuje pouze textový uzel podřízené, který je prázdný, je serializovat s příznakem syntaxe dlouho značek: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="a19e6-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="a19e6-129">Pokud element obsahuje jakkoli žádné podřízené uzly, je serializovat s příznakem syntaxe krátké značek: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="a19e6-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="a19e6-130">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="a19e6-131">Atributy v technologii LINQ to XML stromu jsou obory názvů</span><span class="sxs-lookup"><span data-stu-id="a19e6-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="a19e6-132">I když deklarace oboru názvů mít identické syntaxe atributy, v některých programovací rozhraní, například XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy.</span><span class="sxs-lookup"><span data-stu-id="a19e6-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="a19e6-133">Ale v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="a19e6-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="a19e6-134">Pokud iteraci atributy elementu, který obsahuje deklaraci oboru názvů, zobrazí se deklaraci oboru názvů jako jedna z položek v vrácená kolekce.</span><span class="sxs-lookup"><span data-stu-id="a19e6-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="a19e6-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost určuje, zda je atribut deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a19e6-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="a19e6-136">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="a19e6-137">Metody osy XPath nevrátí podřízené prázdné místo XDocument</span><span class="sxs-lookup"><span data-stu-id="a19e6-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a19e6-138"> Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahovat jenom prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="a19e6-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="a19e6-139">Ale objektový model XPath nezahrnuje mezer jako podřízené uzly dokumentu, tak při procházení podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen prázdný textové uzly.</span><span class="sxs-lookup"><span data-stu-id="a19e6-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="a19e6-140">Ale když iteraci podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí metody XPath osy, nejsou k dispozici prázdný textové uzly.</span><span class="sxs-lookup"><span data-stu-id="a19e6-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="a19e6-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="a19e6-142">Objekty XDeclaration nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="a19e6-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="a19e6-143">Při procházení podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="a19e6-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="a19e6-144">Jde o vlastnost dokumentu, není podřízeným uzlem ho.</span><span class="sxs-lookup"><span data-stu-id="a19e6-144">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="a19e6-145">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a19e6-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="a19e6-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="a19e6-146">See Also</span></span>  
 [<span data-ttu-id="a19e6-147">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="a19e6-147">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
