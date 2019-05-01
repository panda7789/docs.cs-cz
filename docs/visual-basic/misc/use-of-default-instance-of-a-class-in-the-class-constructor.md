---
title: Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 14c498bf3067415f8de2afaeaaa57cf3f28ae857
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022451"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="384ae-102">Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání</span><span class="sxs-lookup"><span data-stu-id="384ae-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="384ae-103">Byla použita výchozí instance třídy v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="384ae-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="384ae-104">To může vést k nekonečné rekurzivní volání, označované také jako nekonečná smyčka.</span><span class="sxs-lookup"><span data-stu-id="384ae-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="384ae-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="384ae-105">To correct this error</span></span>  
  
- <span data-ttu-id="384ae-106">Odebrání výchozí instanci konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="384ae-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384ae-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="384ae-107">See also</span></span>

- [<span data-ttu-id="384ae-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384ae-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
