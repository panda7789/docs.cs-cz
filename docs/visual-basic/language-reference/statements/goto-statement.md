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
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581821"
---
# <a name="goto-statement"></a><span data-ttu-id="fd7ed-102">GoTo – příkaz</span><span class="sxs-lookup"><span data-stu-id="fd7ed-102">GoTo Statement</span></span>
<span data-ttu-id="fd7ed-103">Větve nepodmíněně na určený řádek v proceduře.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd7ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd7ed-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="fd7ed-105">Částí</span><span class="sxs-lookup"><span data-stu-id="fd7ed-105">Part</span></span>  
 `line`  
 <span data-ttu-id="fd7ed-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-106">Required.</span></span> <span data-ttu-id="fd7ed-107">Libovolný popisek čáry.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd7ed-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd7ed-108">Remarks</span></span>  
 <span data-ttu-id="fd7ed-109">Příkaz `GoTo` se může větvit jenom na řádky v proceduře, ve které se vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="fd7ed-110">Řádek musí mít popisek čáry, na který `GoTo` může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="fd7ed-111">Další informace naleznete v tématu [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="fd7ed-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd7ed-112">příkazy `GoTo` mohou ztížit čtení a údržbu kódu.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="fd7ed-113">Kdykoli je to možné, použijte místo toho strukturu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="fd7ed-114">Další informace najdete v tématu [tok řízení](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="fd7ed-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="fd7ed-115">Příkaz `GoTo` nelze použít pro větev mimo `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, 0... 1 nebo 2... 3 konstrukce na popisek uvnitř.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="fd7ed-116">Větvení a vytváření try</span><span class="sxs-lookup"><span data-stu-id="fd7ed-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="fd7ed-117">V rámci `Try`... `Catch`... `Finally` konstrukce se následující pravidla vztahují na větvení pomocí příkazu `GoTo`.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="fd7ed-118">Blok nebo oblast</span><span class="sxs-lookup"><span data-stu-id="fd7ed-118">Block or region</span></span>|<span data-ttu-id="fd7ed-119">Větvení z vnějšku</span><span class="sxs-lookup"><span data-stu-id="fd7ed-119">Branching in from outside</span></span>|<span data-ttu-id="fd7ed-120">Vyskočení z vnitřku</span><span class="sxs-lookup"><span data-stu-id="fd7ed-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="fd7ed-121">blok `Try`</span><span class="sxs-lookup"><span data-stu-id="fd7ed-121">`Try` block</span></span>|<span data-ttu-id="fd7ed-122">Pouze z `Catch`ho bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fd7ed-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="fd7ed-123">Jenom mimo celou konstrukci</span><span class="sxs-lookup"><span data-stu-id="fd7ed-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="fd7ed-124">blok `Catch`</span><span class="sxs-lookup"><span data-stu-id="fd7ed-124">`Catch` block</span></span>|<span data-ttu-id="fd7ed-125">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="fd7ed-125">Never allowed</span></span>|<span data-ttu-id="fd7ed-126">Pouze mimo celou konstrukci nebo do `Try`ho bloku stejné konstrukce <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fd7ed-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="fd7ed-127">blok `Finally`</span><span class="sxs-lookup"><span data-stu-id="fd7ed-127">`Finally` block</span></span>|<span data-ttu-id="fd7ed-128">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="fd7ed-128">Never allowed</span></span>|<span data-ttu-id="fd7ed-129">Nikdy Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="fd7ed-129">Never allowed</span></span>|  
  
 <span data-ttu-id="fd7ed-130"><sup>1</sup> , pokud jedna `Try`... `Catch`... `Finally` konstrukce je vnořená do jiného, `Catch` blok se může větvit do `Try` bloku na vlastní úrovni vnoření, ale ne do žádného jiného `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="fd7ed-131">Vnořený `Try`... `Catch`... konstrukce `Finally` musí být zcela obsažena v bloku `Try` nebo `Catch` konstrukce, v rámci které je vnořena.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="fd7ed-132">Následující ilustrace znázorňuje jeden `Try` konstrukce vnořené v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="fd7ed-133">Různé větve mezi bloky dvou konstrukcí jsou označeny jako platné nebo neplatné.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Grafický diagram větvení v konstrukcích try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="fd7ed-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd7ed-135">Example</span></span>  
 <span data-ttu-id="fd7ed-136">Následující příklad používá příkaz `GoTo` pro větvení popiskům čáry v proceduře.</span><span class="sxs-lookup"><span data-stu-id="fd7ed-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="fd7ed-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd7ed-137">See also</span></span>

- [<span data-ttu-id="fd7ed-138">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="fd7ed-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="fd7ed-139">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="fd7ed-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="fd7ed-140">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="fd7ed-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="fd7ed-141">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="fd7ed-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="fd7ed-142">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="fd7ed-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="fd7ed-143">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="fd7ed-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="fd7ed-144">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="fd7ed-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="fd7ed-145">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="fd7ed-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
