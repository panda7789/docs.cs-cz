---
title: Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400315"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="e0655-102">Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.</span><span class="sxs-lookup"><span data-stu-id="e0655-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="e0655-103">Jednořádkový `If` příkaz obsahuje několik příkazů, které jsou odděleny dvojtečkami (:), jeden z nich je `End` příkaz pro řídicí blok mimo jeden řádek `If` .</span><span class="sxs-lookup"><span data-stu-id="e0655-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="e0655-104">Jednořádkové `If` příkazy nepoužívají `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e0655-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="e0655-105">**ID chyby:** BC32005</span><span class="sxs-lookup"><span data-stu-id="e0655-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0655-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e0655-106">To correct this error</span></span>  
  
- <span data-ttu-id="e0655-107">Přesune příkaz na jeden řádek `If` mimo řídicí blok, který obsahuje `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e0655-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0655-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0655-108">See also</span></span>

- [<span data-ttu-id="e0655-109">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="e0655-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
