---
title: Staticky kompilované dotazy (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253035"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="f619c-102">Staticky kompilované dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f619c-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f619c-103">Jedním z nejdůležitějších výhod výkonu LINQ na <xref:System.Xml.XmlDocument>XML, na rozdíl od , je, že dotazy v LINQ na XML jsou staticky kompilovány, zatímco dotazy XPath musí být interpretovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="f619c-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="f619c-104">Tato funkce je integrována do LINQ do XML, takže není nutné provádět další kroky, abyste ji mohli využít, ale je užitečné pochopit rozdíl při výběru mezi těmito dvěma technologiemi.</span><span class="sxs-lookup"><span data-stu-id="f619c-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="f619c-105">Toto téma vysvětluje rozdíl.</span><span class="sxs-lookup"><span data-stu-id="f619c-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="f619c-106">Staticky zkompilované dotazy vs. XPath</span><span class="sxs-lookup"><span data-stu-id="f619c-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="f619c-107">Následující příklad ukazuje, jak získat potomek prvky se zadaným názvem a s atributem se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f619c-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="f619c-108">Následující je ekvivalentní výraz XPath:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="f619c-108">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f619c-109">Výraz dotazu v tomto příkladu je přepsán kompilátorem na syntaxi dotazu na základě metody.</span><span class="sxs-lookup"><span data-stu-id="f619c-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="f619c-110">Následující příklad, který je napsán v syntaxi dotazu založené na metodě, vytváří stejné výsledky jako předchozí:</span><span class="sxs-lookup"><span data-stu-id="f619c-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f619c-111">Metoda <xref:System.Linq.Enumerable.Where%2A> je metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f619c-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="f619c-112">Další informace naleznete v [tématu Metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f619c-112">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="f619c-113">Protože <xref:System.Linq.Enumerable.Where%2A> je metoda rozšíření, výše uvedený dotaz je zkompilován, jako by byly zapsány takto:</span><span class="sxs-lookup"><span data-stu-id="f619c-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f619c-114">Tento příklad vytváří přesně stejné výsledky jako předchozí dva příklady.</span><span class="sxs-lookup"><span data-stu-id="f619c-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="f619c-115">To ilustruje skutečnost, že dotazy jsou efektivně kompilovány do staticky propojené volání metod.</span><span class="sxs-lookup"><span data-stu-id="f619c-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="f619c-116">To v kombinaci s odloženou sémantikou sémantiky iterátorů zlepšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="f619c-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="f619c-117">Další informace o odložené spuštění sémantiku iterátorů naleznete [v tématu Odložené spuštění a Opožděné vyhodnocení v LINQ na XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f619c-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f619c-118">Tyto příklady jsou reprezentativní pro kód, který může napsat kompilátor.</span><span class="sxs-lookup"><span data-stu-id="f619c-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="f619c-119">Skutečná implementace se může mírně lišit od těchto příkladů, ale výkon bude stejný nebo podobný těmto příkladům.</span><span class="sxs-lookup"><span data-stu-id="f619c-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="f619c-120">Spuštění výrazů XPath s dokumentem XmlDocument</span><span class="sxs-lookup"><span data-stu-id="f619c-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="f619c-121">Následující příklad <xref:System.Xml.XmlDocument> používá k dosažení stejných výsledků jako v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="f619c-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="f619c-122">Tento dotaz vrátí stejný výstup jako příklady, které používají LINQ do XML; jediným rozdílem je, že LINQ na XML odsazuje vytištěný XML, zatímco <xref:System.Xml.XmlDocument> není.</span><span class="sxs-lookup"><span data-stu-id="f619c-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="f619c-123"><xref:System.Xml.XmlDocument> Však přístup obecně neprovádí stejně jako LINQ <xref:System.Xml.XmlNode.SelectNodes%2A> do XML, protože metoda musí provést následující interně pokaždé, když je volána:</span><span class="sxs-lookup"><span data-stu-id="f619c-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="f619c-124">Analyzuje řetězec, který obsahuje výraz XPath, rozdělení řetězce na tokeny.</span><span class="sxs-lookup"><span data-stu-id="f619c-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="f619c-125">Ověří tokeny a ujistěte se, že výraz XPath je platný.</span><span class="sxs-lookup"><span data-stu-id="f619c-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="f619c-126">Převádí výraz do stromu vnitřního výrazu.</span><span class="sxs-lookup"><span data-stu-id="f619c-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="f619c-127">Iterem prostřednictvím uzlů, vhodně výběru uzlů pro sadu výsledků na základě vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="f619c-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="f619c-128">To je výrazně více než práce provedené odpovídající LINQ na dotaz XML.</span><span class="sxs-lookup"><span data-stu-id="f619c-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="f619c-129">Konkrétní rozdíl výkonu se liší pro různé typy dotazů, ale obecně LINQ na XML dotazy méně práce, a <xref:System.Xml.XmlDocument>proto provádět lépe, než vyhodnocení xpath výrazy pomocí .</span><span class="sxs-lookup"><span data-stu-id="f619c-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
