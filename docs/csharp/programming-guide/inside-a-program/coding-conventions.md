---
title: C# Kódovací konvence – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399733"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="43c6f-102">Převody kódování C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="43c6f-102">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="43c6f-103">Kódovací konvence slouží následujícím účelům:</span><span class="sxs-lookup"><span data-stu-id="43c6f-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="43c6f-104">Vytvářejí konzistentní vzhled kódu, takže čtenáři se mohou soustředit na obsah, nikoli na rozložení.</span><span class="sxs-lookup"><span data-stu-id="43c6f-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="43c6f-105">Umožňují čtenářům pochopit kód rychleji tím, že předpoklady na základě předchozích zkušeností.</span><span class="sxs-lookup"><span data-stu-id="43c6f-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="43c6f-106">Usnadňují kopírování, změnu a údržbu kódu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="43c6f-107">Předváděte osvědčené postupy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="43c6f-107">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="43c6f-108">Pokyny v tomto článku používají společnost Microsoft k vývoji ukázek a dokumentace.</span><span class="sxs-lookup"><span data-stu-id="43c6f-108">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="43c6f-109">Konvence vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="43c6f-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="43c6f-110">V krátkých příkladech, které nezahrnují [použití direktiv](../../language-reference/keywords/using-directive.md), použijte kvalifikace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="43c6f-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="43c6f-111">Pokud víte, že obor názvů je importován ve výchozím nastavení v projektu, není třeba plně kvalifikovat názvy z tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="43c6f-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="43c6f-112">Kvalifikované názvy mohou být přerušeny po tečka (.), pokud jsou příliš dlouhé pro jeden řádek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="43c6f-113">Není třeba měnit názvy objektů, které byly vytvořeny pomocí nástrojů aplikace Visual Studio návrháře, aby byly vhodné pro jiné pokyny.</span><span class="sxs-lookup"><span data-stu-id="43c6f-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="43c6f-114">Konvence rozložení</span><span class="sxs-lookup"><span data-stu-id="43c6f-114">Layout Conventions</span></span>  

