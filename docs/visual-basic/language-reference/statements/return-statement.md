---
title: "Return – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="b2363-102">Return – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2363-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="b2363-103">Vrátí ovládací prvek na kód, který volá `Function`, `Sub`, `Get`, `Set`, nebo `Operator` postupu.</span><span class="sxs-lookup"><span data-stu-id="b2363-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2363-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2363-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="b2363-105">Část</span><span class="sxs-lookup"><span data-stu-id="b2363-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="b2363-106">V požadován `Function`, `Get`, nebo `Operator` postupu.</span><span class="sxs-lookup"><span data-stu-id="b2363-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="b2363-107">Výraz, který představuje hodnotu, která má být vrácen pro volací kód.</span><span class="sxs-lookup"><span data-stu-id="b2363-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2363-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2363-108">Remarks</span></span>  
 <span data-ttu-id="b2363-109">V `Sub` nebo `Set` postupu `Return` příkaz je ekvivalentní `Exit Sub` nebo `Exit Property` příkaz, a `expression` nesmí být zadaný.</span><span class="sxs-lookup"><span data-stu-id="b2363-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="b2363-110">V `Function`, `Get`, nebo `Operator` postupu `Return` musí zahrnovat příkaz `expression`, a `expression` se musí vyhodnotit datový typ, který je převést na návratový typ procedury.</span><span class="sxs-lookup"><span data-stu-id="b2363-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="b2363-111">V `Function` nebo `Get` postup, můžete si taky alternativní přiřazování výraz název procedury, která bude sloužit jako návratovou hodnotu a pak provedením `Exit Function` nebo `Exit Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2363-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="b2363-112">V `Operator` postup, musíte použít `Return``expression`.</span><span class="sxs-lookup"><span data-stu-id="b2363-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="b2363-113">Můžete zahrnout tolik `Return` příkazy podle potřeby v stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b2363-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2363-114">Kód v `Finally` bloku se spouští po `Return` příkaz v `Try` nebo `Catch` blok je zjištěno, ale před `Return` provede příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2363-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="b2363-115">A `Return` nemůže být součástí příkazu `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="b2363-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2363-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2363-116">Example</span></span>  
 <span data-ttu-id="b2363-117">Následující příklad používá `Return` příkaz několikrát vrácené volání kódu v případě postup není potřeba dělat žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="b2363-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b2363-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2363-118">See Also</span></span>  
 [<span data-ttu-id="b2363-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="b2363-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="b2363-121">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="b2363-122">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="b2363-123">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="b2363-124">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="b2363-125">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="b2363-126">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2363-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
