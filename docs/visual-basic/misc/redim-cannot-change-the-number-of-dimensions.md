---
title: '&#39;ReDim&#39; nelze změnit počet dimenzí'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: bfd4096141833b85a2126340ef549e1e1d1f8e3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640378"
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="6dba5-102">&#39;ReDim&#39; nelze změnit počet dimenzí</span><span class="sxs-lookup"><span data-stu-id="6dba5-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="6dba5-103">Operace se pokusí použít `ReDim` příkaz Chcete-li změnit pořadí pole (počet dimenzí).</span><span class="sxs-lookup"><span data-stu-id="6dba5-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="6dba5-104">`ReDim` můžete změnit velikost jeden nebo více rozměry pole, které již byla dříve deklarována, ale nedá se změnit pořadí tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="6dba5-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6dba5-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6dba5-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6dba5-106">Ujistěte se, kterou chcete změnit pořadí tohoto pole a není velikosti jeho dimenzí a pokud je to možné, používejte `Dim` deklarovat nové pole se požadované pořadí.</span><span class="sxs-lookup"><span data-stu-id="6dba5-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dba5-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="6dba5-107">See Also</span></span>  
 [<span data-ttu-id="6dba5-108">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dba5-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="6dba5-109">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dba5-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="6dba5-110">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="6dba5-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="6dba5-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="6dba5-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
