---
title: Operaci nelze provést, protože cílový adresář se nachází ve zdrojovém adresáři
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: b821034731514362a3725c390e02542b536f0a59
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542216"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="d0ed7-102">Operaci nelze provést, protože cílový adresář se nachází ve zdrojovém adresáři</span><span class="sxs-lookup"><span data-stu-id="d0ed7-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="d0ed7-103">Cyklické operace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="d0ed7-103">A cyclic operation has failed.</span></span> <span data-ttu-id="d0ed7-104">Cyklické operace cyklu a proto nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="d0ed7-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="d0ed7-105">Například může pokusit objekt A dědí z objektu B, který zase dědí z objektu A.</span><span class="sxs-lookup"><span data-stu-id="d0ed7-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0ed7-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d0ed7-106">To correct this error</span></span>  
  
-   <span data-ttu-id="d0ed7-107">Při dědění, ujistěte se, že neexistují žádné cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="d0ed7-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ed7-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0ed7-108">See Also</span></span>  
 [<span data-ttu-id="d0ed7-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="d0ed7-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="d0ed7-110">Základní informace o ladění: zarážky</span><span class="sxs-lookup"><span data-stu-id="d0ed7-110">Debugging Basics: Breakpoints</span></span>](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
