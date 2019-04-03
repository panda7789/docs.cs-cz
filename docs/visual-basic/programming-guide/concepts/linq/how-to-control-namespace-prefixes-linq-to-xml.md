---
title: 'Postupy: Ovládací prvek Namespace předpony (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 7e5a05d2fa93e61338f450d0a4d890fa94c04fd2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839010"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="fcab5-102">Postupy: Ovládací prvek Namespace předpony (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fcab5-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="fcab5-103">Toto téma popisuje, jak můžete řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fcab5-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcab5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fcab5-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fcab5-105">Popis</span><span class="sxs-lookup"><span data-stu-id="fcab5-105">Description</span></span>  
 <span data-ttu-id="fcab5-106">V tomto příkladu deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="fcab5-106">This example declares two namespaces.</span></span> <span data-ttu-id="fcab5-107">Určuje, že `http://www.adventure-works.com` má předponu oboru názvů `aw`a že `www.fourthcoffee.com` obor názvů má předponu `fc`.</span><span class="sxs-lookup"><span data-stu-id="fcab5-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fcab5-108">Kód</span><span class="sxs-lookup"><span data-stu-id="fcab5-108">Code</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="fcab5-109">Komentáře</span><span class="sxs-lookup"><span data-stu-id="fcab5-109">Comments</span></span>  
 <span data-ttu-id="fcab5-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fcab5-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcab5-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcab5-111">See also</span></span>

- [<span data-ttu-id="fcab5-112">Práce s názvovými prostory XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcab5-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
