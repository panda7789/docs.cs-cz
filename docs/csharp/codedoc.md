---
title: Dokumentace kódu s komentáři XML
description: Naučte se dokumentovat kód pomocí dokumentačních komentářů XML a generovat soubor dokumentace XML v době kompilace.
ms.date: 02/14/2017
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 92a64a8f7a652f8b957013fc05f426e6b983655d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710993"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="9d6e2-103">Dokumentace kódu s komentáři XML</span><span class="sxs-lookup"><span data-stu-id="9d6e2-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="9d6e2-104">Komentáře dokumentace XML jsou zvláštním druhem komentáře, přidané nad definici libovolného uživatelsky definovaného typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="9d6e2-105">Jsou speciální, protože mohou být zpracovány kompilátorem pro generování souboru dokumentace XML v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="9d6e2-106">Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením .NET tak, aby Visual Studio a jiné prostředí pro vývoj mohli používat technologii IntelliSense k zobrazení rychlých informací o typech nebo členech.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="9d6e2-107">Navíc můžete soubor XML spustit prostřednictvím nástrojů, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , pro generování odkazů na webové stránky rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="9d6e2-108">Komentáře dokumentace XML, stejně jako všechny ostatní komentáře, jsou kompilátorem ignorovány.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="9d6e2-109">Soubor XML můžete vygenerovat v době kompilace jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="9d6e2-110">Pokud vyvíjíte aplikaci pomocí .NET Core z příkazového řádku, můžete přidat `GenerateDocumentationFile` element do části `<PropertyGroup>` souboru projektu. csproj.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="9d6e2-111">Můžete také zadat cestu k souboru dokumentace přímo pomocí [`DocumentationFile` elementu](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="9d6e2-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="9d6e2-112">Následující příklad generuje soubor XML v adresáři projektu se stejným kořenovým názvem souboru jako sestavení:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   <span data-ttu-id="9d6e2-113">To je ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-113">This is equivalent to the following:</span></span>
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="9d6e2-114">Pokud vyvíjíte aplikaci pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="9d6e2-115">V dialogovém okně Vlastnosti vyberte kartu **sestavení** a Prohlédněte si **soubor dokumentace XML**.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="9d6e2-116">Můžete také změnit umístění, do kterého kompilátor zapisuje soubor.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="9d6e2-117">Pokud kompilujete .NET Framework aplikaci z příkazového řádku, přidejte při kompilaci [možnost kompilátoru-doc](language-reference/compiler-options/doc-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="9d6e2-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="9d6e2-118">Komentáře dokumentace XML používají tři lomítka (`///`) a tělo komentáře ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="9d6e2-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="9d6e2-120">Podrobné</span><span class="sxs-lookup"><span data-stu-id="9d6e2-120">Walkthrough</span></span>

<span data-ttu-id="9d6e2-121">Pojďme si projít dokumentací velmi základní knihovny pro matematiku, abychom novým vývojářům usnadnili pochopení/přispívání a vývojářům třetích stran používat.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="9d6e2-122">Tady je kód pro jednoduchou knihovnu Math:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="9d6e2-123">Ukázková knihovna podporuje čtyři hlavní aritmetické operace `add`, `subtract`, `multiply` a `divide` na `int` a `double` datových typech.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="9d6e2-124">Nyní chcete být schopni vytvořit referenční dokument rozhraní API z kódu pro vývojáře třetích stran, kteří používají vaši knihovnu, ale nemají přístup ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="9d6e2-125">Jak bylo zmíněno dříve, můžete k tomuto účelu použít Tagy dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="9d6e2-126">Nyní budete zavedeni do standardních značek XML, které C# podporuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="9d6e2-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="9d6e2-127">\<summary></span></span>

<span data-ttu-id="9d6e2-128">Značka `<summary>` přidá stručné informace o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="9d6e2-129">Ukážeme jeho použití tím, že ho přidáte do definice `Math` třídy a první `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="9d6e2-130">Nebojte se použít pro zbytek kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="9d6e2-131">Značka `<summary>` je velmi důležitá a doporučujeme, abyste ji zahrnuli, protože její obsah je primárním zdrojem informací o typu nebo členu v IntelliSense nebo referenčním dokumentu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-131">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d6e2-132">\<poznámky ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-132">\<remarks></span></span>

<span data-ttu-id="9d6e2-133">Značka `<remarks>` doplňuje informace o typech nebo členech, které poskytuje značka `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="9d6e2-134">V tomto příkladu ho stačí přidat do třídy.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="9d6e2-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="9d6e2-135">\<returns></span></span>

<span data-ttu-id="9d6e2-136">Značka `<returns>` popisuje návratovou hodnotu deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="9d6e2-137">Jak dřív, následující příklad ukazuje značku `<returns>` prvního `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="9d6e2-138">Stejný postup můžete provést i pro jiné metody.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="9d6e2-139">\<value></span><span class="sxs-lookup"><span data-stu-id="9d6e2-139">\<value></span></span>

<span data-ttu-id="9d6e2-140">Značka `<value>` je podobná značce `<returns>`, s tím rozdílem, že ji použijete pro vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="9d6e2-141">Za předpokladu, že vaše knihovna `Math` měla statickou vlastnost nazvanou `PI`, tady je postup použití této značky:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="9d6e2-142">\<příklad ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-142">\<example></span></span>

<span data-ttu-id="9d6e2-143">Pomocí značky `<example>` můžete v dokumentaci XML zahrnout příklad.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="9d6e2-144">To zahrnuje použití podřízené značky `<code>`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="9d6e2-145">Značka `code` zachovává zalomení řádků a odsazení po delších příkladech.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="9d6e2-146">\<para ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-146">\<para></span></span>

<span data-ttu-id="9d6e2-147">Použijte značku `<para>` k formátování obsahu v rámci jeho nadřazené značky.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="9d6e2-148">`<para>` se obvykle používá uvnitř značky, jako je například `<remarks>` nebo `<returns>`, k rozdělení textu do odstavců.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="9d6e2-149">Můžete naformátovat obsah značky `<remarks>` pro definici třídy.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="9d6e2-150">\<c ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-150">\<c></span></span>

<span data-ttu-id="9d6e2-151">Stále v tématu formátování, použijte značku `<c>` pro označení části textu jako kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="9d6e2-152">Vypadá to jako značka `<code>`, ale je vložená.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="9d6e2-153">Je užitečné, pokud chcete zobrazit rychlý příklad kódu jako součást obsahu značky.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="9d6e2-154">Pojďme aktualizovat dokumentaci pro třídu `Math`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="9d6e2-155">výjimka \<</span><span class="sxs-lookup"><span data-stu-id="9d6e2-155">\<exception></span></span>

<span data-ttu-id="9d6e2-156">Pomocí značky `<exception>` umožníte vývojářům zjistit, že metoda může vyvolávat konkrétní výjimky.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="9d6e2-157">V knihovně `Math` můžete vidět, že obě metody `Add` vyvolávají výjimku, pokud je splněna určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="9d6e2-158">Není tak zřejmé, ale je to, že celočíselná `Divide` metoda vyvolá i v případě, že je parametr `b` nula.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="9d6e2-159">Nyní přidejte do této metody dokumentaci k výjimce.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="9d6e2-160">Atribut `cref` představuje odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="9d6e2-161">Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="9d6e2-162">Kompilátor vydá upozornění, pokud jeho hodnotu nelze vyřešit.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="9d6e2-163">\<Zobrazit ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-163">\<see></span></span>

<span data-ttu-id="9d6e2-164">Značka `<see>` umožňuje vytvořit odkaz s možnostmi kliknutí na stránku dokumentace pro jiný prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="9d6e2-165">V našem dalším příkladu vytvoříme odkaz kliknutí mezi dvěma metodami `Add`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="9d6e2-166">`cref` je **vyžadovaný** atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="9d6e2-167">Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="9d6e2-168">\<SeeAlso ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-168">\<seealso></span></span>

<span data-ttu-id="9d6e2-169">Značku `<seealso>` používáte stejným způsobem jako značku `<see>`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="9d6e2-170">Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "viz také".</span><span class="sxs-lookup"><span data-stu-id="9d6e2-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="9d6e2-171">Tady přidáme značku `seealso` na celočíselnou `Add` metodu, která bude odkazovat na jiné metody ve třídě, které přijímají celočíselné parametry:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="9d6e2-172">Atribut `cref` představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="9d6e2-173">Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="9d6e2-174">\<param></span><span class="sxs-lookup"><span data-stu-id="9d6e2-174">\<param></span></span>

<span data-ttu-id="9d6e2-175">Použijte značku `<param>` k popisu parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="9d6e2-176">Zde je příklad na metodě Double `Add`: parametr, který tag popisuje, je určen v atributu **required** `name`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="9d6e2-177">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-177">\<typeparam></span></span>

<span data-ttu-id="9d6e2-178">Použijete `<typeparam>` tag stejně jako `<param>` tag, ale pro deklarace obecného typu nebo metody pro popis obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="9d6e2-179">Přidejte rychlou obecnou metodu do třídy `Math`, abyste zkontrolovali, jestli je jedno množství větší než jiné.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="9d6e2-180">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-180">\<paramref></span></span>

<span data-ttu-id="9d6e2-181">Někdy se může stát, že popíšete, co metoda v co by mohla být značka `<summary>` a můžete chtít vytvořit odkaz na parametr.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="9d6e2-182">Označení `<paramref>` je skvělé jenom pro tento.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="9d6e2-183">Pojďme aktualizovat souhrn naší metody s dvojitou přesností `Add`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="9d6e2-184">Podobně jako u značky `<param>` je název parametru zadán v atributu **required** `name`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-184">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="9d6e2-185">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-185">\<typeparamref></span></span>

<span data-ttu-id="9d6e2-186">Použijete `<typeparamref>` tag stejně jako `<paramref>` tag, ale pro deklarace obecného typu nebo metody pro popis obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="9d6e2-187">Můžete použít stejnou obecnou metodu, kterou jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="9d6e2-188">seznam \<</span><span class="sxs-lookup"><span data-stu-id="9d6e2-188">\<list></span></span>

<span data-ttu-id="9d6e2-189">Pomocí značky `<list>` můžete formátovat informace o dokumentaci jako seřazený seznam, neuspořádaný seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="9d6e2-190">Vytvořte neuspořádaný seznam každé matematické operace, kterou podporuje knihovna `Math`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="9d6e2-191">Seřazený seznam nebo tabulku můžete vytvořit tak, že změníte atribut `type` na `number` nebo `table`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="9d6e2-192">Společné umístění</span><span class="sxs-lookup"><span data-stu-id="9d6e2-192">Putting it all together</span></span>

<span data-ttu-id="9d6e2-193">Pokud jste postupovali podle tohoto kurzu a v případě potřeby použili značky v kódu, váš kód by měl nyní vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-193">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="9d6e2-194">Z kódu můžete vygenerovat podrobný web dokumentace s dalšími odkazy, které lze kliknutím Procházet.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-194">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="9d6e2-195">Ale máte s ním jiný problém: váš kód se těžko čte.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-195">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="9d6e2-196">K dispozici je mnoho informací, které by bylo možné proprosévání, takže se jedná o Nightmare pro každého vývojáře, který chce přispívat k tomuto kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-196">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="9d6e2-197">Naštěstí se značka XML, která vám může pomáhat s tímto:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-197">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="9d6e2-198">\<zahrnout ></span><span class="sxs-lookup"><span data-stu-id="9d6e2-198">\<include></span></span>

<span data-ttu-id="9d6e2-199">Značka `<include>` umožňuje odkazování na komentáře v samostatném souboru XML, který popisuje typy a členy ve zdrojovém kódu, na rozdíl od umístění komentářů k dokumentaci přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-199">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="9d6e2-200">Nyní se chystáte přesunout všechny značky XML do samostatného souboru XML s názvem `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-200">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="9d6e2-201">Bez ohledu na název souboru si ho pojmenujte.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-201">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="9d6e2-202">Ve výše uvedeném kódu XML se komentáře k dokumentaci jednotlivých členů zobrazují přímo uvnitř značky s názvem, a to podle toho, co dělají.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-202">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="9d6e2-203">Můžete zvolit vlastní strategii.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-203">You can choose your own strategy.</span></span>
<span data-ttu-id="9d6e2-204">Teď, když máte komentáře XML v samostatném souboru, Podívejme se, jak může být váš kód čitelnější pomocí značky `<include>`:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-204">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="9d6e2-205">A tam máte: náš kód je zpátky čitelný a neztratily se žádné informace o dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-205">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="9d6e2-206">Atribut `file` představuje název souboru XML obsahujícího dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-206">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="9d6e2-207">Atribut `path` představuje dotaz [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) do `tag name` přítomného v zadaném `file`.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-207">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="9d6e2-208">Atribut `name` představuje specifikátor názvu ve značce, která předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-208">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="9d6e2-209">Atribut `id`, který lze použít místo `name` představuje ID značky, která předchází komentář.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-209">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="9d6e2-210">Uživatelsky definované značky</span><span class="sxs-lookup"><span data-stu-id="9d6e2-210">User Defined Tags</span></span>

<span data-ttu-id="9d6e2-211">Všechny značky, které jsou uvedeny výše, představují ty, které jsou rozpoznávány C# kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-211">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="9d6e2-212">Uživatel však může definovat vlastní značky.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-212">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="9d6e2-213">Nástroje, jako je Sandcastle, podporují i další značky, jako je [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) a dokonce i podporu [dokumentace oborů názvů](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="9d6e2-213">Tools like Sandcastle bring support for extra tags like [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="9d6e2-214">Je také možné použít vlastní nebo interní nástroje pro tvorbu dokumentace se standardními značkami a více výstupních formátů z formátu HTML do formátu PDF.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-214">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="9d6e2-215">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9d6e2-215">Recommendations</span></span>

<span data-ttu-id="9d6e2-216">Dokumentování kódu se doporučuje z mnoha důvodů.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-216">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="9d6e2-217">Níže jsou uvedeny některé osvědčené postupy, obecné scénáře použití a věci, které byste měli znát při použití značek dokumentace XML ve vašem C# kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-217">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="9d6e2-218">V zájmu konzistence by měly být zdokumentovány všechny veřejně viditelné typy a jejich členové.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-218">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="9d6e2-219">Pokud to musíte udělat, udělejte to vše.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-219">If you must do it, do it all.</span></span>
- <span data-ttu-id="9d6e2-220">Soukromé členy lze také zdokumentovat pomocí komentářů XML.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-220">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="9d6e2-221">To však zpřístupňuje vnitřní (potenciálně důvěrné) pracovní účely vaší knihovny.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-221">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="9d6e2-222">Minimální typy a jejich členové by měli mít `<summary>` značku, protože její obsah je potřebný pro IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-222">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="9d6e2-223">Text dokumentace by měl být napsán pomocí úplných vět končících s úplnými pozastávkami.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-223">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="9d6e2-224">Částečné třídy jsou plně podporovány a informace o dokumentaci budou zřetězeny do jediné položky pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-224">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="9d6e2-225">Kompilátor ověřuje syntaxi `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` a `<typeparam>` značek.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-225">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="9d6e2-226">Kompilátor ověřuje parametry, které obsahují cesty k souborům a odkazy na jiné části kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6e2-226">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d6e2-227">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d6e2-227">See also</span></span>

- [<span data-ttu-id="9d6e2-228">Komentáře dokumentace XML (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="9d6e2-228">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="9d6e2-229">Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="9d6e2-229">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
