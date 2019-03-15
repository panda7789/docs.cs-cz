---
title: "'ReDim' lze měnit pouze rozměr nejvíce vpravo"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 86d639e70e85b19a91f89fa4e0cab330af07dccf
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58028821"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="ab131-102">'ReDim' lze měnit pouze rozměr nejvíce vpravo</span><span class="sxs-lookup"><span data-stu-id="ab131-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="ab131-103">A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, která není poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="ab131-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="ab131-104">Při použití `Preserve`, změníte velikost jenom poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="ab131-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="ab131-105">Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako u existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="ab131-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab131-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ab131-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ab131-107">Odeberte `Preserve` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ab131-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab131-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab131-108">See also</span></span>

- [<span data-ttu-id="ab131-109">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab131-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="ab131-110">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab131-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="ab131-111">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="ab131-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="ab131-112">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="ab131-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
