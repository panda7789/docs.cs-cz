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
ms.openlocfilehash: 9af1436af950346eef572c34b9d42da3e8c8cf24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671158"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="4c8d1-102">Throw – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c8d1-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="4c8d1-103">Generuje výjimku uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c8d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c8d1-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="4c8d1-105">Část</span><span class="sxs-lookup"><span data-stu-id="4c8d1-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="4c8d1-106">Poskytuje informace o vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="4c8d1-107">Volitelné, při které se nacházejí v `Catch` příkaz, jinak povinné.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c8d1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c8d1-108">Remarks</span></span>  
 <span data-ttu-id="4c8d1-109">`Throw` Příkazu vyvolá výjimku, který dokáže pracovat s kódem strukturované zpracování výjimek (`Try`... `Catch`... `Finally`) nebo nestrukturovaných kód zpracování výjimek (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="4c8d1-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="4c8d1-110">Můžete použít `Throw` příkaz zachytávat chyby v kódu, protože Visual Basic přesune výše v zásobníku volání, dokud nenajde odpovídající kód zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="4c8d1-111">A `Throw` příkazem žádný výraz lze použít pouze v `Catch` příkazu, ve kterém příkazu case znovu vyvolá výjimku, teď nezpracovává nástrojem `Catch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="4c8d1-112">`Throw` Příkaz obnoví zásobník volání pro `expression` výjimky.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="4c8d1-113">Pokud `expression` není k dispozici, zásobník volání je vlevo beze změny.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="4c8d1-114">Zásobník volání výjimky prostřednictvím můžete přistupovat <xref:System.Exception.StackTrace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c8d1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c8d1-115">Example</span></span>  
 <span data-ttu-id="4c8d1-116">Následující kód používá `Throw` příkaz vyvolání výjimky:</span><span class="sxs-lookup"><span data-stu-id="4c8d1-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="4c8d1-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c8d1-117">Requirements</span></span>  
 <span data-ttu-id="4c8d1-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="4c8d1-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="4c8d1-119">**Modul:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="4c8d1-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="4c8d1-120">**Sestavení:** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="4c8d1-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8d1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c8d1-121">See also</span></span>
- [<span data-ttu-id="4c8d1-122">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="4c8d1-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="4c8d1-123">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="4c8d1-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
