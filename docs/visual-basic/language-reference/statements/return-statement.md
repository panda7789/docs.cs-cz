---
title: Return – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404197"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="25cde-102">Return – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25cde-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="25cde-103">Vrátí řízení kódu, který se nazývá `Function` procedura,,, `Sub` `Get` `Set` nebo `Operator` .</span><span class="sxs-lookup"><span data-stu-id="25cde-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25cde-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25cde-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="25cde-105">Část</span><span class="sxs-lookup"><span data-stu-id="25cde-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="25cde-106">Vyžadováno v `Function` proceduře, `Get` nebo `Operator` .</span><span class="sxs-lookup"><span data-stu-id="25cde-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="25cde-107">Výraz, který představuje hodnotu, která má být vrácena volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="25cde-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25cde-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25cde-108">Remarks</span></span>  
 <span data-ttu-id="25cde-109">V `Sub` proceduře nebo `Set` `Return` je příkaz ekvivalentní `Exit Sub` `Exit Property` příkazu nebo a `expression` nesmí být dodán.</span><span class="sxs-lookup"><span data-stu-id="25cde-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="25cde-110">V `Function` proceduře, `Get` nebo `Operator` `Return` musí příkaz obsahovat `expression` a `expression` musí vyhodnotit na datový typ, který lze převést na návratový typ procedury.</span><span class="sxs-lookup"><span data-stu-id="25cde-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="25cde-111">V `Function` proceduře nebo máte `Get` také alternativu k názvu procedury, která má sloužit jako návratová hodnota, a poté provedení `Exit Function` `Exit Property` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="25cde-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="25cde-112">V `Operator` proceduře je nutné použít `Return expression` .</span><span class="sxs-lookup"><span data-stu-id="25cde-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="25cde-113">Stejný postup můžete použít jako `Return` vhodný počet příkazů.</span><span class="sxs-lookup"><span data-stu-id="25cde-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25cde-114">Kód v bloku se `Finally` spustí po `Return` zjištění příkazu v `Try` `Catch` bloku nebo, ale před spuštěním tohoto `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="25cde-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="25cde-115">`Return`Příkaz nelze zahrnout do `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="25cde-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25cde-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="25cde-116">Example</span></span>  
 <span data-ttu-id="25cde-117">Následující příklad používá `Return` příkaz několikrát pro návrat na volající kód v případě, že procedura nemusí dělat cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="25cde-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="25cde-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="25cde-118">See also</span></span>

- [<span data-ttu-id="25cde-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-119">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="25cde-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-120">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="25cde-121">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-121">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="25cde-122">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-122">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="25cde-123">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-123">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="25cde-124">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-124">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="25cde-125">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-125">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="25cde-126">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="25cde-126">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
