---
title: Dokumentace kódu s XML – komentáře
description: Informace o dokumentu kódu s XML – dokumentační komentáře a generování souborů dokumentace XML v době kompilace.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1284f179c7debb323ea3bbd302df1f02bf8b31b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218502"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="37067-103">Dokumentace kódu s XML – komentáře</span><span class="sxs-lookup"><span data-stu-id="37067-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="37067-104">Dokumentační komentáře XML je zvláštní druh komentář, přidané v předchozím kroku definici uživatelem definovaný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="37067-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span> <span data-ttu-id="37067-105">Jsou speciální, protože může být zpracována kompilátorem ke generování souborů dokumentace XML v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="37067-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="37067-106">Kompilátoru vygeneruje soubor XML lze distribuovat souběžně s vaší sestavení .NET, tak, aby Visual Studio a dalších integrovaného vývojového prostředí pomocí technologie IntelliSense můžete zobrazit rychlé informace o typech nebo členy.</span><span class="sxs-lookup"><span data-stu-id="37067-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="37067-107">Kromě toho lze spustit soubor XML prostřednictvím nástrojů, například [DocFX](https://dotnet.github.io/docfx/) a [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) ke generování weby referenční dokumentace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="37067-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="37067-108">Dokumentační komentáře XML, podobně jako všechny ostatní komentáře se ignorují kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="37067-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="37067-109">Soubor XML můžete vygenerovat v době kompilace pomocí jedné z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="37067-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="37067-110">Pokud vyvíjíte aplikace s .NET Core z příkazového řádku, můžete přidat [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) k `<PropertyGroup>` části souboru .csproj projektů.</span><span class="sxs-lookup"><span data-stu-id="37067-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="37067-111">Následující příklad vytvoří soubor XML v adresáři projektu s stejný název kořenového souboru jako sestavení:</span><span class="sxs-lookup"><span data-stu-id="37067-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="37067-112">Můžete také zadat přesné absolutní nebo relativní cesta a název souboru XML.</span><span class="sxs-lookup"><span data-stu-id="37067-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="37067-113">Následující příklad vytvoří soubor XML ve stejném adresáři jako ladicí verze aplikace:</span><span class="sxs-lookup"><span data-stu-id="37067-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="37067-114">Pokud vyvíjíte aplikace pomocí sady Visual Studio, klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="37067-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="37067-115">V dialogovém okně Vlastnosti, vyberte **sestavení** a zkontrolujte **souborů dokumentace XML**.</span><span class="sxs-lookup"><span data-stu-id="37067-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="37067-116">Můžete také změnit umístění, do které kompilátor zapíše soubor.</span><span class="sxs-lookup"><span data-stu-id="37067-116">You can also change the location to which the compiler writes the file.</span></span> 

- <span data-ttu-id="37067-117">Pokud jsou kompilace rozhraní .NET Framework aplikace z příkazového řádku, přidejte [/doc – možnost kompilátoru](language-reference/compiler-options/doc-compiler-option.md) při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="37067-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="37067-118">XML – dokumentační komentáře použít Trojitá lomítka (`///`) a XML formátovaný text komentáře.</span><span class="sxs-lookup"><span data-stu-id="37067-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="37067-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="37067-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="37067-120">Návod</span><span class="sxs-lookup"><span data-stu-id="37067-120">Walkthrough</span></span>

<span data-ttu-id="37067-121">Projděme dokumentace knihovnu velmi základní matematické usnadnili pro nové vývojáře pochopit přispívat a třetích stran vývojářům používat.</span><span class="sxs-lookup"><span data-stu-id="37067-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="37067-122">Tady je kód pro knihovnu jednoduché matematické:</span><span class="sxs-lookup"><span data-stu-id="37067-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="37067-123">Ukázka knihovna podporuje čtyři hlavní aritmetické operace `add`, `subtract`, `multiply` a `divide` na `int` a `double` datové typy.</span><span class="sxs-lookup"><span data-stu-id="37067-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="37067-124">Nyní chcete být schopni vytvořit dokument referenční dokumentace rozhraní API z vašeho kódu pro vývojáře třetích stran, kteří použít knihovnu, ale nemáte přístup ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="37067-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="37067-125">Jako uvedených starší dokumentační značky XML lze použít k dosažení tohoto cíle, můžete nyní zavedl na standardní podporuje kompilátoru značky jazyka C# jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="37067-125">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="37067-126">&lt;Souhrn&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-126">&lt;summary&gt;</span></span>

