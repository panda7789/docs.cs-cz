---
title: "Continue – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="6d2d2-102">Continue – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d2d2-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="6d2d2-103">Řízení přenosů okamžitě do další iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d2d2-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d2d2-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d2d2-105">Remarks</span></span>  
 <span data-ttu-id="6d2d2-106">Můžete přenést z uvnitř `Do`, `For`, nebo `While` smyčky do další iterace této smyčky.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="6d2d2-107">Řízení předává okamžitě do testu podmínku smyčky, která je ekvivalentní přenosu do `For` nebo `While` prohlášení, nebo `Do` nebo `Loop` příkazu, který obsahuje `Until` nebo `While` klauzule.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="6d2d2-108">Můžete použít `Continue` v libovolném umístění ve smyčce, která umožňuje přenosy.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="6d2d2-109">Pravidla umožňující přenos řízení jsou stejné jako s [GoTo – příkaz](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d2d2-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="6d2d2-110">Například, pokud je zcela obsažené v rámci smyčku `Try` bloku `Catch` bloku nebo `Finally` blok, můžete použít `Continue` přenos mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="6d2d2-111">Pokud na druhé straně, `Try`... `End Try` struktura je obsažena v smyčky, nemůžete použít `Continue` přenos řízení z `Finally` blok a může použít k přenosu z `Try` nebo `Catch` blokovat jenom při přenosu zcela z `Try`... `End Try` struktura.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="6d2d2-112">Pokud máte vnořené smyčky stejného typu, například `Do` smyčky v rámci jiného `Do` smyčky, `Continue Do` příkaz přeskočí na další iterace nejvnitřnější `Do` smyčky, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="6d2d2-113">Nemůžete použít `Continue` tak, aby přeskočil do další iterace smyčky obsahující stejného typu.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="6d2d2-114">Pokud například máte vnořené smyčky různých typů `Do` cykly v rámci `For` smyčku, můžete přejít na další iterace buď smyčky pomocí `Continue Do` nebo `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d2d2-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d2d2-115">Example</span></span>  
 <span data-ttu-id="6d2d2-116">Následující příklad kódu používá `Continue While` příkaz a přejděte k další sloupec pole, pokud dělitel je nulová.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="6d2d2-117">`Continue While` Je uvnitř `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="6d2d2-118">Přenosu do `While col < lastcol` příkaz, který je další iterace nejvnitřnější `While` smyčky, který obsahuje `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6d2d2-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d2d2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d2d2-119">See Also</span></span>  
 [<span data-ttu-id="6d2d2-120">Provést... Příkaz smyčky</span><span class="sxs-lookup"><span data-stu-id="6d2d2-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="6d2d2-121">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d2d2-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="6d2d2-122">Chvíli... End While – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d2d2-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="6d2d2-123">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d2d2-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
