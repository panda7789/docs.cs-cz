---
title: Return – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957675"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="84512-102">Return – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84512-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="84512-103">Vrátí řízení kódu `Function`, který se nazývá procedura `Get`, `Sub` `Set`,, nebo `Operator` .</span><span class="sxs-lookup"><span data-stu-id="84512-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84512-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84512-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="84512-105">Částí</span><span class="sxs-lookup"><span data-stu-id="84512-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="84512-106">Vyžadováno v `Function`proceduře, `Get`nebo. `Operator`</span><span class="sxs-lookup"><span data-stu-id="84512-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="84512-107">Výraz, který představuje hodnotu, která má být vrácena volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="84512-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84512-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84512-108">Remarks</span></span>  
 <span data-ttu-id="84512-109">`Sub` V proceduře `Set`neboje příkazekvivalentní`Exit Sub` příkazu nebo`Exit Property` a`expression`nesmíbýtdodán. `Return`</span><span class="sxs-lookup"><span data-stu-id="84512-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="84512-110">`Get` Vproceduře`Return` ,nebo`expression`musí příkaz obsahovat a`expression` musí vyhodnotit na datový typ, který lze převést na návratový typ procedury. `Operator` `Function`</span><span class="sxs-lookup"><span data-stu-id="84512-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="84512-111">V proceduře `Get` `Exit Function` nebo máte také alternativu k názvu procedury, která má sloužit jako návratová hodnota, a poté provedení příkazu nebo `Exit Property`. `Function`</span><span class="sxs-lookup"><span data-stu-id="84512-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="84512-112">V proceduře je nutné použít `Return expression`. `Operator`</span><span class="sxs-lookup"><span data-stu-id="84512-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="84512-113">Stejný postup můžete použít jako `Return` vhodný počet příkazů.</span><span class="sxs-lookup"><span data-stu-id="84512-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84512-114">Kód `Finally` v bloku se spustí `Try` `Return` po zjištění příkazu v bloku nebo `Catch` , ale před spuštěním tohoto `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="84512-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="84512-115">Příkaz nelze zahrnout `Finally` do bloku. `Return`</span><span class="sxs-lookup"><span data-stu-id="84512-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84512-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="84512-116">Example</span></span>  
 <span data-ttu-id="84512-117">Následující příklad používá `Return` příkaz několikrát pro návrat na volající kód v případě, že procedura nemusí dělat cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="84512-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="84512-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84512-118">See also</span></span>

- [<span data-ttu-id="84512-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="84512-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="84512-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="84512-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="84512-121">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="84512-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="84512-122">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="84512-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="84512-123">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="84512-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="84512-124">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="84512-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="84512-125">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="84512-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="84512-126">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="84512-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
