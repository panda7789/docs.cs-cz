---
title: Vyberte uzel pomocí jazyka XPath navigace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c5a7b9113dd5a4de929f5b88569be89bc1f2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572707"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="664dd-102">Vyberte uzel pomocí jazyka XPath navigace</span><span class="sxs-lookup"><span data-stu-id="664dd-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="664dd-103">XML modelu DOM (Document Object) obsahuje metody, které vám umožní používat navigační XML Path Language (XPath) dotazů na informace v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="664dd-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="664dd-104">Pomocí jazyka XPath se najít uzel jeden, konkrétní nebo k vyhledání všech uzlech, jež některé kritériím.</span><span class="sxs-lookup"><span data-stu-id="664dd-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="664dd-105">Vyberte XPath metody</span><span class="sxs-lookup"><span data-stu-id="664dd-105">XPath Select Methods</span></span>  
 <span data-ttu-id="664dd-106">Třídy DOM nabízí dvě metody pro výběr XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda a <xref:System.Xml.XmlNode.SelectNodes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="664dd-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="664dd-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda vrátí první uzlu, který odpovídá kritériím výběru.</span><span class="sxs-lookup"><span data-stu-id="664dd-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="664dd-108"><xref:System.Xml.XmlNode.SelectNodes%2A> Metoda vrátí <xref:System.Xml.XmlNodeList> obsahující odpovídající uzly.</span><span class="sxs-lookup"><span data-stu-id="664dd-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="664dd-109">Následující příklad používá <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda vyberte první `book` uzlu, ve kterém jméno autora poslední splňují zadaná kritéria.</span><span class="sxs-lookup"><span data-stu-id="664dd-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="664dd-110">Soubor bookstore.xml (které je zadáno na konci tohoto tématu) se používá jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="664dd-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="664dd-111">Další příklad používá <xref:System.Xml.XmlNode.SelectNodes%2A> metoda vyberte všechny uzly adresáře, ve kterých je větší než po zadanou dobu cenu.</span><span class="sxs-lookup"><span data-stu-id="664dd-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="664dd-112">Ceny pro každou knihu v seznamu vybraný je pak prostřednictvím kódu programu snížit deset procent.</span><span class="sxs-lookup"><span data-stu-id="664dd-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="664dd-113">Nakonec je aktualizovaný soubor zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="664dd-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="664dd-114">Soubor bookstore.xml (které je zadáno na konci tohoto tématu) se používá jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="664dd-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="664dd-115">Výše uvedených příkladech spustí dotaz XPath na element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="664dd-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="664dd-116">Nastavení výchozí bod pro cestu XPath dotazu nastaví kontext uzlu, který je výchozím bodem pro dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="664dd-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="664dd-117">Pokud nechcete, aby pro spuštění na element dokumentu, ale chcete začít od prvního podřízeného prvku dokumentu, můžete příkaz select kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="664dd-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="664dd-118">Všechny <xref:System.Xml.XmlNodeList> objekty jsou synchronizovány s zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="664dd-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="664dd-119">Proto pokud iteraci v rámci seznamu uzlu a změňte hodnotu uzlu, tento uzel je aktualizované taky v dokumentu, ze které pochází.</span><span class="sxs-lookup"><span data-stu-id="664dd-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="664dd-120">Všimněte si v předchozím příkladu, změny uzlu ve vybraných <xref:System.Xml.XmlNodeList> také změněna zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="664dd-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="664dd-121">Pokud zdrojový dokument je změněn, se doporučuje znovu select.</span><span class="sxs-lookup"><span data-stu-id="664dd-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="664dd-122">Pokud je uzel upravit jeden, který by mohl způsobit uzlu, který má být přidán do seznamu uzlu, pokud nebyla dříve, nebo její odebrání ze seznamu uzlu teď způsobit, není zaručeno, seznam uzlů je nyní přesná.</span><span class="sxs-lookup"><span data-stu-id="664dd-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="664dd-123">Obory názvů ve výrazech XPath</span><span class="sxs-lookup"><span data-stu-id="664dd-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="664dd-124">Výrazech XPath může zahrnovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="664dd-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="664dd-125">Namespace řešení je podporována při použití <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="664dd-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="664dd-126">Obsahuje-li výraz XPath předpony, identifikátor URI pár předpony a oboru názvů musí být přidaný do <xref:System.Xml.XmlNamespaceManager>a <xref:System.Xml.XmlNamespaceManager> je předán <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> nebo <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="664dd-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="664dd-127">Všimněte si, že pomocí výše uvedené příklady kódu <xref:System.Xml.XmlNamespaceManager> vyřešit obor názvů bookstore.xml dokumentu.</span><span class="sxs-lookup"><span data-stu-id="664dd-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="664dd-128">Pokud výraz XPath neobsahuje předpony, předpokládá se, že je obor názvů identifikátor URI (Uniform Resource) prázdného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="664dd-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="664dd-129">Pokud soubor XML obsahuje výchozí obor názvů, musí stále přidejte identifikátor URI oboru názvů a předpony k <xref:System.Xml.XmlNamespaceManager>, jinak budou vybrány žádné uzly.</span><span class="sxs-lookup"><span data-stu-id="664dd-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="664dd-130">Vstupní soubor</span><span class="sxs-lookup"><span data-stu-id="664dd-130">Input File</span></span>  
 <span data-ttu-id="664dd-131">Toto je soubor bookstore.xml, který se používá jako vstupní soubor v příkladech v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="664dd-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="664dd-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="664dd-132">See Also</span></span>  
 [<span data-ttu-id="664dd-133">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="664dd-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
