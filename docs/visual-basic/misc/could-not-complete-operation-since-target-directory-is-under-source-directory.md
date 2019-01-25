---
title: Operaci nelze provést, protože cílový adresář se nachází ve zdrojovém adresáři
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 253e7ff1d457827a2e1cb9f64eae4bfa971a3798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645870"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="608e4-102">Operaci nelze provést, protože cílový adresář se nachází ve zdrojovém adresáři</span><span class="sxs-lookup"><span data-stu-id="608e4-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="608e4-103">Cyklické operace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="608e4-103">A cyclic operation has failed.</span></span> <span data-ttu-id="608e4-104">Cyklické operace cyklu a proto nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="608e4-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="608e4-105">Například může pokusit objekt A dědí z objektu B, který zase dědí z objektu A.</span><span class="sxs-lookup"><span data-stu-id="608e4-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="608e4-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="608e4-106">To correct this error</span></span>  
  
-   <span data-ttu-id="608e4-107">Při dědění, ujistěte se, že neexistují žádné cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="608e4-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608e4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="608e4-108">See also</span></span>
- [<span data-ttu-id="608e4-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="608e4-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="608e4-110">Základy ladění: Zarážky</span><span class="sxs-lookup"><span data-stu-id="608e4-110">Debugging Basics: Breakpoints</span></span>](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
