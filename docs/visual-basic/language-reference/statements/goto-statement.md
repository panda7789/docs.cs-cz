---
title: GoTo – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: adb7668b6a818b2042a38f9458685a6f93085dc8
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332984"
---
# <a name="goto-statement"></a><span data-ttu-id="4fa76-102">GoTo – příkaz</span><span class="sxs-lookup"><span data-stu-id="4fa76-102">GoTo Statement</span></span>
<span data-ttu-id="4fa76-103">Rozvětví se nepodmíněně na určený řádek v proceduře.</span><span class="sxs-lookup"><span data-stu-id="4fa76-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fa76-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="4fa76-105">Část</span><span class="sxs-lookup"><span data-stu-id="4fa76-105">Part</span></span>  
 `line`  
 <span data-ttu-id="4fa76-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4fa76-106">Required.</span></span> <span data-ttu-id="4fa76-107">Žádné čáry popisku.</span><span class="sxs-lookup"><span data-stu-id="4fa76-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fa76-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fa76-108">Remarks</span></span>  
 <span data-ttu-id="4fa76-109">`GoTo` Příkaz větvit pouze pro řádky v postupu, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="4fa76-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="4fa76-110">Na řádku musí mít popisek, který řádek `GoTo` mohou odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="4fa76-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="4fa76-111">Další informace najdete v tématu [jak: popisek příkazy](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="4fa76-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fa76-112">`GoTo` příkazy může ztěžovat kód ke čtení a udržovat.</span><span class="sxs-lookup"><span data-stu-id="4fa76-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="4fa76-113">Kdykoli je to možné, použijte řídicí struktura.</span><span class="sxs-lookup"><span data-stu-id="4fa76-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="4fa76-114">Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="4fa76-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="4fa76-115">Nelze použít `GoTo` příkaz do větve z mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo `Using`... `End Using` konstrukce na popisek uvnitř.</span><span class="sxs-lookup"><span data-stu-id="4fa76-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="4fa76-116">Větvení a konstrukce akci</span><span class="sxs-lookup"><span data-stu-id="4fa76-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="4fa76-117">V rámci `Try`... `Catch`... `Finally` konstrukce, platí následující pravidla pro větvení s `GoTo` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4fa76-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="4fa76-118">Blokování nebo oblasti</span><span class="sxs-lookup"><span data-stu-id="4fa76-118">Block or region</span></span>|<span data-ttu-id="4fa76-119">Větvení v z mimo</span><span class="sxs-lookup"><span data-stu-id="4fa76-119">Branching in from outside</span></span>|<span data-ttu-id="4fa76-120">Větvení navýšení kapacity v rámci</span><span class="sxs-lookup"><span data-stu-id="4fa76-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="4fa76-121">`Try` Blok</span><span class="sxs-lookup"><span data-stu-id="4fa76-121">`Try` block</span></span>|<span data-ttu-id="4fa76-122">Pouze z `Catch` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4fa76-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="4fa76-123">Pouze mimo celý konstrukce</span><span class="sxs-lookup"><span data-stu-id="4fa76-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="4fa76-124">`Catch` Blok</span><span class="sxs-lookup"><span data-stu-id="4fa76-124">`Catch` block</span></span>|<span data-ttu-id="4fa76-125">Nikdy povoleno</span><span class="sxs-lookup"><span data-stu-id="4fa76-125">Never allowed</span></span>|<span data-ttu-id="4fa76-126">Pouze mimo celého procesu vytváření, nebo do adresáře `Try` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4fa76-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="4fa76-127">`Finally` Blok</span><span class="sxs-lookup"><span data-stu-id="4fa76-127">`Finally` block</span></span>|<span data-ttu-id="4fa76-128">Nikdy povoleno</span><span class="sxs-lookup"><span data-stu-id="4fa76-128">Never allowed</span></span>|<span data-ttu-id="4fa76-129">Nikdy povoleno</span><span class="sxs-lookup"><span data-stu-id="4fa76-129">Never allowed</span></span>|  
  
 <span data-ttu-id="4fa76-130"><sup>1</sup> Pokud `Try`... `Catch`... `Finally` konstrukce je vnořená v jiném, `Catch` větvit do bloku `Try` bloku na vlastní úroveň vnoření, ale ne do jiného `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="4fa76-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="4fa76-131">Vnořený `Try`... `Catch`... `Finally` konstrukce musí být obsažena v úplně `Try` nebo `Catch` bloku konstrukce, ve kterém je vnořená.</span><span class="sxs-lookup"><span data-stu-id="4fa76-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="4fa76-132">Následující obrázek znázorňuje jeden `Try` konstrukce vnořit do jiného.</span><span class="sxs-lookup"><span data-stu-id="4fa76-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="4fa76-133">Různými větvemi mezi bloky dvě konstrukce jsou označeny jako platný nebo neplatný.</span><span class="sxs-lookup"><span data-stu-id="4fa76-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="4fa76-134">![Grafický diagram větvení v konstrukcích Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="4fa76-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="4fa76-135">Platné a neplatné větve v konstrukcích Try</span><span class="sxs-lookup"><span data-stu-id="4fa76-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fa76-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fa76-136">Example</span></span>  
 <span data-ttu-id="4fa76-137">V následujícím příkladu `GoTo` příkaz vzorce pro větvení popisků čáry v postupu.</span><span class="sxs-lookup"><span data-stu-id="4fa76-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4fa76-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fa76-138">See Also</span></span>  
 [<span data-ttu-id="4fa76-139">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="4fa76-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="4fa76-140">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="4fa76-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="4fa76-141">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="4fa76-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="4fa76-142">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="4fa76-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="4fa76-143">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="4fa76-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="4fa76-144">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="4fa76-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="4fa76-145">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="4fa76-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="4fa76-146">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="4fa76-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
