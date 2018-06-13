---
title: Visual Basic – konvence kódování
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655358"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="7e967-102">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="7e967-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="7e967-103">Microsoft vyvíjí ukázky a dokumentace, která postupujte podle pokynů v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7e967-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="7e967-104">Pokud budete postupovat podle stejné konvence psaní kódu, získáte následující výhody:</span><span class="sxs-lookup"><span data-stu-id="7e967-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="7e967-105">Váš kód bude mít konzistentní vzhled, tak, aby čtečky můžete lépe zaměřit na obsah, není rozložení.</span><span class="sxs-lookup"><span data-stu-id="7e967-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="7e967-106">Čtečky pochopit váš kód více rychle protože udělat předpoklady založené na předchozí zkušenosti.</span><span class="sxs-lookup"><span data-stu-id="7e967-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="7e967-107">Můžete zkopírovat, změnit a snadněji spravovat kód.</span><span class="sxs-lookup"><span data-stu-id="7e967-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="7e967-108">Můžete zajistit, aby váš kód ukazuje "osvědčené postupy" jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7e967-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="7e967-109">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="7e967-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="7e967-110">Informace o pojmenování pokyny najdete v tématu [pokyny pro pojmenování](../../../standard/design-guidelines/naming-guidelines.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="7e967-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="7e967-111">Nepoužívejte "Moje" nebo "Moje" jako součást název proměnné.</span><span class="sxs-lookup"><span data-stu-id="7e967-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="7e967-112">Tento postup vytvoří záměně se `My` objekty.</span><span class="sxs-lookup"><span data-stu-id="7e967-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="7e967-113">Nemusíte měnit názvy objektů v automaticky vygenerovaný kód tak, aby byly podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="7e967-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="7e967-114">Konvence rozložení</span><span class="sxs-lookup"><span data-stu-id="7e967-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="7e967-115">Vložení karty prostory a používat inteligentní odsazení s odsazení čtyři místa.</span><span class="sxs-lookup"><span data-stu-id="7e967-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="7e967-116">Použití **poměrně výpis (přeformátování) z kódu** k opakovanému formátování kódu v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7e967-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="7e967-117">Další informace najdete v tématu [možnosti, textový Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7e967-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="7e967-118">Použijte pouze jeden příkaz na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="7e967-118">Use only one statement per line.</span></span> <span data-ttu-id="7e967-119">Nepoužívejte oddělovací znak řádku jazyka Visual Basic (:).</span><span class="sxs-lookup"><span data-stu-id="7e967-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="7e967-120">Nepoužívejte znak pokračování řádku explicitní "_" považuje implicitní pokračování řádku bez ohledu na to umožňuje jazyk.</span><span class="sxs-lookup"><span data-stu-id="7e967-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="7e967-121">Použijte pouze jednu deklaraci na každý řádek.</span><span class="sxs-lookup"><span data-stu-id="7e967-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="7e967-122">Pokud **poměrně výpis (přeformátování) z kódu** nepodporuje řádky formátu pokračování automaticky, je nutné ručně odsazovat jeden zarážku pokračování řádků.</span><span class="sxs-lookup"><span data-stu-id="7e967-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="7e967-123">Nicméně vždy doleva align položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="7e967-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="7e967-124">Přidejte alespoň jeden prázdný řádek mezi definice metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7e967-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="7e967-125">Konvence při psaní komentářů</span><span class="sxs-lookup"><span data-stu-id="7e967-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="7e967-126">Komentáře uveďte na samostatném řádku místo na konci řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="7e967-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="7e967-127">Spusťte text poznámky s velkým písmenem a end text poznámky s tečkou.</span><span class="sxs-lookup"><span data-stu-id="7e967-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="7e967-128">Vložte jeden mezer mezi oddělovač komentář (') a text poznámky.</span><span class="sxs-lookup"><span data-stu-id="7e967-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   <span data-ttu-id="7e967-129">Není nutné uvést komentáře s formátovaný bloky hvězdičky.</span><span class="sxs-lookup"><span data-stu-id="7e967-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="7e967-130">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="7e967-130">Program Structure</span></span>  
  
