---
title: "'ReDim' nelze změnit počet rozměrů"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 1e9695bbc7f104aa741de232f1f6d3c76df2cebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591753"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="d25ed-102">'ReDim' nelze změnit počet rozměrů</span><span class="sxs-lookup"><span data-stu-id="d25ed-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="d25ed-103">Operace se pokusí použít `ReDim` prohlášení, chcete-li změnit pořadí (počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="d25ed-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="d25ed-104">`ReDim` můžete změnit velikost nejmíň jeden rozměry pole, které již byl dříve deklarován, ale nedá se změnit pořadí tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="d25ed-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d25ed-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d25ed-105">To correct this error</span></span>  
  
- <span data-ttu-id="d25ed-106">Ujistěte se, že máte v úmyslu změnit pole pořadí a ne velikosti jeho rozměry a pokud je to možné, použijte `Dim` deklarovat nové pole s požadovaný počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="d25ed-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25ed-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d25ed-107">See also</span></span>

- [<span data-ttu-id="d25ed-108">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d25ed-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d25ed-109">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d25ed-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="d25ed-110">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="d25ed-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="d25ed-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="d25ed-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
