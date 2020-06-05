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
ms.openlocfilehash: 68c898145bd8845c657b6ebb8776a3a9027c359c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404262"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="15dda-102">REM – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15dda-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="15dda-103">Slouží k zahrnutí vysvětlujících poznámek do zdrojového kódu programu.</span><span class="sxs-lookup"><span data-stu-id="15dda-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15dda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15dda-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="15dda-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="15dda-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="15dda-106">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="15dda-106">Optional.</span></span> <span data-ttu-id="15dda-107">Text libovolného komentáře, který chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="15dda-107">The text of any comment you want to include.</span></span> <span data-ttu-id="15dda-108">Mezi `REM` klíčovým slovem and se vyžaduje mezera `comment` .</span><span class="sxs-lookup"><span data-stu-id="15dda-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15dda-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15dda-109">Remarks</span></span>  
 <span data-ttu-id="15dda-110">Příkaz můžete umístit `REM` samostatně na řádek nebo ho můžete umístit na řádek za jiným příkazem.</span><span class="sxs-lookup"><span data-stu-id="15dda-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="15dda-111">`REM`Příkaz musí být poslední příkaz na řádku.</span><span class="sxs-lookup"><span data-stu-id="15dda-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="15dda-112">Pokud má jiný příkaz, `REM` musí být oddělen od tohoto příkazu mezerou.</span><span class="sxs-lookup"><span data-stu-id="15dda-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="15dda-113">Místo příkazu můžete použít jednoduchou uvozovku ( `'` ) `REM` .</span><span class="sxs-lookup"><span data-stu-id="15dda-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="15dda-114">To platí bez ohledu na to, jestli váš komentář následuje za jiným příkazem na stejném řádku, nebo se nachází na řádku samostatně.</span><span class="sxs-lookup"><span data-stu-id="15dda-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15dda-115">Nelze pokračovat `REM` příkazem pomocí sekvence řádků pokračování řádku ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="15dda-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="15dda-116">Po zahájení komentáře kompilátor neověřuje znaky pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="15dda-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="15dda-117">Pro Víceřádkový komentář použijte jiný `REM` příkaz nebo symbol komentáře ( `'` ) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="15dda-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15dda-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="15dda-118">Example</span></span>  
 <span data-ttu-id="15dda-119">Následující příklad ukazuje `REM` příkaz, který se používá k zahrnutí vysvětlujících poznámek do programu.</span><span class="sxs-lookup"><span data-stu-id="15dda-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="15dda-120">Také ukazuje alternativu použití jednoduchého znaku uvozovek ( `'` ) místo `REM` .</span><span class="sxs-lookup"><span data-stu-id="15dda-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="15dda-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="15dda-121">See also</span></span>

- [<span data-ttu-id="15dda-122">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="15dda-122">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="15dda-123">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="15dda-123">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
