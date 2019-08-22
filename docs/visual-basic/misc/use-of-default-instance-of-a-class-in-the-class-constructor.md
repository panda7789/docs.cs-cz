---
title: Použití výchozí instance třídy v konstruktoru třídy může vést k nekonečnému rekurzivnímu volání.
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664371"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="e8364-102">Použití výchozí instance třídy v konstruktoru třídy může vést k nekonečnému rekurzivnímu volání.</span><span class="sxs-lookup"><span data-stu-id="e8364-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="e8364-103">V konstruktoru třídy byla použita výchozí instance třídy.</span><span class="sxs-lookup"><span data-stu-id="e8364-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="e8364-104">To může vést k nekonečnému rekurzivnímu volání, známému také jako nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="e8364-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e8364-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e8364-105">To correct this error</span></span>  
  
- <span data-ttu-id="e8364-106">Odeberte výchozí instanci z konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="e8364-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8364-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8364-107">See also</span></span>

- [<span data-ttu-id="e8364-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e8364-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
