---
title: Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664410"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="0de35-102">Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.</span><span class="sxs-lookup"><span data-stu-id="0de35-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="0de35-103">Příkaz se pokusil o `Preserve` použití klíčového slova pro změnu rozměru pole, které není poslední dimenzí. `ReDim`</span><span class="sxs-lookup"><span data-stu-id="0de35-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="0de35-104">Při použití `Preserve`můžete změnit velikost jenom na poslední rozměr pole.</span><span class="sxs-lookup"><span data-stu-id="0de35-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="0de35-105">Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako pro existující pole.</span><span class="sxs-lookup"><span data-stu-id="0de35-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0de35-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0de35-106">To correct this error</span></span>  
  
- <span data-ttu-id="0de35-107">`Preserve` Odeberte klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0de35-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de35-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0de35-108">See also</span></span>

- [<span data-ttu-id="0de35-109">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0de35-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="0de35-110">Rozměry pole v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0de35-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="0de35-111">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="0de35-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="0de35-112">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="0de35-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
