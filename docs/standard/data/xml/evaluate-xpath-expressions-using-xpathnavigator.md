---
title: Vyhodnocení výrazů XPath pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8666aa9cb9f0512c600a77891b16f439c46995a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517406"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="f99ac-102">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f99ac-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="f99ac-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu pro vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="f99ac-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="f99ac-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda má výraz XPath, se vyhodnotí a vrátí W3C XPath typu logická hodnota, číslo, řetězec nebo sada uzlů na základě výsledku výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="f99ac-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="f99ac-105">Vyhodnocení metody</span><span class="sxs-lookup"><span data-stu-id="f99ac-105">The Evaluate Method</span></span>  
 <span data-ttu-id="f99ac-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda má výraz XPath, se vyhodnotí a vrátí zadaný výsledek logickou hodnotu (<xref:System.Boolean>), počet (<xref:System.Double>), řetězec (<xref:System.String>), nebo sada uzlů (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="f99ac-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="f99ac-107">Například <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu lze použít v matematické metodě.</span><span class="sxs-lookup"><span data-stu-id="f99ac-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="f99ac-108">Následující příklad kódu vypočítá celková cena všech knih v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="f99ac-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="f99ac-109">V příkladu přebírá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f99ac-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="f99ac-110">pozice a poslední funkce</span><span class="sxs-lookup"><span data-stu-id="f99ac-110">position and last Functions</span></span>  
 <span data-ttu-id="f99ac-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="f99ac-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="f99ac-112">Jeden z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> přebírá metody <xref:System.Xml.XPath.XPathNodeIterator> objektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f99ac-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="f99ac-113">Tento konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodou je stejný jako <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu, která přebírá pouze <xref:System.Xml.XPath.XPathExpression> objektu jako parametr, s tím rozdílem, že umožňuje uzel nastavení argumentu pro zadání pro provedení vyhodnocení na aktuální kontext.</span><span class="sxs-lookup"><span data-stu-id="f99ac-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="f99ac-114">Je vyžadován pro cestu XPath tento kontext `position()` a `last()` funkce jsou relativní vzhledem k aktuální uzel kontextu.</span><span class="sxs-lookup"><span data-stu-id="f99ac-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="f99ac-115">Není-li použít jako predikát v kroku umístění, `position()` a `last()` funkce vyžadují odkaz na uzel nastavení, aby se vyhodnotilo, jinak `position` a `last` funkce vrátit `0`.</span><span class="sxs-lookup"><span data-stu-id="f99ac-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99ac-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f99ac-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f99ac-117">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="f99ac-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f99ac-118">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f99ac-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f99ac-119">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f99ac-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="f99ac-120">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="f99ac-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="f99ac-121">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="f99ac-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="f99ac-122">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="f99ac-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
