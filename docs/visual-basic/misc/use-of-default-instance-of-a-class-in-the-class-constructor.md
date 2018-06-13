---
title: Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cf5d3e16c43920a90b69c815f91601c6d33c845d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638368"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="d9b2d-102">Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání</span><span class="sxs-lookup"><span data-stu-id="d9b2d-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="d9b2d-103">Výchozí instance třídy se používá v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="d9b2d-104">To může vést k nekonečné rekurzivní volání, také známé jako nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9b2d-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d9b2d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d9b2d-106">Výchozí instance odeberte z konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b2d-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9b2d-107">See Also</span></span>  
 [<span data-ttu-id="d9b2d-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d9b2d-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
