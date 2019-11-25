---
title: Obor výchozích názvových prostorů
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8ba4d13b6d40180a88651f0503d1323f2b78f36c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343648"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="91999-102">Scope of Default Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91999-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="91999-103">Default namespaces as represented in the XML tree are not in scope for queries.</span><span class="sxs-lookup"><span data-stu-id="91999-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="91999-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span><span class="sxs-lookup"><span data-stu-id="91999-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="91999-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span><span class="sxs-lookup"><span data-stu-id="91999-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="91999-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span><span class="sxs-lookup"><span data-stu-id="91999-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="91999-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span><span class="sxs-lookup"><span data-stu-id="91999-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91999-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="91999-108">Example</span></span>  
 <span data-ttu-id="91999-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span><span class="sxs-lookup"><span data-stu-id="91999-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="91999-110">Kód</span><span class="sxs-lookup"><span data-stu-id="91999-110">Code</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="91999-111">Komentáře</span><span class="sxs-lookup"><span data-stu-id="91999-111">Comments</span></span>  
 <span data-ttu-id="91999-112">This example produces the following result:</span><span class="sxs-lookup"><span data-stu-id="91999-112">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="91999-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="91999-113">Example</span></span>  
 <span data-ttu-id="91999-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span><span class="sxs-lookup"><span data-stu-id="91999-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="91999-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span><span class="sxs-lookup"><span data-stu-id="91999-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="91999-116">This places all XML properties in the default namespace.</span><span class="sxs-lookup"><span data-stu-id="91999-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="91999-117">No other modifications are required to the example to make it work properly.</span><span class="sxs-lookup"><span data-stu-id="91999-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="91999-118">Kód</span><span class="sxs-lookup"><span data-stu-id="91999-118">Code</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="91999-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="91999-119">Comments</span></span>  
 <span data-ttu-id="91999-120">This example produces the following result:</span><span class="sxs-lookup"><span data-stu-id="91999-120">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="91999-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91999-121">See also</span></span>

- [<span data-ttu-id="91999-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91999-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
