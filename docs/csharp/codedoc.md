---
title: Dokumentace kódu pomocí komentářů XML
description: Zjistěte, jak váš kód, který se dokumentační komentáře XML dokumentu a generovat soubor dokumentace XML v době kompilace.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: e211543a6a5cc5f6f29d8c195492b474eb24a38d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584070"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="4eeb6-103">Dokumentace kódu pomocí komentářů XML</span><span class="sxs-lookup"><span data-stu-id="4eeb6-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="4eeb6-104">Dokumentační komentáře XML jsou zvláštním druhem komentáře přidané v předchozím kroku definice uživatelem definovaného typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="4eeb6-105">Jsou speciální, protože mohou být zpracovány kompilátor generuje soubor dokumentace XML v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="4eeb6-106">Soubor XML generované kompilátorem lze distribuovat spolu s sestavení .NET, tak, aby sada Visual Studio a jiná Integrovaná vývojová prostředí pomocí technologie IntelliSense můžete zobrazit rychlé informace o typech nebo členech.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="4eeb6-107">Kromě toho lze spustit soubor XML prostřednictvím nástrojů jako [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) ke generování websites referenční dokumentace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="4eeb6-108">Dokumentační komentáře XML, stejně jako všechny ostatní komentáře ignorovány kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="4eeb6-109">Soubor XML v době kompilace můžete vygenerovat pomocí jedné z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="4eeb6-110">Pokud vyvíjíte aplikaci .NET Core z příkazového řádku, můžete přidat [DocumentationFile element](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) k `<PropertyGroup>` část souboru projektu CSPROJ.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="4eeb6-111">Následující příklad generuje soubor XML v adresáři projektu se stejným názvem kořenového jako sestavení:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="4eeb6-112">Můžete také zadat přesné absolutní nebo relativní cestu a název souboru XML.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="4eeb6-113">Následující příklad generuje soubor XML ve stejném adresáři jako ladicí verze aplikace:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="4eeb6-114">Pokud vyvíjíte aplikace pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="4eeb6-115">V dialogovém okně Vlastnosti vyberte **sestavení** kartě a zaškrtněte **soubor dokumentace XML**.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="4eeb6-116">Můžete také změnit umístění, do které kompilátor zapíše soubor.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="4eeb6-117">Pokud kompilujete aplikace rozhraní .NET Framework z příkazového řádku, přidejte [/doc – možnost kompilátoru](language-reference/compiler-options/doc-compiler-option.md) při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="4eeb6-118">Dokumentační komentáře XML používat Trojitá lomítka (`///`) a XML formátovaný text komentáře.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="4eeb6-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="4eeb6-120">Názorný postup</span><span class="sxs-lookup"><span data-stu-id="4eeb6-120">Walkthrough</span></span>

<span data-ttu-id="4eeb6-121">Projděme si velmi základní matematické knihovny k tomu, aby noví vývojáři pochopit/přispívat a vývojářům třetích stran pomocí dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="4eeb6-122">Zde je kód pro jednoduché matematické knihovny:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="4eeb6-123">Ukázka knihovny podporuje čtyři hlavní aritmetické operace `add`, `subtract`, `multiply` a `divide` na `int` a `double` datové typy.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="4eeb6-124">Nyní chcete být schopni vytvořit dokument referenční dokumentace rozhraní API z kódu pro vývojáře třetích stran, kteří používají knihovny ale nemají přístup ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="4eeb6-125">Jak jsme už zmínili starší dokumentační značky XML je možné dosáhnout, jste nyní seznámili s standard podporuje kompilátoru značky jazyka C# jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-125">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="4eeb6-126">&lt;Souhrn&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-126">&lt;summary&gt;</span></span>

