---
title: Continue – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638243"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="b2f34-102">Continue – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2f34-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="b2f34-103">Přenosy ovládacího prvku okamžitě na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="b2f34-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2f34-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2f34-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2f34-105">Remarks</span></span>  
 <span data-ttu-id="b2f34-106">Můžete přenášet z uvnitř `Do`, `For`, nebo `While` smyčky na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="b2f34-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="b2f34-107">Ovládací prvek ihned přejde k testovací podmínky smyčky, který je ekvivalentem k přenosu do `For` nebo `While` příkazu, nebo `Do` nebo `Loop` příkazu, který obsahuje `Until` nebo `While` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b2f34-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="b2f34-108">Můžete použít `Continue` v libovolném umístění v smyčky, která umožňuje přenosy.</span><span class="sxs-lookup"><span data-stu-id="b2f34-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="b2f34-109">Pravidla povolení přenos řízení jsou stejné jako [příkazu GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b2f34-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="b2f34-110">Například, pokud je zcela obsažený v rámci smyčky `Try` bloku, `Catch` bloku nebo `Finally` blok, můžete použít `Continue` přenos ze smyčky.</span><span class="sxs-lookup"><span data-stu-id="b2f34-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="b2f34-111">Pokud na druhou stranu, `Try`... `End Try` struktura je obsažen v rámci smyčky, nebude možné použít `Continue` k přenosu řízení z celkového počtu `Finally` bloku a vy můžete použít k převodu z `Try` nebo `Catch` blokovat jenom v případě, že je úplně přenést z celkového počtu `Try`... `End Try` struktury.</span><span class="sxs-lookup"><span data-stu-id="b2f34-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="b2f34-112">Pokud třeba máte vnořené smyčky stejného typu `Do` smyčky v jiném `Do` smyčky, `Continue Do` příkaz přeskočí na další iteraci nejvnitřnější `Do` smyčku, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="b2f34-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="b2f34-113">Nemůžete použít `Continue` přeskočit na další iteraci smyčky obsahující stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b2f34-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="b2f34-114">Pokud máte vnořené smyčky různých typů, třeba `Do` smyčky v rámci `For` smyčky, můžete přeskočit na další iteraci smyčky, buď pomocí `Continue Do` nebo `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="b2f34-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2f34-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2f34-115">Example</span></span>  
 <span data-ttu-id="b2f34-116">Následující příklad kódu používá `Continue While` příkaz přejděte tak do dalšího sloupce pole, pokud dělitel je nula.</span><span class="sxs-lookup"><span data-stu-id="b2f34-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="b2f34-117">`Continue While` Se nachází uvnitř `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="b2f34-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="b2f34-118">Přenese na `While col < lastcol` příkazu, který je na další iteraci nejvnitřnější `While` smyčku, která obsahuje `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="b2f34-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="b2f34-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2f34-119">See also</span></span>

- [<span data-ttu-id="b2f34-120">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="b2f34-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="b2f34-121">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="b2f34-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="b2f34-122">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="b2f34-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="b2f34-123">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="b2f34-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
