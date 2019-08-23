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
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957761"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="2fb50-102">REM – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fb50-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="2fb50-103">Slouží k zahrnutí vysvětlujících poznámek do zdrojového kódu programu.</span><span class="sxs-lookup"><span data-stu-id="2fb50-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fb50-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="2fb50-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2fb50-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="2fb50-106">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="2fb50-106">Optional.</span></span> <span data-ttu-id="2fb50-107">Text libovolného komentáře, který chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="2fb50-107">The text of any comment you want to include.</span></span> <span data-ttu-id="2fb50-108">Mezi `REM` klíčovým slovem and `comment`se vyžaduje mezera.</span><span class="sxs-lookup"><span data-stu-id="2fb50-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb50-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fb50-109">Remarks</span></span>  
 <span data-ttu-id="2fb50-110">`REM` Příkaz můžete umístit samostatně na řádek nebo ho můžete umístit na řádek za jiným příkazem.</span><span class="sxs-lookup"><span data-stu-id="2fb50-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="2fb50-111">`REM` Příkaz musí být poslední příkaz na řádku.</span><span class="sxs-lookup"><span data-stu-id="2fb50-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="2fb50-112">Pokud má jiný příkaz, `REM` musí být oddělen od tohoto příkazu mezerou.</span><span class="sxs-lookup"><span data-stu-id="2fb50-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="2fb50-113">Místo příkazu můžete použít jednoduchou uvozovku (`'`). `REM`</span><span class="sxs-lookup"><span data-stu-id="2fb50-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="2fb50-114">To platí bez ohledu na to, jestli váš komentář následuje za jiným příkazem na stejném řádku, nebo se nachází na řádku samostatně.</span><span class="sxs-lookup"><span data-stu-id="2fb50-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb50-115">Nelze pokračovat `REM` příkazem pomocí sekvence řádků pokračování řádku (`_`).</span><span class="sxs-lookup"><span data-stu-id="2fb50-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="2fb50-116">Po zahájení komentáře kompilátor neověřuje znaky pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="2fb50-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="2fb50-117">Pro Víceřádkový komentář použijte jiný `REM` příkaz nebo symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="2fb50-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fb50-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fb50-118">Example</span></span>  
 <span data-ttu-id="2fb50-119">Následující příklad ukazuje `REM` příkaz, který se používá k zahrnutí vysvětlujících poznámek do programu.</span><span class="sxs-lookup"><span data-stu-id="2fb50-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="2fb50-120">Také ukazuje alternativu použití jednoduchého znaku uvozovek (`'`) `REM`místo.</span><span class="sxs-lookup"><span data-stu-id="2fb50-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2fb50-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fb50-121">See also</span></span>

- [<span data-ttu-id="2fb50-122">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="2fb50-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="2fb50-123">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="2fb50-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
