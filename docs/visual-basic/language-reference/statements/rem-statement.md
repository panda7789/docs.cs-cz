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
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="c4237-102">REM – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4237-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="c4237-103">Slouží k zahrnutí vysvětlujících poznámek do zdrojového kódu programu.</span><span class="sxs-lookup"><span data-stu-id="c4237-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4237-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="c4237-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c4237-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="c4237-106">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="c4237-106">Optional.</span></span> <span data-ttu-id="c4237-107">Text libovolného komentáře, který chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="c4237-107">The text of any comment you want to include.</span></span> <span data-ttu-id="c4237-108">Mezi klíčovým slovem `REM` a `comment`se vyžaduje mezera.</span><span class="sxs-lookup"><span data-stu-id="c4237-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4237-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4237-109">Remarks</span></span>  
 <span data-ttu-id="c4237-110">Příkaz `REM` můžete umístit na řádek, nebo ho můžete umístit na řádek za jiným příkazem.</span><span class="sxs-lookup"><span data-stu-id="c4237-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="c4237-111">Příkaz `REM` musí být poslední příkaz na řádku.</span><span class="sxs-lookup"><span data-stu-id="c4237-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="c4237-112">Pokud se tento příkaz řídí jiným příkazem, `REM` musí být od tohoto příkazu oddělen mezerou.</span><span class="sxs-lookup"><span data-stu-id="c4237-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="c4237-113">Místo `REM`můžete použít jednoduchou uvozovku (`'`).</span><span class="sxs-lookup"><span data-stu-id="c4237-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="c4237-114">To platí bez ohledu na to, jestli váš komentář následuje za jiným příkazem na stejném řádku, nebo se nachází na řádku samostatně.</span><span class="sxs-lookup"><span data-stu-id="c4237-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4237-115">Příkaz `REM` nelze pokračovat pomocí posloupnosti pokračování řádku (`_`).</span><span class="sxs-lookup"><span data-stu-id="c4237-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="c4237-116">Po zahájení komentáře kompilátor neověřuje znaky pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="c4237-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="c4237-117">Pro Víceřádkový komentář použijte jiný příkaz `REM` nebo symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="c4237-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4237-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4237-118">Example</span></span>  
 <span data-ttu-id="c4237-119">Následující příklad znázorňuje příkaz `REM`, který se používá k zahrnutí vysvětlujících poznámek do programu.</span><span class="sxs-lookup"><span data-stu-id="c4237-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="c4237-120">Také ukazuje alternativu použití jednoduchého znaku pro uvozovky (`'`) místo `REM`.</span><span class="sxs-lookup"><span data-stu-id="c4237-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c4237-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4237-121">See also</span></span>

- [<span data-ttu-id="c4237-122">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="c4237-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="c4237-123">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="c4237-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