<span data-ttu-id="4eeb6-127">`<summary>` Značka přidá stručné informace o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="4eeb6-128">Vám předvedu jeho použití tak, že ji přidáte `Math` třídy definice a první `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="4eeb6-129">Můžete použít i pro zbývající část kódu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="4eeb6-130">`<summary>` Značka je velmi důležité, a doporučujeme, abyste ho použili protože obsah není primární zdroj informací pro typ nebo člen v IntelliSense nebo dokument referenční dokumentace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-130">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="4eeb6-131">&lt;Poznámky&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-131">&lt;remarks&gt;</span></span>

<span data-ttu-id="4eeb6-132">`<remarks>` Značky doplňuje informace o typech nebo členech, který `<summary>` poskytuje značky.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-132">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="4eeb6-133">V tomto příkladu budete stačí přidat jej do třídy.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-133">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="4eeb6-134">&lt;Vrátí&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-134">&lt;returns&gt;</span></span>

<span data-ttu-id="4eeb6-135">`<returns>` Značky popisuje vrácenou hodnotu deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-135">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="4eeb6-136">Jak předtím následující příklad ukazuje `<returns>` značky na první `Add` metoda.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-136">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="4eeb6-137">Můžete provést stejný na jiné metody.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-137">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="4eeb6-138">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-138">&lt;value&gt;</span></span>

<span data-ttu-id="4eeb6-139">`<value>` Značka je podobný `<returns>` značku, s tím rozdílem, že ji použijete k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-139">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="4eeb6-140">Za předpokladu, že vaše `Math` knihovny měl statickou vlastnost s názvem `PI`, zde je, jak můžete využít tuto značku:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-140">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="4eeb6-141">&lt;Příklad&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-141">&lt;example&gt;</span></span>

<span data-ttu-id="4eeb6-142">Můžete použít `<example>` značka, které zahrnují příklad v dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-142">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="4eeb6-143">To zahrnuje použití podřízených `<code>` značky.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-143">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="4eeb6-144">`code` Zachová značka konce řádků a odsazení delší příklady.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-144">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="4eeb6-145">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-145">&lt;para&gt;</span></span>

<span data-ttu-id="4eeb6-146">Můžete použít `<para>` značku k naformátování obsahu v rámci své nadřazené značky.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-146">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="4eeb6-147">`<para>` obvykle slouží uvnitř značky, například `<remarks>` nebo `<returns>`, k rozdělení textového na odstavcích.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-147">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="4eeb6-148">Obsah můžete naformátovat `<remarks>` značky pro vaší definice třídy.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-148">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="4eeb6-149">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-149">&lt;c&gt;</span></span>

<span data-ttu-id="4eeb6-150">Stále na téma formátování, použijte `<c>` značky pro označení část textu jako kód.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-150">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="4eeb6-151">Je třeba `<code>` značky, ale vložená.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-151">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="4eeb6-152">To je užitečné, pokud chcete zobrazit příklad rychlý kód jako součást obsahu na značku.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-152">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="4eeb6-153">Umožňuje aktualizovat dokumentaci pro `Math` třídy.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-153">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="4eeb6-154">&lt;Výjimka&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-154">&lt;exception&gt;</span></span>

<span data-ttu-id="4eeb6-155">S použitím `<exception>` značky, informovat vaše vývojáře, metoda může vyvolat specifických výjimek.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-155">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="4eeb6-156">Na vaše `Math` knihovny, vidíme, že oba `Add` metody vyvolání výjimky, pokud je splněna určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-156">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="4eeb6-157">Není to zřejmé, je však tento celé číslo `Divide` metoda vyvolá také, pokud `b` parametru je nula.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-157">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="4eeb6-158">Nyní přidáte výjimky dokumentace v této metodě.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-158">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="4eeb6-159">`cref` Atributu představuje odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-159">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="4eeb6-160">To může být libovolný typ definovaný v projektu nebo v odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-160">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="4eeb6-161">Kompilátor vydá upozornění, pokud jeho hodnotu nelze přeložit.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-161">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="4eeb6-162">&lt;V tématu&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-162">&lt;see&gt;</span></span>

<span data-ttu-id="4eeb6-163">`<see>` Značky vám umožní vytvářet prokliknutelný odkaz na stránku dokumentace pro jiný element kódu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-163">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="4eeb6-164">V našem dalším příkladu vytvoříme prokliknutelný odkaz mezi těmito dvěma `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-164">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="4eeb6-165">`cref` Je **požadované** atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-165">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="4eeb6-166">To může být libovolný typ definovaný v projektu nebo v odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-166">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="4eeb6-167">&lt;Viz také&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-167">&lt;seealso&gt;</span></span>

