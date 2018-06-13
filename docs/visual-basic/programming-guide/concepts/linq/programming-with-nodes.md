---
title: Programování s uzly (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 871755ef0293513f07c60b1d5735c47692163b78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648343"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="6aa5a-102">Programování s uzly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6aa5a-102">Programming with Nodes (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6aa5a-103"> Vývojáři, kteří potřebují často psát programy, jako je například editoru XML, transformace systému nebo Autor sestavy je potřeba psát programy, které fungují na jemnějšího úrovni členitosti než elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-103"> developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="6aa5a-104">Často potřebují k práci na úrovni uzlu, manipulace s textové uzly, pokyny pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="6aa5a-105">Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="6aa5a-106">Podrobnosti o uzlu</span><span class="sxs-lookup"><span data-stu-id="6aa5a-106">Node Details</span></span>  
 <span data-ttu-id="6aa5a-107">Existuje několik podrobností programování, které programátorem práce na úrovni uzlu měli vědět.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="6aa5a-108">Nadřazené vlastnost z podřízené uzly z XDocument je nastaven na hodnotu Null</span><span class="sxs-lookup"><span data-stu-id="6aa5a-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="6aa5a-109"><xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazený <xref:System.Xml.Linq.XElement>, není nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="6aa5a-110">Uzly podřízené <xref:System.Xml.Linq.XDocument> mít žádný nadřazený <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="6aa5a-111">Jejich nadřazená položka dokumentu, proto <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro uzly, je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="6aa5a-112">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="6aa5a-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="6aa5a-114">Sousední textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="6aa5a-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="6aa5a-115">Počet programovací modely XML jsou vždy sloučit uzly okolního textu.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="6aa5a-116">To se někdy nazývá normalizaci textové uzly.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6aa5a-117"> Normalizuje není textové uzly.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-117"> does not normalize text nodes.</span></span> <span data-ttu-id="6aa5a-118">Pokud přidáte dva textové uzly stejného elementu, bude výsledkem uzly okolního textu.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="6aa5a-119">Ale pokud přidáte obsah zadán jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučení řetězec s do okolního textu uzlu.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="6aa5a-120">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="6aa5a-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="6aa5a-122">Prázdný textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="6aa5a-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="6aa5a-123">V některých programovacích modelů XML je zaručeno textové uzly nebude obsahovat prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="6aa5a-124">Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="6aa5a-125">Však ze stejného důvodu, které jsou uzly okolního textu možné, pokud odeberte text ze textový uzel podle nastavení její hodnoty na prázdný řetězec, uzel text nebudou odstraněna.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="6aa5a-126">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="6aa5a-127">Prázdný textový uzel ovlivňuje serializace</span><span class="sxs-lookup"><span data-stu-id="6aa5a-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="6aa5a-128">Pokud element obsahuje pouze textový uzel podřízené, který je prázdný, je serializovat s příznakem syntaxe dlouho značek: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="6aa5a-129">Pokud element obsahuje jakkoli žádné podřízené uzly, je serializovat s příznakem syntaxe krátké značek: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="6aa5a-130">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="6aa5a-131">Atributy v technologii LINQ to XML stromu jsou obory názvů</span><span class="sxs-lookup"><span data-stu-id="6aa5a-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="6aa5a-132">I když deklarace oboru názvů mít identické syntaxe atributy, v některých programovací rozhraní, například XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="6aa5a-133">Ale v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="6aa5a-134">Pokud iteraci atributy elementu, který obsahuje deklaraci oboru názvů, zobrazí se deklaraci oboru názvů jako jedna z položek v vrácená kolekce.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="6aa5a-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost určuje, zda je atribut deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="6aa5a-136">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="6aa5a-137">Metody osy XPath nevrátí podřízené prázdné místo XDocument</span><span class="sxs-lookup"><span data-stu-id="6aa5a-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6aa5a-138"> Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahovat jenom prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="6aa5a-139">Ale objektový model XPath nezahrnuje mezer jako podřízené uzly dokumentu, tak při procházení podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen mezer textové uzly.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="6aa5a-140">Ale když iteraci podřízené objekty daného <xref:System.Xml.Linq.XDocument> pomocí metody XPath osy, nejsou k dispozici mezer textové uzly.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="6aa5a-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="6aa5a-142">Objekty XDeclaration nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="6aa5a-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="6aa5a-143">Při procházení podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="6aa5a-144">Jde o vlastnost dokumentu, není podřízeným uzlem ho.</span><span class="sxs-lookup"><span data-stu-id="6aa5a-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="6aa5a-145">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6aa5a-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="6aa5a-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="6aa5a-146">See Also</span></span>  
 [<span data-ttu-id="6aa5a-147">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6aa5a-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
