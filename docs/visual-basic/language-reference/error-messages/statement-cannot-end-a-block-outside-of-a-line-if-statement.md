---
title: Příkaz nemůže ukončit blok mimo řádek s &#39;Pokud&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596681"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="c75b2-102">Příkaz nemůže ukončit blok mimo řádek s &#39;Pokud&#39; – příkaz</span><span class="sxs-lookup"><span data-stu-id="c75b2-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="c75b2-103">Jeden řádek `If` příkaz obsahuje několik příkazů oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jeden řádek `If`.</span><span class="sxs-lookup"><span data-stu-id="c75b2-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="c75b2-104">Jeden řádek `If` příkazy se nedoporučuje používat `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c75b2-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="c75b2-105">**ID chyby:** BC32005</span><span class="sxs-lookup"><span data-stu-id="c75b2-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c75b2-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c75b2-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c75b2-107">Přesunout jednom řádku `If` příkaz mimo řídicí blok, který obsahuje `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c75b2-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75b2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c75b2-108">See Also</span></span>  
 [<span data-ttu-id="c75b2-109">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="c75b2-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
