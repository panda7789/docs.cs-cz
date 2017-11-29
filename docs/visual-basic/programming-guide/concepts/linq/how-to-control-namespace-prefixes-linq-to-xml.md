---
title: "Postupy: řízení Namespace předpony (Visual Basic) (technologie LINQ to XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a48feeb25cc8d28d57edc7421f73b2829f8c19ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="6c25e-102">Postupy: řízení Namespace předpony (Visual Basic) (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6c25e-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="6c25e-103">Toto téma popisuje, jak můžete řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6c25e-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c25e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c25e-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6c25e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="6c25e-105">Description</span></span>  
 <span data-ttu-id="6c25e-106">Tento příklad deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="6c25e-106">This example declares two namespaces.</span></span> <span data-ttu-id="6c25e-107">Určuje, že `http://www.adventure-works.com` obor názvů se předponou `aw`a že `www.fourthcoffee.com` má předponu oboru názvů `fc`.</span><span class="sxs-lookup"><span data-stu-id="6c25e-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6c25e-108">Kód</span><span class="sxs-lookup"><span data-stu-id="6c25e-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6c25e-109">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6c25e-109">Comments</span></span>  
 <span data-ttu-id="6c25e-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6c25e-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c25e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c25e-111">See Also</span></span>  
 [<span data-ttu-id="6c25e-112">Práce s obory názvů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c25e-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