-   <span data-ttu-id="7e967-131">Při použití `Main` metoda, použít konstrukce výchozí pro nové konzolové aplikace a používat `My` pro argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7e967-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="7e967-132">Pokyny pro jazyk</span><span class="sxs-lookup"><span data-stu-id="7e967-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="7e967-133">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="7e967-133">String Data Type</span></span>  
  
-   <span data-ttu-id="7e967-134">Zřetězení řetězců, použijte znak ampersand (&).</span><span class="sxs-lookup"><span data-stu-id="7e967-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   <span data-ttu-id="7e967-135">Chcete-li připojit řetězců v smyčky, použijte <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="7e967-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="7e967-136">Volný Delegáti v obslužné rutiny událostí</span><span class="sxs-lookup"><span data-stu-id="7e967-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="7e967-137">Nemohou být explicitně argumenty (objekt a EventArgs) do obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="7e967-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="7e967-138">Pokud nepoužíváte argumenty událostí, které se budou předávat událost (například odesílatel jako objekt, jako EventArgs e), použijte volný Delegáti a vynechte argumenty událostí v kódu:</span><span class="sxs-lookup"><span data-stu-id="7e967-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="7e967-139">Nepodepsaný datový typ</span><span class="sxs-lookup"><span data-stu-id="7e967-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="7e967-140">Použití `Integer` místo typy bez znaménka, s výjimkou tam, kde jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="7e967-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="7e967-141">Pole</span><span class="sxs-lookup"><span data-stu-id="7e967-141">Arrays</span></span>  
  
-   <span data-ttu-id="7e967-142">Při inicializaci pole na ose deklarace, použijte krátký syntaxi.</span><span class="sxs-lookup"><span data-stu-id="7e967-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="7e967-143">Například použijte následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="7e967-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     <span data-ttu-id="7e967-144">Nepoužívejte následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="7e967-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   <span data-ttu-id="7e967-145">Uveďte označení pole na typu, nikoli na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7e967-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="7e967-146">Například použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7e967-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     <span data-ttu-id="7e967-147">Nepoužívejte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7e967-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   <span data-ttu-id="7e967-148">Pokud deklarace a inicializace pole základní datové typy, použijte syntaxi {}.</span><span class="sxs-lookup"><span data-stu-id="7e967-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="7e967-149">Například použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7e967-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     <span data-ttu-id="7e967-150">Nepoužívejte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7e967-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="7e967-151">Použití s – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="7e967-151">Use the With Keyword</span></span>  
 <span data-ttu-id="7e967-152">Pokud provedete řadu volání jeden objekt, zvažte použití `With` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="7e967-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="7e967-153">Použijte Try... Catch a pomocí příkazy při použití zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="7e967-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="7e967-154">Nepoužívejte `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="7e967-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="7e967-155">Použití klíčového slova IsNot</span><span class="sxs-lookup"><span data-stu-id="7e967-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="7e967-156">Použití `IsNot` – klíčové slovo místo `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7e967-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="7e967-157">New – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="7e967-157">New Keyword</span></span>  
  
-   <span data-ttu-id="7e967-158">Použijte krátký vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="7e967-158">Use short instantiation.</span></span> <span data-ttu-id="7e967-159">Například použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7e967-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     <span data-ttu-id="7e967-160">Předchozí řádek je ekvivalentní k tomuto:</span><span class="sxs-lookup"><span data-stu-id="7e967-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   <span data-ttu-id="7e967-161">Inicializátory objektů použijte pro všechny nové objekty místo konstruktor bez parametrů:</span><span class="sxs-lookup"><span data-stu-id="7e967-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a><span data-ttu-id="7e967-162">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="7e967-162">Event Handling</span></span>  
  
