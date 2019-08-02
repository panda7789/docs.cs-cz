---
title: 'Postupy: Předpony oboru názvů ovládacího prvku (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 2b89b49aa76df526c08143cad49685386ffd5e7c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709820"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="7147c-102">Postupy: Předpony oboru názvů ovládacího prvku (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7147c-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="7147c-103">Toto téma popisuje, jak lze řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7147c-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7147c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7147c-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7147c-105">Popis</span><span class="sxs-lookup"><span data-stu-id="7147c-105">Description</span></span>  
 <span data-ttu-id="7147c-106">Tento příklad deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7147c-106">This example declares two namespaces.</span></span> <span data-ttu-id="7147c-107">Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw`a že `www.fourthcoffee.com` má obor názvů předponu `fc`.</span><span class="sxs-lookup"><span data-stu-id="7147c-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7147c-108">Kód</span><span class="sxs-lookup"><span data-stu-id="7147c-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="7147c-109">Komentáře</span><span class="sxs-lookup"><span data-stu-id="7147c-109">Comments</span></span>  
 <span data-ttu-id="7147c-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7147c-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7147c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7147c-111">See also</span></span>

- [<span data-ttu-id="7147c-112">Přehled oborů názvů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7147c-112">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
