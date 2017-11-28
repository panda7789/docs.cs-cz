---
title: "Operaci nelze provést, protože cílový adresář je pod zdrojový adresář"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 429d679157d25655ca73afef14ecd642f7cac37f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="028bc-102">Operaci nelze provést, protože cílový adresář je pod zdrojový adresář</span><span class="sxs-lookup"><span data-stu-id="028bc-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="028bc-103">Cyklická operace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="028bc-103">A cyclic operation has failed.</span></span> <span data-ttu-id="028bc-104">Cyklická operace cyklus a proto nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="028bc-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="028bc-105">Například objekt A pokusit dědění z objektu B, který zase dědí z objektu A.</span><span class="sxs-lookup"><span data-stu-id="028bc-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="028bc-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="028bc-106">To correct this error</span></span>  
  
-   <span data-ttu-id="028bc-107">Když je zděděný, ujistěte se, že neexistují žádné cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="028bc-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028bc-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="028bc-108">See Also</span></span>  
 [<span data-ttu-id="028bc-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="028bc-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="028bc-110">Základní informace o ladění: zarážky</span><span class="sxs-lookup"><span data-stu-id="028bc-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
