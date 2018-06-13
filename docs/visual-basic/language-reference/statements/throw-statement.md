---
title: Throw – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602850"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="e9344-102">Throw – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9344-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="e9344-103">Vyvolá výjimku, v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="e9344-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9344-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9344-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="e9344-105">Část</span><span class="sxs-lookup"><span data-stu-id="e9344-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="e9344-106">Poskytuje informace o vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="e9344-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="e9344-107">Volitelné, při které se nacházejí v `Catch` příkaz, jinak vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e9344-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9344-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9344-108">Remarks</span></span>  
 <span data-ttu-id="e9344-109">`Throw` Příkaz vyvolá výjimku, která dokáže zpracovat kódem strukturované zpracování výjimek (`Try`... `Catch`... `Finally`) nebo nestrukturovaných kódu zpracování výjimek (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="e9344-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="e9344-110">Můžete použít `Throw` příkaz na depeše chyb v kódu, protože jazyka Visual Basic přesune nahoru zásobníku volání, dokud nenajde odpovídající kód zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="e9344-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="e9344-111">A `Throw` příkaz s žádný výraz lze použít pouze v `Catch` příkaz, ve kterém případ příkaz znovu vyvolá výjimku aktuálně zpracovanou pomocí `Catch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9344-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="e9344-112">`Throw` Příkaz obnoví zásobníku volání pro `expression` výjimka.</span><span class="sxs-lookup"><span data-stu-id="e9344-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="e9344-113">Pokud `expression` není k dispozici, zásobník volání ponecháno změny.</span><span class="sxs-lookup"><span data-stu-id="e9344-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="e9344-114">Dostanete zásobníku volání pro výjimky prostřednictvím <xref:System.Exception.StackTrace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e9344-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9344-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9344-115">Example</span></span>  
 <span data-ttu-id="e9344-116">Následující kód používá `Throw` příkaz, který má být vyvolána výjimka:</span><span class="sxs-lookup"><span data-stu-id="e9344-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="e9344-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9344-117">Requirements</span></span>  
 <span data-ttu-id="e9344-118">**Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="e9344-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="e9344-119">**Modul:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="e9344-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="e9344-120">**Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="e9344-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9344-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9344-121">See Also</span></span>  
 [<span data-ttu-id="e9344-122">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="e9344-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="e9344-123">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="e9344-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
