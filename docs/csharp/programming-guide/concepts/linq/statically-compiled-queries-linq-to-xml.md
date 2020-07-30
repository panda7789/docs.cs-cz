---
title: Staticky kompilované dotazy (LINQ to XML) (C#)
description: Přečtěte si o staticky kompilovaných dotazech v LINQ to XML v jazyce C# a o tom, jak se liší od dotazů XPath, které je nutné interpretovat za běhu.
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: cd2e6a6507311d5fc17215a22c70bd0449292b6f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302305"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="b1d07-103">Staticky kompilované dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1d07-103">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b1d07-104">Jedna z nejdůležitějších výhod výkonu LINQ to XML, na rozdíl od <xref:System.Xml.XmlDocument> , je, že dotazy v LINQ to XML jsou staticky kompilovány, zatímco dotazy XPath musí být interpretovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="b1d07-104">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="b1d07-105">Tato funkce je integrovaná do LINQ to XML, takže není nutné provádět další kroky, abyste je mohli využít, ale je užitečné pochopit rozdíl mezi těmito dvěma technologiemi.</span><span class="sxs-lookup"><span data-stu-id="b1d07-105">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="b1d07-106">Toto téma popisuje rozdíl.</span><span class="sxs-lookup"><span data-stu-id="b1d07-106">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="b1d07-107">Staticky kompilované dotazy vs. XPath</span><span class="sxs-lookup"><span data-stu-id="b1d07-107">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="b1d07-108">Následující příklad ukazuje, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b1d07-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="b1d07-109">Následuje ekvivalentní výraz XPath:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="b1d07-109">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="b1d07-110">Výraz dotazu v tomto příkladu je znovu napsán kompilátorem do syntaxe dotazu založeného na metodě.</span><span class="sxs-lookup"><span data-stu-id="b1d07-110">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="b1d07-111">Následující příklad, který je napsán v syntaxi dotazu založeného na metodách, vytváří stejné výsledky jako předchozí:</span><span class="sxs-lookup"><span data-stu-id="b1d07-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="b1d07-112"><xref:System.Linq.Enumerable.Where%2A>Metoda je rozšiřující metoda.</span><span class="sxs-lookup"><span data-stu-id="b1d07-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="b1d07-113">Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b1d07-113">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="b1d07-114">Vzhledem k tomu <xref:System.Linq.Enumerable.Where%2A> , že je metoda rozšíření, je dotaz výše zkompilován, jako by byl napsán takto:</span><span class="sxs-lookup"><span data-stu-id="b1d07-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="b1d07-115">Tento příklad vytváří přesně stejné výsledky jako v předchozích dvou příkladech.</span><span class="sxs-lookup"><span data-stu-id="b1d07-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="b1d07-116">To ukazuje fakt, že dotazy jsou efektivně zkompilovány do staticky propojených volání metody.</span><span class="sxs-lookup"><span data-stu-id="b1d07-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="b1d07-117">V kombinaci s sémantikou pro odložené provádění iterátorů zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="b1d07-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="b1d07-118">Další informace o devodit sémantikě iterátorů naleznete [v tématu Odložené provádění a opožděné hodnocení v LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b1d07-118">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1d07-119">Tyto příklady jsou zástupci kódu, který kompilátor může zapisovat.</span><span class="sxs-lookup"><span data-stu-id="b1d07-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="b1d07-120">Skutečná implementace se může mírně lišit od těchto příkladů, ale výkon bude stejný nebo podobný jako v těchto příkladech.</span><span class="sxs-lookup"><span data-stu-id="b1d07-120">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="b1d07-121">Provádění výrazů XPath s XmlDocument</span><span class="sxs-lookup"><span data-stu-id="b1d07-121">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="b1d07-122">Následující příklad používá <xref:System.Xml.XmlDocument> k dosažení stejných výsledků jako předchozí příklady:</span><span class="sxs-lookup"><span data-stu-id="b1d07-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="b1d07-123">Tento dotaz vrátí stejný výstup jako příklady, které používají LINQ to XML; Jediným rozdílem je, že LINQ to XML odsadí vytištěný XML, zatímco <xref:System.Xml.XmlDocument> ne.</span><span class="sxs-lookup"><span data-stu-id="b1d07-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="b1d07-124">Obecně se ale <xref:System.Xml.XmlDocument> neprovádí ani LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda musí provést následující interně při každém volání:</span><span class="sxs-lookup"><span data-stu-id="b1d07-124">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="b1d07-125">Analyzuje řetězec, který obsahuje výraz XPath a přerušuje řetězec na tokeny.</span><span class="sxs-lookup"><span data-stu-id="b1d07-125">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="b1d07-126">Ověřuje tokeny, aby bylo zajištěno, že je výraz XPath platný.</span><span class="sxs-lookup"><span data-stu-id="b1d07-126">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="b1d07-127">Převede výraz do vnitřního stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="b1d07-127">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="b1d07-128">Projde uzly a odpovídajícím způsobem vybere uzly sady výsledků na základě vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="b1d07-128">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="b1d07-129">To je podstatně větší než práce prováděná odpovídajícím dotazem LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="b1d07-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="b1d07-130">Konkrétní rozdíl mezi výkonem se liší v různých typech dotazů, ale obecně LINQ to XML dotazy méně fungují, a proto je lepší, než vyhodnocování výrazů XPath pomocí <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="b1d07-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
