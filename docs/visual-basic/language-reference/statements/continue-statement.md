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
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="8b22e-102">Continue – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b22e-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="8b22e-103">Okamžitě přenese řízení na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="8b22e-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b22e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b22e-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="8b22e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b22e-105">Remarks</span></span>  
 <span data-ttu-id="8b22e-106">Můžete přenášet z `Do`, `For`nebo `While` smyčky do další iterace této smyčky.</span><span class="sxs-lookup"><span data-stu-id="8b22e-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="8b22e-107">Řízení se okamžitě předává do testu podmínky smyčky, který je ekvivalentní k přenosu do příkazu `For` nebo `While` nebo k příkazu `Do` nebo `Loop`, který obsahuje klauzuli `Until` nebo `While`.</span><span class="sxs-lookup"><span data-stu-id="8b22e-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="8b22e-108">`Continue` můžete použít v jakémkoli umístění smyčky, která umožňuje přenosy.</span><span class="sxs-lookup"><span data-stu-id="8b22e-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="8b22e-109">Pravidla umožňující přenos řízení se shodují s [příkazem goto](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8b22e-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="8b22e-110">Například pokud je smyčka úplně obsažena v bloku `Try`, bloku `Catch` nebo bloku `Finally`, můžete použít `Continue` k přenosu ze smyčky.</span><span class="sxs-lookup"><span data-stu-id="8b22e-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="8b22e-111">Je-li na druhé straně struktura `Try`...`End Try` obsažena v rámci smyčky, nelze použít `Continue` k přenosu řízení z bloku `Finally` a můžete jej použít k přenosu z `Try` nebo `Catch` bloku pouze v případě, že jste přenesli z `Try`struktury...`End Try`.</span><span class="sxs-lookup"><span data-stu-id="8b22e-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="8b22e-112">Pokud máte vnořené smyčky stejného typu, například `Do` smyčka v rámci jiné smyčky `Do`, příkaz `Continue Do` skočí na další iteraci nejvnitřnějšího `Do` cyklu, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="8b22e-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="8b22e-113">`Continue` nelze použít k přeskočení na další iteraci obsahující smyčky stejného typu.</span><span class="sxs-lookup"><span data-stu-id="8b22e-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="8b22e-114">Pokud máte vnořené smyčky různých typů, například `Do` smyčka v rámci `For` smyčky, můžete přeskočit na další iteraci smyčky buď pomocí `Continue Do` nebo `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="8b22e-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b22e-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b22e-115">Example</span></span>  
 <span data-ttu-id="8b22e-116">Následující příklad kódu používá příkaz `Continue While` pro přechod k dalšímu sloupci pole, je-li dělitel nula.</span><span class="sxs-lookup"><span data-stu-id="8b22e-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="8b22e-117">`Continue While` je uvnitř smyčka `For`.</span><span class="sxs-lookup"><span data-stu-id="8b22e-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="8b22e-118">Přenáší na příkaz `While col < lastcol`, což je další iterace nejvnitřnější `While` smyčky, která obsahuje `For` smyčku.</span><span class="sxs-lookup"><span data-stu-id="8b22e-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="8b22e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b22e-119">See also</span></span>

- [<span data-ttu-id="8b22e-120">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="8b22e-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="8b22e-121">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="8b22e-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="8b22e-122">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="8b22e-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="8b22e-123">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="8b22e-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
