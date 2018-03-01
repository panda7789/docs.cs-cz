---
title: "Call – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="31eb1-102">Call – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31eb1-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="31eb1-103">Přenos řízení `Function`, `Sub`, nebo postup dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="31eb1-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31eb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31eb1-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="31eb1-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="31eb1-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="31eb1-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="31eb1-106">Required.</span></span> <span data-ttu-id="31eb1-107">Název procedury k volání.</span><span class="sxs-lookup"><span data-stu-id="31eb1-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="31eb1-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="31eb1-108">Optional.</span></span> <span data-ttu-id="31eb1-109">Seznam proměnných nebo výrazů představující argumenty, které se budou předávat procesu při jejím volání.</span><span class="sxs-lookup"><span data-stu-id="31eb1-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="31eb1-110">Více argumentů jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="31eb1-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="31eb1-111">Pokud zahrnete `argumentList`, je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="31eb1-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31eb1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31eb1-112">Remarks</span></span>  
 <span data-ttu-id="31eb1-113">Můžete použít `Call` – klíčové slovo při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="31eb1-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="31eb1-114">Pro většinu volání procedur není nutné používat toto klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="31eb1-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="31eb1-115">Obvykle se používá `Call` – klíčové slovo volané výraz nezačíná identifikátor.</span><span class="sxs-lookup"><span data-stu-id="31eb1-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="31eb1-116">Použití `Call` – klíčové slovo pro jiné účely se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="31eb1-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="31eb1-117">Pokud postup vrátí hodnotu, `Call` příkaz zruší ho.</span><span class="sxs-lookup"><span data-stu-id="31eb1-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31eb1-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="31eb1-118">Example</span></span>  
 <span data-ttu-id="31eb1-119">Následující kód ukazuje dva příklady kde `Call` – klíčové slovo je potřeba volání procedury.</span><span class="sxs-lookup"><span data-stu-id="31eb1-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="31eb1-120">V obou příkladech volané výraz nezačíná identifikátor.</span><span class="sxs-lookup"><span data-stu-id="31eb1-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="31eb1-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="31eb1-121">See Also</span></span>  
 [<span data-ttu-id="31eb1-122">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="31eb1-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="31eb1-123">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="31eb1-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="31eb1-124">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="31eb1-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="31eb1-125">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="31eb1-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
