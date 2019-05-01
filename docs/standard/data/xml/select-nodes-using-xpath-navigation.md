---
title: Výběr uzlů pomocí navigace XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026975"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="8e8f3-102">Výběr uzlů pomocí navigace XPath</span><span class="sxs-lookup"><span data-stu-id="8e8f3-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="8e8f3-103">XML Document Object Model (DOM) obsahuje metody, které vám umožní použít navigační jazyk XML Path (XPath) dotaz na informace v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="8e8f3-104">Výraz XPath můžete použít k vyhledání jednoho, konkrétní uzel nebo najít všechny uzly, které odpovídají kritérií.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="8e8f3-105">Výběr XPath metody</span><span class="sxs-lookup"><span data-stu-id="8e8f3-105">XPath Select Methods</span></span>  
 <span data-ttu-id="8e8f3-106">Třídy modelu DOM poskytují dvě metody pro výběr XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda a <xref:System.Xml.XmlNode.SelectNodes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="8e8f3-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda vrátí první uzel, který by odpovídal kritériím výběru.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="8e8f3-108"><xref:System.Xml.XmlNode.SelectNodes%2A> Vrátí metoda <xref:System.Xml.XmlNodeList> , která obsahuje odpovídající uzly.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="8e8f3-109">V následujícím příkladu <xref:System.Xml.XmlNode.SelectSingleNode%2A> metoda vyberte první `book` uzel, ve kterém autora příjmení splňují zadaná kritéria.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="8e8f3-110">Soubor bookstore.xml (který je k dispozici na konci tohoto tématu) se používá jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="8e8f3-111">Následující příklad používá <xref:System.Xml.XmlNode.SelectNodes%2A> metoda vybere všechny uzly adresáře, ve kterých je větší než zadaná velikost cena.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="8e8f3-112">Cena za jednotlivé knihy ve vybraném seznamu je potom programově snižuje deset procent.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="8e8f3-113">Nakonec je aktualizovaný soubor zapsán do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="8e8f3-114">Soubor bookstore.xml (který je k dispozici na konci tohoto tématu) se používá jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="8e8f3-115">Výše uvedených příkladech spustit dotaz XPath na element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="8e8f3-116">Nastavení výchozí bod pro cestu XPath dotaz nastaví kontextu uzlu, který je výchozím bodem pro dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="8e8f3-117">Pokud nechcete, aby začínal element dokumentu, ale chcete začít od první podřízený element dokumentu, vám umožní kódování příkaz select následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8e8f3-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="8e8f3-118">Všechny <xref:System.Xml.XmlNodeList> objekty jsou synchronizovány s zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="8e8f3-119">Proto pokud iteraci v rámci seznamu uzlů a změňte hodnotu uzlu, uzlu jsou aktualizované taky v dokumentu, ze které pochází.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="8e8f3-120">Všimněte si, že v předchozím příkladu, která při změně uzlu ve vybraném období <xref:System.Xml.XmlNodeList> etag zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e8f3-121">Při změně podkladového dokumentu, je vhodné spustit znovu vybrat.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="8e8f3-122">Je-li upravit uzlu je ten, který může způsobit, že uzel, který má přidat do seznamu uzlu, pokud nebyla dříve, nebo ho odebrat ze seznamu uzlů nyní způsobí, není zaručeno, že seznam uzlů je nyní přesné.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="8e8f3-123">Obory názvů ve výrazech XPath</span><span class="sxs-lookup"><span data-stu-id="8e8f3-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="8e8f3-124">Výrazy XPath může zahrnovat obory názvů.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="8e8f3-125">Namespace rozlišení není podporováno použití <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="8e8f3-126">Pokud výraz XPath obsahuje předponu, identifikátor URI dvojice předpony a oboru názvů musí být přidané do <xref:System.Xml.XmlNamespaceManager>a <xref:System.Xml.XmlNamespaceManager> je předán <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> nebo <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="8e8f3-127">Všimněte si, že pomocí výše uvedených příkladech kódu <xref:System.Xml.XmlNamespaceManager> určit obor názvů bookstore.xml dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e8f3-128">Pokud výraz XPath neobsahuje předponu, předpokládá se, že je obor názvů identifikátoru URI (Uniform Resource) prázdný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="8e8f3-129">Pokud soubor XML obsahuje výchozí obor názvů, přesto musí přidat předpony a oboru názvů identifikátoru URI k <xref:System.Xml.XmlNamespaceManager>; v opačném případě bude vybráno žádné uzly.</span><span class="sxs-lookup"><span data-stu-id="8e8f3-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="8e8f3-130">Vstupní soubor</span><span class="sxs-lookup"><span data-stu-id="8e8f3-130">Input File</span></span>  
 <span data-ttu-id="8e8f3-131">Toto je bookstore.xml soubor, který slouží jako vstupní soubor v příkladech v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="8e8f3-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e8f3-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e8f3-132">See also</span></span>

- [<span data-ttu-id="8e8f3-133">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="8e8f3-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
