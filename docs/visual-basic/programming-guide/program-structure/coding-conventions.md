---
title: Visual Basic – konvence kódování
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f73648888b28c349104a70e78c29eb208d438b78
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814559"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="04765-102">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="04765-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="04765-103">Microsoft vyvíjí vzorky a dokumentaci, postupujte podle pokynů v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="04765-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="04765-104">Pokud budete postupovat podle stejné konvence psaní kódu, může získat následující výhody:</span><span class="sxs-lookup"><span data-stu-id="04765-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="04765-105">Váš kód bude mít jednotný vzhled tak, aby se čtenáři mohli lépe soustředit na obsah ne na rozložení.</span><span class="sxs-lookup"><span data-stu-id="04765-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="04765-106">Čtenáři pochopí váš kód rychle vzhledem k tomu, že budou mít předpoklady na základě předchozích zkušeností.</span><span class="sxs-lookup"><span data-stu-id="04765-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="04765-107">Můžete zkopírovat, změnit a mnohem snazší údržbu kódu.</span><span class="sxs-lookup"><span data-stu-id="04765-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="04765-108">Zajistíte, že váš kód ukazuje "osvědčené postupy" v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="04765-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="04765-109">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="04765-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="04765-110">Informace o pokyny pro pojmenování naleznete v tématu [pokyny pro pojmenování](../../../standard/design-guidelines/naming-guidelines.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="04765-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="04765-111">Nepoužívejte "My" nebo "my" jako součást názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="04765-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="04765-112">Tento postup vytvoří zmatení s `My` objekty.</span><span class="sxs-lookup"><span data-stu-id="04765-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="04765-113">Nemusíte změnit názvy objektů v automaticky vygenerovaném kódu, aby se daly přizpůsobit pokynům.</span><span class="sxs-lookup"><span data-stu-id="04765-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="04765-114">Konvence rozložení</span><span class="sxs-lookup"><span data-stu-id="04765-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="04765-115">Vložte tabulátory mezer a použijte inteligentní odsazení o čtyři místa.</span><span class="sxs-lookup"><span data-stu-id="04765-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="04765-116">Použití **Hezký výpis (přeformátování) kódu** k přeformátování kódu v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="04765-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="04765-117">Další informace najdete v tématu [možnosti, textový Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="04765-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="04765-118">Použijte pouze jeden příkaz na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="04765-118">Use only one statement per line.</span></span> <span data-ttu-id="04765-119">Nepoužívejte znak oddělovače řádku jazyka Visual Basic (:).</span><span class="sxs-lookup"><span data-stu-id="04765-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="04765-120">Nepoužívejte znak pokračování explicitní řádku "_" ve prospěch implicitní pokračování řádku bez ohledu na to jazyk umožňuje.</span><span class="sxs-lookup"><span data-stu-id="04765-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="04765-121">Použijte pouze jednu deklaraci na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="04765-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="04765-122">Pokud **Hezký výpis (přeformátování) kódu** nebude pokračovací řádky automaticky, ručně je odsaďte pokračování řádků jednu zarážku tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="04765-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="04765-123">Nicméně vždy vlevo zarovnávejte položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="04765-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="04765-124">Přidejte alespoň jeden prázdný řádek mezi definice metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="04765-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="04765-125">Konvence při psaní komentářů</span><span class="sxs-lookup"><span data-stu-id="04765-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="04765-126">Vložte poznámky na samostatný řádek místo na konci řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="04765-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="04765-127">Začněte text komentáře velkým písmenem a ukončit komentář tečkou.</span><span class="sxs-lookup"><span data-stu-id="04765-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="04765-128">Vložte jednu mezeru mezi oddělovač komentáře (') a text komentáře.</span><span class="sxs-lookup"><span data-stu-id="04765-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
-   <span data-ttu-id="04765-129">Nepoužívejte k ohraničení komentářů formátované bloky hvězdičky z obou stran.</span><span class="sxs-lookup"><span data-stu-id="04765-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="04765-130">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="04765-130">Program Structure</span></span>  
  
-   <span data-ttu-id="04765-131">Při použití `Main` metody, použijte výchozí konstrukci pro nové aplikace konzoly a použít `My` pro argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="04765-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="04765-132">Pokyny pro jazyk</span><span class="sxs-lookup"><span data-stu-id="04765-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="04765-133">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="04765-133">String Data Type</span></span>  
  
-   <span data-ttu-id="04765-134">Chcete-li řetězení řetězců, použijte znak ampersand (&).</span><span class="sxs-lookup"><span data-stu-id="04765-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
-   <span data-ttu-id="04765-135">K přidání řetězce ve smyčkách použijte <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="04765-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="04765-136">Uvolněné delegáty v obslužných rutinách událostí</span><span class="sxs-lookup"><span data-stu-id="04765-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="04765-137">Nekvalifikujte explicitně argumenty (Object a EventArgs) pro obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="04765-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="04765-138">Pokud nepoužíváte argumenty události, které jsou předány události (například odesílatel jako Object, e jako EventArgs), použijte uvolněné delegáty a nechte argumenty události ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="04765-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="04765-139">Nepodepsaný datový typ</span><span class="sxs-lookup"><span data-stu-id="04765-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="04765-140">Použití `Integer` místo typů bez znaménka, s výjimkou případů, kdy jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="04765-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="04765-141">Pole</span><span class="sxs-lookup"><span data-stu-id="04765-141">Arrays</span></span>  
  
-   <span data-ttu-id="04765-142">Použijte krátkou syntaxi, když inicializujete pole v řádku deklarace.</span><span class="sxs-lookup"><span data-stu-id="04765-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="04765-143">Například použijte následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="04765-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="04765-144">Nepoužívejte následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="04765-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
-   <span data-ttu-id="04765-145">Vložte pole označení typu, nikoli na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="04765-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="04765-146">Například použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="04765-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="04765-147">Nepoužívejte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="04765-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
-   <span data-ttu-id="04765-148">Když deklarujete a inicializujete pole základních datových typů, použijte syntax {}.</span><span class="sxs-lookup"><span data-stu-id="04765-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="04765-149">Například použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="04765-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="04765-150">Nepoužívejte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="04765-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="04765-151">Používá s klíčovým slovem</span><span class="sxs-lookup"><span data-stu-id="04765-151">Use the With Keyword</span></span>  
 <span data-ttu-id="04765-152">Pokud provedete sérii volání jednoho objektu, zvažte použití `With` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="04765-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="04765-153">Použijte Try... Catch a použití příkazů, když používáte zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="04765-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="04765-154">Nepoužívejte `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="04765-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="04765-155">Použijte klíčové slovo IsNot</span><span class="sxs-lookup"><span data-stu-id="04765-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="04765-156">Použití `IsNot` – klíčové slovo místo `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="04765-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="04765-157">New – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="04765-157">New Keyword</span></span>  
  
-   <span data-ttu-id="04765-158">Použijte krátkou instanciaci.</span><span class="sxs-lookup"><span data-stu-id="04765-158">Use short instantiation.</span></span> <span data-ttu-id="04765-159">Například použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="04765-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="04765-160">Na každém řádku je ekvivalentem tohoto:</span><span class="sxs-lookup"><span data-stu-id="04765-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
-   <span data-ttu-id="04765-161">Pro nové objekty namísto konstruktoru bez parametrů, použijte inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="04765-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="04765-162">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="04765-162">Event Handling</span></span>  
  
-   <span data-ttu-id="04765-163">Použití `Handles` spíše než `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="04765-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
-   <span data-ttu-id="04765-164">Použití `AddressOf`a nikoli instanci delegáta explicitně:</span><span class="sxs-lookup"><span data-stu-id="04765-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
-   <span data-ttu-id="04765-165">Když definujete událost, použijte krátkou syntaxi a nechte kompilátor definovat delegáta:</span><span class="sxs-lookup"><span data-stu-id="04765-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
-   <span data-ttu-id="04765-166">Nelze ověřit, zda je událost `Nothing` (null), dříve než zavoláte `RaiseEvent` metody.</span><span class="sxs-lookup"><span data-stu-id="04765-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="04765-167">`RaiseEvent` Vyhledá `Nothing` předtím, než vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="04765-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="04765-168">Použití sdílených členů</span><span class="sxs-lookup"><span data-stu-id="04765-168">Using Shared Members</span></span>  
 <span data-ttu-id="04765-169">Volání `Shared` členy pomocí názvu třídy, nikoli z proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="04765-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="04765-170">Použijte literály XML</span><span class="sxs-lookup"><span data-stu-id="04765-170">Use XML Literals</span></span>  
 <span data-ttu-id="04765-171">Literály XML zjednodušují zvládnout běžné úkoly, které se vyskytnou při práci s XML (například načtení, dotaz a transformace).</span><span class="sxs-lookup"><span data-stu-id="04765-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="04765-172">Při vývoji v XML postupujte podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="04765-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="04765-173">Použijte literály XML k vytváření dokumentů XML a fragmentů namísto přímého volání rozhraní API XML.</span><span class="sxs-lookup"><span data-stu-id="04765-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="04765-174">Importujte obory názvů XML na úrovni souboru nebo projektu, abyste mohli využít optimalizace výkonu pro literály XML.</span><span class="sxs-lookup"><span data-stu-id="04765-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="04765-175">Použijte vlastnosti osy XML pro přístup k prvkům a atributům v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="04765-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="04765-176">Použijte vložené výrazy pro zahrnutí hodnota a vytvoření XML z existujících hodnot namísto použití volání rozhraní API, jako `Add` metody:</span><span class="sxs-lookup"><span data-stu-id="04765-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="04765-177">Dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="04765-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="04765-178">Použijte smysluplné názvy proměnných dotazu:</span><span class="sxs-lookup"><span data-stu-id="04765-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
-   <span data-ttu-id="04765-179">Zadejte názvy prvků v dotazu a ujistěte se, že názvy vlastností anonymních typů mají správnou velikost písmen Pascal použití malých a velkých písmen:</span><span class="sxs-lookup"><span data-stu-id="04765-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
-   <span data-ttu-id="04765-180">Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku nejednoznačné.</span><span class="sxs-lookup"><span data-stu-id="04765-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="04765-181">Například pokud dotaz vrátí zákazníka, název a ID objednávky, přejmenujte je, než byste museli opustit jako `Name` a `ID` ve výsledku:</span><span class="sxs-lookup"><span data-stu-id="04765-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
-   <span data-ttu-id="04765-182">Odvození typu použijte v deklaraci proměnné dotazu a proměnných rozsahu:</span><span class="sxs-lookup"><span data-stu-id="04765-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
-   <span data-ttu-id="04765-183">Zarovnejte klauzule dotazu v `From` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="04765-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
-   <span data-ttu-id="04765-184">Použití `Where` klauzule před dalšími klauzulemi dotazu tak, aby pozdější klauzule dotazu pracovaly na filtrované sadě dat:</span><span class="sxs-lookup"><span data-stu-id="04765-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
-   <span data-ttu-id="04765-185">Použití `Join` klauzule k explicitnímu definování operace spojení namísto použití `Where` klauzule k implicitnímu definování operace spojení:</span><span class="sxs-lookup"><span data-stu-id="04765-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="04765-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04765-186">See also</span></span>

- [<span data-ttu-id="04765-187">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="04765-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
