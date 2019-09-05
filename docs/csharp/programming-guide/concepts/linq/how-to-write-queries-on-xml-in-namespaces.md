---
title: 'Postupy: Zápis dotazů do XML v oborechC#názvů ()'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 1ded47ced44bebfda92b96f4dc908f1c1b2bbf6b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253204"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="3448a-102">Postupy: Zápis dotazů do XML v oborechC#názvů ()</span><span class="sxs-lookup"><span data-stu-id="3448a-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="3448a-103">Chcete-li zapsat dotaz na XML, který je v oboru názvů, je <xref:System.Xml.Linq.XName> nutné použít objekty, které mají správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3448a-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="3448a-104">C#Nejběžnějším přístupem je inicializovat <xref:System.Xml.Linq.XNamespace> pomocí řetězce, který obsahuje identifikátor URI, potom použít přetížení operátoru sčítání ke kombinování oboru názvů s místním názvem.</span><span class="sxs-lookup"><span data-stu-id="3448a-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="3448a-105">První sada příkladů v tomto tématu ukazuje, jak vytvořit strom XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3448a-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="3448a-106">Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="3448a-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3448a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3448a-107">Example</span></span>  
 <span data-ttu-id="3448a-108">Následující příklad vytvoří strom XML, který je ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3448a-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="3448a-109">Poté načte kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="3448a-109">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="3448a-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3448a-110">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="3448a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3448a-111">Example</span></span>  
 <span data-ttu-id="3448a-112">V C#systému píšete dotazy stejným způsobem bez ohledu na to, zda píšete dotazy ve stromu XML, který používá obor názvů s předponou nebo ve stromu XML s výchozím oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="3448a-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="3448a-113">Následující příklad vytvoří strom XML, který je v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="3448a-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="3448a-114">Poté načte kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="3448a-114">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="3448a-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3448a-115">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="3448a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3448a-116">See also</span></span>

- [<span data-ttu-id="3448a-117">Přehled oborů názvů (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="3448a-117">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
