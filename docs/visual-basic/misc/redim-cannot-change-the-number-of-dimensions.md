---
title: Příkaz ReDim nemůže měnit počet rozměrů.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: fb60c93f988ca40305f13cca07f55a70bd779081
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664401"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="f69e7-102">Příkaz ReDim nemůže měnit počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="f69e7-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="f69e7-103">Operace se pokusí použít `ReDim` příkaz ke změně pořadí (počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="f69e7-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="f69e7-104">`ReDim`může změnit velikost jedné nebo více dimenzí pole, které je již formálně deklarované, ale nemůže změnit rozměr pole.</span><span class="sxs-lookup"><span data-stu-id="f69e7-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f69e7-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f69e7-105">To correct this error</span></span>  
  
- <span data-ttu-id="f69e7-106">Ujistěte se, že máte v úmyslu změnit pořadí pole, nikoli velikost jeho rozměrů, a pokud je to možné, `Dim` použijte k deklaraci nového pole s požadovaným pořadím.</span><span class="sxs-lookup"><span data-stu-id="f69e7-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69e7-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f69e7-107">See also</span></span>

- [<span data-ttu-id="f69e7-108">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f69e7-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f69e7-109">Rozměry pole v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f69e7-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="f69e7-110">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="f69e7-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="f69e7-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="f69e7-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
