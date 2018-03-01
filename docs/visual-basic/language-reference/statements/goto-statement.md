---
title: "GoTo – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a><span data-ttu-id="61511-102">GoTo – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-102">GoTo Statement</span></span>
<span data-ttu-id="61511-103">Větvích bezpodmínečně zadaný řádek v postupu.</span><span class="sxs-lookup"><span data-stu-id="61511-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61511-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61511-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="61511-105">Část</span><span class="sxs-lookup"><span data-stu-id="61511-105">Part</span></span>  
 `line`  
 <span data-ttu-id="61511-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="61511-106">Required.</span></span> <span data-ttu-id="61511-107">Žádné čáry popisku.</span><span class="sxs-lookup"><span data-stu-id="61511-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61511-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61511-108">Remarks</span></span>  
 <span data-ttu-id="61511-109">`GoTo` Příkaz můžete větev jenom na řádky v postupu, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="61511-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="61511-110">Na řádku musí mít čáry popisku, který `GoTo` mohou odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="61511-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="61511-111">Další informace najdete v tématu [postup: příkazy popisek](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="61511-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61511-112">`GoTo`příkazy můžete nastavit kód obtížné číst a spravovat.</span><span class="sxs-lookup"><span data-stu-id="61511-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="61511-113">Pokud je to možné, použijte místo toho řídicí struktury.</span><span class="sxs-lookup"><span data-stu-id="61511-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="61511-114">Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="61511-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="61511-115">Nelze použít `GoTo` příkaz na větev z mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo `Using`... `End Using` konstrukce na štítek uvnitř.</span><span class="sxs-lookup"><span data-stu-id="61511-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="61511-116">Vytvoření větve a zkuste to konstrukce</span><span class="sxs-lookup"><span data-stu-id="61511-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="61511-117">V rámci `Try`... `Catch`... `Finally` konstrukce, platí následující pravidla pro vytvoření větve s `GoTo` příkaz.</span><span class="sxs-lookup"><span data-stu-id="61511-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="61511-118">Blokování nebo oblast</span><span class="sxs-lookup"><span data-stu-id="61511-118">Block or region</span></span>|<span data-ttu-id="61511-119">Větvení v z mimo</span><span class="sxs-lookup"><span data-stu-id="61511-119">Branching in from outside</span></span>|<span data-ttu-id="61511-120">Větvení se z uvnitř</span><span class="sxs-lookup"><span data-stu-id="61511-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="61511-121">`Try`blok</span><span class="sxs-lookup"><span data-stu-id="61511-121">`Try` block</span></span>|<span data-ttu-id="61511-122">Pouze z `Catch` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="61511-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="61511-123">Pouze mimo celou konstrukce</span><span class="sxs-lookup"><span data-stu-id="61511-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="61511-124">`Catch`blok</span><span class="sxs-lookup"><span data-stu-id="61511-124">`Catch` block</span></span>|<span data-ttu-id="61511-125">Nikdy povoleno.</span><span class="sxs-lookup"><span data-stu-id="61511-125">Never allowed</span></span>|<span data-ttu-id="61511-126">Pouze mimo celou konstrukce, nebo na `Try` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="61511-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="61511-127">`Finally`blok</span><span class="sxs-lookup"><span data-stu-id="61511-127">`Finally` block</span></span>|<span data-ttu-id="61511-128">Nikdy povoleno.</span><span class="sxs-lookup"><span data-stu-id="61511-128">Never allowed</span></span>|<span data-ttu-id="61511-129">Nikdy povoleno.</span><span class="sxs-lookup"><span data-stu-id="61511-129">Never allowed</span></span>|  
  
 <span data-ttu-id="61511-130"><sup>1</sup> Pokud `Try`... `Catch`... `Finally` konstrukce vnořen v rámci druhého, `Catch` bloku můžete větev do `Try` bloku na svůj vlastní úroveň vnoření, ale ne do žádné jiné `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="61511-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="61511-131">Vnořený `Try`... `Catch`... `Finally` konstrukce musí být obsaženy v úplně `Try` nebo `Catch` konstrukce, ve kterém je vnořený blok.</span><span class="sxs-lookup"><span data-stu-id="61511-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="61511-132">Následující obrázek znázorňuje jednu `Try` konstrukce vnořené v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="61511-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="61511-133">Různé větví mezi bloky dvě struktur, se označují jako platný nebo neplatný.</span><span class="sxs-lookup"><span data-stu-id="61511-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="61511-134">![Grafický diagram větvení v konstrukce zkuste](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="61511-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="61511-135">Platné a neplatné větve v zkuste konstrukce</span><span class="sxs-lookup"><span data-stu-id="61511-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="61511-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="61511-136">Example</span></span>  
 <span data-ttu-id="61511-137">Následující příklad používá `GoTo` příkaz pro připojení popisků čáry v postupu.</span><span class="sxs-lookup"><span data-stu-id="61511-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="61511-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="61511-138">See Also</span></span>  
 [<span data-ttu-id="61511-139">Provést... Příkaz smyčky</span><span class="sxs-lookup"><span data-stu-id="61511-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="61511-140">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="61511-141">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="61511-142">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="61511-143">Vyberte... Case – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="61511-144">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="61511-145">Chvíli... End While – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="61511-146">S... End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="61511-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
