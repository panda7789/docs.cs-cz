---
title: Vyhodnocení výrazů XPath pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 1a17aea66be7f9d35336434408c49bae8046b7e7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710905"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="44319-102">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44319-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="44319-103">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje metodu <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> k vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="44319-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="44319-104">Metoda <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> přebírá výraz XPath, vyhodnocuje ho a vrací typ XPath typu Boolean, Number, String nebo Node v závislosti na výsledku výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="44319-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="44319-105">Metoda Evaluate</span><span class="sxs-lookup"><span data-stu-id="44319-105">The Evaluate Method</span></span>  
 <span data-ttu-id="44319-106">Metoda <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> přebírá výraz XPath, vyhodnocuje ho a vrátí typový výsledek Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>) nebo set Node (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="44319-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="44319-107">Například metoda <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> může být použita v matematické metodě.</span><span class="sxs-lookup"><span data-stu-id="44319-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="44319-108">Následující příklad kódu vypočítá celkovou cenu ze všech knih v souboru `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="44319-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="44319-109">V příkladu se jako vstup používá soubor `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="44319-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="44319-110">pozice a poslední funkce</span><span class="sxs-lookup"><span data-stu-id="44319-110">position and last Functions</span></span>  
 <span data-ttu-id="44319-111">Metoda <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> je přetížena.</span><span class="sxs-lookup"><span data-stu-id="44319-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="44319-112">Jedna z metod <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> přebírá objekt <xref:System.Xml.XPath.XPathNodeIterator> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="44319-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="44319-113">Tato konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda je shodná s metodou <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>, která přebírá jako parametr pouze objekt <xref:System.Xml.XPath.XPathExpression>, s výjimkou toho, že umožňuje argumentu sady uzlů určit aktuální kontext k provedení vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="44319-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="44319-114">Tento kontext je vyžadován pro `position()` XPath a `last()` funkce, protože jsou relativní vzhledem k aktuálnímu uzlu kontextu.</span><span class="sxs-lookup"><span data-stu-id="44319-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="44319-115">Pokud není použit jako predikát v kroku umístění, funkce `position()` a `last()` vyžadují odkaz na sadu uzlů, aby bylo možné je vyhodnotit jinak, `position` a `last` funkce vrátí `0`.</span><span class="sxs-lookup"><span data-stu-id="44319-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44319-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44319-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="44319-117">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="44319-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="44319-118">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44319-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="44319-119">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44319-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="44319-120">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="44319-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="44319-121">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="44319-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="44319-122">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="44319-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