<span data-ttu-id="43c6f-115">Dobré rozložení používá formátování ke zdůraznění struktury kódu a k usnadnění čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="43c6f-116">Příklady a ukázky společnosti Microsoft odpovídají následujícím konvencím:</span><span class="sxs-lookup"><span data-stu-id="43c6f-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="43c6f-117">Použijte výchozí nastavení Editoru kódu (inteligentní odsazení, čtyřmístné odsazení, karty uložené jako mezery).</span><span class="sxs-lookup"><span data-stu-id="43c6f-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="43c6f-118">Další informace naleznete v [tématu Možnosti, Textový editor, C#, Formátování](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="43c6f-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="43c6f-119">Napište pouze jeden příkaz na řádek.</span><span class="sxs-lookup"><span data-stu-id="43c6f-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="43c6f-120">Napište pouze jednu deklaraci na řádek.</span><span class="sxs-lookup"><span data-stu-id="43c6f-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="43c6f-121">Pokud řádky pokračování nejsou odsazeny automaticky, odsaďte je o jednu zarážku tabulátoru (čtyři mezery).</span><span class="sxs-lookup"><span data-stu-id="43c6f-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="43c6f-122">Přidejte alespoň jeden prázdný řádek mezi definice metody a definice vlastností.</span><span class="sxs-lookup"><span data-stu-id="43c6f-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="43c6f-123">Pomocí závorek můžete klauzule ve výrazu zdánlivě zjevit, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="43c6f-124">Konvence při psaní komentářů</span><span class="sxs-lookup"><span data-stu-id="43c6f-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="43c6f-125">Umístěte komentář na samostatný řádek, nikoli na konec řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="43c6f-126">Začněte text komentáře s velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="43c6f-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="43c6f-127">Ukončit text komentáře tečkou</span><span class="sxs-lookup"><span data-stu-id="43c6f-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="43c6f-128">Vložte jednu mezeru mezi oddělovač poznámek (//) a text komentáře, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="43c6f-129">Nevytvářejte formátované bloky hvězdiček kolem komentářů.</span><span class="sxs-lookup"><span data-stu-id="43c6f-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="43c6f-130">Pokyny pro jazyk</span><span class="sxs-lookup"><span data-stu-id="43c6f-130">Language Guidelines</span></span>  

<span data-ttu-id="43c6f-131">Následující části popisují postupy, které tým C# následuje připravit příklady kódu a ukázky.</span><span class="sxs-lookup"><span data-stu-id="43c6f-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="43c6f-132">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="43c6f-132">String Data Type</span></span>  
  
- <span data-ttu-id="43c6f-133">Pomocí [interpolace řetězců](../../language-reference/tokens/interpolated.md) zřetězete krátké řetězce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="43c6f-134">Chcete-li připojit řetězce ve smyčkách, zejména při práci <xref:System.Text.StringBuilder> s velkým množstvím textu, použijte objekt.</span><span class="sxs-lookup"><span data-stu-id="43c6f-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="43c6f-135">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="43c6f-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="43c6f-136">[Implicitní psaní](../classes-and-structs/implicitly-typed-local-variables.md) pro místní proměnné, pokud je typ proměnné zřejmý z pravé strany přiřazení nebo pokud přesný typ není důležitý.</span><span class="sxs-lookup"><span data-stu-id="43c6f-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="43c6f-137">Nepoužívejte [var,](../../language-reference/keywords/var.md) pokud typ není zřejmý z pravé strany přiřazení.</span><span class="sxs-lookup"><span data-stu-id="43c6f-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="43c6f-138">Nespoléhejte na název proměnné k určení typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="43c6f-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="43c6f-139">Možná to není správné.</span><span class="sxs-lookup"><span data-stu-id="43c6f-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="43c6f-140">Vyhněte `var` se použití místo [dynamického](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="43c6f-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="43c6f-141">Implicitní psaní slouží k určení typu proměnné smyčky v [pro](../../language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="43c6f-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="43c6f-142">Následující příklad používá implicitní `for` psaní v příkazu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="43c6f-143">Nepoužívejte implicitní psaní k určení typu proměnné smyčky v [foreach](../../language-reference/keywords/foreach-in.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="43c6f-143">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="43c6f-144">Následující příklad používá explicitní psaní `foreach` v příkazu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-144">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="43c6f-145">Dávejte pozor, abyste omylem nezměnili typ prvku iterable kolekce.</span><span class="sxs-lookup"><span data-stu-id="43c6f-145">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="43c6f-146">Například je snadné přepnout <xref:System.Linq.IQueryable?displayProperty=nameWithType> <xref:System.Collections.IEnumerable?displayProperty=nameWithType> z `foreach` v příkazu, který změní provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-146">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="43c6f-147">Nepodepsaný datový typ</span><span class="sxs-lookup"><span data-stu-id="43c6f-147">Unsigned Data Type</span></span>  
  
<span data-ttu-id="43c6f-148">Obecně používejte `int` spíše než nepodepsané typy.</span><span class="sxs-lookup"><span data-stu-id="43c6f-148">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="43c6f-149">Použití `int` je běžné v celém c#, a je snazší komunikovat `int`s jinými knihovnami při použití .</span><span class="sxs-lookup"><span data-stu-id="43c6f-149">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="43c6f-150">Pole</span><span class="sxs-lookup"><span data-stu-id="43c6f-150">Arrays</span></span>  
  
<span data-ttu-id="43c6f-151">Při inicializaci polí na řádku deklarace použijte stručnou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="43c6f-151">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="43c6f-152">Delegáty</span><span class="sxs-lookup"><span data-stu-id="43c6f-152">Delegates</span></span>  
  
<span data-ttu-id="43c6f-153">Pomocí stručné syntaxe můžete vytvářet instance typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="43c6f-153">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="43c6f-154">Zpracování výjimek s použitím příkazů try-catch a using</span><span class="sxs-lookup"><span data-stu-id="43c6f-154">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="43c6f-155">Pro většinu zpracování výjimek použijte příkaz [try-catch.](../../language-reference/keywords/try-catch.md)</span><span class="sxs-lookup"><span data-stu-id="43c6f-155">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="43c6f-156">Zjednodušte kód pomocí [příkazu](../../language-reference/keywords/using-statement.md)C# using .</span><span class="sxs-lookup"><span data-stu-id="43c6f-156">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="43c6f-157">Pokud máte [příkaz try-finally,](../../language-reference/keywords/try-finally.md) ve kterém `finally` je jediným kódem <xref:System.IDisposable.Dispose%2A> v bloku `using` volání metody, použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="43c6f-157">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="43c6f-158">&& a &#124;&#124; operátory</span><span class="sxs-lookup"><span data-stu-id="43c6f-158">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="43c6f-159">Chcete-li se vyhnout výjimkám a zvýšit [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) výkon [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) přeskočením zbytečných porovnání, použijte místo a [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) místo [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) při provádění porovnání, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-159">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="43c6f-160">Operátor new</span><span class="sxs-lookup"><span data-stu-id="43c6f-160">New Operator</span></span>  
  
- <span data-ttu-id="43c6f-161">Použijte stručnou formu instance objektu s implicitním psaním, jak je znázorněno v následujícím prohlášení.</span><span class="sxs-lookup"><span data-stu-id="43c6f-161">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="43c6f-162">Předchozí řádek je ekvivalentní následující prohlášení.</span><span class="sxs-lookup"><span data-stu-id="43c6f-162">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="43c6f-163">Ke zjednodušení vytváření objektů použijte inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="43c6f-163">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="43c6f-164">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="43c6f-164">Event Handling</span></span>  
  
<span data-ttu-id="43c6f-165">Pokud definujete obslužnou rutinu události, kterou není nutné později odebrat, použijte výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="43c6f-165">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="43c6f-166">Statické členy</span><span class="sxs-lookup"><span data-stu-id="43c6f-166">Static Members</span></span>  
  
<span data-ttu-id="43c6f-167">Volání [statických](../../language-reference/keywords/static.md) členů pomocí názvu třídy: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="43c6f-167">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="43c6f-168">Tento postup umožňuje kód čitelnější tím, že statický přístup jasné.</span><span class="sxs-lookup"><span data-stu-id="43c6f-168">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="43c6f-169">Nekvalifikujte statický člen definovaný v základní třídě s názvem odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="43c6f-169">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="43c6f-170">Zatímco tento kód zkompiluje, čitelnost kódu je zavádějící a kód může přerušit v budoucnu, pokud přidáte statický člen se stejným názvem do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="43c6f-170">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="43c6f-171">Dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="43c6f-171">LINQ Queries</span></span>  
  
- <span data-ttu-id="43c6f-172">Pro proměnné dotazu použijte smysluplné názvy.</span><span class="sxs-lookup"><span data-stu-id="43c6f-172">Use meaningful names for query variables.</span></span> <span data-ttu-id="43c6f-173">Následující příklad `seattleCustomers` používá pro zákazníky, kteří se nacházejí v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-173">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="43c6f-174">Pomocí aliasů se ujistěte, že názvy vlastností anonymních typů jsou správně velkými písmeny pomocí pascalu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-174">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="43c6f-175">Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku byly nejednoznačné.</span><span class="sxs-lookup"><span data-stu-id="43c6f-175">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="43c6f-176">Například pokud dotaz vrátí jméno zákazníka a ID distributora, `ID` namísto jejich ponechání jako `Name` `Name` a ve výsledku, `ID` přejmenujte je, aby bylo jasné, že je jméno zákazníka a je ID distributora.</span><span class="sxs-lookup"><span data-stu-id="43c6f-176">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="43c6f-177">Použijte implicitní psaní v deklaraci proměnných dotazu a proměnných rozsahu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-177">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="43c6f-178">Zarovnejte klauzule dotazu pod klauzulí [from,](../../language-reference/keywords/from-clause.md) jak je znázorněno v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="43c6f-178">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="43c6f-179">Použijte [kde](../../language-reference/keywords/where-clause.md) klauzule před jiné klauzule dotazu k zajištění, že novější klauzule dotazu pracovat na redukované, filtrované sadu dat.</span><span class="sxs-lookup"><span data-stu-id="43c6f-179">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="43c6f-180">Použijte `from` více klauzulí namísto [join](../../language-reference/keywords/join-clause.md) klauzule pro přístup k vnitřní kolekce.</span><span class="sxs-lookup"><span data-stu-id="43c6f-180">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="43c6f-181">Například kolekce `Student` objektů může obsahovat kolekci výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="43c6f-181">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="43c6f-182">Při spuštění následujícího dotazu vrátí každé skóre, které je starší 90, spolu s příjmením studenta, který obdržel skóre.</span><span class="sxs-lookup"><span data-stu-id="43c6f-182">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="43c6f-183">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="43c6f-183">Security</span></span>  

<span data-ttu-id="43c6f-184">Postupujte podle pokynů v [pokynech pro bezpečné kódování](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="43c6f-184">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c6f-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="43c6f-185">See also</span></span>

- [<span data-ttu-id="43c6f-186">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="43c6f-186">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="43c6f-187">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="43c6f-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
