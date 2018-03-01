---
title: "& č. 39; ReDim & č. 39; nelze změnit počet dimenzí"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cf3713c72bd07803935065780e894c130911a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="aaaf8-102">& č. 39; ReDim & č. 39; nelze změnit počet dimenzí</span><span class="sxs-lookup"><span data-stu-id="aaaf8-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="aaaf8-103">Operace se pokusí použít `ReDim` příkaz Chcete-li změnit pořadí pole (počet dimenzí).</span><span class="sxs-lookup"><span data-stu-id="aaaf8-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="aaaf8-104">`ReDim`můžete změnit velikost jeden nebo více rozměry pole, které již byla dříve deklarována, ale nedá se změnit pořadí tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aaaf8-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aaaf8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="aaaf8-106">Ujistěte se, kterou chcete změnit pořadí tohoto pole a není velikosti jeho dimenzí a pokud je to možné, používejte `Dim` deklarovat nové pole se požadované pořadí.</span><span class="sxs-lookup"><span data-stu-id="aaaf8-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaaf8-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="aaaf8-107">See Also</span></span>  
 [<span data-ttu-id="aaaf8-108">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aaaf8-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="aaaf8-109">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aaaf8-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="aaaf8-110">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="aaaf8-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="aaaf8-111">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="aaaf8-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
