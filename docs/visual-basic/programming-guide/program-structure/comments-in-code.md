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
ms.openlocfilehash: 4486b5be42f4a356b2017fe8629bc96f6ad47eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650966"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="e9bd7-102">Komentáře v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9bd7-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="e9bd7-103">Při čtení ukázky kódu, často narazíte na symbol komentáře (`'`).</span><span class="sxs-lookup"><span data-stu-id="e9bd7-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="e9bd7-104">Tento symbol informuje Visual Basic – kompilátor ignorovat, následující text nebo *komentář*.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="e9bd7-105">Komentáře jsou stručné vysvětlivky doplněné do kódu kvůli lepší orientaci těch, kteří si ho prohlížejí.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="e9bd7-106">Při programování je dobrým zvykem začínat všechny procedury stručným komentářem, který popisuje funkční charakteristiky procedury (co dělá).</span><span class="sxs-lookup"><span data-stu-id="e9bd7-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="e9bd7-107">Budete z toho mít prospěch jak vy, tak všichni ostatní, kteří tento kód prověřují.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="e9bd7-108">Podrobnosti implementace (jak to procedura dělá) byste měli oddělit od komentářů, které popisují funkční charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="e9bd7-109">Pokud do popisu zahrnete podrobnosti implementace, při úpravě funkce je nezapomeňte aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="e9bd7-110">Komentáře mohou následovat za příkazem na stejném řádku, nebo obsazovat celý řádek.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="e9bd7-111">Obě varianty jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 <span data-ttu-id="e9bd7-112">Pokud komentář vyžaduje více než jeden řádek, použijte symbol komentáře na každém řádku, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="e9bd7-113">Pokyny ke komentování</span><span class="sxs-lookup"><span data-stu-id="e9bd7-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="e9bd7-114">Následující tabulka obsahuje obecné pokyny k tomu, jaké typy komentářů mohou být před kódem.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="e9bd7-115">Jedná se o návrhy; Visual Basic nedokáže vynutit pravidla pro přidávání komentářů.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="e9bd7-116">Napište všechno, co má význam pro vás i pro kohokoli jiného, kdo si váš kód bude prohlížet.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="e9bd7-117">Typ komentáře</span><span class="sxs-lookup"><span data-stu-id="e9bd7-117">Comment type</span></span>|<span data-ttu-id="e9bd7-118">Popis komentáře</span><span class="sxs-lookup"><span data-stu-id="e9bd7-118">Comment description</span></span>|  
|<span data-ttu-id="e9bd7-119">Účel</span><span class="sxs-lookup"><span data-stu-id="e9bd7-119">Purpose</span></span>|<span data-ttu-id="e9bd7-120">Popisuje, co procedura dělá (ne jak to dělá).</span><span class="sxs-lookup"><span data-stu-id="e9bd7-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="e9bd7-121">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="e9bd7-121">Assumptions</span></span>|<span data-ttu-id="e9bd7-122">Uvádí všechny externí proměnné, ovládací prvky, otevřené soubory nebo jiné prvky, ke kterým procedura přistupuje.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="e9bd7-123">Účinek</span><span class="sxs-lookup"><span data-stu-id="e9bd7-123">Effects</span></span>|<span data-ttu-id="e9bd7-124">Uvádí všechny ovlivněné externí proměnné, ovládací prvky nebo soubory a účinek, který má (pouze pokud to není zřejmé).</span><span class="sxs-lookup"><span data-stu-id="e9bd7-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="e9bd7-125">Vstupy</span><span class="sxs-lookup"><span data-stu-id="e9bd7-125">Inputs</span></span>|<span data-ttu-id="e9bd7-126">Určuje účel argumentu.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="e9bd7-127">Vrací</span><span class="sxs-lookup"><span data-stu-id="e9bd7-127">Returns</span></span>|<span data-ttu-id="e9bd7-128">Vysvětluje hodnoty vrácené procedurou.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="e9bd7-129">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="e9bd7-129">Remember the following points:</span></span>  
  
-   <span data-ttu-id="e9bd7-130">Každou deklaraci důležité proměnné by měl předcházet komentář popisující použití této deklarované proměnné.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="e9bd7-131">Proměnné, ovládací prvky a procedury by měly být pojmenovány dostatečně výstižně, aby byly komentáře zapotřebí pouze pro složité podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="e9bd7-132">Komentáře nemohou následovat za posloupností pokračování řádku na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="e9bd7-133">Můžete přidat nebo odebrat komentář symboly pro blok kódu výběrem jednoho nebo více řádků kódu a zvolením **komentář** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) a **zrušte komentáře u** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) tlačítka na **upravit**  panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9bd7-134">Komentáře můžete také přidat do kódu tak, že před textu pomocí `REM` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="e9bd7-135">Ale `'` symbol a **komentář**/**zrušte komentáře u** tlačítka se snadněji používat a vyžadovat méně místa a paměti.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bd7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9bd7-136">See Also</span></span>  
 [<span data-ttu-id="e9bd7-137">Dokumentace kódu s XML – komentáře</span><span class="sxs-lookup"><span data-stu-id="e9bd7-137">Documenting Your Code With XML Comments</span></span>](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [<span data-ttu-id="e9bd7-138">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="e9bd7-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="e9bd7-139">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e9bd7-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="e9bd7-140">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="e9bd7-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="e9bd7-141">Příkaz REM</span><span class="sxs-lookup"><span data-stu-id="e9bd7-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
