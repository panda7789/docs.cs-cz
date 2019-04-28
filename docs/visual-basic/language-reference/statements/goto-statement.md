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
ms.openlocfilehash: c4dd249620ba1bf445642ce4600498f6beb30461
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637971"
---
# <a name="goto-statement"></a><span data-ttu-id="630e5-102">GoTo – příkaz</span><span class="sxs-lookup"><span data-stu-id="630e5-102">GoTo Statement</span></span>
<span data-ttu-id="630e5-103">Rozvětví se nepodmíněně na určený řádek v proceduře.</span><span class="sxs-lookup"><span data-stu-id="630e5-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="630e5-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="630e5-105">Část</span><span class="sxs-lookup"><span data-stu-id="630e5-105">Part</span></span>  
 `line`  
 <span data-ttu-id="630e5-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="630e5-106">Required.</span></span> <span data-ttu-id="630e5-107">Žádné čáry popisku.</span><span class="sxs-lookup"><span data-stu-id="630e5-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="630e5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="630e5-108">Remarks</span></span>  
 <span data-ttu-id="630e5-109">`GoTo` Příkaz větvit pouze pro řádky v postupu, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="630e5-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="630e5-110">Na řádku musí mít popisek, který řádek `GoTo` mohou odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="630e5-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="630e5-111">Další informace najdete v tématu [jak: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="630e5-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="630e5-112">`GoTo` příkazy může ztěžovat kód ke čtení a udržovat.</span><span class="sxs-lookup"><span data-stu-id="630e5-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="630e5-113">Kdykoli je to možné, použijte řídicí struktura.</span><span class="sxs-lookup"><span data-stu-id="630e5-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="630e5-114">Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="630e5-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="630e5-115">Nelze použít `GoTo` příkaz do větve z mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo `Using`... `End Using` konstrukce na popisek uvnitř.</span><span class="sxs-lookup"><span data-stu-id="630e5-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="630e5-116">Větvení a konstrukce akci</span><span class="sxs-lookup"><span data-stu-id="630e5-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="630e5-117">V rámci `Try`... `Catch`... `Finally` konstrukce, platí následující pravidla pro větvení s `GoTo` příkazu.</span><span class="sxs-lookup"><span data-stu-id="630e5-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="630e5-118">Blokování nebo oblasti</span><span class="sxs-lookup"><span data-stu-id="630e5-118">Block or region</span></span>|<span data-ttu-id="630e5-119">Větvení v z mimo</span><span class="sxs-lookup"><span data-stu-id="630e5-119">Branching in from outside</span></span>|<span data-ttu-id="630e5-120">Větvení navýšení kapacity v rámci</span><span class="sxs-lookup"><span data-stu-id="630e5-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="630e5-121">`Try` Blok</span><span class="sxs-lookup"><span data-stu-id="630e5-121">`Try` block</span></span>|<span data-ttu-id="630e5-122">Pouze z `Catch` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="630e5-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="630e5-123">Pouze mimo celý konstrukce</span><span class="sxs-lookup"><span data-stu-id="630e5-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="630e5-124">`Catch` Blok</span><span class="sxs-lookup"><span data-stu-id="630e5-124">`Catch` block</span></span>|<span data-ttu-id="630e5-125">Nikdy povoleno</span><span class="sxs-lookup"><span data-stu-id="630e5-125">Never allowed</span></span>|<span data-ttu-id="630e5-126">Pouze mimo celého procesu vytváření, nebo do adresáře `Try` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="630e5-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="630e5-127">`Finally` Blok</span><span class="sxs-lookup"><span data-stu-id="630e5-127">`Finally` block</span></span>|<span data-ttu-id="630e5-128">Nikdy povoleno</span><span class="sxs-lookup"><span data-stu-id="630e5-128">Never allowed</span></span>|<span data-ttu-id="630e5-129">Nikdy povoleno</span><span class="sxs-lookup"><span data-stu-id="630e5-129">Never allowed</span></span>|  
  
 <span data-ttu-id="630e5-130"><sup>1</sup> Pokud `Try`... `Catch`... `Finally` konstrukce je vnořená v jiném, `Catch` větvit do bloku `Try` bloku na vlastní úroveň vnoření, ale ne do jiného `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="630e5-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="630e5-131">Vnořený `Try`... `Catch`... `Finally` konstrukce musí být obsažena v úplně `Try` nebo `Catch` bloku konstrukce, ve kterém je vnořená.</span><span class="sxs-lookup"><span data-stu-id="630e5-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="630e5-132">Následující obrázek znázorňuje jeden `Try` konstrukce vnořit do jiného.</span><span class="sxs-lookup"><span data-stu-id="630e5-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="630e5-133">Různými větvemi mezi bloky dvě konstrukce jsou označeny jako platný nebo neplatný.</span><span class="sxs-lookup"><span data-stu-id="630e5-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Grafický diagram větvení v konstrukcích Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="630e5-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="630e5-135">Example</span></span>  
 <span data-ttu-id="630e5-136">V následujícím příkladu `GoTo` příkaz vzorce pro větvení popisků čáry v postupu.</span><span class="sxs-lookup"><span data-stu-id="630e5-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="630e5-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="630e5-137">See also</span></span>

- [<span data-ttu-id="630e5-138">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="630e5-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="630e5-139">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="630e5-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="630e5-140">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="630e5-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="630e5-141">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="630e5-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="630e5-142">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="630e5-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="630e5-143">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="630e5-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="630e5-144">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="630e5-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="630e5-145">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="630e5-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
