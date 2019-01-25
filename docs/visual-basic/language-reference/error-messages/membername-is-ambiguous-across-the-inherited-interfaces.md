---
title: '&#39;&lt;MemberName&gt; &#39; je dvojznačný ve zděděných rozhraních &#39; &lt;interfacename1&gt; &#39; a &#39; &lt;interfacename2&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: e6d6a82331185060d6f08c3375dc5a628b65df1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506292"
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a><span data-ttu-id="e605b-102">&#39;&lt;MemberName&gt; &#39; je dvojznačný ve zděděných rozhraních &#39; &lt;interfacename1&gt; &#39; a &#39; &lt;interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e605b-102">&#39;&lt;membername&gt;&#39; is ambiguous across the inherited interfaces &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="e605b-103">Dva nebo více členů se stejným názvem rozhraní dědí z více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e605b-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="e605b-104">**ID chyby:** BC30685</span><span class="sxs-lookup"><span data-stu-id="e605b-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e605b-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e605b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e605b-106">Přetypujte hodnotu na základní rozhraní, které chcete použít; Příklad:</span><span class="sxs-lookup"><span data-stu-id="e605b-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e605b-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e605b-107">See also</span></span>
- [<span data-ttu-id="e605b-108">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e605b-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
