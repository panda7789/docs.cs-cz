---
title: Název '<membername>' je dvojznačný ve zděděných rozhraních '<interfacename1>' a '<interfacename2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 4415608bcfca63b43b3d9ebf17ce622ccd418775
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921001"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="f32a4-102">"\<membername >' je dvojznačný ve zděděných rozhraních\<interfacename1 >' a '\<interfacename2 >"</span><span class="sxs-lookup"><span data-stu-id="f32a4-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>
<span data-ttu-id="f32a4-103">Dva nebo více členů se stejným názvem rozhraní dědí z více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f32a4-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="f32a4-104">**ID chyby:** BC30685</span><span class="sxs-lookup"><span data-stu-id="f32a4-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f32a4-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f32a4-105">To correct this error</span></span>  
  
- <span data-ttu-id="f32a4-106">Přetypujte hodnotu na základní rozhraní, které chcete použít; Příklad:</span><span class="sxs-lookup"><span data-stu-id="f32a4-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f32a4-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f32a4-107">See also</span></span>

- [<span data-ttu-id="f32a4-108">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f32a4-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
