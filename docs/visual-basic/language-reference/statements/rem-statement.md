---
title: REM – příkaz
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
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346733"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="f2f4e-102">REM – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f4e-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="f2f4e-103">Used to include explanatory remarks in the source code of a program.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f4e-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="f2f4e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f2f4e-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="f2f4e-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-106">Optional.</span></span> <span data-ttu-id="f2f4e-107">The text of any comment you want to include.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-107">The text of any comment you want to include.</span></span> <span data-ttu-id="f2f4e-108">A space is required between the `REM` keyword and `comment`.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f4e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2f4e-109">Remarks</span></span>  
 <span data-ttu-id="f2f4e-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="f2f4e-111">The `REM` statement must be the last statement on the line.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="f2f4e-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="f2f4e-113">You can use a single quotation mark (`'`) instead of `REM`.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="f2f4e-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2f4e-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span><span class="sxs-lookup"><span data-stu-id="f2f4e-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="f2f4e-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="f2f4e-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2f4e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2f4e-118">Example</span></span>  
 <span data-ttu-id="f2f4e-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="f2f4e-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span><span class="sxs-lookup"><span data-stu-id="f2f4e-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f2f4e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2f4e-121">See also</span></span>

- [<span data-ttu-id="f2f4e-122">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="f2f4e-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="f2f4e-123">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="f2f4e-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
