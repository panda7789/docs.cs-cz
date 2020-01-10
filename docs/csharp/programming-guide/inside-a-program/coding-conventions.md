---
title: C#Konvence kódování C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: c56d673de958f49a9ace60350442e89039e1d69f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712101"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="4fc93-102">Převody kódování C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4fc93-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="4fc93-103">Konvence kódování slouží k následujícím účelům:</span><span class="sxs-lookup"><span data-stu-id="4fc93-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="4fc93-104">Vytvářejí konzistentní vzhled kódu, aby se čtenáři mohli soustředit na obsah, nikoli na rozložení.</span><span class="sxs-lookup"><span data-stu-id="4fc93-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="4fc93-105">Umožňují čtenářům lépe pochopit kód tím, že se na základě předchozích zkušeností vydávají předpoklady.</span><span class="sxs-lookup"><span data-stu-id="4fc93-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="4fc93-106">Usnadňují kopírování, změny a údržbu kódu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="4fc93-107">Ukazují C# osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="4fc93-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="4fc93-108">Pokyny v tomto tématu používá společnost Microsoft k vývoji ukázek a dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4fc93-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="4fc93-109">Konvence vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="4fc93-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="4fc93-110">V krátkých příkladech, které neobsahují [direktivy using](../../language-reference/keywords/using-directive.md), použijte kvalifikaci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4fc93-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="4fc93-111">Pokud víte, že je ve výchozím nastavení v projektu importován obor názvů, nemusíte plně kvalifikovat názvy z tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4fc93-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="4fc93-112">Kvalifikované názvy mohou být porušeny za tečku (.), pokud jsou příliš dlouhé pro jeden řádek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="4fc93-113">Nemusíte měnit názvy objektů, které byly vytvořeny pomocí nástrojů návrháře sady Visual Studio, aby vyhovovaly jiným pokynům.</span><span class="sxs-lookup"><span data-stu-id="4fc93-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="4fc93-114">Konvence rozložení</span><span class="sxs-lookup"><span data-stu-id="4fc93-114">Layout Conventions</span></span>  
 <span data-ttu-id="4fc93-115">Dobrá rozložení používá formátování k zdůraznění struktury kódu a k usnadnění čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="4fc93-116">Příklady a ukázky společnosti Microsoft splňují následující konvence:</span><span class="sxs-lookup"><span data-stu-id="4fc93-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="4fc93-117">Použijte výchozí nastavení editoru kódu (inteligentní odrážky, odsazení čtyř znaků, tabulátory uložené jako mezery).</span><span class="sxs-lookup"><span data-stu-id="4fc93-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="4fc93-118">Další informace naleznete v tématu [Možnosti, textový editor, C#formátování](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="4fc93-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="4fc93-119">Zapsat pouze jeden příkaz na řádek.</span><span class="sxs-lookup"><span data-stu-id="4fc93-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="4fc93-120">Zapsat pouze jednu deklaraci na řádek.</span><span class="sxs-lookup"><span data-stu-id="4fc93-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="4fc93-121">Pokud nejsou řádky pro pokračování automaticky odsazeny, odsadíte je o jednu zarážku tabulátoru (čtyři mezery).</span><span class="sxs-lookup"><span data-stu-id="4fc93-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="4fc93-122">Přidejte alespoň jeden prázdný řádek mezi definice metody a definice vlastností.</span><span class="sxs-lookup"><span data-stu-id="4fc93-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="4fc93-123">Použijte závorky k vytvoření klauzulí ve výrazu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="4fc93-124">Konvence při psaní komentářů</span><span class="sxs-lookup"><span data-stu-id="4fc93-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="4fc93-125">Komentář umístěte na samostatný řádek, nikoli na konci řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="4fc93-126">Začněte text komentáře velkým písmenem.</span><span class="sxs-lookup"><span data-stu-id="4fc93-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="4fc93-127">Konec textu komentáře s tečkou</span><span class="sxs-lookup"><span data-stu-id="4fc93-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="4fc93-128">Vložte jednu mezeru mezi oddělovač komentáře (//) a text komentáře, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="4fc93-129">Nevytvářejte formátované bloky hvězdiček kolem komentářů.</span><span class="sxs-lookup"><span data-stu-id="4fc93-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="4fc93-130">Pokyny pro jazyk</span><span class="sxs-lookup"><span data-stu-id="4fc93-130">Language Guidelines</span></span>  
 <span data-ttu-id="4fc93-131">Následující části popisují postupy, které C# tým sleduje pro přípravu příkladů kódu a ukázek.</span><span class="sxs-lookup"><span data-stu-id="4fc93-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="4fc93-132">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="4fc93-132">String Data Type</span></span>  
  
- <span data-ttu-id="4fc93-133">Použijte [interpolaci řetězce](../../language-reference/tokens/interpolated.md) k zřetězení krátkých řetězců, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="4fc93-134">Pro připojení řetězců ve smyčce, zejména při práci s velkým množstvím textu, použijte objekt <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="4fc93-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="4fc93-135">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="4fc93-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="4fc93-136">Použijte [implicitní psaní](../classes-and-structs/implicitly-typed-local-variables.md) pro lokální proměnné, pokud je typ proměnné zjevný z pravé strany přiřazení, nebo pokud přesný typ není důležitý.</span><span class="sxs-lookup"><span data-stu-id="4fc93-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="4fc93-137">Nepoužívejte [var](../../language-reference/keywords/var.md) v případě, že typ není na pravé straně přiřazení zřejmý.</span><span class="sxs-lookup"><span data-stu-id="4fc93-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="4fc93-138">Nespoléhá na název proměnné, abyste určili typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="4fc93-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="4fc93-139">Nemusí být správné.</span><span class="sxs-lookup"><span data-stu-id="4fc93-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="4fc93-140">Vyhněte se použití `var` místo [dynamického](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="4fc93-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="4fc93-141">Pomocí implicitního zápisu určete typ proměnné smyčky v [pro smyčky for](../../language-reference/keywords/for.md) a [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="4fc93-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) and [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="4fc93-142">Následující příklad používá implicitní zadání v příkazu `for`.</span><span class="sxs-lookup"><span data-stu-id="4fc93-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
     <span data-ttu-id="4fc93-143">Následující příklad používá implicitní zadání v příkazu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="4fc93-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="4fc93-144">Nepodepsaný datový typ</span><span class="sxs-lookup"><span data-stu-id="4fc93-144">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="4fc93-145">Obecně použijte `int` spíše než typy bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="4fc93-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="4fc93-146">Použití `int` je běžné v celém C#a při použití `int`je snazší pracovat s ostatními knihovnami.</span><span class="sxs-lookup"><span data-stu-id="4fc93-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="4fc93-147">Pole</span><span class="sxs-lookup"><span data-stu-id="4fc93-147">Arrays</span></span>  
  
- <span data-ttu-id="4fc93-148">Použijte stručnou syntaxi při inicializaci polí na řádku deklarace.</span><span class="sxs-lookup"><span data-stu-id="4fc93-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="4fc93-149">Delegáti</span><span class="sxs-lookup"><span data-stu-id="4fc93-149">Delegates</span></span>  
  
- <span data-ttu-id="4fc93-150">K vytvoření instancí typu delegáta použijte stručnou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="4fc93-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="4fc93-151">Zpracování výjimek s použitím příkazů try-catch a using</span><span class="sxs-lookup"><span data-stu-id="4fc93-151">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="4fc93-152">Použijte příkaz [try-catch](../../language-reference/keywords/try-catch.md) pro většinu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="4fc93-152">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="4fc93-153">Zjednodušte svůj kód pomocí C# [příkazu Using](../../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fc93-153">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="4fc93-154">Pokud máte příkaz [try-finally](../../language-reference/keywords/try-finally.md) , ve kterém jediný kód v bloku `finally` je voláním metody <xref:System.IDisposable.Dispose%2A>, použijte místo toho příkaz `using`.</span><span class="sxs-lookup"><span data-stu-id="4fc93-154">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="4fc93-155">& & a &#124; &#124; operátory</span><span class="sxs-lookup"><span data-stu-id="4fc93-155">&& and &#124;&#124; Operators</span></span>  
  
- <span data-ttu-id="4fc93-156">Aby nedocházelo k výjimkám a zvýšili výkon přeskočením zbytečných porovnání, použijte [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) namísto [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) a [ &#124; ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) místo [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) při porovnávání, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="4fc93-157">Operátor new</span><span class="sxs-lookup"><span data-stu-id="4fc93-157">New Operator</span></span>  
  
- <span data-ttu-id="4fc93-158">Použijte stručnou formu instance objektu s implicitním zadáním, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4fc93-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="4fc93-159">Předchozí řádek je ekvivalentní následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4fc93-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="4fc93-160">K zjednodušení vytvoření objektu použijte Inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="4fc93-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="4fc93-161">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="4fc93-161">Event Handling</span></span>  
  
- <span data-ttu-id="4fc93-162">Pokud definujete obslužnou rutinu události, kterou nemusíte později odebrat, použijte výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="4fc93-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="4fc93-163">Statické členy</span><span class="sxs-lookup"><span data-stu-id="4fc93-163">Static Members</span></span>  
  
- <span data-ttu-id="4fc93-164">Volejte [statické](../../language-reference/keywords/static.md) členy pomocí názvu třídy: *ClassName. StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="4fc93-164">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="4fc93-165">Tento postup usnadňuje čitelnost kódu tím, že provádí jasné zrušení statického přístupu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="4fc93-166">Nekvalifikovat statický člen definovaný v základní třídě s názvem odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4fc93-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="4fc93-167">Při kompilaci kódu je čitelnost kódu zavádějící a kód může být v budoucnu přerušen, pokud přidáte statický člen se stejným názvem do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4fc93-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="4fc93-168">Dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="4fc93-168">LINQ Queries</span></span>  
  
- <span data-ttu-id="4fc93-169">Pro proměnné dotazů použijte smysluplné názvy.</span><span class="sxs-lookup"><span data-stu-id="4fc93-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="4fc93-170">Následující příklad používá `seattleCustomers` pro zákazníky nacházející se v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="4fc93-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="4fc93-171">Použijte aliasy k zajištění správného kapitálu názvů vlastností anonymních typů pomocí malých a velkých písmen Pascal.</span><span class="sxs-lookup"><span data-stu-id="4fc93-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="4fc93-172">Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku byly dvojznačné.</span><span class="sxs-lookup"><span data-stu-id="4fc93-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="4fc93-173">Pokud například váš dotaz vrátí název zákazníka a ID distributora, nemusíte je opustit jako `Name` a `ID` ve výsledku, přejmenujte je, aby se vyjasnilo, že `Name` je název zákazníka, a `ID` je ID distributora.</span><span class="sxs-lookup"><span data-stu-id="4fc93-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="4fc93-174">V deklaraci proměnných dotazu a proměnných rozsahu použijte implicitní zadání.</span><span class="sxs-lookup"><span data-stu-id="4fc93-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="4fc93-175">Zarovnat klauzule dotazu pod klauzulí [from](../../language-reference/keywords/from-clause.md) , jak je znázorněno v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="4fc93-175">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="4fc93-176">Pomocí klauzulí [WHERE](../../language-reference/keywords/where-clause.md) před jinými klauzulemi dotazu zajistěte, aby pozdější klauzule dotazu pracovaly na omezené a filtrované sadě dat.</span><span class="sxs-lookup"><span data-stu-id="4fc93-176">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="4fc93-177">Pro přístup k vnitřním kolekcím použijte místo klauzule [Join](../../language-reference/keywords/join-clause.md) více klauzulí `from`.</span><span class="sxs-lookup"><span data-stu-id="4fc93-177">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="4fc93-178">Například kolekce objektů `Student` může obsahovat kolekci hodnocení testů.</span><span class="sxs-lookup"><span data-stu-id="4fc93-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="4fc93-179">Při spuštění následujícího dotazu vrátí všechny skóre, které je více než 90, spolu s posledním názvem studenta, který skóre přijal.</span><span class="sxs-lookup"><span data-stu-id="4fc93-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="4fc93-180">Zabezpečení –</span><span class="sxs-lookup"><span data-stu-id="4fc93-180">Security</span></span>  
 <span data-ttu-id="4fc93-181">Postupujte podle pokynů v části [zásady bezpečného kódování](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="4fc93-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc93-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fc93-182">See also</span></span>

- [<span data-ttu-id="4fc93-183">Visual Basic konvence kódování</span><span class="sxs-lookup"><span data-stu-id="4fc93-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="4fc93-184">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="4fc93-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
