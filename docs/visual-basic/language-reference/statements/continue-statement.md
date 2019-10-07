---
title: Continue – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005100"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="95862-102">Continue – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95862-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="95862-103">Okamžitě přenese řízení na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="95862-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95862-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95862-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="95862-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95862-105">Remarks</span></span>  
 <span data-ttu-id="95862-106">V rámci smyčky `Do`, `For` nebo `While` se můžete přenést do další iterace této smyčky.</span><span class="sxs-lookup"><span data-stu-id="95862-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="95862-107">Řízení se okamžitě předává do testu podmínky smyčky, který odpovídá přenosu do příkazu `For` nebo `While` nebo do příkazu `Do` nebo `Loop`, který obsahuje klauzuli `Until` nebo `While`.</span><span class="sxs-lookup"><span data-stu-id="95862-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="95862-108">Můžete použít `Continue` v jakémkoli umístění smyčky, která umožňuje přenosy.</span><span class="sxs-lookup"><span data-stu-id="95862-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="95862-109">Pravidla umožňující přenos řízení se shodují s [příkazem goto](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="95862-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="95862-110">Například pokud je smyčka úplně obsažena v bloku `Try`, bloku `Catch` nebo bloku `Finally`, můžete k přenosu ze smyčky použít `Continue`.</span><span class="sxs-lookup"><span data-stu-id="95862-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="95862-111">Je-li na druhé straně struktura `Try`... `End Try` obsažena v rámci smyčky, nelze použít `Continue` pro přenos řízení z bloku `Finally` a můžete ho použít k přenosu z bloku `Try` nebo `Catch` pouze v případě, že jste přenesli zcela z @no_ – 6... `End Try` struktura.</span><span class="sxs-lookup"><span data-stu-id="95862-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="95862-112">Pokud máte vnořené smyčky stejného typu, například smyčka `Do` v rámci jiné smyčky `Do`, příkaz `Continue Do` přeskočí na další iteraci nejvnitřnější smyčky `Do`, která ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="95862-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="95862-113">@No__t-0 nelze použít k přeskočení na další iteraci obsahující smyčky stejného typu.</span><span class="sxs-lookup"><span data-stu-id="95862-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="95862-114">Pokud máte vnořené smyčky různých typů, například smyčka `Do` v rámci smyčky `For`, můžete přeskočit na další iteraci smyčky buď pomocí `Continue Do` nebo `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="95862-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95862-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="95862-115">Example</span></span>  
 <span data-ttu-id="95862-116">Následující příklad kódu používá příkaz `Continue While` k přeskočení na další sloupec pole, pokud je dělitel nula.</span><span class="sxs-lookup"><span data-stu-id="95862-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="95862-117">@No__t-0 je uvnitř smyčky `For`.</span><span class="sxs-lookup"><span data-stu-id="95862-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="95862-118">Přenáší na příkaz `While col < lastcol`, což je další iterace nejvnitřnější smyčky "`While`", která obsahuje smyčku `For`.</span><span class="sxs-lookup"><span data-stu-id="95862-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="95862-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95862-119">See also</span></span>

- [<span data-ttu-id="95862-120">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="95862-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="95862-121">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="95862-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="95862-122">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="95862-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="95862-123">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="95862-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