<span data-ttu-id="37067-127">`<summary>` Značka přidá stručné informace o typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="37067-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="37067-128">I budete přidáním k předvedení jeho použití `Math` třídy definice a první `Add` metoda.</span><span class="sxs-lookup"><span data-stu-id="37067-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="37067-129">Nebojte se, že platí pro zbytek vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="37067-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="37067-130">`<summary>` Značka je velmi důležité, a doporučujeme, abyste ho použili vzhledem k tomu, že její obsah není primární zdroj informací pro typ nebo člen v IntelliSense nebo dokument referenční dokumentace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="37067-130">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="37067-131">&lt;Poznámky&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-131">&lt;remarks&gt;</span></span>

<span data-ttu-id="37067-132">`<remarks>` Značky doplňuje informace o typech nebo členy, `<summary>` poskytuje značky.</span><span class="sxs-lookup"><span data-stu-id="37067-132">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="37067-133">V tomto příkladu budete stačí přidat ji do třídy.</span><span class="sxs-lookup"><span data-stu-id="37067-133">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="37067-134">&lt;Vrátí&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-134">&lt;returns&gt;</span></span>

<span data-ttu-id="37067-135">`<returns>` Značky popisuje vrácenou hodnotu deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="37067-135">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="37067-136">Jak před, následující příklad ukazuje `<returns>` značky v prvním `Add` metoda.</span><span class="sxs-lookup"><span data-stu-id="37067-136">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="37067-137">Můžete provést stejný na jiné metody.</span><span class="sxs-lookup"><span data-stu-id="37067-137">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="37067-138">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-138">&lt;value&gt;</span></span>

<span data-ttu-id="37067-139">`<value>` Značka je podobná `<returns>` značka, s tím rozdílem, že použijete pro vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37067-139">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="37067-140">Za předpokladu, že vaše `Math` knihovny měl statickou vlastnost s názvem `PI`, zde je, jak použijete tuto značku:</span><span class="sxs-lookup"><span data-stu-id="37067-140">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="37067-141">&lt;Příklad&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-141">&lt;example&gt;</span></span>

<span data-ttu-id="37067-142">Můžete použít `<example>` značka, které zahrnují příklady v dokumentaci k XML.</span><span class="sxs-lookup"><span data-stu-id="37067-142">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="37067-143">To zahrnuje použití podřízených `<code>` značky.</span><span class="sxs-lookup"><span data-stu-id="37067-143">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="37067-144">`code` Značky zachovává konce řádků a odsazení delší příklady.</span><span class="sxs-lookup"><span data-stu-id="37067-144">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="37067-145">&lt;Para&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-145">&lt;para&gt;</span></span>

<span data-ttu-id="37067-146">Můžete použít `<para>` značky k formátování obsahu v rámci své nadřazené značky.</span><span class="sxs-lookup"><span data-stu-id="37067-146">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="37067-147">`<para>` obvykle používá uvnitř značky, jako například `<remarks>` nebo `<returns>`, k rozdělení text do odstavcích.</span><span class="sxs-lookup"><span data-stu-id="37067-147">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="37067-148">Můžete ho naformátovat obsah `<remarks>` značky pro vaše definice třídy.</span><span class="sxs-lookup"><span data-stu-id="37067-148">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="37067-149">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-149">&lt;c&gt;</span></span>

