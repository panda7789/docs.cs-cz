---
title: Převody kódování C# (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 430cf3f1bc5e0b5ebe1a05530059516f36a473a1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209456"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="3c409-102">Převody kódování C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3c409-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="3c409-103">Konvence kódování slouží k následujícím účelům:</span><span class="sxs-lookup"><span data-stu-id="3c409-103">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="3c409-104">Vytváření konzistentního vzhledu na kód, tak, aby se čtenáři mohli soustředit na obsah ne na rozložení.</span><span class="sxs-lookup"><span data-stu-id="3c409-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="3c409-105">Umožňují uživatelům pochopit kód rychleji odhad na základě předchozích zkušeností.</span><span class="sxs-lookup"><span data-stu-id="3c409-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="3c409-106">Usnadňují kopírování, změna a údržba kódu.</span><span class="sxs-lookup"><span data-stu-id="3c409-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="3c409-107">Vysvětlují, C# osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="3c409-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="3c409-108">Pokyny v tomto tématu se používá společnost Microsoft pro vývoj ukázky a dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3c409-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="3c409-109">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="3c409-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="3c409-110">V krátké příklady, které neobsahují [direktiv using](../../../csharp/language-reference/keywords/using-directive.md), použijte kvalifikaci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3c409-110">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="3c409-111">Pokud víte, že je ve výchozím nastavení v projektu importován oboru názvů, není nutné k plnému určení názvů z daného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3c409-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="3c409-112">Kvalifikované názvy může být přerušeno za tečku (.) Pokud jsou příliš dlouhé pro jeden řádek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3c409-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="3c409-113">Nemusíte změnit názvy objektů, které byly vytvořeny pomocí návrhářské nástroje Visual Studio, aby se daly přizpůsobit další pokyny.</span><span class="sxs-lookup"><span data-stu-id="3c409-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="3c409-114">Konvence rozložení</span><span class="sxs-lookup"><span data-stu-id="3c409-114">Layout Conventions</span></span>  
 <span data-ttu-id="3c409-115">Dobré rozložení používá formátování zvýraznit struktury kódu a aby byl kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="3c409-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="3c409-116">Microsoft příkladů a ukázek splňovat následující konvence:</span><span class="sxs-lookup"><span data-stu-id="3c409-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="3c409-117">Použijte výchozí nastavení editoru kódu (inteligentní odsazení, čtyřmístný odsazení, uložení jako mezery tabulátory).</span><span class="sxs-lookup"><span data-stu-id="3c409-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="3c409-118">Další informace najdete v tématu [možnosti, textový Editor, C#, formátování vzorků](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="3c409-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="3c409-119">Zapište pouze jeden příkaz na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="3c409-119">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="3c409-120">Zapisovat pouze jednu deklaraci na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="3c409-120">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="3c409-121">Pokud nejsou pokračovací řádky automaticky odsazený, odsazení, je o jednu zarážku tabulátoru (čtyři mezery).</span><span class="sxs-lookup"><span data-stu-id="3c409-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="3c409-122">Přidejte alespoň jeden prázdný řádek mezi definice metod a definicích vlastností.</span><span class="sxs-lookup"><span data-stu-id="3c409-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="3c409-123">Chcete-li klauzule ve výrazu je zřejmé, jak je znázorněno v následujícím kódu pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="3c409-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="3c409-124">Konvence při psaní komentářů</span><span class="sxs-lookup"><span data-stu-id="3c409-124">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="3c409-125">Místo komentář na samostatném řádku, není na konci řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="3c409-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="3c409-126">Zahájit text komentáře velkým písmenem.</span><span class="sxs-lookup"><span data-stu-id="3c409-126">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="3c409-127">Ukončit komentář tečkou.</span><span class="sxs-lookup"><span data-stu-id="3c409-127">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="3c409-128">Vložte jednu mezeru mezi oddělovač komentáře (/ /) a text komentáře, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3c409-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="3c409-129">Nevytvářejte hvězdičky z obou stran kolem komentářů formátované bloky.</span><span class="sxs-lookup"><span data-stu-id="3c409-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="3c409-130">Pokyny pro jazyk</span><span class="sxs-lookup"><span data-stu-id="3c409-130">Language Guidelines</span></span>  
 <span data-ttu-id="3c409-131">Následující části popisují postupy, které tým C# následujících pokynů můžete připravit příklady kódu a ukázky.</span><span class="sxs-lookup"><span data-stu-id="3c409-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="3c409-132">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="3c409-132">String Data Type</span></span>  
  
