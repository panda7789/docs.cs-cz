---
title: Staticky zkompilován dotazy (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 842f8c1c2fa07e1658992e94e5163222f38f80ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514787"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="e5e79-102">Staticky zkompilován dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5e79-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="e5e79-103">Jeden z vašich nejdůležitějších výkonu výhody LINQ to XML, nikoli <xref:System.Xml.XmlDocument>, dotazy v LINQ to XML nejsou staticky zkompilován, zatímco v době běhu musí být interpretován dotazy XPath.</span><span class="sxs-lookup"><span data-stu-id="e5e79-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="e5e79-104">Tato funkce je založená na technologii LINQ to XML, takže není potřeba provést další kroky pro jejich výhod, ale je vhodné pochopit v čem při volbě mezi tyto technologie.</span><span class="sxs-lookup"><span data-stu-id="e5e79-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="e5e79-105">Toto téma vysvětluje rozdíl.</span><span class="sxs-lookup"><span data-stu-id="e5e79-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="e5e79-106">Staticky kompilaci dotazů vs. XPath</span><span class="sxs-lookup"><span data-stu-id="e5e79-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="e5e79-107">Následující příklad ukazuje, jak získat Následnické prvky se zadaným názvem a atribut se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e5e79-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="e5e79-108">Toto je ekvivalentní výraz XPath:</span><span class="sxs-lookup"><span data-stu-id="e5e79-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5e79-109">Výraz dotazu v tomto příkladu je znovu zapsat pomocí kompilátoru, aby syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="e5e79-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="e5e79-110">V následujícím příkladu, který je napsán v syntaxe dotazů založených na volání metody, vytvoří stejné výsledky jako předchozí:</span><span class="sxs-lookup"><span data-stu-id="e5e79-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5e79-111"><xref:System.Linq.Enumerable.Where%2A> Metoda je metodou rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e5e79-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="e5e79-112">Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e5e79-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="e5e79-113">Protože <xref:System.Linq.Enumerable.Where%2A> je metodu rozšíření se výše uvedený dotaz je zkompilován, jako by byl napsán takto:</span><span class="sxs-lookup"><span data-stu-id="e5e79-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5e79-114">Tento příklad vytvoří stejné výsledky jako v předchozích dvou příkladech.</span><span class="sxs-lookup"><span data-stu-id="e5e79-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="e5e79-115">To ukazuje na skutečnost, že jsou dotazy efektivně kompilovány do volání metody staticky propojené.</span><span class="sxs-lookup"><span data-stu-id="e5e79-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="e5e79-116">Ve spojení se sémantika odložené provedení iterátory, přičemž zlepšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="e5e79-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="e5e79-117">Další informace o sémantice odložené provedení iterátory, naleznete v tématu [odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e5e79-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5e79-118">Tyto příklady jsou zástupce kód, který kompilátor může zapsat.</span><span class="sxs-lookup"><span data-stu-id="e5e79-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="e5e79-119">Skutečná implementace může mírně lišit od těchto příkladech, ale výkon bude stejná nebo podobný tyto příklady.</span><span class="sxs-lookup"><span data-stu-id="e5e79-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="e5e79-120">Výrazy XPath s třídou XMLDocument nastavenou na provádění</span><span class="sxs-lookup"><span data-stu-id="e5e79-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="e5e79-121">Následující příklad používá <xref:System.Xml.XmlDocument> provádět stejné výsledky jako v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="e5e79-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="e5e79-122">Tento dotaz vrací stejný výstup jako příklady, které používají technologii LINQ to XML jediným rozdílem je, že technologie LINQ to XML odsazení tištěné XML, zatímco <xref:System.Xml.XmlDocument> tak není.</span><span class="sxs-lookup"><span data-stu-id="e5e79-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="e5e79-123">Ale <xref:System.Xml.XmlDocument> přístup obvykle neprovádí tak LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> metoda musí takto interně pokaždé, když je volána:</span><span class="sxs-lookup"><span data-stu-id="e5e79-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="e5e79-124">Analyzuje řetězec, který obsahuje výraz XPath, rozdělení řetězec do tokenů.</span><span class="sxs-lookup"><span data-stu-id="e5e79-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="e5e79-125">Ověřuje tokeny, abyste měli jistotu, že výraz XPath je neplatný.</span><span class="sxs-lookup"><span data-stu-id="e5e79-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="e5e79-126">Převádí výraz, který strom interních výrazů.</span><span class="sxs-lookup"><span data-stu-id="e5e79-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="e5e79-127">Prochází uzly, odpovídajícím způsobem výběru uzlů pro sady výsledků na základě vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="e5e79-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="e5e79-128">To je mnohem větší než práce provádí odpovídající dotazu LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="e5e79-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="e5e79-129">Rozdíl měřené liší pro jednotlivé typy dotazů, ale v obecné LINQ to XML dotazy méně práci a proto fungoval lépe, než vyhodnocení výrazů XPath pomocí <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="e5e79-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e79-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5e79-130">See also</span></span>

- [<span data-ttu-id="e5e79-131">Výkon (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5e79-131">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
