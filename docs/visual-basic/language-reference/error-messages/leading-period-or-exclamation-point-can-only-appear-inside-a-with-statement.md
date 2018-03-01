---
title: "Úvodní & č. 39;. & č. 39; nebo & č. 39;! & č. 39; může být použit pouze uvnitř a & č. 39; S & č. 39; příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="f9fe8-102">Úvodní & č. 39;. & č. 39; nebo & č. 39;! & č. 39; může být použit pouze uvnitř a & č. 39; S & č. 39; příkaz</span><span class="sxs-lookup"><span data-stu-id="f9fe8-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="f9fe8-103">Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="f9fe8-104">Přístup ke členu (`.`) a přístup ke členu slovníku (`!`) vyžadují zadání elementu, který obsahuje člen výrazu.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="f9fe8-105">Ta musí okamžitě zobrazí nalevo přistupujícího objektu nebo jako cíl `With` bloku obsahující přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="f9fe8-106">**ID chyby:** BC30157</span><span class="sxs-lookup"><span data-stu-id="f9fe8-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9fe8-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f9fe8-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="f9fe8-108">Ujistěte se, že `With` bloku je správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="f9fe8-109">Pokud není žádná `With` blokovat, přidejte výraz nalevo od přistupujícího objektu, která vyhodnotí definovaný element obsahující člena.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fe8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9fe8-110">See Also</span></span>  
 [<span data-ttu-id="f9fe8-111">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="f9fe8-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [<span data-ttu-id="f9fe8-112">S... End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="f9fe8-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
