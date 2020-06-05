---
title: Continue – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382091"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="9b825-102">Continue – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b825-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="9b825-103">Okamžitě přenese řízení na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="9b825-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b825-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="9b825-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b825-105">Remarks</span></span>  
 <span data-ttu-id="9b825-106">Z smyčky dovnitř, nebo můžete přenášet `Do` `For` `While` do další iterace této smyčky.</span><span class="sxs-lookup"><span data-stu-id="9b825-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="9b825-107">Řízení se okamžitě předává do testu podmínky smyčky, který je ekvivalentní k přenosu do `For` příkazu nebo nebo `While` k `Do` `Loop` příkazu nebo, který obsahuje `Until` `While` klauzuli OR.</span><span class="sxs-lookup"><span data-stu-id="9b825-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="9b825-108">Můžete použít v `Continue` jakémkoli umístění smyčky, která umožňuje přenosy.</span><span class="sxs-lookup"><span data-stu-id="9b825-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="9b825-109">Pravidla umožňující přenos řízení se shodují s [příkazem goto](goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b825-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="9b825-110">Například pokud je smyčka úplně obsažena v `Try` bloku, `Catch` bloku nebo `Finally` bloku, můžete použít `Continue` k přenosu mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="9b825-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="9b825-111">Je-li na druhé straně `Try` Struktura... `End Try` obsažena v rámci smyčky, nelze použít `Continue` k přenosu řízení mimo `Finally` blok a lze jej použít k přenosu z `Try` bloku nebo pouze v případě, že `Catch` se přenáší zcela ze `Try` struktury... `End Try` .</span><span class="sxs-lookup"><span data-stu-id="9b825-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="9b825-112">Pokud máte vnořené smyčky stejného typu, například `Do` smyčka v rámci jiné `Do` smyčky, `Continue Do` příkaz se přeskočí na další iteraci nejvnitřnější `Do` smyčky, která ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9b825-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="9b825-113">Nelze použít `Continue` k přeskočení na další iteraci obsahující smyčky stejného typu.</span><span class="sxs-lookup"><span data-stu-id="9b825-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="9b825-114">Máte-li vnořené smyčky různých typů, například `Do` smyčka ve `For` smyčce, můžete přeskočit na další iteraci smyčky buď pomocí `Continue Do` nebo `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="9b825-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b825-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b825-115">Example</span></span>  
 <span data-ttu-id="9b825-116">Následující příklad kódu používá `Continue While` příkaz k přeskočení na další sloupec pole, pokud je dělitel nula.</span><span class="sxs-lookup"><span data-stu-id="9b825-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="9b825-117">`Continue While`Je uvnitř `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="9b825-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="9b825-118">Převede na `While col < lastcol` příkaz, což je další iterace nejvnitřnější `While` smyčky, která obsahuje `For` smyčku.</span><span class="sxs-lookup"><span data-stu-id="9b825-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="9b825-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b825-119">See also</span></span>

- [<span data-ttu-id="9b825-120">Do...Loop – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b825-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="9b825-121">For...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b825-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="9b825-122">While...End While – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b825-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="9b825-123">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b825-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
