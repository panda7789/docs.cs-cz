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
ms.openlocfilehash: efc85a3a844898345aa2d16926ba0e35d7346d1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333018"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="5bf44-102">Return – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bf44-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="5bf44-103">Vrátí řízení kódu, který se nazývá `Function`, `Sub`, `Get`, `Set`nebo `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="5bf44-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bf44-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="5bf44-105">Částí</span><span class="sxs-lookup"><span data-stu-id="5bf44-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="5bf44-106">Vyžaduje se v `Function`, `Get`nebo `Operator` postupu.</span><span class="sxs-lookup"><span data-stu-id="5bf44-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="5bf44-107">Výraz, který představuje hodnotu, která má být vrácena volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="5bf44-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bf44-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bf44-108">Remarks</span></span>  
 <span data-ttu-id="5bf44-109">V proceduře `Sub` nebo `Set` je příkaz `Return` ekvivalentem `Exit Sub` nebo příkazu `Exit Property` a `expression` nesmí být dodán.</span><span class="sxs-lookup"><span data-stu-id="5bf44-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="5bf44-110">V `Function`, `Get`nebo `Operator`, musí příkaz `Return` zahrnovat `expression`a `expression` musí vyhodnotit na datový typ, který lze převést na návratový typ procedury.</span><span class="sxs-lookup"><span data-stu-id="5bf44-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="5bf44-111">V proceduře `Function` nebo `Get` máte také alternativu k názvu procedury, která bude sloužit jako návratová hodnota, a následným spuštěním příkazu `Exit Function` nebo `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="5bf44-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="5bf44-112">V `Operator` proceduře je nutné použít `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="5bf44-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="5bf44-113">Stejným postupem můžete zahrnout tolik `Return` příkazů.</span><span class="sxs-lookup"><span data-stu-id="5bf44-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bf44-114">Kód v `Finally`ovém bloku se spustí po zjištění `Return` v `Try` nebo `Catch` bloku, ale před tím, než se spustí příkaz `Return`.</span><span class="sxs-lookup"><span data-stu-id="5bf44-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="5bf44-115">Příkaz `Return` nelze zahrnout do bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="5bf44-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bf44-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="5bf44-116">Example</span></span>  
 <span data-ttu-id="5bf44-117">Následující příklad používá příkaz `Return` několikrát pro návrat k volajícímu kódu, když procedura nemusí dělat něco jiného.</span><span class="sxs-lookup"><span data-stu-id="5bf44-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="5bf44-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bf44-118">See also</span></span>

- [<span data-ttu-id="5bf44-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="5bf44-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="5bf44-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="5bf44-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="5bf44-121">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="5bf44-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="5bf44-122">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="5bf44-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="5bf44-123">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="5bf44-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="5bf44-124">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="5bf44-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="5bf44-125">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="5bf44-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="5bf44-126">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="5bf44-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
