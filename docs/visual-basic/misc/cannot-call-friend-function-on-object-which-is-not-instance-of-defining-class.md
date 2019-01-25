---
title: Nelze volat spřátelenou funkci pro objekt, který není instancí definující třídy
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a107b2a11f6f8324c3029e83c5eca64c2ee32ebf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742829"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="680fd-102">Nelze volat spřátelenou funkci pro objekt, který není instancí definující třídy</span><span class="sxs-lookup"><span data-stu-id="680fd-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="680fd-103">Buď se snažíte volat `Friend` postup třídy, nebo jste se pokusili získat přístup `Friend` vlastnosti nebo metody procesy nebo mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="680fd-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="680fd-104">A `Friend` procedury lze volat z modulu vně třídy, ale je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="680fd-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="680fd-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="680fd-105">To correct this error</span></span>  
  
-   <span data-ttu-id="680fd-106">Ujistěte se, že jsou volání nebo přístupu k postupu z modulu, který je součástí projektu, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="680fd-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680fd-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="680fd-107">See also</span></span>
- [<span data-ttu-id="680fd-108">Friend</span><span class="sxs-lookup"><span data-stu-id="680fd-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
