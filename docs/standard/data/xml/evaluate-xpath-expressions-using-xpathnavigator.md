---
title: Vyhodnocení výrazů XPath pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: b6e18fe02a828ae307ac7ade15650d3303f2600c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287802"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="f518e-102">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f518e-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="f518e-103"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu pro vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="f518e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="f518e-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda přebírá výraz XPath, vyhodnocuje ho a vrací typ XPath typu Boolean, Number, String nebo Node v závislosti na výsledku výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="f518e-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="f518e-105">Metoda Evaluate</span><span class="sxs-lookup"><span data-stu-id="f518e-105">The Evaluate Method</span></span>  
 <span data-ttu-id="f518e-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda přebírá výraz XPath, vyhodnocuje ho a vrátí typový výsledek Boolean ( <xref:System.Boolean> ), Number ( <xref:System.Double> ), String ( <xref:System.String> ) nebo set Node ( <xref:System.Xml.XPath.XPathNodeIterator> ).</span><span class="sxs-lookup"><span data-stu-id="f518e-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="f518e-107">Například <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda může být použita v matematické metodě.</span><span class="sxs-lookup"><span data-stu-id="f518e-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="f518e-108">Následující příklad kódu vypočítá celkovou cenu ze všech knih v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="f518e-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="f518e-109">Příklad přebírá `books.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f518e-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="f518e-110">pozice a poslední funkce</span><span class="sxs-lookup"><span data-stu-id="f518e-110">position and last Functions</span></span>  
 <span data-ttu-id="f518e-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda je přetížena.</span><span class="sxs-lookup"><span data-stu-id="f518e-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="f518e-112">Jedna z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod přebírá <xref:System.Xml.XPath.XPathNodeIterator> objekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f518e-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="f518e-113">Tato konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda je shodná s <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodou, která <xref:System.Xml.XPath.XPathExpression> jako parametr přijímá pouze objekt, s tím rozdílem, že umožňuje argumentu sady uzlů určit aktuální kontext k provedení vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="f518e-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="f518e-114">Tento kontext je vyžadován pro výraz XPath `position()` a `last()` funkce, protože jsou relativní vzhledem k aktuálnímu uzlu kontextu.</span><span class="sxs-lookup"><span data-stu-id="f518e-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="f518e-115">Pokud není použit jako predikát v kroku umístění, `position()` `last()` funkce a vyžadují odkaz na uzel sady, aby bylo možné je vyhodnotit jinak, `position` `last` funkce a vrátí `0` .</span><span class="sxs-lookup"><span data-stu-id="f518e-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f518e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f518e-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f518e-117">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="f518e-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f518e-118">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f518e-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f518e-119">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f518e-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="f518e-120">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="f518e-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="f518e-121">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="f518e-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="f518e-122">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="f518e-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
