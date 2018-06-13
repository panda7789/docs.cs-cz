---
title: Struktura programu a pravidla týkající se kódu (Visual Basic)
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
ms.openlocfilehash: b79e339ebe81a7228a02837e5c0c23c80a8132e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654939"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="2aebb-102">Struktura programu a pravidla týkající se kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2aebb-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="2aebb-103">Tato část představuje typické struktura programu jazyka Visual Basic, poskytuje jednoduché programu jazyka Visual Basic, "Hello, World" a popisuje pravidla týkající se kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2aebb-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="2aebb-104">Pravidla týkající se kódu jsou návrhy, které soustředit není na programu logiku, ale na její fyzickou strukturu a vzhled.</span><span class="sxs-lookup"><span data-stu-id="2aebb-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="2aebb-105">Následující je snazší kódu pro čtení, pochopit a údržbu.</span><span class="sxs-lookup"><span data-stu-id="2aebb-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="2aebb-106">Pravidla týkající se kódu mohou zahrnovat mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="2aebb-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="2aebb-107">Standardizovaná formátech pro označování a komentářů kódu.</span><span class="sxs-lookup"><span data-stu-id="2aebb-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="2aebb-108">Pokyny pro mezery, formátování a odsazení kódu.</span><span class="sxs-lookup"><span data-stu-id="2aebb-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="2aebb-109">Zásady vytváření názvů pro objekty, proměnné a postupy.</span><span class="sxs-lookup"><span data-stu-id="2aebb-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="2aebb-110">Následující témata poskytují sadu programovací pokyny pro programy Visual Basic, společně s příklady dobrý využití.</span><span class="sxs-lookup"><span data-stu-id="2aebb-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2aebb-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2aebb-111">In This Section</span></span>  
 [<span data-ttu-id="2aebb-112">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aebb-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="2aebb-113">Obsahuje přehled prvků, které tvoří programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2aebb-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="2aebb-114">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aebb-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="2aebb-115">Popisuje postup, který slouží jako počáteční bod a celkové řízení pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="2aebb-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="2aebb-116">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="2aebb-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="2aebb-117">Popisuje, jak odkazovat na objekty v jiných sestavení.</span><span class="sxs-lookup"><span data-stu-id="2aebb-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="2aebb-118">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aebb-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="2aebb-119">Popisuje, jak obory názvů uspořádání objektů v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="2aebb-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="2aebb-120">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aebb-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="2aebb-121">Obsahuje obecné pokyny pro pojmenování procedury, konstanty, proměnné, argumentů a objekty.</span><span class="sxs-lookup"><span data-stu-id="2aebb-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="2aebb-122">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="2aebb-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="2aebb-123">Zkontroluje pokyny použité při vývoji ukázky v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="2aebb-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="2aebb-124">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="2aebb-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="2aebb-125">Popisuje, jak selektivně zkompilovat konkrétní bloky kódu při řízení kompilátoru ostatní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="2aebb-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="2aebb-126">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="2aebb-127">Ukazuje, jak k rozdělení dlouhých příkazů do více řádků a kombinace příkazů krátký na jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="2aebb-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="2aebb-128">Postupy: Sbalení a skrytí sekcí kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="2aebb-129">Ukazuje, jak sbalení a skrytí sekcí kódu v jazyce Visual Basic editor kódu.</span><span class="sxs-lookup"><span data-stu-id="2aebb-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="2aebb-130">Postupy: Vytváření popisků příkazů</span><span class="sxs-lookup"><span data-stu-id="2aebb-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="2aebb-131">Ukazuje, jak označit řádek kódu pro jeho rozpoznání pro použití s příkazy, jako `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="2aebb-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="2aebb-132">Speciální znaky v kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="2aebb-133">Popisuje, jak a kde chcete použít jiné než číselné a neabecední znaky.</span><span class="sxs-lookup"><span data-stu-id="2aebb-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="2aebb-134">Komentáře v kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="2aebb-135">Popisuje postup přidání popisný komentáře do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2aebb-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="2aebb-136">Klíčová slova jako názvy elementů v kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="2aebb-137">Popisuje, jak použít závorky (`[]`) a tím vymezit názvy proměnných, které jsou také Visual Basic – klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="2aebb-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="2aebb-138">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="2aebb-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="2aebb-139">Popisuje různé způsoby, jak odkazovat na elementy programu v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2aebb-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="2aebb-140">Omezení jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aebb-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="2aebb-141">Popisuje odebrání známé omezení kódování v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2aebb-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2aebb-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2aebb-142">Related Sections</span></span>  
 [<span data-ttu-id="2aebb-143">Typografická pravidla a pravidla vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="2aebb-144">Poskytuje standardní konvence psaní kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2aebb-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="2aebb-145">Psaní kódu</span><span class="sxs-lookup"><span data-stu-id="2aebb-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="2aebb-146">Popisuje funkce, které usnadňují můžete zapsat a spravovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="2aebb-146">Describes features that make it easier for you to write and manage your code.</span></span>
