---
title: Operaci se nepovedlo dokončit, protože cílový adresář se nachází ve zdrojovém adresáři.
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 46ec7ae452d4f8259d0f8ca3a896d1b29151ed61
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376739"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="7f2e5-102">Operaci se nepovedlo dokončit, protože cílový adresář se nachází ve zdrojovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="7f2e5-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="7f2e5-103">Cyklická operace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="7f2e5-103">A cyclic operation has failed.</span></span> <span data-ttu-id="7f2e5-104">Cyklická cyklus operací, a proto nemůže být dokončena.</span><span class="sxs-lookup"><span data-stu-id="7f2e5-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="7f2e5-105">Například objekt A se může pokusit o dědění z objektu B, který zase dědí z Object A.</span><span class="sxs-lookup"><span data-stu-id="7f2e5-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f2e5-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7f2e5-106">To correct this error</span></span>  
  
- <span data-ttu-id="7f2e5-107">Při dědění se ujistěte, že neexistují žádné cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="7f2e5-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2e5-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f2e5-108">See also</span></span>

- [<span data-ttu-id="7f2e5-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="7f2e5-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="7f2e5-110">Použití zarážek v ladicím programu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7f2e5-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
