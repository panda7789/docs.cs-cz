---
title: Počet indexů překračuje počet rozměrů indexovaného pole.
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 01659205f271b089fe4e8aa87cf7a8c44e7a4000
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837977"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="23816-102">Počet indexů překračuje počet rozměrů indexovaného pole.</span><span class="sxs-lookup"><span data-stu-id="23816-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="23816-103">Počet indexů pro přístup k elementu pole musí být přesně stejné jako řád objektu array, to znamená, počet rozměrů deklarované pro něj.</span><span class="sxs-lookup"><span data-stu-id="23816-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="23816-104">**ID chyby:** BC30106</span><span class="sxs-lookup"><span data-stu-id="23816-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="23816-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="23816-105">To correct this error</span></span>  
  
-   <span data-ttu-id="23816-106">Dokud celkový počet dolních indexů rovná řád objektu array, odeberte z odkazu na pole dolních indexů.</span><span class="sxs-lookup"><span data-stu-id="23816-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="23816-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="23816-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="23816-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23816-108">See also</span></span>

- [<span data-ttu-id="23816-109">Pole</span><span class="sxs-lookup"><span data-stu-id="23816-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
