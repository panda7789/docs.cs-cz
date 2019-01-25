---
title: Úvodní &#39;. &#39; nebo &#39;! &#39; může být použito pouze uvnitř &#39;s&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e64318d4ececbd887f55a1a202cc2d58c90c8fc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625949"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="f06ea-102">Úvodní &#39;. &#39; nebo &#39;! &#39; může být použito pouze uvnitř &#39;s&#39; – příkaz</span><span class="sxs-lookup"><span data-stu-id="f06ea-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="f06ea-103">Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně.</span><span class="sxs-lookup"><span data-stu-id="f06ea-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="f06ea-104">Přístup ke členu (`.`) a přístup ke členu slovník (`!`) vyžadují výraz určující prvek, který obsahuje člena.</span><span class="sxs-lookup"><span data-stu-id="f06ea-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="f06ea-105">Toto musí být uvedena ihned na levé straně přístupového objektu nebo jako cíl `With` bloku, který obsahuje přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="f06ea-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="f06ea-106">**ID chyby:** BC30157</span><span class="sxs-lookup"><span data-stu-id="f06ea-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f06ea-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f06ea-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="f06ea-108">Ujistěte se, `With` blok je správně formátovaný.</span><span class="sxs-lookup"><span data-stu-id="f06ea-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="f06ea-109">Pokud není žádný `With` blokovat, zadejte nějaký výraz nalevo od přístupový objekt, který se vyhodnotí na definovaný element obsahující tento člen.</span><span class="sxs-lookup"><span data-stu-id="f06ea-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06ea-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f06ea-110">See also</span></span>
- [<span data-ttu-id="f06ea-111">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="f06ea-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="f06ea-112">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="f06ea-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