-   <span data-ttu-id="3c409-133">Použití [interpolace](../../language-reference/tokens/interpolated.md) ke zřetězení krátké řetězce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3c409-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="3c409-134">Pro přidání řetězce ve smyčkách, zejména v případě, že pracujete s velkého množství textu, použijte <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="3c409-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="3c409-135">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="3c409-135">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="3c409-136">Použití [implicitního zápisu](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) pro místní proměnné, když je typ proměnné zřejmý z pravé strany přiřazení, nebo pokud přesný typ není důležité.</span><span class="sxs-lookup"><span data-stu-id="3c409-136">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="3c409-137">Nepoužívejte [var](../../../csharp/language-reference/keywords/var.md) když typ není zřejmé z pravé strany přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3c409-137">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="3c409-138">Nespoléhejte na název proměnné k určení typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="3c409-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="3c409-139">Nemusí být správné.</span><span class="sxs-lookup"><span data-stu-id="3c409-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="3c409-140">Nepoužívejte `var` místo [dynamické](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="3c409-140">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="3c409-141">K určení typu proměnné smyčky v použití implicitního zápisu [pro](../../../csharp/language-reference/keywords/for.md) a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="3c409-141">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="3c409-142">Následující příklad používá implicitní psát `for` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3c409-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="3c409-143">Následující příklad používá implicitní psát `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3c409-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="3c409-144">Nepodepsaný datový typ</span><span class="sxs-lookup"><span data-stu-id="3c409-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="3c409-145">Obecně platí, `int` místo typů bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="3c409-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="3c409-146">Použití `int` je běžné v C#, a je jednodušší pracovat s dalšími knihovnami, při použití `int`.</span><span class="sxs-lookup"><span data-stu-id="3c409-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="3c409-147">Pole</span><span class="sxs-lookup"><span data-stu-id="3c409-147">Arrays</span></span>  
  
-   <span data-ttu-id="3c409-148">Pomocí stručnější syntaxe, když inicializujete pole v řádku deklarace.</span><span class="sxs-lookup"><span data-stu-id="3c409-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="3c409-149">Delegáty</span><span class="sxs-lookup"><span data-stu-id="3c409-149">Delegates</span></span>  
  
-   <span data-ttu-id="3c409-150">Pomocí stručnější syntaxe pro vytvoření instancí typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="3c409-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="3c409-151">Zpracování výjimek s použitím příkazů try-catch a using</span><span class="sxs-lookup"><span data-stu-id="3c409-151">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="3c409-152">Použití [bloku try-catch](../../../csharp/language-reference/keywords/try-catch.md) příkaz pro většinu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="3c409-152">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="3c409-153">Zjednodušení kódu pomocí jazyka C# [příkaz using](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3c409-153">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="3c409-154">Pokud máte [try-finally](../../../csharp/language-reference/keywords/try-finally.md) příkazu, ve kterém pouze kód v `finally` blok je volání <xref:System.IDisposable.Dispose%2A> metody, použijte `using` příkaz místo toho.</span><span class="sxs-lookup"><span data-stu-id="3c409-154">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="3c409-155">& & a &#124; &#124; operátory</span><span class="sxs-lookup"><span data-stu-id="3c409-155">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="3c409-156">Pokud chcete zabránit výjimky a zvýšit výkon přeskočením zbytečné porovnání, použijte [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) místo [ & ](../../../csharp/language-reference/operators/and-operator.md) a [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)místo [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) při provádění porovnání, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3c409-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="3c409-157">Operátor new</span><span class="sxs-lookup"><span data-stu-id="3c409-157">New Operator</span></span>  
  
-   <span data-ttu-id="3c409-158">Pomocí Stručná forma vytváření instancí objektu implicitního zápisu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="3c409-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="3c409-159">Předchozí řádek odpovídá následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="3c409-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="3c409-160">Používejte inicializátory objektů pro zjednodušení vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="3c409-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="3c409-161">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="3c409-161">Event Handling</span></span>  
  
-   <span data-ttu-id="3c409-162">Pokud definujete obslužnou rutinu události, která není potřeba později odebrat, použijte výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="3c409-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="3c409-163">Statické členy</span><span class="sxs-lookup"><span data-stu-id="3c409-163">Static Members</span></span>  
  
-   <span data-ttu-id="3c409-164">Volání [statické](../../../csharp/language-reference/keywords/static.md) pomocí názvu třídy členů: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="3c409-164">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="3c409-165">Tento postup vytvoří kód lépe čitelný tím, že statická přístup zrušte.</span><span class="sxs-lookup"><span data-stu-id="3c409-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="3c409-166">Nekvalifikujte statické člena definovaného v základní třídě s názvem odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="3c409-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="3c409-167">Tento kód se zkompiluje, je zavádějící čitelnost kódu a kód může v budoucnu přerušit, pokud chcete přidat statický člen se stejným názvem do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="3c409-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="3c409-168">Dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="3c409-168">LINQ Queries</span></span>  
  
-   <span data-ttu-id="3c409-169">Použijte smysluplné názvy proměnných dotazu.</span><span class="sxs-lookup"><span data-stu-id="3c409-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="3c409-170">Následující příklad používá `seattleCustomers` pro zákazníky, kteří se nacházejí v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="3c409-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="3c409-171">Ujistěte se, že názvy vlastností anonymních typů mají správnou velikost písmen, pomocí Pascal pomocí aliasů velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="3c409-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="3c409-172">Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku nejednoznačné.</span><span class="sxs-lookup"><span data-stu-id="3c409-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="3c409-173">Například, pokud dotaz vrátí zákazníka, název a ID distributora, nenechávejte jako `Name` a `ID` ve výsledku, je pro vysvětlení, že přejmenovat `Name` je název zákazníka, a `ID` je ID distributora.</span><span class="sxs-lookup"><span data-stu-id="3c409-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="3c409-174">Použití implicitního zápisu v deklaraci proměnné dotazu a proměnných rozsahu.</span><span class="sxs-lookup"><span data-stu-id="3c409-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="3c409-175">Zarovnejte klauzule dotazu v [z](../../../csharp/language-reference/keywords/from-clause.md) klauzule, jak je znázorněno v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="3c409-175">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="3c409-176">Použití [kde](../../../csharp/language-reference/keywords/where-clause.md) klauzule před další klauzule dotazu zajistit, aby pozdější klauzule dotazu pracovaly na snížení, filtrovat sadu data.</span><span class="sxs-lookup"><span data-stu-id="3c409-176">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="3c409-177">Použití více `from` klauzule místo [spojení](../../../csharp/language-reference/keywords/join-clause.md) klauzuli pro přístup k vnitřních kolekcí.</span><span class="sxs-lookup"><span data-stu-id="3c409-177">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="3c409-178">Například kolekce `Student` každý objekty mohou obsahovat kolekce skóre v testech.</span><span class="sxs-lookup"><span data-stu-id="3c409-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="3c409-179">Při spuštění následující dotaz vrátí každý skóre, které je více než 90, spolu s příjmení studentů, kteří obdrželi skóre.</span><span class="sxs-lookup"><span data-stu-id="3c409-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="3c409-180">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3c409-180">Security</span></span>  
 <span data-ttu-id="3c409-181">Postupujte podle pokynů v [zabezpečené kódování zásady](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="3c409-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c409-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c409-182">See Also</span></span>

- [<span data-ttu-id="3c409-183">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="3c409-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
- [<span data-ttu-id="3c409-184">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="3c409-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
