---
title: '&#39;ReDim&#39; lze měnit pouze rozměr nejvíce vpravo'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 94e0fe81f7e750a67943b68f2db700e3a7831da1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482714"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="91401-102">&#39;ReDim&#39; lze měnit pouze rozměr nejvíce vpravo</span><span class="sxs-lookup"><span data-stu-id="91401-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="91401-103">A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, která není poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="91401-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="91401-104">Při použití `Preserve`, změníte velikost jenom poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="91401-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="91401-105">Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako u existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="91401-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="91401-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="91401-106">To correct this error</span></span>  
  
-   <span data-ttu-id="91401-107">Odeberte `Preserve` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="91401-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91401-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="91401-108">See Also</span></span>  
 [<span data-ttu-id="91401-109">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91401-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="91401-110">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91401-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="91401-111">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="91401-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="91401-112">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="91401-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="91401-113">Zachovat – odstranit</span><span class="sxs-lookup"><span data-stu-id="91401-113">Preserve - delete</span></span>](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
