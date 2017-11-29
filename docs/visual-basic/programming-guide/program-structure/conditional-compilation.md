---
title: "Podmíněná kompilace v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="430db-102">Podmíněná kompilace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="430db-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="430db-103">V *Podmíněná kompilace*, konkrétní bloky kódu v programu kompilovány selektivně, zatímco další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="430db-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="430db-104">Například můžete chtít zápisu ladění příkazy, které porovnávají rychlosti různý přístup do stejné programovací úlohy, nebo můžete chtít lokalizace aplikace pro více jazyků.</span><span class="sxs-lookup"><span data-stu-id="430db-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="430db-105">Podmíněná kompilace příkazy jsou navrženy pro spuštění při kompilaci, není v době běhu.</span><span class="sxs-lookup"><span data-stu-id="430db-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="430db-106">Označují bloky kódu podmíněně sestavují s `#If...Then...#Else` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="430db-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="430db-107">Například k vytvoření francouzštinu a češtinu jazykové verze stejné aplikace ze stejného zdrojového kódu, vložení kódu pro konkrétní platformu segmentů v `#If...Then` příkazy pomocí předdefinovaných konstanty `FrenchVersion` a `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="430db-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="430db-108">Následující příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="430db-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="430db-109">Pokud nastavíte hodnotu `FrenchVersion` konstanta Podmíněná kompilace pro `True` při kompilaci, kompilace podmíněného kódu pro je francouzská verze.</span><span class="sxs-lookup"><span data-stu-id="430db-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="430db-110">Pokud nastavíte hodnotu `GermanVersion` konstanta, která se `True`, kompilátor použije německé verzi.</span><span class="sxs-lookup"><span data-stu-id="430db-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="430db-111">Pokud ani jeden z nich je nastavený na `True`, kód za posledních `Else` blokovat spuštění.</span><span class="sxs-lookup"><span data-stu-id="430db-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="430db-112">Automatické dokončování není funkce při úpravě code a pomocí direktiv Podmíněná kompilace, pokud kód není součástí aktuální větve.</span><span class="sxs-lookup"><span data-stu-id="430db-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="430db-113">Deklarace konstant Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="430db-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="430db-114">Podmíněná kompilace konstanty můžete nastavit v jednom ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="430db-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="430db-115">V **Návrhář projektu**</span><span class="sxs-lookup"><span data-stu-id="430db-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="430db-116">Na příkazovém řádku při použití příkazového řádku kompilátoru</span><span class="sxs-lookup"><span data-stu-id="430db-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="430db-117">V kódu</span><span class="sxs-lookup"><span data-stu-id="430db-117">In your code</span></span>  
  
 <span data-ttu-id="430db-118">Podmíněná kompilace konstanty mít speciální obor a nelze získat přístup z standardní kódu.</span><span class="sxs-lookup"><span data-stu-id="430db-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="430db-119">Rozsah konstanta Podmíněná kompilace je závislé na způsobu, jakým je nastavena.</span><span class="sxs-lookup"><span data-stu-id="430db-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="430db-120">Následující tabulka uvádí oboru konstanty deklarováno s použitím každého ze tří způsobů uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="430db-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="430db-121">Nastavení konstanta</span><span class="sxs-lookup"><span data-stu-id="430db-121">How constant is set</span></span>|<span data-ttu-id="430db-122">Rozsah konstanta</span><span class="sxs-lookup"><span data-stu-id="430db-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="430db-123">**Návrhář projektu**</span><span class="sxs-lookup"><span data-stu-id="430db-123">**Project Designer**</span></span>|<span data-ttu-id="430db-124">Veřejné pro všechny soubory v projektu</span><span class="sxs-lookup"><span data-stu-id="430db-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="430db-125">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="430db-125">Command line</span></span>|<span data-ttu-id="430db-126">Veřejné ke všem souborům předaný kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="430db-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="430db-127">`#Const`příkaz v kódu</span><span class="sxs-lookup"><span data-stu-id="430db-127">`#Const` statement in code</span></span>|<span data-ttu-id="430db-128">Privátní do souboru, ve kterém je deklarovaná</span><span class="sxs-lookup"><span data-stu-id="430db-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="430db-129">Chcete-li nastavit konstanty v Návrháři projektu</span><span class="sxs-lookup"><span data-stu-id="430db-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="430db-130">-Před vytvořením spustitelný soubor, nastavte konstanty **Návrhář projektu** podle kroků uvedených v [vlastností Správa projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="430db-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="430db-131">Chcete-li nastavit konstanty na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="430db-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="430db-132">-Použít **/d** přepínač tak, aby zadejte Podmíněná kompilace konstanty, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="430db-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="430db-133">Je vyžadován mezi žádné místo **/d** přepínač a první konstanta.</span><span class="sxs-lookup"><span data-stu-id="430db-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="430db-134">Další informace najdete v tématu [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="430db-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="430db-135">Příkazového řádku deklarace přepsání deklarace zadané v **Návrhář projektu**, ale není z nich vymazat obsah.</span><span class="sxs-lookup"><span data-stu-id="430db-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="430db-136">Argumenty nastavit **Návrhář projektu** zůstávají platná pro následné kompilace.</span><span class="sxs-lookup"><span data-stu-id="430db-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="430db-137">Při zápisu konstanty v samotný kód, nejsou vzhledem k tomu, že jejich obor je celý modul, ve které jsou deklarované žádná striktní pravidla, jejich umístění.</span><span class="sxs-lookup"><span data-stu-id="430db-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="430db-138">Chcete-li nastavit konstanty v kódu</span><span class="sxs-lookup"><span data-stu-id="430db-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="430db-139">-Umístíte konstanty v bloku deklarace modulu, ve kterém se používají.</span><span class="sxs-lookup"><span data-stu-id="430db-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="430db-140">To pomáhá chránit váš kód uspořádány snadněji číst.</span><span class="sxs-lookup"><span data-stu-id="430db-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="430db-141">Související témata</span><span class="sxs-lookup"><span data-stu-id="430db-141">Related Topics</span></span>  
  
|<span data-ttu-id="430db-142">Název</span><span class="sxs-lookup"><span data-stu-id="430db-142">Title</span></span>|<span data-ttu-id="430db-143">Popis</span><span class="sxs-lookup"><span data-stu-id="430db-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="430db-144">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="430db-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="430db-145">Poskytuje doporučení pro snadné číst a spravovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="430db-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="430db-146">Odkaz</span><span class="sxs-lookup"><span data-stu-id="430db-146">Reference</span></span>  
 [<span data-ttu-id="430db-147">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="430db-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="430db-148">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="430db-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="430db-149">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="430db-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
