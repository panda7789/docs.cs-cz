---
title: Podmíněná kompilace v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 0767b2054697735c3f5190b6e30a2c80ea5288bc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775705"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="e0ad8-102">Podmíněná kompilace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e0ad8-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="e0ad8-103">V *podmíněné kompilaci*jsou konkrétní bloky kódu v programu kompilovány selektivně, zatímco ostatní jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="e0ad8-104">Například můžete chtít napsat příkazy ladění, které porovnávají rychlost různých přístupů ke stejnému programovacímu úkolu, nebo můžete chtít lokalizovat aplikaci pro více jazyků.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="e0ad8-105">Příkazy podmíněné kompilace jsou navrženy tak, aby běžely v době kompilace, nikoli v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="e0ad8-106">Všimněte si, že bloky kódu budou podmíněně kompilovány pomocí direktivy `#If...Then...#Else`.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="e0ad8-107">Chcete-li například vytvořit francouzsky a německé verze stejné aplikace ze stejného zdrojového kódu, vložte segmenty kódu specifické pro platformu v příkazu `#If...Then` pomocí předdefinovaných konstant `FrenchVersion` a `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="e0ad8-108">Následující příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="e0ad8-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="e0ad8-109">Pokud nastavíte hodnotu `FrenchVersion` konstanty podmíněné kompilace na `True` v době kompilace, bude zkompilován podmíněný kód pro francouzskou verzi.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="e0ad8-110">Pokud nastavíte hodnotu `GermanVersion` konstanty na `True`, kompilátor použije německou verzi.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="e0ad8-111">Pokud není ani nastaveno na `True`, kód v posledním bloku `Else` spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0ad8-112">Automatického dokončování nebude fungovat při úpravách kódu a použití direktiv podmíněné kompilace, pokud kód není součástí aktuální větve.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="e0ad8-113">Deklarace konstant podmíněné kompilace</span><span class="sxs-lookup"><span data-stu-id="e0ad8-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="e0ad8-114">Můžete nastavit konstanty podmíněné kompilace jedním ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="e0ad8-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="e0ad8-115">V **Návrháři projektu**</span><span class="sxs-lookup"><span data-stu-id="e0ad8-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="e0ad8-116">Při použití kompilátoru příkazového řádku na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="e0ad8-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="e0ad8-117">Ve vašem kódu</span><span class="sxs-lookup"><span data-stu-id="e0ad8-117">In your code</span></span>  
  
 <span data-ttu-id="e0ad8-118">Konstanty podmíněné kompilace mají speciální rozsah a nelze k němu přicházet ze standardního kódu.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="e0ad8-119">Rozsah podmíněné kompilační konstanty závisí na způsobu, jakým je nastaven.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="e0ad8-120">V následující tabulce je uveden rozsah konstant deklarovaných pomocí každého ze tří způsobů uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="e0ad8-121">Jak je nastavená konstanta</span><span class="sxs-lookup"><span data-stu-id="e0ad8-121">How constant is set</span></span>|<span data-ttu-id="e0ad8-122">Rozsah konstanty</span><span class="sxs-lookup"><span data-stu-id="e0ad8-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="e0ad8-123">**Návrhář projektu**</span><span class="sxs-lookup"><span data-stu-id="e0ad8-123">**Project Designer**</span></span>|<span data-ttu-id="e0ad8-124">Veřejné pro všechny soubory v projektu</span><span class="sxs-lookup"><span data-stu-id="e0ad8-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="e0ad8-125">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="e0ad8-125">Command line</span></span>|<span data-ttu-id="e0ad8-126">Veřejné ke všem souborům předaným kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e0ad8-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="e0ad8-127">`#Const` – příkaz v kódu</span><span class="sxs-lookup"><span data-stu-id="e0ad8-127">`#Const` statement in code</span></span>|<span data-ttu-id="e0ad8-128">Soukromá k souboru, ve kterém je deklarovaný</span><span class="sxs-lookup"><span data-stu-id="e0ad8-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="e0ad8-129">Nastavení konstant v Návrháři projektu</span><span class="sxs-lookup"><span data-stu-id="e0ad8-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="e0ad8-130">– Před vytvořením spustitelného souboru nastavte konstanty v **Návrháři projektu** podle kroků uvedených v části [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="e0ad8-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="e0ad8-131">Nastavení konstant na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="e0ad8-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="e0ad8-132">– Použijte přepínač **-d** k zadání konstant podmíněné kompilace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e0ad8-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="e0ad8-133">Mezi přepínačem **-d** a první konstantou není nutné žádné místo.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="e0ad8-134">Další informace naleznete v tématu [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="e0ad8-134">For more information, see [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="e0ad8-135">Deklarace příkazového řádku, které jsou popsány v **Návrháři projektu**, však nejsou smazány.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="e0ad8-136">Argumenty nastavené v **Návrháři projektu** zůstávají platné pro následné kompilace.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="e0ad8-137">Při psaní konstant v samotném kódu nejsou k dispozici žádná striktní pravidla pro jejich umístění, protože jejich rozsah je celý modul, ve kterém jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="e0ad8-138">Nastavení konstant v kódu</span><span class="sxs-lookup"><span data-stu-id="e0ad8-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="e0ad8-139">-Vložte konstanty do bloku deklarací modulu, ve kterém jsou použity.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="e0ad8-140">To pomáhá zajistit, aby byl kód uspořádán a čitelnější.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="e0ad8-141">Související témata</span><span class="sxs-lookup"><span data-stu-id="e0ad8-141">Related Topics</span></span>  
  
|<span data-ttu-id="e0ad8-142">Název</span><span class="sxs-lookup"><span data-stu-id="e0ad8-142">Title</span></span>|<span data-ttu-id="e0ad8-143">Popis</span><span class="sxs-lookup"><span data-stu-id="e0ad8-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="e0ad8-144">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="e0ad8-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="e0ad8-145">Poskytuje návrhy, jak snadno číst a udržovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="e0ad8-146">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e0ad8-146">Reference</span></span>  
 [<span data-ttu-id="e0ad8-147">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="e0ad8-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="e0ad8-148">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="e0ad8-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="e0ad8-149">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0ad8-149">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
