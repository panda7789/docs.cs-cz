---
title: 'Postupy: vytváření dotazů na XML v oborech názvů (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 29c4b01bfce75ce71d5214fef0cc55cd82c4e776
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525640"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="25d9c-102">Postupy: vytváření dotazů na XML v oborech názvů (C#)</span><span class="sxs-lookup"><span data-stu-id="25d9c-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="25d9c-103">Chcete-li napsat dotaz na XML, který je v oboru názvů, musíte použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="25d9c-104">Pro jazyk C#, je nejběžnější přístup k inicializaci <xref:System.Xml.Linq.XNamespace> řetězec, který obsahuje identifikátor URI, pak pomocí přetížení operátoru sčítání zkombinovat s místním názvem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="25d9c-105">První sada příklady v tomto tématu ukazuje, jak vytvořit stromu XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="25d9c-106">Druhá sada ukazuje postup vytvoření stromu XML v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="25d9c-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d9c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="25d9c-107">Example</span></span>  
 <span data-ttu-id="25d9c-108">Následující příklad vytvoří stromu XML, který je ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="25d9c-109">Potom načte kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-109">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="25d9c-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="25d9c-110">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="25d9c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="25d9c-111">Example</span></span>  
 <span data-ttu-id="25d9c-112">V jazyce C# psát dotazy stejným způsobem bez ohledu na to, zda jsou psaní dotazů na stromu XML, který používá obor názvů s předponou nebo stromu XML pomocí výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="25d9c-113">Následující příklad vytvoří stromu XML, který je v oboru názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="25d9c-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="25d9c-114">Potom načte kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="25d9c-114">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="25d9c-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="25d9c-115">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="25d9c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="25d9c-116">See Also</span></span>

- [<span data-ttu-id="25d9c-117">Práce s názvovými prostory XML (C#)</span><span class="sxs-lookup"><span data-stu-id="25d9c-117">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
