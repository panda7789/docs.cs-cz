---
title: Call – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: e706650ac6da84d9b4e77fc549811e731be61b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594158"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="e0f44-102">Call – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0f44-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="e0f44-103">Přenosy ovládacího prvku `Function`, `Sub`, nebo procedura dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="e0f44-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0f44-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e0f44-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e0f44-105">Parts</span></span>  
|||
|---|---|
|`procedureName`|<span data-ttu-id="e0f44-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e0f44-106">Required.</span></span> <span data-ttu-id="e0f44-107">Název procedury pro volání.</span><span class="sxs-lookup"><span data-stu-id="e0f44-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="e0f44-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e0f44-108">Optional.</span></span> <span data-ttu-id="e0f44-109">Seznam proměnných a výrazů představujících argumenty, které jsou předány na postup, když je volána.</span><span class="sxs-lookup"><span data-stu-id="e0f44-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="e0f44-110">Více argumentů jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="e0f44-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="e0f44-111">Pokud zahrnete `argumentList`, je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="e0f44-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="e0f44-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0f44-112">Remarks</span></span>  
 <span data-ttu-id="e0f44-113">Můžete použít `Call` – klíčové slovo při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="e0f44-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="e0f44-114">Pro většinu volání procedur není nutné používat toto klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e0f44-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="e0f44-115">Obvykle se používá `Call` – klíčové slovo volané výrazu nelze spustit s identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="e0f44-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="e0f44-116">Použití `Call` – klíčové slovo pro jiné účely se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="e0f44-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="e0f44-117">Pokud se proces vrátí hodnotu, která `Call` příkaz zahodí ji.</span><span class="sxs-lookup"><span data-stu-id="e0f44-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f44-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0f44-118">Example</span></span>  
 <span data-ttu-id="e0f44-119">Následující kód ukazuje dva příklady kde `Call` – klíčové slovo je potřeba volání procedury.</span><span class="sxs-lookup"><span data-stu-id="e0f44-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="e0f44-120">V obou příkladech nezačíná názvem výraz identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e0f44-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e0f44-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0f44-121">See also</span></span>
- [<span data-ttu-id="e0f44-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="e0f44-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="e0f44-123">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="e0f44-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="e0f44-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="e0f44-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="e0f44-125">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="e0f44-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
