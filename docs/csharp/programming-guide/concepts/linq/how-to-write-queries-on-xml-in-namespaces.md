---
title: Zápis dotazů na XML v oborech názvů (C#)
description: Naučte se zapisovat dotazy do XML v oborech názvů. Pro tyto dotazy je nutné použít objekty XName, které mají správný obor názvů.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303176"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="97ea7-104">Zápis dotazů na XML v oborech názvů (C#)</span><span class="sxs-lookup"><span data-stu-id="97ea7-104">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="97ea7-105">Chcete-li zapsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="97ea7-105">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="97ea7-106">V jazyce C# je nejběžnějším přístupem inicializace <xref:System.Xml.Linq.XNamespace> pomocí řetězce, který obsahuje identifikátor URI, a poté použití přetížení operátoru sčítání ke kombinování oboru názvů s místním názvem.</span><span class="sxs-lookup"><span data-stu-id="97ea7-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="97ea7-107">První sada příkladů v tomto tématu ukazuje, jak vytvořit strom XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="97ea7-107">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="97ea7-108">Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="97ea7-108">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97ea7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="97ea7-109">Example</span></span>  
 <span data-ttu-id="97ea7-110">Následující příklad vytvoří strom XML, který je ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="97ea7-110">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="97ea7-111">Poté načte kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="97ea7-111">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="97ea7-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="97ea7-112">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="97ea7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="97ea7-113">Example</span></span>  
 <span data-ttu-id="97ea7-114">V jazyce C# píšete dotazy stejným způsobem bez ohledu na to, zda píšete dotazy ve stromu XML, který používá obor názvů s předponou nebo ve stromu XML s výchozím oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="97ea7-114">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="97ea7-115">Následující příklad vytvoří strom XML, který je v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="97ea7-115">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="97ea7-116">Poté načte kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="97ea7-116">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="97ea7-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="97ea7-117">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="97ea7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97ea7-118">See also</span></span>

- [<span data-ttu-id="97ea7-119">Přehled oborů názvů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="97ea7-119">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
