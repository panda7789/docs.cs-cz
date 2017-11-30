---
title: "REM – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="52688-102">REM – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52688-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="52688-103">Umožňuje zahrnout poznámky vysvětlující ve zdrojovém kódu programu.</span><span class="sxs-lookup"><span data-stu-id="52688-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52688-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52688-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="52688-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="52688-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="52688-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="52688-106">Optional.</span></span> <span data-ttu-id="52688-107">Text jakékoli komentáře, které chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="52688-107">The text of any comment you want to include.</span></span> <span data-ttu-id="52688-108">Je vyžadován mezi mezeru `REM` – klíčové slovo a `comment`.</span><span class="sxs-lookup"><span data-stu-id="52688-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52688-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52688-109">Remarks</span></span>  
 <span data-ttu-id="52688-110">Můžete vložit `REM` příkaz samostatně na řádku, nebo ji umístit na řádku za jiný příkaz.</span><span class="sxs-lookup"><span data-stu-id="52688-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="52688-111">`REM` Příkaz musí být poslední příkaz v řádku.</span><span class="sxs-lookup"><span data-stu-id="52688-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="52688-112">Pokud postupuje jiný příkaz `REM` musí být oddělené od tohoto příkazu mezerou.</span><span class="sxs-lookup"><span data-stu-id="52688-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="52688-113">Můžete provádět jednoduché uvozovky (`'`) místo `REM`.</span><span class="sxs-lookup"><span data-stu-id="52688-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="52688-114">To platí, jestli váš komentář následuje jiný příkaz na stejném řádku umístěn nebo samostatně na řádek.</span><span class="sxs-lookup"><span data-stu-id="52688-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52688-115">Nelze pokračovat, `REM` příkaz s použitím posloupnost pokračování řádku (`_`).</span><span class="sxs-lookup"><span data-stu-id="52688-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="52688-116">Jakmile začne komentář, kompilátor není zkontrolujte znaků pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="52688-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="52688-117">Pro více řádků komentář, použít jiný `REM` příkaz nebo symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="52688-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52688-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="52688-118">Example</span></span>  
 <span data-ttu-id="52688-119">Následující příklad ukazuje `REM` příkaz, který se používá k zahrnují vysvětlující poznámky v programu.</span><span class="sxs-lookup"><span data-stu-id="52688-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="52688-120">Také ukazuje použití znak jednoduché uvozovky (`'`) místo `REM`.</span><span class="sxs-lookup"><span data-stu-id="52688-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52688-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="52688-121">See Also</span></span>  
 [<span data-ttu-id="52688-122">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="52688-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [<span data-ttu-id="52688-123">Postupy: přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="52688-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
