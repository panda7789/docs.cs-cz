---
title: Podmíněná kompilace v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 4698435cb2ab15d16d8a8a898a01a9ffbc4f69c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639813"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="a1544-102">Podmíněná kompilace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1544-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="a1544-103">V *podmíněné kompilace*, konkrétní bloky kódu v programu v jazyce jsou selektivně zkompilován, zatímco jiné jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="a1544-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="a1544-104">Například můžete chtít napsat ladění příkazů, které porovnat rychlost různé přístupy k stejné programovací úlohy, nebo může být vhodné lokalizovat aplikaci pro více jazyků.</span><span class="sxs-lookup"><span data-stu-id="a1544-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="a1544-105">Příkazy podmíněné kompilace jsou navrženy ke spouštění během kompilace, ne za běhu.</span><span class="sxs-lookup"><span data-stu-id="a1544-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="a1544-106">Označení bloky kódu, který se podmíněně kompilována s `#If...Then...#Else` směrnice.</span><span class="sxs-lookup"><span data-stu-id="a1544-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="a1544-107">Například vytvořit francouzština a němčina jazykové verze stejné aplikace ze stejného zdrojového kódu, vložení příslušných segmentech kódu specifické pro platformu v `#If...Then` příkazy pomocí předdefinovaných konstant `FrenchVersion` a `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="a1544-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="a1544-108">Následující příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="a1544-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a1544-109">Pokud nastavíte hodnotu `FrenchVersion` Konstanta podmíněné kompilace do `True` v době kompilace, je zkompilován podmíněný kód pro francouzské verze.</span><span class="sxs-lookup"><span data-stu-id="a1544-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="a1544-110">Pokud nastavíte hodnotu `GermanVersion` konstanta, která se `True`, kterou kompilátor používá německé verzi.</span><span class="sxs-lookup"><span data-stu-id="a1544-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="a1544-111">Pokud ani jedno je nastavená na `True`, kód za posledních `Else` blok.</span><span class="sxs-lookup"><span data-stu-id="a1544-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1544-112">Automatického doplňování se nebude fungovat při úpravách kódu a pomocí direktivy podmíněné kompilace, pokud kód není součástí aktuální větve.</span><span class="sxs-lookup"><span data-stu-id="a1544-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="a1544-113">Deklarace konstanty pro podmíněnou kompilaci</span><span class="sxs-lookup"><span data-stu-id="a1544-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="a1544-114">Konstanty pro podmíněnou kompilaci můžete nastavit v jednom ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="a1544-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="a1544-115">V **Návrhář projektu**</span><span class="sxs-lookup"><span data-stu-id="a1544-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="a1544-116">Na příkazovém řádku při použití kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a1544-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="a1544-117">V kódu</span><span class="sxs-lookup"><span data-stu-id="a1544-117">In your code</span></span>  
  
 <span data-ttu-id="a1544-118">Konstanty pro podmíněnou kompilaci mají zvláštní obor a nelze přistupovat z standardní kód.</span><span class="sxs-lookup"><span data-stu-id="a1544-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="a1544-119">Rozsah Konstanta podmíněné kompilace je závislé na způsobu, jakým je nastavena.</span><span class="sxs-lookup"><span data-stu-id="a1544-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="a1544-120">V následující tabulce jsou uvedeny oboru konstanty, které jsou deklarovány pomocí každé ze tří způsobů uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="a1544-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="a1544-121">Jak nastavit – konstanta</span><span class="sxs-lookup"><span data-stu-id="a1544-121">How constant is set</span></span>|<span data-ttu-id="a1544-122">Obor – konstanta</span><span class="sxs-lookup"><span data-stu-id="a1544-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="a1544-123">**Project Designer**</span><span class="sxs-lookup"><span data-stu-id="a1544-123">**Project Designer**</span></span>|<span data-ttu-id="a1544-124">Veřejné na všechny soubory v projektu</span><span class="sxs-lookup"><span data-stu-id="a1544-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="a1544-125">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="a1544-125">Command line</span></span>|<span data-ttu-id="a1544-126">Veřejné na všechny soubory, které jsou předány kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a1544-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="a1544-127">`#Const` příkaz v kódu</span><span class="sxs-lookup"><span data-stu-id="a1544-127">`#Const` statement in code</span></span>|<span data-ttu-id="a1544-128">Soukromé vzhledem k souboru, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="a1544-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="a1544-129">Chcete-li nastavit konstanty v Návrháři projektu</span><span class="sxs-lookup"><span data-stu-id="a1544-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="a1544-130">-Před vytvořením spustitelného souboru, nastavte konstanty **Návrháře projektu** podle postupu uvedeného v [vlastností správy projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="a1544-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="a1544-131">Chcete-li nastavit konstanty na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="a1544-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="a1544-132">– Použijte **/d** přepínač tak, aby zadejte konstanty pro podmíněnou kompilaci, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a1544-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="a1544-133">Mezera není je vyžadován mezi **/d** přepínače a první konstanta.</span><span class="sxs-lookup"><span data-stu-id="a1544-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="a1544-134">Další informace najdete v tématu [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="a1544-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="a1544-135">Příkazového řádku deklarace přepsání zadaná v deklaracích **Návrháře projektu**, ale ne z nich vymazat obsah.</span><span class="sxs-lookup"><span data-stu-id="a1544-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="a1544-136">Argumenty nastavit **Návrháře projektu** zůstávají v platnosti pro následné kompilace.</span><span class="sxs-lookup"><span data-stu-id="a1544-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="a1544-137">Při zápisu konstanty v samotný kód, nejsou žádná pravidla striktní jde o jejich umístění, protože jejich oboru je celý modul, ve kterém jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="a1544-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="a1544-138">Chcete-li nastavit konstanty v kódu</span><span class="sxs-lookup"><span data-stu-id="a1544-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="a1544-139">-Umístíte konstanty v bloku deklaraci modulu, ve kterém jsou použity.</span><span class="sxs-lookup"><span data-stu-id="a1544-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="a1544-140">Díky tomu váš kód uspořádané a snadněji čitelné.</span><span class="sxs-lookup"><span data-stu-id="a1544-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="a1544-141">Související témata</span><span class="sxs-lookup"><span data-stu-id="a1544-141">Related Topics</span></span>  
  
|<span data-ttu-id="a1544-142">Název</span><span class="sxs-lookup"><span data-stu-id="a1544-142">Title</span></span>|<span data-ttu-id="a1544-143">Popis</span><span class="sxs-lookup"><span data-stu-id="a1544-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="a1544-144">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="a1544-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="a1544-145">Nabízí návrhy pro snadné čtení a udržovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="a1544-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="a1544-146">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a1544-146">Reference</span></span>  
 [<span data-ttu-id="a1544-147">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="a1544-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="a1544-148">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="a1544-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="a1544-149">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1544-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
