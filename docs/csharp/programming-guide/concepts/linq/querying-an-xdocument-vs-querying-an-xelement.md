---
title: Dotazování xdocument vs dotazování XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253128"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="90938-102">Dotazování xdocument vs dotazování XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="90938-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="90938-103">Při načítání dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>prostřednictvím , zjistíte, že budete muset psát dotazy mírně <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>odlišně, než při načítání přes .</span><span class="sxs-lookup"><span data-stu-id="90938-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="90938-104">Porovnání XDocument.Load a XElement.Load</span><span class="sxs-lookup"><span data-stu-id="90938-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="90938-105">Když načtete dokument <xref:System.Xml.Linq.XElement> XML <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>do <xref:System.Xml.Linq.XElement> via , kořenový adresář stromu XML obsahuje kořenový prvek načteného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="90938-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="90938-106">Však při načtení stejného <xref:System.Xml.Linq.XDocument> dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>XML do via , <xref:System.Xml.Linq.XDocument> kořen stromu je uzel a kořenový prvek <xref:System.Xml.Linq.XElement> načteného <xref:System.Xml.Linq.XDocument>dokumentu je jeden povolený podřízený uzel .</span><span class="sxs-lookup"><span data-stu-id="90938-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="90938-107">Osy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pracují vzhledem ke kořenovému uzlu.</span><span class="sxs-lookup"><span data-stu-id="90938-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="90938-108">Tento první příklad načte <xref:System.Xml.Linq.XElement.Load%2A>strom XML pomocí .</span><span class="sxs-lookup"><span data-stu-id="90938-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="90938-109">Potom dotazy na podřízené prvky kořene stromu.</span><span class="sxs-lookup"><span data-stu-id="90938-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="90938-110">Podle očekávání tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="90938-110">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="90938-111">Následující příklad je stejný jako výše uvedený, s výjimkou, že <xref:System.Xml.Linq.XDocument> strom XML <xref:System.Xml.Linq.XElement>je načten do místo .</span><span class="sxs-lookup"><span data-stu-id="90938-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="90938-112">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="90938-112">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="90938-113">Všimněte si, že `Root` stejný dotaz vrátil jeden uzel namísto tří podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="90938-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="90938-114">Jedním z přístupů k řešení <xref:System.Xml.Linq.XDocument.Root%2A> tohoto je použití vlastnosti před přístupem k osy metody, takto:</span><span class="sxs-lookup"><span data-stu-id="90938-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="90938-115">Tento dotaz nyní provádí stejným způsobem jako dotaz <xref:System.Xml.Linq.XElement>na stromu zakořeněné v .</span><span class="sxs-lookup"><span data-stu-id="90938-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="90938-116">Příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="90938-116">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  