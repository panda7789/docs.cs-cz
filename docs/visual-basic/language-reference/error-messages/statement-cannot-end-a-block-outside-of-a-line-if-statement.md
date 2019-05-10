---
title: Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0e645ccf17d0aba702a576791622aa4e9b3dd5e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593257"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="e4326-102">Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.</span><span class="sxs-lookup"><span data-stu-id="e4326-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="e4326-103">Jeden řádek `If` příkaz obsahuje několik příkazy oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jedním řádkem `If`.</span><span class="sxs-lookup"><span data-stu-id="e4326-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="e4326-104">Jednořádkový `If` příkazy nepoužívejte `End If` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e4326-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="e4326-105">**ID chyby:** BC32005</span><span class="sxs-lookup"><span data-stu-id="e4326-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e4326-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e4326-106">To correct this error</span></span>  
  
- <span data-ttu-id="e4326-107">Přesunout jedním řádkem `If` příkazu mimo blok ovládací prvek, který obsahuje `End If` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e4326-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4326-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4326-108">See also</span></span>

- [<span data-ttu-id="e4326-109">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="e4326-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
