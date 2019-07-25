---
title: Visual Basic – konvence kódování
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 580a6e1caa78ea981b6d2be68a6e7c61e2ad55d7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433814"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="8844c-102">Visual Basic – konvence kódování</span><span class="sxs-lookup"><span data-stu-id="8844c-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="8844c-103">Společnost Microsoft vyvíjí ukázky a dokumentaci, které se řídí pokyny v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8844c-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="8844c-104">Pokud se řídíte stejnými konvencemi kódování, můžete získat následující výhody:</span><span class="sxs-lookup"><span data-stu-id="8844c-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="8844c-105">Váš kód bude mít konzistentní vzhled, aby se čtenáři mohli lépe soustředit na obsah, nikoli na rozložení.</span><span class="sxs-lookup"><span data-stu-id="8844c-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="8844c-106">Čtenáři porozuměli kódu rychleji, protože mohou vytvářet předpoklady na základě předchozích zkušeností.</span><span class="sxs-lookup"><span data-stu-id="8844c-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="8844c-107">Kód můžete snadněji kopírovat, měnit a udržovat.</span><span class="sxs-lookup"><span data-stu-id="8844c-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="8844c-108">Pomůžete zajistit, aby váš kód předvádí "osvědčené postupy" pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8844c-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="8844c-109">Konvence vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="8844c-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="8844c-110">Informace o pokynech pro pojmenování najdete v tématu [pokyny](../../../standard/design-guidelines/naming-guidelines.md) pro pojmenování.</span><span class="sxs-lookup"><span data-stu-id="8844c-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="8844c-111">Nepoužívejte "my" nebo "my" jako součást názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="8844c-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="8844c-112">Tento postup vytváří nejasnost s `My` objekty.</span><span class="sxs-lookup"><span data-stu-id="8844c-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="8844c-113">Nemusíte měnit názvy objektů v automaticky generovaném kódu, aby se vešly podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="8844c-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="8844c-114">Konvence rozložení</span><span class="sxs-lookup"><span data-stu-id="8844c-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="8844c-115">Vložte tabulátory jako mezery a používejte inteligentní odsazení se čtyřmi mezerami.</span><span class="sxs-lookup"><span data-stu-id="8844c-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="8844c-116">Použijte k přeformátování kódu v editoru kódu formátování (přeformátování **)** .</span><span class="sxs-lookup"><span data-stu-id="8844c-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="8844c-117">Další informace najdete v tématu [Možnosti, textový editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8844c-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="8844c-118">Použijte pouze jeden příkaz na řádek.</span><span class="sxs-lookup"><span data-stu-id="8844c-118">Use only one statement per line.</span></span> <span data-ttu-id="8844c-119">Nepoužívejte znak oddělovače Visual Basic čáry (:).</span><span class="sxs-lookup"><span data-stu-id="8844c-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="8844c-120">Vyhněte se použití znaku explicitního pokračování řádku "_" místo implicitního pokračování řádku, kdykoli to jazyk umožňuje.</span><span class="sxs-lookup"><span data-stu-id="8844c-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="8844c-121">Použijte pouze jednu deklaraci na řádek.</span><span class="sxs-lookup"><span data-stu-id="8844c-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="8844c-122">Pokud je **v podstatě výpis (přeformátování) kódu** neformátované řádky pokračování automaticky, odsadí řádky pokračování jednu zarážku tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="8844c-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="8844c-123">V seznamu ale vždycky zarovnáváme položky vlevo.</span><span class="sxs-lookup"><span data-stu-id="8844c-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="8844c-124">Mezi definice metod a vlastností přidejte alespoň jeden prázdný řádek.</span><span class="sxs-lookup"><span data-stu-id="8844c-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="8844c-125">Konvence při psaní komentářů</span><span class="sxs-lookup"><span data-stu-id="8844c-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="8844c-126">Komentáře umístěte na samostatný řádek místo na konci řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="8844c-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="8844c-127">Začněte text komentáře velkým písmenem a ukončete text komentáře s tečkou.</span><span class="sxs-lookup"><span data-stu-id="8844c-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="8844c-128">Vložte jednu mezeru mezi oddělovač komentáře (') a text komentáře.</span><span class="sxs-lookup"><span data-stu-id="8844c-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="8844c-129">Nezadávejte komentáře pomocí formátovaných bloků hvězdiček.</span><span class="sxs-lookup"><span data-stu-id="8844c-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="8844c-130">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="8844c-130">Program Structure</span></span>  
  
- <span data-ttu-id="8844c-131">Při použití `Main` metody použijte výchozí konstrukci pro nové konzolové aplikace a použijte `My` pro argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8844c-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="8844c-132">Pokyny pro jazyk</span><span class="sxs-lookup"><span data-stu-id="8844c-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="8844c-133">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="8844c-133">String Data Type</span></span>  
  
- <span data-ttu-id="8844c-134">Použijte [interpolaci řetězce](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) k zřetězení krátkých řetězců, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8844c-134">Use [string interpolation](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="8844c-135">Chcete-li připojit řetězce ve smyčce, použijte <xref:System.Text.StringBuilder> objekt.</span><span class="sxs-lookup"><span data-stu-id="8844c-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="8844c-136">Odlehčení Delegáti v obslužných rutinách událostí</span><span class="sxs-lookup"><span data-stu-id="8844c-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="8844c-137">Explicitně nekvalifikovat argumenty (Object a EventArgs) pro obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="8844c-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="8844c-138">Pokud nepoužíváte argumenty události, které jsou předány události (například odesilatel jako objekt, e jako EventArgs), použijte odlehčené delegáty a vynechte argumenty události v kódu:</span><span class="sxs-lookup"><span data-stu-id="8844c-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="8844c-139">Nepodepsaný datový typ</span><span class="sxs-lookup"><span data-stu-id="8844c-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="8844c-140">Použijte `Integer` spíše než typy bez znaménka, s výjimkou případů, kdy jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="8844c-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="8844c-141">Pole</span><span class="sxs-lookup"><span data-stu-id="8844c-141">Arrays</span></span>  
  
- <span data-ttu-id="8844c-142">Použijte krátkou syntaxi při inicializaci polí na řádku deklarace.</span><span class="sxs-lookup"><span data-stu-id="8844c-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="8844c-143">Použijte například následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="8844c-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="8844c-144">Nepoužívejte následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="8844c-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="8844c-145">Uveďte označení pole pro typ, nikoli proměnnou.</span><span class="sxs-lookup"><span data-stu-id="8844c-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="8844c-146">Použijte například následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="8844c-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="8844c-147">Nepoužívejte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="8844c-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="8844c-148">Použijte syntaxi {} při deklaraci a inicializaci polí základních datových typů.</span><span class="sxs-lookup"><span data-stu-id="8844c-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="8844c-149">Použijte například následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="8844c-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="8844c-150">Nepoužívejte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="8844c-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="8844c-151">Použití klíčového slova with</span><span class="sxs-lookup"><span data-stu-id="8844c-151">Use the With Keyword</span></span>  
 <span data-ttu-id="8844c-152">Při vytváření řady volání jednoho objektu zvažte použití `With` klíčového slova:</span><span class="sxs-lookup"><span data-stu-id="8844c-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="8844c-153">Použijte try... Zachytit a použít příkazy při zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="8844c-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="8844c-154">Nepoužívejte `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="8844c-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="8844c-155">Použití klíčového slova IsNot</span><span class="sxs-lookup"><span data-stu-id="8844c-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="8844c-156">Místo použijte `IsNot` klíčové slovo `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="8844c-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="8844c-157">New – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="8844c-157">New Keyword</span></span>  
  
- <span data-ttu-id="8844c-158">Používejte krátkodobé vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="8844c-158">Use short instantiation.</span></span> <span data-ttu-id="8844c-159">Použijte například následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="8844c-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="8844c-160">Předchozí řádek je podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="8844c-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="8844c-161">Použít inicializátory objektů pro nové objekty místo konstruktoru bez parametrů:</span><span class="sxs-lookup"><span data-stu-id="8844c-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="8844c-162">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="8844c-162">Event Handling</span></span>  
  
- <span data-ttu-id="8844c-163">`Handles` Použijte`AddHandler`místo:</span><span class="sxs-lookup"><span data-stu-id="8844c-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="8844c-164">Použijte `AddressOf`, a nevytvářejte instanci delegáta explicitně:</span><span class="sxs-lookup"><span data-stu-id="8844c-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="8844c-165">Při definování události použijte krátkou syntaxi a nechejte kompilátor definovat delegáta:</span><span class="sxs-lookup"><span data-stu-id="8844c-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="8844c-166">Neověřuje, zda je `Nothing` událost (null) před `RaiseEvent` voláním metody.</span><span class="sxs-lookup"><span data-stu-id="8844c-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="8844c-167">`RaiseEvent`zkontroluje, `Nothing` než se událost vyvolá.</span><span class="sxs-lookup"><span data-stu-id="8844c-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="8844c-168">Použití sdílených členů</span><span class="sxs-lookup"><span data-stu-id="8844c-168">Using Shared Members</span></span>  
 <span data-ttu-id="8844c-169">Volejte `Shared` členy pomocí názvu třídy, nikoli z proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="8844c-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="8844c-170">Použití literálů XML</span><span class="sxs-lookup"><span data-stu-id="8844c-170">Use XML Literals</span></span>  
 <span data-ttu-id="8844c-171">Literály XML zjednodušují nejběžnější úlohy, které se vyskytnou při práci s XML (například načtení, dotazování a transformace).</span><span class="sxs-lookup"><span data-stu-id="8844c-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="8844c-172">Při vývoji s jazykem XML postupujte podle těchto pokynů:</span><span class="sxs-lookup"><span data-stu-id="8844c-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="8844c-173">Použijte literály XML k vytvoření dokumentů a fragmentů XML namísto přímého volání rozhraní API XML.</span><span class="sxs-lookup"><span data-stu-id="8844c-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="8844c-174">Importujte obory názvů XML na úrovni souboru nebo projektu, abyste mohli využívat optimalizace výkonu pro literály XML.</span><span class="sxs-lookup"><span data-stu-id="8844c-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="8844c-175">Použijte Vlastnosti osy XML pro přístup k prvkům a atributům v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="8844c-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="8844c-176">Vložené výrazy použijte k zahrnutí hodnot a k vytvoření XML z existujících hodnot namísto použití volání rozhraní API, jako je `Add` například metoda:</span><span class="sxs-lookup"><span data-stu-id="8844c-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="8844c-177">Dotazy LINQ</span><span class="sxs-lookup"><span data-stu-id="8844c-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="8844c-178">Pro proměnné dotazů použijte smysluplné názvy:</span><span class="sxs-lookup"><span data-stu-id="8844c-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="8844c-179">Zadejte názvy prvků v dotazu, abyste se ujistili, že názvy vlastností anonymních typů jsou správně velkými písmeny v jazyce Pascal:</span><span class="sxs-lookup"><span data-stu-id="8844c-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="8844c-180">Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku byly dvojznačné.</span><span class="sxs-lookup"><span data-stu-id="8844c-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="8844c-181">Například pokud váš dotaz vrátí název zákazníka a ID objednávky, přejmenujte ho místo toho `Name` , aby a `ID` ve výsledku:</span><span class="sxs-lookup"><span data-stu-id="8844c-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="8844c-182">Použijte odvození typu v deklaraci proměnných dotazu a proměnných rozsahu:</span><span class="sxs-lookup"><span data-stu-id="8844c-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="8844c-183">Zarovnat klauzule dotazu pod `From` příkazem:</span><span class="sxs-lookup"><span data-stu-id="8844c-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="8844c-184">Klauzule `Where` použijte před ostatními klauzulemi dotazu tak, aby pozdější klauzule dotazu pracovaly na filtrované sadě dat:</span><span class="sxs-lookup"><span data-stu-id="8844c-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="8844c-185">Použijte klauzuli k explicitnímu definování operace spojení namísto `Where` použití klauzule k implicitnímu definování operace spojení: `Join`</span><span class="sxs-lookup"><span data-stu-id="8844c-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="8844c-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8844c-186">See also</span></span>

- [<span data-ttu-id="8844c-187">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="8844c-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
