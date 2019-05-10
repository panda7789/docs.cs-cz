---
title: Počet indexů překračuje počet rozměrů indexovaného pole.
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665694"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="2abf4-102">Počet indexů překračuje počet rozměrů indexovaného pole.</span><span class="sxs-lookup"><span data-stu-id="2abf4-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="2abf4-103">Počet indexů pro přístup k elementu pole musí být přesně stejné jako řád objektu array, to znamená, počet rozměrů deklarované pro něj.</span><span class="sxs-lookup"><span data-stu-id="2abf4-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="2abf4-104">**ID chyby:** BC30106</span><span class="sxs-lookup"><span data-stu-id="2abf4-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2abf4-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2abf4-105">To correct this error</span></span>  
  
- <span data-ttu-id="2abf4-106">Dokud celkový počet dolních indexů rovná řád objektu array, odeberte z odkazu na pole dolních indexů.</span><span class="sxs-lookup"><span data-stu-id="2abf4-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="2abf4-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2abf4-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2abf4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2abf4-108">See also</span></span>

- [<span data-ttu-id="2abf4-109">Pole</span><span class="sxs-lookup"><span data-stu-id="2abf4-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
