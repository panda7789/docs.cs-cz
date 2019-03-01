---
title: Komentáře v kódu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 19cd2dbaa055ab6e927ef1ddc9623723ea8c5f2f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977497"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="894da-102">Komentáře v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="894da-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="894da-103">Při prohlížení příklady kódu, můžete často narazit na symbol komentáře (`'`).</span><span class="sxs-lookup"><span data-stu-id="894da-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="894da-104">Tento symbol instruuje kompilátor jazyka Visual Basic, aby ignoroval text ním následuje nebo *komentář*.</span><span class="sxs-lookup"><span data-stu-id="894da-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="894da-105">Komentáře jsou stručné vysvětlivky doplněné do kódu kvůli lepší orientaci těch, kteří si ho prohlížejí.</span><span class="sxs-lookup"><span data-stu-id="894da-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="894da-106">Při programování je dobrým zvykem začínat všechny procedury stručným komentářem, který popisuje funkční charakteristiky procedury (co dělá).</span><span class="sxs-lookup"><span data-stu-id="894da-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="894da-107">Budete z toho mít prospěch jak vy, tak všichni ostatní, kteří tento kód prověřují.</span><span class="sxs-lookup"><span data-stu-id="894da-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="894da-108">Podrobnosti implementace (jak to procedura dělá) byste měli oddělit od komentářů, které popisují funkční charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="894da-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="894da-109">Pokud do popisu zahrnete podrobnosti implementace, při úpravě funkce je nezapomeňte aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="894da-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="894da-110">Komentáře mohou následovat za příkazem na stejném řádku, nebo obsazovat celý řádek.</span><span class="sxs-lookup"><span data-stu-id="894da-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="894da-111">Obě varianty jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="894da-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="894da-112">Pokud komentář vyžaduje více než jeden řádek, použijte symbol komentáře na každém řádku, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="894da-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="894da-113">Pokyny ke komentování</span><span class="sxs-lookup"><span data-stu-id="894da-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="894da-114">Následující tabulka obsahuje obecné pokyny k tomu, jaké typy komentářů mohou být před kódem.</span><span class="sxs-lookup"><span data-stu-id="894da-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="894da-115">Jsou to pouze návrhy; Visual Basic nevynucuje pravidla pro přidávání komentářů.</span><span class="sxs-lookup"><span data-stu-id="894da-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="894da-116">Napište všechno, co má význam pro vás i pro kohokoli jiného, kdo si váš kód bude prohlížet.</span><span class="sxs-lookup"><span data-stu-id="894da-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="894da-117">Typ komentáře</span><span class="sxs-lookup"><span data-stu-id="894da-117">Comment type</span></span>|<span data-ttu-id="894da-118">Popis komentáře</span><span class="sxs-lookup"><span data-stu-id="894da-118">Comment description</span></span>|  
|<span data-ttu-id="894da-119">Účel</span><span class="sxs-lookup"><span data-stu-id="894da-119">Purpose</span></span>|<span data-ttu-id="894da-120">Popisuje, co procedura dělá (ne jak to dělá).</span><span class="sxs-lookup"><span data-stu-id="894da-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="894da-121">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="894da-121">Assumptions</span></span>|<span data-ttu-id="894da-122">Uvádí všechny externí proměnné, ovládací prvky, otevřené soubory nebo jiné prvky, ke kterým procedura přistupuje.</span><span class="sxs-lookup"><span data-stu-id="894da-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="894da-123">Účinek</span><span class="sxs-lookup"><span data-stu-id="894da-123">Effects</span></span>|<span data-ttu-id="894da-124">Uvádí všechny ovlivněné externí proměnné, ovládací prvky nebo soubory a účinek, který má (pouze pokud to není zřejmé).</span><span class="sxs-lookup"><span data-stu-id="894da-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="894da-125">Vstupy</span><span class="sxs-lookup"><span data-stu-id="894da-125">Inputs</span></span>|<span data-ttu-id="894da-126">Určuje účel argumentu.</span><span class="sxs-lookup"><span data-stu-id="894da-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="894da-127">Vrací</span><span class="sxs-lookup"><span data-stu-id="894da-127">Returns</span></span>|<span data-ttu-id="894da-128">Vysvětluje hodnoty vrácené procedurou.</span><span class="sxs-lookup"><span data-stu-id="894da-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="894da-129">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="894da-129">Remember the following points:</span></span>  
  
-   <span data-ttu-id="894da-130">Každou deklaraci důležité proměnné by měl předcházet komentář popisující použití této deklarované proměnné.</span><span class="sxs-lookup"><span data-stu-id="894da-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="894da-131">Proměnné, ovládací prvky a procedury by měly být pojmenovány dostatečně výstižně, aby byly komentáře zapotřebí pouze pro složité podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="894da-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="894da-132">Komentáře nemohou následovat za posloupností pokračování řádku na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="894da-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="894da-133">Můžete přidat nebo odebrat symboly komentáře bloku kódu tak, že vyberete jeden nebo více řádků kódu a zvolíte **komentář** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) a **zrušit komentář** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) tlačítka **upravit**  nástrojů.</span><span class="sxs-lookup"><span data-stu-id="894da-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="894da-134">Můžete také přidat komentáře do kódu tak, že text uvodíte `REM` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="894da-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="894da-135">Ale `'` symbolů a **komentář**/**zrušit komentář** tlačítka jsou snadněji používají a vyžadují méně místa a paměti.</span><span class="sxs-lookup"><span data-stu-id="894da-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894da-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="894da-136">See also</span></span>
- [<span data-ttu-id="894da-137">Dokumentace kódu pomocí komentářů XML</span><span class="sxs-lookup"><span data-stu-id="894da-137">Documenting Your Code With XML Comments</span></span>](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [<span data-ttu-id="894da-138">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="894da-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="894da-139">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="894da-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="894da-140">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="894da-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="894da-141">Příkaz REM</span><span class="sxs-lookup"><span data-stu-id="894da-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
