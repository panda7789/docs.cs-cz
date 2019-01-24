---
title: "'ReDim' nelze změnit počet rozměrů"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 80546b427afdafaf6e9fcea493d58cf1019e79e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638454"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="2d10b-102">'ReDim' nelze změnit počet rozměrů</span><span class="sxs-lookup"><span data-stu-id="2d10b-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="2d10b-103">Operace se pokusí použít `ReDim` prohlášení, chcete-li změnit pořadí (počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="2d10b-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="2d10b-104">`ReDim` můžete změnit velikost nejmíň jeden rozměry pole, které již byl dříve deklarován, ale nedá se změnit pořadí tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="2d10b-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d10b-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2d10b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2d10b-106">Ujistěte se, že máte v úmyslu změnit pole pořadí a ne velikosti jeho rozměry a pokud je to možné, použijte `Dim` deklarovat nové pole s požadovaný počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="2d10b-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d10b-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d10b-107">See also</span></span>
- [<span data-ttu-id="2d10b-108">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d10b-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="2d10b-109">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d10b-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="2d10b-110">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="2d10b-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="2d10b-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="2d10b-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
