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
ms.openlocfilehash: c8d851afc33e7e898ab16abc941d8680f74145e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398302"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="72d30-102">Struktura programu a pravidla týkající se kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72d30-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="72d30-103">Tato část zavádí typickou strukturu Visual Basic programu, poskytuje jednoduchý Visual Basic program "Hello, World" a popisuje Visual Basic konvence kódu.</span><span class="sxs-lookup"><span data-stu-id="72d30-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="72d30-104">Konvence kódu jsou návrhy, které se zaměřují na logiku programu, ale na jeho fyzickou strukturu a vzhled.</span><span class="sxs-lookup"><span data-stu-id="72d30-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="72d30-105">Po nich je váš kód snazší číst, pochopit a udržovat.</span><span class="sxs-lookup"><span data-stu-id="72d30-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="72d30-106">Konvence kódu můžou zahrnovat mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="72d30-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="72d30-107">Standardizované formáty pro označování popisků a kódu pro komentáře</span><span class="sxs-lookup"><span data-stu-id="72d30-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="72d30-108">Pokyny pro mezery, formátování a odsazení kódu.</span><span class="sxs-lookup"><span data-stu-id="72d30-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="72d30-109">Zásady vytváření názvů pro objekty, proměnné a procedury.</span><span class="sxs-lookup"><span data-stu-id="72d30-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="72d30-110">Následující témata obsahují sadu pokynů pro programování pro Visual Basic programy spolu s příklady dobrého využití.</span><span class="sxs-lookup"><span data-stu-id="72d30-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72d30-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="72d30-111">In This Section</span></span>  
 [<span data-ttu-id="72d30-112">Struktura programu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72d30-112">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="72d30-113">Poskytuje přehled prvků, které tvoří Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="72d30-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="72d30-114">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72d30-114">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="72d30-115">Popisuje postup, který slouží jako výchozí bod a celkový ovládací prvek pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72d30-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="72d30-116">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="72d30-116">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="72d30-117">Popisuje, jak odkazovat na objekty v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="72d30-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="72d30-118">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72d30-118">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="72d30-119">Popisuje, jak obory názvů organizují objekty v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="72d30-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="72d30-120">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72d30-120">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="72d30-121">Obsahuje obecné pokyny pro názvové procedury, konstanty, proměnné, argumenty a objekty.</span><span class="sxs-lookup"><span data-stu-id="72d30-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="72d30-122">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="72d30-122">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="72d30-123">Kontroluje pokyny používané při vývoji ukázek v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="72d30-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="72d30-124">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="72d30-124">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="72d30-125">Popisuje, jak selektivně zkompilovat konkrétní bloky kódu při směrování kompilátoru tak, aby ignoroval jiné.</span><span class="sxs-lookup"><span data-stu-id="72d30-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="72d30-126">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-126">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="72d30-127">Ukazuje, jak rozdělit dlouhé příkazy na více řádků a kombinovat krátké příkazy na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="72d30-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="72d30-128">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-128">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="72d30-129">Ukazuje, jak sbalit a skrýt části kódu v editoru kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72d30-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="72d30-130">Postupy: Vytváření popisků příkazů</span><span class="sxs-lookup"><span data-stu-id="72d30-130">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="72d30-131">Ukazuje, jak označit řádek kódu k identifikaci pro použití s příkazy, jako je například `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="72d30-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="72d30-132">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-132">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="72d30-133">Ukazuje, jak a kde používat nečíselné a neabecední znaky.</span><span class="sxs-lookup"><span data-stu-id="72d30-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="72d30-134">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-134">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="72d30-135">Popisuje, jak přidat do kódu popisné komentáře.</span><span class="sxs-lookup"><span data-stu-id="72d30-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="72d30-136">Klíčová slova jako názvy elementů v kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-136">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="72d30-137">Popisuje, jak použít hranaté závorky ( `[]` ) k oddělování názvů proměnných, které jsou také Visual Basic klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="72d30-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="72d30-138">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="72d30-138">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="72d30-139">Popisuje různé způsoby, jak odkazovat na prvky Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="72d30-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="72d30-140">Omezení jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72d30-140">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="72d30-141">Popisuje odebrání známých omezení kódování v rámci Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72d30-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="72d30-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="72d30-142">Related Sections</span></span>  
 [<span data-ttu-id="72d30-143">Typografická pravidla a pravidla vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-143">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="72d30-144">Poskytuje standardní konvence kódování pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72d30-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="72d30-145">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="72d30-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="72d30-146">Popisuje funkce, které usnadňují zápis a správu kódu.</span><span class="sxs-lookup"><span data-stu-id="72d30-146">Describes features that make it easier for you to write and manage your code.</span></span>
