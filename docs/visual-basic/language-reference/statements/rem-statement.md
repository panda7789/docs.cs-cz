---
title: REM – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: b25910f5215585914094b7bc4420f537a400934b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967993"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="1db78-102">REM – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1db78-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="1db78-103">Používá se k zahrnutí poznámky vysvětlující ve zdrojovém kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1db78-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db78-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="1db78-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1db78-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="1db78-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1db78-106">Optional.</span></span> <span data-ttu-id="1db78-107">Text všechny komentáře, které chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="1db78-107">The text of any comment you want to include.</span></span> <span data-ttu-id="1db78-108">Mezera mezi vyžádáním `REM` – klíčové slovo a `comment`.</span><span class="sxs-lookup"><span data-stu-id="1db78-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1db78-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1db78-109">Remarks</span></span>  
 <span data-ttu-id="1db78-110">Můžete vložit `REM` příkaz samostatně na řádku, nebo můžete umístit na řádek po jiného příkazu.</span><span class="sxs-lookup"><span data-stu-id="1db78-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="1db78-111">`REM` Příkaz musí být poslední příkaz na řádku.</span><span class="sxs-lookup"><span data-stu-id="1db78-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="1db78-112">Pokud následuje jiný příkaz, `REM` musí být odděleny od, který tento příkaz oddělte mezerou.</span><span class="sxs-lookup"><span data-stu-id="1db78-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="1db78-113">Můžete použít jednoduchou uvozovkou (`'`) namísto `REM`.</span><span class="sxs-lookup"><span data-stu-id="1db78-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="1db78-114">To platí, jestli váš komentář následuje jiný příkaz na stejném řádku nebo samostatně uložených na řádku.</span><span class="sxs-lookup"><span data-stu-id="1db78-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1db78-115">Nejde pokračovat `REM` příkaz s použitím posloupností pokračování řádku (`_`).</span><span class="sxs-lookup"><span data-stu-id="1db78-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="1db78-116">Po zahájení komentář, kompilátor nezkoumá znaků pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="1db78-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="1db78-117">Komentář k více řádků, použijte jiný `REM` příkazu nebo symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="1db78-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db78-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="1db78-118">Example</span></span>  
 <span data-ttu-id="1db78-119">Následující příklad ukazuje, `REM` příkaz, který se používá k zahrnutí do programu poznámky vysvětlující.</span><span class="sxs-lookup"><span data-stu-id="1db78-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="1db78-120">Ukazuje také použití znak jednoduché uvozovky (`'`) namísto `REM`.</span><span class="sxs-lookup"><span data-stu-id="1db78-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1db78-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1db78-121">See also</span></span>
- [<span data-ttu-id="1db78-122">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="1db78-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="1db78-123">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="1db78-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
