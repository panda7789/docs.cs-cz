---
title: Spravované třídy odvozené od třídy COM nelze volat s pozdní vazbou.
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: 401cb5d7194cbef616c87d59e5b1ed7f923fe6f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402119"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="1105a-102">Spravované třídy odvozené od třídy COM nelze volat s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="1105a-102">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="1105a-103">Pokusili jste se provést volání s pozdní vazbou na spravovanou třídu odvozenou od třídy COM; taková volání nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="1105a-103">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="1105a-104">Postup odstranění problému</span><span class="sxs-lookup"><span data-stu-id="1105a-104">To correct the problem</span></span>

<span data-ttu-id="1105a-105">Zajistěte, aby hovor byl včasnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="1105a-105">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="1105a-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="1105a-106">See also</span></span>

- [<span data-ttu-id="1105a-107">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="1105a-107">Error Types</span></span>](../programming-guide/language-features/error-types.md)