<span data-ttu-id="37067-150">Ještě na téma formátování, můžete použít `<c>` značky pro označení součástí textu jako kód.</span><span class="sxs-lookup"><span data-stu-id="37067-150">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="37067-151">Je třeba `<code>` značky, ale vložené.</span><span class="sxs-lookup"><span data-stu-id="37067-151">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="37067-152">Je vhodné, pokud chcete zobrazit příklad rychlé kódu v rámci obsah značky.</span><span class="sxs-lookup"><span data-stu-id="37067-152">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="37067-153">Umožňuje aktualizovat v dokumentaci `Math` třídy.</span><span class="sxs-lookup"><span data-stu-id="37067-153">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="37067-154">&lt;Výjimka&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-154">&lt;exception&gt;</span></span>

<span data-ttu-id="37067-155">Pomocí `<exception>` značky, umožníte vaší vývojáři vědět, že metoda může vyvolat konkrétní výjimky.</span><span class="sxs-lookup"><span data-stu-id="37067-155">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="37067-156">Prohlížení vaší `Math` knihovny, můžete uvidíte, že oba `Add` metody vyvolána výjimka, pokud je splněna určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="37067-156">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="37067-157">Není proto zřejmé, je ale, že celé číslo `Divide` metoda zjistí také, zda `b` parametr je nulová.</span><span class="sxs-lookup"><span data-stu-id="37067-157">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="37067-158">Nyní přidejte výjimka dokumentaci k této metodě.</span><span class="sxs-lookup"><span data-stu-id="37067-158">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="37067-159">`cref` Atribut představuje odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="37067-159">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="37067-160">Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="37067-160">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="37067-161">Kompilátor vás upozorní, pokud jeho hodnotu nelze přeložit.</span><span class="sxs-lookup"><span data-stu-id="37067-161">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="37067-162">&lt;V tématu&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-162">&lt;see&gt;</span></span>

<span data-ttu-id="37067-163">`<see>` Značka umožňuje vytvářet prokliknutelný odkaz na stránku dokumentace pro jiný element kódu.</span><span class="sxs-lookup"><span data-stu-id="37067-163">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="37067-164">V našem příkladu další vytvoříme prokliknutelný odkaz mezi těmito dvěma `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="37067-164">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="37067-165">`cref` Je **požadované** atribut, který představuje odkaz na typ nebo jeho člena, který je k dispozici z aktuální prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="37067-165">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span> <span data-ttu-id="37067-166">Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="37067-166">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="37067-167">&lt;Viz také&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-167">&lt;seealso&gt;</span></span>

<span data-ttu-id="37067-168">Můžete použít `<seealso>` značky stejným způsobem, jako je provést `<see>` značky.</span><span class="sxs-lookup"><span data-stu-id="37067-168">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="37067-169">Jediným rozdílem je, že jeho obsah je obvykle umístěny v části "V části Viz také".</span><span class="sxs-lookup"><span data-stu-id="37067-169">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="37067-170">Zde přidáme `seealso` značky na celé číslo `Add` metoda tak, aby odkazovaly jiných metod ve třídě, které přijímají celé číslo parametry:</span><span class="sxs-lookup"><span data-stu-id="37067-170">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="37067-171">`cref` Atribut představuje odkaz na typ nebo jeho člena, který je k dispozici z aktuální prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="37067-171">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="37067-172">Může to být libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="37067-172">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="37067-173">&lt;Param&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-173">&lt;param&gt;</span></span>

<span data-ttu-id="37067-174">Můžete použít `<param>` značka, které popisují parametry metody.</span><span class="sxs-lookup"><span data-stu-id="37067-174">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="37067-175">Tady je příklad na dvojitého `Add` metoda: je zadaný parametr popisuje značky v **požadované** `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="37067-175">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="37067-176">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-176">&lt;typeparam&gt;</span></span>

