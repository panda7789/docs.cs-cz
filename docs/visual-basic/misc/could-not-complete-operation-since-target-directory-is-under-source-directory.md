---
title: Operaci nelze provést, protože cílový adresář se nachází ve zdrojovém adresáři
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: f53ad664b341d4db803dee1f0f008c3918d13d93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970115"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="d21cd-102">Operaci nelze provést, protože cílový adresář se nachází ve zdrojovém adresáři</span><span class="sxs-lookup"><span data-stu-id="d21cd-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="d21cd-103">Cyklické operace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="d21cd-103">A cyclic operation has failed.</span></span> <span data-ttu-id="d21cd-104">Cyklické operace cyklu a proto nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="d21cd-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="d21cd-105">Například může pokusit objekt A dědí z objektu B, který zase dědí z objektu A.</span><span class="sxs-lookup"><span data-stu-id="d21cd-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d21cd-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d21cd-106">To correct this error</span></span>  
  
- <span data-ttu-id="d21cd-107">Při dědění, ujistěte se, že neexistují žádné cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="d21cd-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21cd-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d21cd-108">See also</span></span>

- [<span data-ttu-id="d21cd-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="d21cd-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="d21cd-110">Používání zarážek v ladicím programu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d21cd-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
