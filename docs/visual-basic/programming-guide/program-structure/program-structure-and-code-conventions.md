---
title: Struktura programu a pravidla týkající se kódu
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: bacd532361de18936bac96c631f7f7247246b1de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347289"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="ba219-102">Struktura programu a pravidla týkající se kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba219-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="ba219-103">Tato část zavádí typickou strukturu Visual Basic programu, poskytuje jednoduchý Visual Basic program "Hello, World" a popisuje Visual Basic konvence kódu.</span><span class="sxs-lookup"><span data-stu-id="ba219-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="ba219-104">Konvence kódu jsou návrhy, které se zaměřují na logiku programu, ale na jeho fyzickou strukturu a vzhled.</span><span class="sxs-lookup"><span data-stu-id="ba219-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="ba219-105">Po nich je váš kód snazší číst, pochopit a udržovat.</span><span class="sxs-lookup"><span data-stu-id="ba219-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="ba219-106">Konvence kódu můžou zahrnovat mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="ba219-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="ba219-107">Standardizované formáty pro označování popisků a kódu pro komentáře</span><span class="sxs-lookup"><span data-stu-id="ba219-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="ba219-108">Pokyny pro mezery, formátování a odsazení kódu.</span><span class="sxs-lookup"><span data-stu-id="ba219-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="ba219-109">Zásady vytváření názvů pro objekty, proměnné a procedury.</span><span class="sxs-lookup"><span data-stu-id="ba219-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="ba219-110">Následující témata obsahují sadu pokynů pro programování pro Visual Basic programy spolu s příklady dobrého využití.</span><span class="sxs-lookup"><span data-stu-id="ba219-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba219-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ba219-111">In This Section</span></span>  
 [<span data-ttu-id="ba219-112">Struktura Visual Basic programu</span><span class="sxs-lookup"><span data-stu-id="ba219-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="ba219-113">Poskytuje přehled prvků, které tvoří Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="ba219-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="ba219-114">Hlavní postup v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba219-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="ba219-115">Popisuje postup, který slouží jako výchozí bod a celkový ovládací prvek pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba219-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="ba219-116">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="ba219-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="ba219-117">Popisuje, jak odkazovat na objekty v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="ba219-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="ba219-118">Obory názvů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba219-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="ba219-119">Popisuje, jak obory názvů organizují objekty v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba219-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="ba219-120">Visual Basic konvence pojmenování</span><span class="sxs-lookup"><span data-stu-id="ba219-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="ba219-121">Obsahuje obecné pokyny pro názvové procedury, konstanty, proměnné, argumenty a objekty.</span><span class="sxs-lookup"><span data-stu-id="ba219-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="ba219-122">Visual Basic konvence kódování</span><span class="sxs-lookup"><span data-stu-id="ba219-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="ba219-123">Kontroluje pokyny používané při vývoji ukázek v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="ba219-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="ba219-124">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="ba219-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="ba219-125">Popisuje, jak selektivně zkompilovat konkrétní bloky kódu při směrování kompilátoru tak, aby ignoroval jiné.</span><span class="sxs-lookup"><span data-stu-id="ba219-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="ba219-126">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="ba219-127">Ukazuje, jak rozdělit dlouhé příkazy na více řádků a kombinovat krátké příkazy na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="ba219-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="ba219-128">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="ba219-129">Ukazuje, jak sbalit a skrýt části kódu v editoru kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba219-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="ba219-130">Postupy: Vytváření popisků příkazů</span><span class="sxs-lookup"><span data-stu-id="ba219-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="ba219-131">Ukazuje, jak označit řádek kódu k identifikaci pro použití s příkazy, jako je například `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="ba219-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="ba219-132">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="ba219-133">Ukazuje, jak a kde používat nečíselné a neabecední znaky.</span><span class="sxs-lookup"><span data-stu-id="ba219-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="ba219-134">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="ba219-135">Popisuje, jak přidat do kódu popisné komentáře.</span><span class="sxs-lookup"><span data-stu-id="ba219-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="ba219-136">Klíčová slova jako názvy elementů v kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="ba219-137">Popisuje, jak použít hranaté závorky (`[]`) k oddělování názvů proměnných, které jsou také Visual Basic klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="ba219-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="ba219-138">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="ba219-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="ba219-139">Popisuje různé způsoby, jak odkazovat na prvky Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="ba219-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="ba219-140">Omezení Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba219-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="ba219-141">Popisuje odebrání známých omezení kódování v rámci Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba219-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba219-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ba219-142">Related Sections</span></span>  
 [<span data-ttu-id="ba219-143">Typografická pravidla a pravidla vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="ba219-144">Poskytuje standardní konvence kódování pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba219-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="ba219-145">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="ba219-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="ba219-146">Popisuje funkce, které usnadňují zápis a správu kódu.</span><span class="sxs-lookup"><span data-stu-id="ba219-146">Describes features that make it easier for you to write and manage your code.</span></span>
