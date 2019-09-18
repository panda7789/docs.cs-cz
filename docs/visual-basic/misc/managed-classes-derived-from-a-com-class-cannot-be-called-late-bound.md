---
title: Spravované třídy odvozené od třídy COM nelze volat s pozdní vazbou.
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: c18f2b6e1751d39ceb81c190f70ee161ca716bc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054188"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="63a3c-102">Spravované třídy odvozené od třídy COM nelze volat s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="63a3c-102">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="63a3c-103">Pokusili jste se provést volání s pozdní vazbou na spravovanou třídu odvozenou od třídy COM; taková volání nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="63a3c-103">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="63a3c-104">Postup odstranění problému</span><span class="sxs-lookup"><span data-stu-id="63a3c-104">To correct the problem</span></span>

<span data-ttu-id="63a3c-105">Zajistěte, aby hovor byl včasnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="63a3c-105">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="63a3c-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63a3c-106">See also</span></span>

- [<span data-ttu-id="63a3c-107">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="63a3c-107">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
