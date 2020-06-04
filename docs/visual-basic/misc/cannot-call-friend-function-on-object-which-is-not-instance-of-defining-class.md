---
title: Nejde volat funkci Friend u objektu, který není instancí definující třídy.
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c18c04470c4c49113e8195b92185326c5c4197c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400845"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="8f6a6-102">Nejde volat funkci Friend u objektu, který není instancí definující třídy.</span><span class="sxs-lookup"><span data-stu-id="8f6a6-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="8f6a6-103">Buď jste se pokusili zavolat `Friend` proceduru třídy, nebo jste se pokusili získat přístup k `Friend` vlastnosti nebo metodě buď mezi procesy, nebo mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="8f6a6-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="8f6a6-104">`Friend`Procedura se může volat z modulu mimo třídu, ale je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="8f6a6-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8f6a6-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8f6a6-105">To correct this error</span></span>  
  
- <span data-ttu-id="8f6a6-106">Ujistěte se, že zavoláte nebo přistupujete k proceduře z modulu, který je součástí projektu, ve kterém je třída definována.</span><span class="sxs-lookup"><span data-stu-id="8f6a6-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f6a6-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f6a6-107">See also</span></span>

- [<span data-ttu-id="8f6a6-108">Friend</span><span class="sxs-lookup"><span data-stu-id="8f6a6-108">Friend</span></span>](../language-reference/modifiers/friend.md)
