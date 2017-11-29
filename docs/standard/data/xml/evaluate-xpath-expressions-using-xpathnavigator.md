---
title: "Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d513f48155a582a5158cccdd682f5b8485caefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="5d40c-102">Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="5d40c-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="5d40c-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody k vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="5d40c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="5d40c-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda přebírá výraz XPath, vyhodnotí ji a vrátí typ W3C XPath logická hodnota, čísla, řetězce nebo sada uzlů na základě výsledku výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="5d40c-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="5d40c-105">Vyhodnocení metody</span><span class="sxs-lookup"><span data-stu-id="5d40c-105">The Evaluate Method</span></span>  
 <span data-ttu-id="5d40c-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda přebírá výraz XPath, vyhodnotí ji a vrátí zadaný výsledek logická hodnota (<xref:System.Boolean>), čísla (<xref:System.Double>), řetězec (<xref:System.String>), nebo sada uzlů (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="5d40c-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="5d40c-107">Například <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu lze použít v matematickém metoda.</span><span class="sxs-lookup"><span data-stu-id="5d40c-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="5d40c-108">Následující příklad kódu vypočítá celková cena všech knih v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="5d40c-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="5d40c-109">V příkladu trvá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="5d40c-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="5d40c-110">pozice a poslední funkce</span><span class="sxs-lookup"><span data-stu-id="5d40c-110">position and last Functions</span></span>  
 <span data-ttu-id="5d40c-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda je přetížena.</span><span class="sxs-lookup"><span data-stu-id="5d40c-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="5d40c-112">Jeden z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> trvá metody <xref:System.Xml.XPath.XPathNodeIterator> objektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5d40c-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="5d40c-113">Tato konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda je stejná jako <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody, která přijímá pouze <xref:System.Xml.XPath.XPathExpression> objektu jako parametr, s tím rozdílem, že umožňuje uzlu nastavit ke specifikaci aktuální kontext k vyhodnocení plnění.</span><span class="sxs-lookup"><span data-stu-id="5d40c-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="5d40c-114">Tento kontext se vyžaduje pro cestu XPath `position()` a `last()` funkce, jako jsou relativní vzhledem k uzlu aktuálního kontextu.</span><span class="sxs-lookup"><span data-stu-id="5d40c-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="5d40c-115">Není-li použít jako predikát v kroku umístění, `position()` a `last()` funkce vyžadují odkaz na uzlu nastavit, aby se vyhodnotilo, jinak hodnota `position` a `last` funkce vrátí `0`.</span><span class="sxs-lookup"><span data-stu-id="5d40c-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d40c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d40c-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="5d40c-117">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="5d40c-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="5d40c-118">Vyberte pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="5d40c-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="5d40c-119">Odpovídající pomocí objektem XPathNavigator nastaveným na uzly</span><span class="sxs-lookup"><span data-stu-id="5d40c-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="5d40c-120">Typy uzlů rozpoznána s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="5d40c-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="5d40c-121">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="5d40c-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="5d40c-122">Výrazy kompilované XPath</span><span class="sxs-lookup"><span data-stu-id="5d40c-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
