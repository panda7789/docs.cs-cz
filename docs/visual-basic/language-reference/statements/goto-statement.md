---
title: GoTo – příkaz
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
ms.openlocfilehash: eb6f48d04b7d14591003e340464451da7df45cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404612"
---
# <a name="goto-statement"></a><span data-ttu-id="b2d5a-102">GoTo – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-102">GoTo Statement</span></span>
<span data-ttu-id="b2d5a-103">Větve nepodmíněně na určený řádek v proceduře.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2d5a-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="b2d5a-105">Část</span><span class="sxs-lookup"><span data-stu-id="b2d5a-105">Part</span></span>  
 `line`  
 <span data-ttu-id="b2d5a-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-106">Required.</span></span> <span data-ttu-id="b2d5a-107">Libovolný popisek čáry.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2d5a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2d5a-108">Remarks</span></span>  
 <span data-ttu-id="b2d5a-109">`GoTo`Příkaz může být větví pouze na řádky v proceduře, ve které se vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="b2d5a-110">Řádek musí mít popisek řádku, na který `GoTo` může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="b2d5a-111">Další informace naleznete v tématu [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="b2d5a-111">For more information, see [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2d5a-112">`GoTo`příkazy mohou ztížit čtení a údržbu kódu.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="b2d5a-113">Kdykoli je to možné, použijte místo toho strukturu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="b2d5a-114">Další informace najdete v tématu [tok řízení](../../programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2d5a-114">For more information, see [Control Flow](../../programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="b2d5a-115">Nemůžete použít `GoTo` příkaz k vytvoření větve mimo `For` ... `Next` , `For Each` ..., `Next` `SyncLock` `End SyncLock` `Try` ...,. `Catch` .. ... `Finally` , `With` ...,... `End With` , nebo `Using` ... `End Using` konstrukce na návěští uvnitř.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="b2d5a-116">Větvení a vytváření try</span><span class="sxs-lookup"><span data-stu-id="b2d5a-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="b2d5a-117">V rámci `Try` ... `Catch` ...`Finally` konstrukce: následující pravidla platí pro větvení s `GoTo` příkazem.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="b2d5a-118">Blok nebo oblast</span><span class="sxs-lookup"><span data-stu-id="b2d5a-118">Block or region</span></span>|<span data-ttu-id="b2d5a-119">Větvení z vnějšku</span><span class="sxs-lookup"><span data-stu-id="b2d5a-119">Branching in from outside</span></span>|<span data-ttu-id="b2d5a-120">Vyskočení z vnitřku</span><span class="sxs-lookup"><span data-stu-id="b2d5a-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="b2d5a-121">Blok `Try`</span><span class="sxs-lookup"><span data-stu-id="b2d5a-121">`Try` block</span></span>|<span data-ttu-id="b2d5a-122">Pouze z `Catch` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b2d5a-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="b2d5a-123">Jenom mimo celou konstrukci</span><span class="sxs-lookup"><span data-stu-id="b2d5a-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="b2d5a-124">Blok `Catch`</span><span class="sxs-lookup"><span data-stu-id="b2d5a-124">`Catch` block</span></span>|<span data-ttu-id="b2d5a-125">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="b2d5a-125">Never allowed</span></span>|<span data-ttu-id="b2d5a-126">Pouze vně celé konstrukce nebo do `Try` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b2d5a-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="b2d5a-127">Blok `Finally`</span><span class="sxs-lookup"><span data-stu-id="b2d5a-127">`Finally` block</span></span>|<span data-ttu-id="b2d5a-128">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="b2d5a-128">Never allowed</span></span>|<span data-ttu-id="b2d5a-129">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="b2d5a-129">Never allowed</span></span>|  
  
 <span data-ttu-id="b2d5a-130"><sup>1</sup> , pokud jedna `Try` ... `Catch` ...`Finally` konstrukce je vnořena do jiného, `Catch` blok může být větví do `Try` bloku na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="b2d5a-131">Vnořený `Try` ... `Catch` ...`Finally` konstrukce musí být zcela obsažena v `Try` `Catch` bloku nebo konstrukce, v rámci které je vnořena.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="b2d5a-132">Následující ilustrace znázorňuje jeden `Try` konstrukcí vnořený do jiného.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="b2d5a-133">Různé větve mezi bloky dvou konstrukcí jsou označeny jako platné nebo neplatné.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Grafický diagram větvení v konstrukcích try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="b2d5a-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2d5a-135">Example</span></span>  
 <span data-ttu-id="b2d5a-136">Následující příklad používá `GoTo` příkaz pro větvení popiskům čáry v proceduře.</span><span class="sxs-lookup"><span data-stu-id="b2d5a-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="b2d5a-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2d5a-137">See also</span></span>

- [<span data-ttu-id="b2d5a-138">Do...Loop – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-138">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="b2d5a-139">For...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-139">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="b2d5a-140">For Each...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-140">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="b2d5a-141">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-141">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="b2d5a-142">Select...Case – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-142">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="b2d5a-143">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-143">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="b2d5a-144">While...End While – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-144">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="b2d5a-145">With...End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2d5a-145">With...End With Statement</span></span>](with-end-with-statement.md)