-   <span data-ttu-id="7e967-163">Použití `Handles` místo `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="7e967-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   <span data-ttu-id="7e967-164">Použití `AddressOf`a ne doložit explicitně delegát:</span><span class="sxs-lookup"><span data-stu-id="7e967-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   <span data-ttu-id="7e967-165">Když definujete událost, použijte krátký syntaxe a nechat kompilátoru definovat delegát:</span><span class="sxs-lookup"><span data-stu-id="7e967-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   <span data-ttu-id="7e967-166">Neověřovat, zda je událost `Nothing` (null) před voláním `RaiseEvent` metoda.</span><span class="sxs-lookup"><span data-stu-id="7e967-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="7e967-167">`RaiseEvent` zkontroluje `Nothing` předtím, než se vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="7e967-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="7e967-168">Pomocí sdílení členové</span><span class="sxs-lookup"><span data-stu-id="7e967-168">Using Shared Members</span></span>  
 <span data-ttu-id="7e967-169">Volání `Shared` členy pomocí názvu třídy, ne z proměnnou instance.</span><span class="sxs-lookup"><span data-stu-id="7e967-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="7e967-170">Použití XML – literály</span><span class="sxs-lookup"><span data-stu-id="7e967-170">Use XML Literals</span></span>  
 <span data-ttu-id="7e967-171">XML – literály zjednodušit běžné úkoly, které dojde při práci s XML (například zatížení, dotazů a transformace).</span><span class="sxs-lookup"><span data-stu-id="7e967-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="7e967-172">Při vývoji s XML, postupujte podle těchto pokynů:</span><span class="sxs-lookup"><span data-stu-id="7e967-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="7e967-173">XML – literály použijte k vytvoření dokumentů XML a fragmenty místo přímé volání rozhraní API XML.</span><span class="sxs-lookup"><span data-stu-id="7e967-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="7e967-174">Importujte obory názvů XML na úrovni souboru nebo projektu chcete využít výhod optimalizací výkonu pro literály XML.</span><span class="sxs-lookup"><span data-stu-id="7e967-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="7e967-175">Pomocí vlastnosti osy XML pro přístup k elementů a atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7e967-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="7e967-176">Použít vložené výrazy zahrnout hodnoty a vytvářet XML z existující hodnoty namísto volání rozhraní API, jako `Add` metoda:</span><span class="sxs-lookup"><span data-stu-id="7e967-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a><span data-ttu-id="7e967-177">Dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="7e967-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="7e967-178">Použijte smysluplné názvy proměnných dotazu:</span><span class="sxs-lookup"><span data-stu-id="7e967-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   <span data-ttu-id="7e967-179">Zadejte názvy elementů v dotazu, abyste měli jistotu, že jsou názvy vlastností anonymní typů správně písmeno pomocí Pascal velká a malá písmena:</span><span class="sxs-lookup"><span data-stu-id="7e967-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   <span data-ttu-id="7e967-180">Přejmenujte vlastnosti názvy vlastností, které ve výsledku by být nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="7e967-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="7e967-181">Například pokud dotaz vrátí zákazníka, název a ID pořadí, přejmenujte je místo necháte jako `Name` a `ID` ve výsledku:</span><span class="sxs-lookup"><span data-stu-id="7e967-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   <span data-ttu-id="7e967-182">V deklaraci proměnné dotazu a proměnné rozsahu používejte odvození typu:</span><span class="sxs-lookup"><span data-stu-id="7e967-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   <span data-ttu-id="7e967-183">Zarovnat klauzule dotazu v části `From` příkaz:</span><span class="sxs-lookup"><span data-stu-id="7e967-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   <span data-ttu-id="7e967-184">Použití `Where` klauzule před ostatními dotaz klauzule tak, aby novější klauzule dotazu pracovat na filtrovanou sadu dat:</span><span class="sxs-lookup"><span data-stu-id="7e967-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   <span data-ttu-id="7e967-185">Použití `Join` klauzule explicitně definujte operace spojení místo použití `Where` klauzule implicitně definovat operace spojení:</span><span class="sxs-lookup"><span data-stu-id="7e967-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7e967-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e967-186">See Also</span></span>  
 [<span data-ttu-id="7e967-187">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="7e967-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
