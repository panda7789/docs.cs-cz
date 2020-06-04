---
title: Úvodní operátor '.' nebo '!' může být použit pouze uvnitř příkazu 'With'.
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397321"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="8d5d6-102">Úvodní operátor '.' nebo '!' může být použit pouze uvnitř příkazu 'With'.</span><span class="sxs-lookup"><span data-stu-id="8d5d6-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="8d5d6-103">Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku, nastávají bez výrazu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="8d5d6-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="8d5d6-104">Přístup ke členu ( `.` ) a přístup ke členu slovníku ( `!` ) vyžadují výraz určující prvek, který obsahuje člena.</span><span class="sxs-lookup"><span data-stu-id="8d5d6-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="8d5d6-105">Ta se musí objevit hned nalevo od přístupového objektu nebo jako cíl `With` bloku obsahujícího přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="8d5d6-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="8d5d6-106">**ID chyby:** BC30157</span><span class="sxs-lookup"><span data-stu-id="8d5d6-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d5d6-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8d5d6-107">To correct this error</span></span>  
  
1. <span data-ttu-id="8d5d6-108">Zajistěte, aby byl `With` blok správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="8d5d6-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="8d5d6-109">Pokud není žádný `With` blok, přidejte výraz nalevo od přístupového objektu, který se vyhodnotí na definovaný element obsahující člena.</span><span class="sxs-lookup"><span data-stu-id="8d5d6-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5d6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d5d6-110">See also</span></span>

- [<span data-ttu-id="8d5d6-111">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="8d5d6-111">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="8d5d6-112">With...End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="8d5d6-112">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