<span data-ttu-id="4eeb6-168">Můžete použít `<seealso>` značka stejným způsobem provedete `<see>` značky.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-168">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="4eeb6-169">Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "V části Viz také".</span><span class="sxs-lookup"><span data-stu-id="4eeb6-169">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="4eeb6-170">Tady přidáme `seealso` značku na celé číslo `Add` metoda odkazovat na jiné metody ve třídě, které přijímají celočíselné parametry:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-170">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="4eeb6-171">`cref` Atributu představuje odkaz na typ nebo jeho člen, který je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-171">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="4eeb6-172">To může být libovolný typ definovaný v projektu nebo v odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-172">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="4eeb6-173">&lt;Param&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-173">&lt;param&gt;</span></span>

<span data-ttu-id="4eeb6-174">Můžete použít `<param>` značka, které popisují parametry metody.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-174">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="4eeb6-175">Tady je příklad, double `Add` metoda: Parametr popisuje značka je zadán v **požadované** `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-175">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="4eeb6-176">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-176">&lt;typeparam&gt;</span></span>

<span data-ttu-id="4eeb6-177">Použijete `<typeparam>` označit stejně jako `<param>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-177">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="4eeb6-178">Přidat rychlé obecnou metodu pro vaše `Math` třídy zkontrolujte, jestli jedna množství je větší než druhý.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-178">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="4eeb6-179">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-179">&lt;paramref&gt;</span></span>

<span data-ttu-id="4eeb6-180">V některých případech může být uprostřed popisující, co dělá metodu v co může být `<summary>` značku a budete chtít vytvořit odkaz na parametr.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-180">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="4eeb6-181">`<paramref>` Značky se skvěle hodí pro právě to.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-181">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="4eeb6-182">Pojďme na základě aktualizace souhrn naše double `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-182">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="4eeb6-183">Podobně jako `<param>` značky název parametru je zadán v **požadované** `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-183">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="4eeb6-184">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-184">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="4eeb6-185">Použijete `<typeparamref>` označit stejně jako `<paramref>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-185">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="4eeb6-186">Můžete použít stejné obecné metody, které jste dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-186">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="4eeb6-187">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-187">&lt;list&gt;</span></span>

<span data-ttu-id="4eeb6-188">Můžete použít `<list>` značku a informací o formátování dokumentaci jako uspořádaného seznamu, neuspořádaný seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-188">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="4eeb6-189">Ujistěte se, Neseřazený seznam všech matematické operace vaše `Math` knihovna podporuje.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-189">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="4eeb6-190">Můžete dělat seřazený seznam nebo tabulku můžete změnit `type` atribut `number` nebo `table`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-190">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="4eeb6-191">Vložení všechno dohromady</span><span class="sxs-lookup"><span data-stu-id="4eeb6-191">Putting it all together</span></span>

<span data-ttu-id="4eeb6-192">Pokud jste postupovali podle tohoto kurzu a v případě potřeby použít značky pro váš kód, váš kód by teď měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-192">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="4eeb6-193">V kódu můžete vygenerovat kompletní s křížovými odkazy kliknout, čímž podrobnou dokumentaci webu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-193">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="4eeb6-194">Ale se potýkají s dalším problémem: váš kód přestal těžko čitelný.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-194">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="4eeb6-195">Existuje mnoho informace probrat se, že to bude připomínající každý vývojář, který chce, abyste mohli přispívat na tento kód.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-195">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="4eeb6-196">Naštěstí je značky XML, které vám to vyřešit:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-196">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="4eeb6-197">&lt;Zahrnout&gt;</span><span class="sxs-lookup"><span data-stu-id="4eeb6-197">&lt;include&gt;</span></span>

