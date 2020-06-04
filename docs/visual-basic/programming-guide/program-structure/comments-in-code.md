---
title: Komentáře v kódu
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
ms.openlocfilehash: b50e76b8f832c3a214ca54f97bab8b0b6789ac25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403314"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="fcbfe-102">Komentáře v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcbfe-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="fcbfe-103">Při čtení příkladů kódu často narazíte na symbol komentáře ( `'` ).</span><span class="sxs-lookup"><span data-stu-id="fcbfe-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="fcbfe-104">Tento symbol instruuje kompilátor Visual Basic, že má ignorovat text, který následuje, nebo *Komentář*.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="fcbfe-105">Komentáře jsou stručné vysvětlivky doplněné do kódu kvůli lepší orientaci těch, kteří si ho prohlížejí.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="fcbfe-106">Při programování je dobrým zvykem začínat všechny procedury stručným komentářem, který popisuje funkční charakteristiky procedury (co dělá).</span><span class="sxs-lookup"><span data-stu-id="fcbfe-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="fcbfe-107">Budete z toho mít prospěch jak vy, tak všichni ostatní, kteří tento kód prověřují.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="fcbfe-108">Podrobnosti implementace (jak to procedura dělá) byste měli oddělit od komentářů, které popisují funkční charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="fcbfe-109">Pokud do popisu zahrnete podrobnosti implementace, při úpravě funkce je nezapomeňte aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="fcbfe-110">Komentáře mohou následovat za příkazem na stejném řádku, nebo obsazovat celý řádek.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="fcbfe-111">Obě varianty jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="fcbfe-112">Pokud komentář vyžaduje více než jeden řádek, použijte symbol komentáře na každém řádku, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="fcbfe-113">Pokyny ke komentování</span><span class="sxs-lookup"><span data-stu-id="fcbfe-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="fcbfe-114">Následující tabulka obsahuje obecné pokyny k tomu, jaké typy komentářů mohou být před kódem.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="fcbfe-115">Jedná se o návrhy; Visual Basic nevynutila pravidla pro přidávání komentářů.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="fcbfe-116">Napište všechno, co má význam pro vás i pro kohokoli jiného, kdo si váš kód bude prohlížet.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="fcbfe-117">Typ komentáře</span><span class="sxs-lookup"><span data-stu-id="fcbfe-117">Comment type</span></span>|<span data-ttu-id="fcbfe-118">Popis komentáře</span><span class="sxs-lookup"><span data-stu-id="fcbfe-118">Comment description</span></span>|  
|<span data-ttu-id="fcbfe-119">Účel</span><span class="sxs-lookup"><span data-stu-id="fcbfe-119">Purpose</span></span>|<span data-ttu-id="fcbfe-120">Popisuje, co procedura dělá (ne jak to dělá).</span><span class="sxs-lookup"><span data-stu-id="fcbfe-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="fcbfe-121">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="fcbfe-121">Assumptions</span></span>|<span data-ttu-id="fcbfe-122">Uvádí všechny externí proměnné, ovládací prvky, otevřené soubory nebo jiné prvky, ke kterým procedura přistupuje.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="fcbfe-123">Účinek</span><span class="sxs-lookup"><span data-stu-id="fcbfe-123">Effects</span></span>|<span data-ttu-id="fcbfe-124">Uvádí všechny ovlivněné externí proměnné, ovládací prvky nebo soubory a účinek, který má (pouze pokud to není zřejmé).</span><span class="sxs-lookup"><span data-stu-id="fcbfe-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="fcbfe-125">Vstupy</span><span class="sxs-lookup"><span data-stu-id="fcbfe-125">Inputs</span></span>|<span data-ttu-id="fcbfe-126">Určuje účel argumentu.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="fcbfe-127">Návraty</span><span class="sxs-lookup"><span data-stu-id="fcbfe-127">Returns</span></span>|<span data-ttu-id="fcbfe-128">Vysvětluje hodnoty vrácené procedurou.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="fcbfe-129">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="fcbfe-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="fcbfe-130">Každou deklaraci důležité proměnné by měl předcházet komentář popisující použití této deklarované proměnné.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="fcbfe-131">Proměnné, ovládací prvky a procedury by měly být pojmenovány dostatečně výstižně, aby byly komentáře zapotřebí pouze pro složité podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="fcbfe-132">Komentáře nemohou následovat za posloupností pokračování řádku na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="fcbfe-133">Můžete přidat nebo odebrat symboly komentářů pro blok kódu tak, že vyberete jeden nebo více řádků kódu a kliknete na tlačítko **Komentář** ( ![ Visual Basic komentář v sadě Visual Studio. ](./media/comments-in-code/visual-basic-comment-button.gif) ) a zrušit **Komentář** ( ![ Visual Basic tlačítko zrušit komentář v sadě Visual Studio. ](./media/comments-in-code/visual-basic-uncomment-button.gif) ) na panelu nástrojů **Úpravy** .</span><span class="sxs-lookup"><span data-stu-id="fcbfe-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcbfe-134">Komentáře můžete do kódu přidat také tak, že před text vložíte `REM` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="fcbfe-135">Nicméně `'` symbol a tlačítka pro zrušení komentářů k **komentářům** / **Uncomment** je snazší použít a vyžadují méně místa a paměti.</span><span class="sxs-lookup"><span data-stu-id="fcbfe-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbfe-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcbfe-136">See also</span></span>

- [<span data-ttu-id="fcbfe-137">Základní instinkty – dokumentování kódu pomocí komentářů XML</span><span class="sxs-lookup"><span data-stu-id="fcbfe-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="fcbfe-138">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="fcbfe-138">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="fcbfe-139">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="fcbfe-139">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="fcbfe-140">Struktura programu a konvence kódu</span><span class="sxs-lookup"><span data-stu-id="fcbfe-140">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="fcbfe-141">REM – příkaz</span><span class="sxs-lookup"><span data-stu-id="fcbfe-141">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
