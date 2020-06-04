---
title: Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 8e42e0df7b97fb96f468ce37dd4cfc52fad8c596
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358293"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="2a42d-102">Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.</span><span class="sxs-lookup"><span data-stu-id="2a42d-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="2a42d-103">`ReDim`Příkaz se pokusil o použití `Preserve` klíčového slova pro změnu rozměru pole, které není poslední dimenzí.</span><span class="sxs-lookup"><span data-stu-id="2a42d-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="2a42d-104">Při použití `Preserve` můžete změnit velikost jenom na poslední rozměr pole.</span><span class="sxs-lookup"><span data-stu-id="2a42d-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="2a42d-105">Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako pro existující pole.</span><span class="sxs-lookup"><span data-stu-id="2a42d-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2a42d-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2a42d-106">To correct this error</span></span>  
  
- <span data-ttu-id="2a42d-107">Odeberte `Preserve` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2a42d-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a42d-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a42d-108">See also</span></span>

- [<span data-ttu-id="2a42d-109">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a42d-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="2a42d-110">Rozměry pole v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a42d-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="2a42d-111">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="2a42d-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="2a42d-112">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="2a42d-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