<span data-ttu-id="37067-177">Používáte `<typeparam>` značky podobně jako `<param>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="37067-177">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="37067-178">Přidání rychlé obecné metody pro vaše `Math` třídy ke kontrole, pokud jeden množství je větší než jiné.</span><span class="sxs-lookup"><span data-stu-id="37067-178">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="37067-179">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-179">&lt;paramref&gt;</span></span>

<span data-ttu-id="37067-180">V některých případech může být uprostřed popisující metodu provádí v co může být `<summary>` značku a budete chtít vytvořit odkaz na parametr.</span><span class="sxs-lookup"><span data-stu-id="37067-180">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="37067-181">`<paramref>` Značka je skvělá pro právě to.</span><span class="sxs-lookup"><span data-stu-id="37067-181">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="37067-182">Umožňuje na základě aktualizace souhrn naše dvojitou `Add` metoda.</span><span class="sxs-lookup"><span data-stu-id="37067-182">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="37067-183">Jako `<param>` značky je zadaný název parametru v **požadované** `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="37067-183">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="37067-184">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-184">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="37067-185">Používáte `<typeparamref>` značky podobně jako `<paramref>` značky, ale pro obecný typ nebo metoda deklarace k popisu obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="37067-185">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="37067-186">Můžete použít stejné obecné metody, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="37067-186">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="37067-187">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-187">&lt;list&gt;</span></span>

<span data-ttu-id="37067-188">Můžete použít `<list>` značky na formát dokumentaci informace jako uspořádaného seznamu, neuspořádaný seznam nebo tabulky.</span><span class="sxs-lookup"><span data-stu-id="37067-188">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="37067-189">Ujistěte se, neuspořádaný seznam každé matematické operace vaše `Math` knihovna podporuje.</span><span class="sxs-lookup"><span data-stu-id="37067-189">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="37067-190">Můžete nastavit uspořádaný seznam nebo tabulka změnou `type` atribut `number` nebo `table`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="37067-190">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="37067-191">Třeba umisťovat všechny společně</span><span class="sxs-lookup"><span data-stu-id="37067-191">Putting it all together</span></span>

<span data-ttu-id="37067-192">Pokud jste postupovali podle tohoto kurzu a použili značky v kódu potřeby, váš kód by teď měl vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="37067-192">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="37067-193">Z vašeho kódu můžete vygenerovat podrobnou dokumentaci webu, který je kompletní s prokliknutelný křížové odkazy.</span><span class="sxs-lookup"><span data-stu-id="37067-193">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="37067-194">Ale se potýkají s dalším problémem: kódu se stal těžko čitelný.</span><span class="sxs-lookup"><span data-stu-id="37067-194">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="37067-195">Existuje mnoho informace, které procházet, že to bude při důvodů pro všechny vývojáře, kdo chce podílet se na tento kód.</span><span class="sxs-lookup"><span data-stu-id="37067-195">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span> <span data-ttu-id="37067-196">Naštěstí je značky XML, který můžete zpracovat takové:</span><span class="sxs-lookup"><span data-stu-id="37067-196">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="37067-197">&lt;Zahrnout&gt;</span><span class="sxs-lookup"><span data-stu-id="37067-197">&lt;include&gt;</span></span>

