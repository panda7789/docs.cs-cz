---
title: 'How to: Write Queries on XML in Namespaces'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 496cf8daf5136e8aafff000312bbd730a5152e9f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344462"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="119b5-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="119b5-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="119b5-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span><span class="sxs-lookup"><span data-stu-id="119b5-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="119b5-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span><span class="sxs-lookup"><span data-stu-id="119b5-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="119b5-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span><span class="sxs-lookup"><span data-stu-id="119b5-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="119b5-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span><span class="sxs-lookup"><span data-stu-id="119b5-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="119b5-107">As with other forms of XML, attributes are always in no namespace by default.</span><span class="sxs-lookup"><span data-stu-id="119b5-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="119b5-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span><span class="sxs-lookup"><span data-stu-id="119b5-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="119b5-109">The second set shows how to create an XML tree in a namespace with a prefix.</span><span class="sxs-lookup"><span data-stu-id="119b5-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="119b5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="119b5-110">Example</span></span>  
 <span data-ttu-id="119b5-111">The following example creates an XML tree that is in a default namespace.</span><span class="sxs-lookup"><span data-stu-id="119b5-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="119b5-112">It then retrieves a collection of elements.</span><span class="sxs-lookup"><span data-stu-id="119b5-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
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
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="119b5-113">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="119b5-113">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="119b5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="119b5-114">Example</span></span>  
 <span data-ttu-id="119b5-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span><span class="sxs-lookup"><span data-stu-id="119b5-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="119b5-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span><span class="sxs-lookup"><span data-stu-id="119b5-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="119b5-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span><span class="sxs-lookup"><span data-stu-id="119b5-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="119b5-118">You also use the prefix when querying an XML tree using XML properties.</span><span class="sxs-lookup"><span data-stu-id="119b5-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="119b5-119">The following example creates an XML tree that is in a namespace with a prefix.</span><span class="sxs-lookup"><span data-stu-id="119b5-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="119b5-120">It then retrieves a collection of elements.</span><span class="sxs-lookup"><span data-stu-id="119b5-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="119b5-121">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="119b5-121">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="119b5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="119b5-122">See also</span></span>

- [<span data-ttu-id="119b5-123">Namespaces Overview (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="119b5-123">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
