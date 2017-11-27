---
title: "& č. 39; &lt;membername&gt;& č. 39; je nejednoznačný přes rozhraní zděděné & č. 39;&lt; interfacename1&gt;& č. 39; a & č. 39;&lt; interfacename2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords: BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf4a9c263fd197cdd5d5b4886ee18e2ff112488
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a><span data-ttu-id="2acd8-102">& č. 39; &lt;membername&gt;& č. 39; je nejednoznačný přes rozhraní zděděné & č. 39;&lt; interfacename1&gt;& č. 39; a & č. 39;&lt; interfacename2&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="2acd8-102">&#39;&lt;membername&gt;&#39; is ambiguous across the inherited interfaces &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="2acd8-103">Rozhraní dědí z více rozhraní dvě nebo více členů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="2acd8-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="2acd8-104">**ID chyby:** BC30685</span><span class="sxs-lookup"><span data-stu-id="2acd8-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2acd8-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2acd8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2acd8-106">Převést hodnotu na základní rozhraní, které chcete použít; například:</span><span class="sxs-lookup"><span data-stu-id="2acd8-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2acd8-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="2acd8-107">See Also</span></span>  
 [<span data-ttu-id="2acd8-108">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="2acd8-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