<span data-ttu-id="4eeb6-198">`<include>` Značky umožňuje odkazovat na komentáře v samostatném souboru jazyka XML, které popisují typy a členy ve zdrojovém kódu, na rozdíl od uvedení dokumentační komentáře přímo v souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-198">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="4eeb6-199">Teď se chystáte přesunout všechny značky XML do samostatného souboru XML s názvem `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-199">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="4eeb6-200">Nebojte se, že název souboru cokoliv, co chcete.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-200">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="4eeb6-201">V souboru XML výše uvedené se zobrazí každý člen dokumentační komentáře přímo uvnitř značky s názvem po co dělají.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-201">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="4eeb6-202">Můžete použít vlastní strategii.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-202">You can choose your own strategy.</span></span>
<span data-ttu-id="4eeb6-203">Teď, když máte komentáře XML v samostatném souboru, Podívejme se, jak váš kód lze pracovat pomocí `<include>` značky:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-203">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="4eeb6-204">A že máte: našeho kódu je zpět ke a nebyly ztraceny žádné informace o dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-204">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="4eeb6-205">`filename` Atribut představuje název souboru XML, který obsahuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-205">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="4eeb6-206">`path` Atributu představuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) dotaz pro `tag name` k dispozici v zadaném `filename`.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-206">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="4eeb6-207">`name` Atribut představuje název specifikátor ve značce, který předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-207">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="4eeb6-208">`id` Atribut, který lze použít místo `name` představuje ID značky, které předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-208">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="4eeb6-209">Uživatelem definované značky</span><span class="sxs-lookup"><span data-stu-id="4eeb6-209">User Defined Tags</span></span>

<span data-ttu-id="4eeb6-210">Všechny značky uvedených výše představují ty, které jsou rozpoznány modulem pro kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-210">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="4eeb6-211">Uživatel je však můžete definovat jejich vlastní značky.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-211">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="4eeb6-212">Nástroje, jako je Sandcastle přenést podpory pro další značky, jako jsou [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) a dokonce i podporu [dokumentace obory názvů](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="4eeb6-212">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="4eeb6-213">Vlastní nebo nástroje pro generování interní dokumentace lze také pomocí standardních značek a může podporovat více formátů výstupu z HTML do formátu PDF.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-213">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="4eeb6-214">Doporučení</span><span class="sxs-lookup"><span data-stu-id="4eeb6-214">Recommendations</span></span>

<span data-ttu-id="4eeb6-215">Dokumentace kódu se doporučuje pro mnoho důvodů, proč.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-215">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="4eeb6-216">Následují některé osvědčené postupy, hlavní scénáře použití a věci, které byste měli znát při použití dokumentace XML značky v kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-216">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="4eeb6-217">Pro účely konzistence musí být zdokumentována všechny veřejně viditelné typy a jejich členy.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-217">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="4eeb6-218">Pokud musíte to provést, to všechno.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-218">If you must do it, do it all.</span></span>
* <span data-ttu-id="4eeb6-219">Soukromé členy můžete rovněž popsány pomocí komentářů XML.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-219">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="4eeb6-220">Nicméně tato třída zveřejňuje vnitřní (potenciálně důvěrné) fungování své knihovny.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-220">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="4eeb6-221">Minimálně, by měly mít typy a členové `<summary>` značku, protože jeho obsah je potřeba pro technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-221">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="4eeb6-222">Text dokumentace by měly být zapsány pomocí úplných větách končí plně zastaví.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-222">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="4eeb6-223">Částečné třídy jsou plně podporované a informace o dokumentaci se nedá zřetězit do jedna položka u tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-223">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="4eeb6-224">Kompilátor ověří syntaxi `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` a `<typeparam>` značky.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-224">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="4eeb6-225">Kompilátor ověří parametry, které obsahují cesty k souborům a odkazy na ostatní části kódu.</span><span class="sxs-lookup"><span data-stu-id="4eeb6-225">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="4eeb6-226">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4eeb6-226">See also</span></span>

* [<span data-ttu-id="4eeb6-227">XML – dokumentační komentáře (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="4eeb6-227">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)
* [<span data-ttu-id="4eeb6-228">Doporučené značky pro dokumentační komentáře (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="4eeb6-228">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
