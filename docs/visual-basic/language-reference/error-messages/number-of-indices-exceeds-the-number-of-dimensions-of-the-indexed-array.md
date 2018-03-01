---
title: "Počet indexů překračuje počet rozměrů indexovaného pole."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8fdf031734d441daca2073925f6d45d6ba9f1f52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="5a0fb-102">Počet indexů překračuje počet rozměrů indexovaného pole.</span><span class="sxs-lookup"><span data-stu-id="5a0fb-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="5a0fb-103">Počet indexů použila k přístupu k elementu pole musí být přesně stejný jako pořadí pole, který je počet dimenzí deklarovaný pro něj.</span><span class="sxs-lookup"><span data-stu-id="5a0fb-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="5a0fb-104">**ID chyby:** BC30106</span><span class="sxs-lookup"><span data-stu-id="5a0fb-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5a0fb-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5a0fb-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5a0fb-106">Odeberte dolní indexy z odkaz na pole, dokud celkový počet dolní indexy rovná pořadí pole.</span><span class="sxs-lookup"><span data-stu-id="5a0fb-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="5a0fb-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5a0fb-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5a0fb-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a0fb-108">See Also</span></span>  
 [<span data-ttu-id="5a0fb-109">Pole</span><span class="sxs-lookup"><span data-stu-id="5a0fb-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