<span data-ttu-id="37067-198">`<include>` Umožňuje značka odkazovat komentáře v samostatném souboru XML, které popisují typy a členy ve zdrojovém kódu, na rozdíl od umístění dokumentační komentáře ve zdrojovém kódu souboru přímo.</span><span class="sxs-lookup"><span data-stu-id="37067-198">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="37067-199">Teď se chystáte přesunout všechny značky XML do samostatného souboru XML s názvem `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="37067-199">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="37067-200">Nebojte se, že jste název souboru libovolně.</span><span class="sxs-lookup"><span data-stu-id="37067-200">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="37067-201">Ve výše uvedené souboru XML zobrazí dokumentační komentáře každý člen přímo uvnitř značky s názvem po co dělají.</span><span class="sxs-lookup"><span data-stu-id="37067-201">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="37067-202">Můžete si vlastní strategii.</span><span class="sxs-lookup"><span data-stu-id="37067-202">You can choose your own strategy.</span></span> <span data-ttu-id="37067-203">Nyní když máte komentáře XML v samostatném souboru, podíváme se, jak váš kód můžete provést srozumitelnější pomocí `<include>` značky:</span><span class="sxs-lookup"><span data-stu-id="37067-203">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="37067-204">A že máte: Naše kód je zpět do probíhá čtení a žádné informace dokumentace bylo ztraceno.</span><span class="sxs-lookup"><span data-stu-id="37067-204">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span> 

<span data-ttu-id="37067-205">`filename` Atribut představuje název souboru XML, který obsahuje v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="37067-205">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="37067-206">`path` Atribut představuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) dotazy s cílem `tag name` přítomen v zadané `filename`.</span><span class="sxs-lookup"><span data-stu-id="37067-206">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="37067-207">`name` Atribut představuje název specifikátor ve značce, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="37067-207">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="37067-208">`id` Atribut, který může být použit místo `name` reprezentuje ID pro značku, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="37067-208">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="37067-209">Uživatelem definované značky</span><span class="sxs-lookup"><span data-stu-id="37067-209">User Defined Tags</span></span>

<span data-ttu-id="37067-210">Všechny značky uvedených výše představují ty, které jsou rozpoznáno kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="37067-210">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="37067-211">Uživatel je však můžete definovat vlastní značky.</span><span class="sxs-lookup"><span data-stu-id="37067-211">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="37067-212">Nástroje, například aplikaci Sandcastle přineste podpory pro další značky [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) a i podpora [dokumentace obory názvů](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="37067-212">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="37067-213">Vlastní nebo nástroje pro generování interní dokumentace lze také standardní značkami a může podporovat více formátů výstup z kódu HTML do PDF.</span><span class="sxs-lookup"><span data-stu-id="37067-213">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="37067-214">Doporučení</span><span class="sxs-lookup"><span data-stu-id="37067-214">Recommendations</span></span>

<span data-ttu-id="37067-215">Dokumentace kódu se doporučuje z mnoha důvodů.</span><span class="sxs-lookup"><span data-stu-id="37067-215">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="37067-216">Jaké způsobem jsou některé osvědčené postupy Obecné použijte scénářích případů a další věci, které byste měli vědět, když pomocí dokumentace XML značky v kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="37067-216">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="37067-217">Z důvodu konzistence musí být zdokumentována všechny veřejně viditelný typy a jejich členové.</span><span class="sxs-lookup"><span data-stu-id="37067-217">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="37067-218">Pokud musíte to provést, proveďte všechny.</span><span class="sxs-lookup"><span data-stu-id="37067-218">If you must do it, do it all.</span></span>
* <span data-ttu-id="37067-219">Soukromé členy můžete rovněž popsány pomocí komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="37067-219">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="37067-220">To však zveřejňuje vnitřního (potenciálně důvěrné) chodu své knihovny.</span><span class="sxs-lookup"><span data-stu-id="37067-220">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="37067-221">Úplné, typy a jejich členové by měl mít minimálně `<summary>` značky, protože jeho obsah je potřeba pro technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="37067-221">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="37067-222">Dokumentace text by měly být zapsány pomocí dokončení věty konče úplné zastaví.</span><span class="sxs-lookup"><span data-stu-id="37067-222">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="37067-223">Částečné třídy jsou plně podporované a dokumentaci informace budou zřetězen do jeden záznam pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="37067-223">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="37067-224">Kompilátor ověřuje syntaxe `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` a `<typeparam>` značky.</span><span class="sxs-lookup"><span data-stu-id="37067-224">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="37067-225">Kompilátor ověří parametry, které obsahují cesty k souborům a odkazy na další části kódu.</span><span class="sxs-lookup"><span data-stu-id="37067-225">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="37067-226">Viz také</span><span class="sxs-lookup"><span data-stu-id="37067-226">See also</span></span>
[<span data-ttu-id="37067-227">Dokumentační komentáře XML (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="37067-227">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)

[<span data-ttu-id="37067-228">Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="37067-228">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
