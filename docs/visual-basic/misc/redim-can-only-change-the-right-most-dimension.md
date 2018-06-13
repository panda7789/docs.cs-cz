---
title: '&#39;ReDim&#39; lze změnit pouze dimenze nejvíce vpravo'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: efb98df13a7e3e378347b30b6fc00b90030ec194
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641180"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="65211-102">&#39;ReDim&#39; lze změnit pouze dimenze nejvíce vpravo</span><span class="sxs-lookup"><span data-stu-id="65211-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="65211-103">A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, které není poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="65211-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="65211-104">Při použití `Preserve`, můžete změnit velikost pouze poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="65211-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="65211-105">Pro všechny další dimenze musíte zadat stejnou velikost jako existující pole.</span><span class="sxs-lookup"><span data-stu-id="65211-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65211-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="65211-106">To correct this error</span></span>  
  
-   <span data-ttu-id="65211-107">Odeberte `Preserve` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="65211-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65211-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="65211-108">See Also</span></span>  
 [<span data-ttu-id="65211-109">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65211-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="65211-110">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65211-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="65211-111">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="65211-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="65211-112">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="65211-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="65211-113">Zachovat – odstranit</span><span class="sxs-lookup"><span data-stu-id="65211-113">Preserve - delete</span></span>](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
