---
title: Název '<membername>' je dvojznačný ve zděděných rozhraních '<interfacename1>' a '<interfacename2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: f242db9e02a1983e731dce280be0e8f8a8b12712
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397269"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="47a68-102">Název '\<membername>' je dvojznačný ve zděděných rozhraních '\<interfacename1>' a '\<interfacename2>'.</span><span class="sxs-lookup"><span data-stu-id="47a68-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>
<span data-ttu-id="47a68-103">Rozhraní dědí dva nebo více členů se stejným názvem z více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47a68-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="47a68-104">**ID chyby:** BC30685</span><span class="sxs-lookup"><span data-stu-id="47a68-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47a68-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="47a68-105">To correct this error</span></span>  
  
- <span data-ttu-id="47a68-106">Přetypování hodnoty na základní rozhraní, které chcete použít; například:</span><span class="sxs-lookup"><span data-stu-id="47a68-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```vb  
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
  
## <a name="see-also"></a><span data-ttu-id="47a68-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="47a68-107">See also</span></span>

- [<span data-ttu-id="47a68-108">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="47a68-108">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
