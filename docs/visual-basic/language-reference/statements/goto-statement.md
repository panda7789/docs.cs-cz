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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912451"
---
# <a name="goto-statement"></a><span data-ttu-id="d5854-102">GoTo – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5854-102">GoTo Statement</span></span>
<span data-ttu-id="d5854-103">Větve nepodmíněně na určený řádek v proceduře.</span><span class="sxs-lookup"><span data-stu-id="d5854-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5854-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5854-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="d5854-105">Částí</span><span class="sxs-lookup"><span data-stu-id="d5854-105">Part</span></span>  
 `line`  
 <span data-ttu-id="d5854-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d5854-106">Required.</span></span> <span data-ttu-id="d5854-107">Libovolný popisek čáry.</span><span class="sxs-lookup"><span data-stu-id="d5854-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5854-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5854-108">Remarks</span></span>  
 <span data-ttu-id="d5854-109">`GoTo` Příkaz může být větví pouze na řádky v proceduře, ve které se vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="d5854-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="d5854-110">Řádek musí mít popisek řádku, na který `GoTo` může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="d5854-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="d5854-111">Další informace najdete v tématu [jak: Příkazy](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)Label.</span><span class="sxs-lookup"><span data-stu-id="d5854-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5854-112">`GoTo`příkazy mohou ztížit čtení a údržbu kódu.</span><span class="sxs-lookup"><span data-stu-id="d5854-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="d5854-113">Kdykoli je to možné, použijte místo toho strukturu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d5854-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="d5854-114">Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="d5854-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="d5854-115">Nemůžete použít `GoTo` příkaz k vytvoření `For`větve mimo... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, nebo`Using`... `End Using` konstrukce na návěští uvnitř.</span><span class="sxs-lookup"><span data-stu-id="d5854-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="d5854-116">Větvení a vytváření try</span><span class="sxs-lookup"><span data-stu-id="d5854-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="d5854-117">V rámci `Try`... `Catch`... konstrukce: následující pravidla platí pro větvení `GoTo` s příkazem. `Finally`</span><span class="sxs-lookup"><span data-stu-id="d5854-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="d5854-118">Blok nebo oblast</span><span class="sxs-lookup"><span data-stu-id="d5854-118">Block or region</span></span>|<span data-ttu-id="d5854-119">Větvení z vnějšku</span><span class="sxs-lookup"><span data-stu-id="d5854-119">Branching in from outside</span></span>|<span data-ttu-id="d5854-120">Vyskočení z vnitřku</span><span class="sxs-lookup"><span data-stu-id="d5854-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="d5854-121">`Try`Blokované</span><span class="sxs-lookup"><span data-stu-id="d5854-121">`Try` block</span></span>|<span data-ttu-id="d5854-122">Pouze z `Catch` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d5854-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="d5854-123">Jenom mimo celou konstrukci</span><span class="sxs-lookup"><span data-stu-id="d5854-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="d5854-124">`Catch`Blokované</span><span class="sxs-lookup"><span data-stu-id="d5854-124">`Catch` block</span></span>|<span data-ttu-id="d5854-125">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="d5854-125">Never allowed</span></span>|<span data-ttu-id="d5854-126">Pouze vně celé konstrukce nebo do `Try` bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d5854-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="d5854-127">`Finally`Blokované</span><span class="sxs-lookup"><span data-stu-id="d5854-127">`Finally` block</span></span>|<span data-ttu-id="d5854-128">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="d5854-128">Never allowed</span></span>|<span data-ttu-id="d5854-129">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="d5854-129">Never allowed</span></span>|  
  
 <span data-ttu-id="d5854-130"><sup>1</sup> , pokud `Try`jedna... `Catch`... konstrukce je vnořena do jiného, `Catch` `Try` blok může být větví do bloku na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku. `Finally`</span><span class="sxs-lookup"><span data-stu-id="d5854-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="d5854-131">Vnořený `Try`... `Catch`... konstrukce musí být zcela obsažena `Try` v bloku `Catch` nebo konstrukce, v rámci které je vnořena. `Finally`</span><span class="sxs-lookup"><span data-stu-id="d5854-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="d5854-132">Následující ilustrace znázorňuje jeden `Try` konstrukcí vnořený do jiného.</span><span class="sxs-lookup"><span data-stu-id="d5854-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="d5854-133">Různé větve mezi bloky dvou konstrukcí jsou označeny jako platné nebo neplatné.</span><span class="sxs-lookup"><span data-stu-id="d5854-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Grafický diagram větvení v konstrukcích try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="d5854-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5854-135">Example</span></span>  
 <span data-ttu-id="d5854-136">Následující příklad používá `GoTo` příkaz pro větvení popiskům čáry v proceduře.</span><span class="sxs-lookup"><span data-stu-id="d5854-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="d5854-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5854-137">See also</span></span>

- [<span data-ttu-id="d5854-138">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="d5854-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="d5854-139">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="d5854-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="d5854-140">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="d5854-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="d5854-141">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="d5854-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="d5854-142">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="d5854-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="d5854-143">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="d5854-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="d5854-144">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="d5854-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="d5854-145">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="d5854-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
