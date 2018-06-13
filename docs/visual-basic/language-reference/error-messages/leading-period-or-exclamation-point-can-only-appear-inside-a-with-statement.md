---
title: Úvodní &#39;. &#39; nebo &#39;! &#39; může vyskytovat pouze uvnitř &#39;s&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 7802b8e0aaf3dff83d5bfbe11f0b8bb1b5bb46cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589444"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="94374-102">Úvodní &#39;. &#39; nebo &#39;! &#39; může vyskytovat pouze uvnitř &#39;s&#39; – příkaz</span><span class="sxs-lookup"><span data-stu-id="94374-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="94374-103">Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně.</span><span class="sxs-lookup"><span data-stu-id="94374-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="94374-104">Přístup ke členu (`.`) a přístup ke členu slovníku (`!`) vyžadují zadání elementu, který obsahuje člen výrazu.</span><span class="sxs-lookup"><span data-stu-id="94374-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="94374-105">Ta musí okamžitě zobrazí nalevo přistupujícího objektu nebo jako cíl `With` bloku obsahující přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="94374-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="94374-106">**ID chyby:** BC30157</span><span class="sxs-lookup"><span data-stu-id="94374-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="94374-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="94374-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="94374-108">Ujistěte se, že `With` bloku je správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="94374-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="94374-109">Pokud není žádná `With` blokovat, přidejte výraz nalevo od přistupujícího objektu, která vyhodnotí definovaný element obsahující člena.</span><span class="sxs-lookup"><span data-stu-id="94374-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94374-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="94374-110">See Also</span></span>  
 [<span data-ttu-id="94374-111">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="94374-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [<span data-ttu-id="94374-112">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="94374-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
