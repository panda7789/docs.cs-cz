---
title: "Postupy: zápis dotazů na XML v oborech názvů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 194e12f88f7c22c365a18bc2dd42a3dd26b5c569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="d7581-102">Postupy: zápis dotazů na XML v oborech názvů (C#)</span><span class="sxs-lookup"><span data-stu-id="d7581-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="d7581-103">Pokud chcete napsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7581-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="d7581-104">Pro jazyk C#, je nejběžnější přístup k chybě při inicializaci <xref:System.Xml.Linq.XNamespace> pomocí řetězec, který obsahuje identifikátor URI, potom použijte přetížení operátor přidání kombinovat s místní název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7581-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="d7581-105">První sadu příklady v tomto tématu ukazuje, jak vytvořit strom XML ve výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7581-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="d7581-106">Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="d7581-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7581-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7581-107">Example</span></span>  
 <span data-ttu-id="d7581-108">Následující příklad vytvoří ve stromu XML, který je ve výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7581-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="d7581-109">Potom načte kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="d7581-109">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="d7581-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d7581-110">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="d7581-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7581-111">Example</span></span>  
 <span data-ttu-id="d7581-112">V jazyce C# můžete psát dotazy stejným způsobem, bez ohledu na to, jestli jsou zápis dotazů na XML stromové struktury, která používá obor názvů s předponou nebo na strom XML s výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7581-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="d7581-113">Následující příklad vytvoří strom XML, který je v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="d7581-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="d7581-114">Potom načte kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="d7581-114">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="d7581-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d7581-115">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7581-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7581-116">See Also</span></span>  
 [<span data-ttu-id="d7581-117">Práce s obory názvů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d7581-117">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
