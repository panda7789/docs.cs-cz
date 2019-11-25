---
title: Continue – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354114"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="3c343-102">Continue – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c343-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="3c343-103">Transfers control immediately to the next iteration of a loop.</span><span class="sxs-lookup"><span data-stu-id="3c343-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c343-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="3c343-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c343-105">Remarks</span></span>  
 <span data-ttu-id="3c343-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span><span class="sxs-lookup"><span data-stu-id="3c343-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="3c343-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span><span class="sxs-lookup"><span data-stu-id="3c343-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="3c343-108">You can use `Continue` at any location in the loop that allows transfers.</span><span class="sxs-lookup"><span data-stu-id="3c343-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="3c343-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3c343-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="3c343-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span><span class="sxs-lookup"><span data-stu-id="3c343-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="3c343-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span><span class="sxs-lookup"><span data-stu-id="3c343-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="3c343-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span><span class="sxs-lookup"><span data-stu-id="3c343-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="3c343-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span><span class="sxs-lookup"><span data-stu-id="3c343-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="3c343-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="3c343-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c343-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c343-115">Example</span></span>  
 <span data-ttu-id="3c343-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span><span class="sxs-lookup"><span data-stu-id="3c343-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="3c343-117">The `Continue While` is inside a `For` loop.</span><span class="sxs-lookup"><span data-stu-id="3c343-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="3c343-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span><span class="sxs-lookup"><span data-stu-id="3c343-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="3c343-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c343-119">See also</span></span>

- [<span data-ttu-id="3c343-120">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="3c343-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="3c343-121">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="3c343-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3c343-122">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="3c343-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="3c343-123">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="3c343-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
