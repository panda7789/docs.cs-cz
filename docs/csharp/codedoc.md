---
title: Dokumentace kódu pomocí komentářů XML
description: Zjistěte, jak dokumentovat kód pomocí komentářů v dokumentaci XML a vygenerovat soubor dokumentace XML v době kompilace.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ed39c4733c36b3932fcb85bf50d4f4c0e53aa6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146314"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="84ac7-103">Dokumentování kódu pomocí komentářů XML</span><span class="sxs-lookup"><span data-stu-id="84ac7-103">Document your code with XML comments</span></span>

<span data-ttu-id="84ac7-104">Komentáře k dokumentaci XML jsou zvláštním druhem komentáře, který je přidán nad definici libovolného uživatelem definovaného typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="84ac7-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="84ac7-105">Jsou zvláštní, protože mohou být zpracovány kompilátorem pro generování souboru dokumentace XML v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="84ac7-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="84ac7-106">Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením rozhraní .NET, aby visual studio a další idemohly pomocí technologie IntelliSense zobrazit rychlé informace o typech nebo členech.</span><span class="sxs-lookup"><span data-stu-id="84ac7-106">The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="84ac7-107">Soubor XML lze navíc spustit prostřednictvím nástrojů, jako jsou [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle,](https://github.com/EWSoftware/SHFB) které generují referenční webové stránky rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="84ac7-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="84ac7-108">Komentáře dokumentace XML, stejně jako všechny ostatní komentáře, jsou kompilátorem ignorovány.</span><span class="sxs-lookup"><span data-stu-id="84ac7-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="84ac7-109">Soubor XML můžete vygenerovat v době kompilace jedním z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="84ac7-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="84ac7-110">Pokud vyvíjíte aplikaci s rozhraním .NET Core z `GenerateDocumentationFile` příkazového `<PropertyGroup>` řádku, můžete přidat prvek do části souboru projektu .csproj.</span><span class="sxs-lookup"><span data-stu-id="84ac7-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="84ac7-111">Cestu k souboru dokumentace můžete také zadat přímo pomocí [ `DocumentationFile` elementu](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="84ac7-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="84ac7-112">Následující příklad generuje soubor XML v adresáři projektu se stejným kořenovým názvem jako sestavení:</span><span class="sxs-lookup"><span data-stu-id="84ac7-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   <span data-ttu-id="84ac7-113">To odpovídá následujícímu:</span><span class="sxs-lookup"><span data-stu-id="84ac7-113">This is equivalent to the following:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="84ac7-114">Pokud vyvíjíte aplikaci pomocí sady Visual Studio, klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="84ac7-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="84ac7-115">V dialogovém okně vlastností vyberte kartu **Sestavení** a **zkontrolujte soubor dokumentace XML**.</span><span class="sxs-lookup"><span data-stu-id="84ac7-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="84ac7-116">Můžete také změnit umístění, do kterého kompilátor zapíše soubor.</span><span class="sxs-lookup"><span data-stu-id="84ac7-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="84ac7-117">Pokud kompilujete aplikaci rozhraní .NET Framework z příkazového řádku, přidejte při kompilaci [možnost kompilátoru -doc.](language-reference/compiler-options/doc-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="84ac7-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="84ac7-118">Komentáře k dokumentaci XML`///`používají trojitá lomítka ( ) a text komentáře ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="84ac7-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="84ac7-119">Například:</span><span class="sxs-lookup"><span data-stu-id="84ac7-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="84ac7-120">Názorný postup</span><span class="sxs-lookup"><span data-stu-id="84ac7-120">Walkthrough</span></span>

<span data-ttu-id="84ac7-121">Pojďme projít dokumentování velmi základní matematické knihovny, aby bylo snadné pro nové vývojáře pochopit / přispět a pro vývojáře třetích stran k použití.</span><span class="sxs-lookup"><span data-stu-id="84ac7-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="84ac7-122">Zde je kód pro jednoduchou knihovnu matematiky:</span><span class="sxs-lookup"><span data-stu-id="84ac7-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="84ac7-123">Ukázková knihovna podporuje čtyři hlavní`add`aritmetické operace ( , `subtract`, `multiply`, `divide`a ) a `int` `double` datové typy.</span><span class="sxs-lookup"><span data-stu-id="84ac7-123">The sample library supports four major arithmetic operations (`add`, `subtract`, `multiply`, and `divide`) on `int` and `double` data types.</span></span>

<span data-ttu-id="84ac7-124">Nyní chcete mít možnost vytvořit referenční dokument rozhraní API z vašeho kódu pro vývojáře třetích stran, kteří používají vaši knihovnu, ale nemají přístup ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="84ac7-125">Jak již bylo zmíněno dříve XML dokumentace značky lze použít k dosažení tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="84ac7-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="84ac7-126">Nyní se zobrazí standardní značky XML, které kompilátor Jazyka C# podporuje.</span><span class="sxs-lookup"><span data-stu-id="84ac7-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="84ac7-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="84ac7-127">\<summary></span></span>

<span data-ttu-id="84ac7-128">Značka `<summary>` přidá stručné informace o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="84ac7-129">Budu demonstrovat jeho použití přidáním `Math` do definice `Add` třídy a první metody.</span><span class="sxs-lookup"><span data-stu-id="84ac7-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="84ac7-130">Nebojte se použít na zbytek kódu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="84ac7-131">Značka `<summary>` je důležitá a doporučujeme ji zahrnout, protože její obsah je primárním zdrojem informací typu nebo člena v aplikaci IntelliSense nebo referenčním dokumentu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="84ac7-131">The `<summary>` tag is important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="84ac7-132">\<poznámky></span><span class="sxs-lookup"><span data-stu-id="84ac7-132">\<remarks></span></span>

<span data-ttu-id="84ac7-133">Značka `<remarks>` doplňuje informace o typech `<summary>` nebo členech, které značka poskytuje.</span><span class="sxs-lookup"><span data-stu-id="84ac7-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="84ac7-134">V tomto příkladu jej přidáte do třídy.</span><span class="sxs-lookup"><span data-stu-id="84ac7-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="84ac7-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="84ac7-135">\<returns></span></span>

<span data-ttu-id="84ac7-136">Značka `<returns>` popisuje vrácenou hodnotu deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="84ac7-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="84ac7-137">Stejně jako dříve, následující `<returns>` příklad ilustruje `Add` značku na první metodě.</span><span class="sxs-lookup"><span data-stu-id="84ac7-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="84ac7-138">Totéž můžete udělat s jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="84ac7-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="84ac7-139">\<value></span><span class="sxs-lookup"><span data-stu-id="84ac7-139">\<value></span></span>

<span data-ttu-id="84ac7-140">Značka `<value>` je podobná `<returns>` značce s tím rozdílem, že ji používáte pro vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="84ac7-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="84ac7-141">Za `Math` předpokladu, že `PI`vaše knihovna měla statickou vlastnost nazvanou , použijte tuto značku takto:</span><span class="sxs-lookup"><span data-stu-id="84ac7-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="84ac7-142">\<příklad></span><span class="sxs-lookup"><span data-stu-id="84ac7-142">\<example></span></span>

<span data-ttu-id="84ac7-143">`<example>` Značku slouží k zahrnutí příkladu do dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="84ac7-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="84ac7-144">To zahrnuje použití `<code>` podřízené značky.</span><span class="sxs-lookup"><span data-stu-id="84ac7-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="84ac7-145">Značka `code` zachová konce řádků a odsazení pro delší příklady.</span><span class="sxs-lookup"><span data-stu-id="84ac7-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="84ac7-146">\<para></span><span class="sxs-lookup"><span data-stu-id="84ac7-146">\<para></span></span>

<span data-ttu-id="84ac7-147">`<para>` Značku slouží k formátování obsahu v rámci nadřazené značky.</span><span class="sxs-lookup"><span data-stu-id="84ac7-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="84ac7-148">`<para>`se obvykle používá uvnitř značky, například `<remarks>` nebo `<returns>`, k rozdělení textu na odstavce.</span><span class="sxs-lookup"><span data-stu-id="84ac7-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="84ac7-149">Obsah značky `<remarks>` můžete formátovat pro definici třídy.</span><span class="sxs-lookup"><span data-stu-id="84ac7-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="84ac7-150">\<c></span><span class="sxs-lookup"><span data-stu-id="84ac7-150">\<c></span></span>

<span data-ttu-id="84ac7-151">Stále na téma formátování, můžete použít `<c>` značku pro označení části textu jako kód.</span><span class="sxs-lookup"><span data-stu-id="84ac7-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="84ac7-152">Je to jako `<code>` značka, ale inline.</span><span class="sxs-lookup"><span data-stu-id="84ac7-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="84ac7-153">Je to užitečné, když chcete zobrazit příklad rychlého kódu jako součást obsahu značky.</span><span class="sxs-lookup"><span data-stu-id="84ac7-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="84ac7-154">Pojďme aktualizovat dokumentaci `Math` pro třídu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="84ac7-155">\<výjimka></span><span class="sxs-lookup"><span data-stu-id="84ac7-155">\<exception></span></span>

<span data-ttu-id="84ac7-156">Pomocí značky, `<exception>` dejte vývojářům vědět, že metoda může vyvolat konkrétní výjimky.</span><span class="sxs-lookup"><span data-stu-id="84ac7-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="84ac7-157">Při pohledu na `Math` knihovnu, `Add` uvidíte, že obě metody vyvolat výjimku, pokud je splněna určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="84ac7-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="84ac7-158">Není to však tak zřejmé, `Divide` že celá metoda `b` vyvolá také, pokud je parametr nula.</span><span class="sxs-lookup"><span data-stu-id="84ac7-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="84ac7-159">Nyní přidejte dokumentaci výjimky k této metodě.</span><span class="sxs-lookup"><span data-stu-id="84ac7-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="84ac7-160">Atribut `cref` představuje odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="84ac7-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="84ac7-161">Může se jedná o libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="84ac7-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="84ac7-162">Kompilátor vydá upozornění, pokud jeho hodnotu nelze vyřešit.</span><span class="sxs-lookup"><span data-stu-id="84ac7-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="84ac7-163">\<viz></span><span class="sxs-lookup"><span data-stu-id="84ac7-163">\<see></span></span>

<span data-ttu-id="84ac7-164">Značka `<see>` umožňuje vytvořit odkaz na stránku dokumentace, na který lze kliknout pro jiný prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="84ac7-165">V našem dalším příkladu vytvoříme odkaz, na `Add` který lze kliknout mezi těmito dvěma metodami.</span><span class="sxs-lookup"><span data-stu-id="84ac7-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="84ac7-166">Je `cref` **povinný** atribut, který představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="84ac7-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="84ac7-167">Může se jedná o libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="84ac7-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="84ac7-168">\<seealso></span><span class="sxs-lookup"><span data-stu-id="84ac7-168">\<seealso></span></span>

<span data-ttu-id="84ac7-169">`<seealso>` Značku používáte stejným způsobem jako `<see>` značka.</span><span class="sxs-lookup"><span data-stu-id="84ac7-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="84ac7-170">Jediným rozdílem je, že jeho obsah je obvykle umístěn v části "Viz také".</span><span class="sxs-lookup"><span data-stu-id="84ac7-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="84ac7-171">Zde přidáme `seealso` značku na metodu `Add` celého čísla, abychom odkazovali na jiné metody ve třídě, které přijímají parametry celého čísla:</span><span class="sxs-lookup"><span data-stu-id="84ac7-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="84ac7-172">Atribut `cref` představuje odkaz na typ nebo jeho člen, který je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="84ac7-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="84ac7-173">Může se jedná o libovolný typ definovaný v projektu nebo odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="84ac7-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="84ac7-174">\<param></span><span class="sxs-lookup"><span data-stu-id="84ac7-174">\<param></span></span>

<span data-ttu-id="84ac7-175">`<param>` Značku slouží k popisu parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="84ac7-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="84ac7-176">Zde je příklad metody `Add` double: Parametr, který značka popisuje, je zadán v **požadovaném** `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="84ac7-177">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="84ac7-177">\<typeparam></span></span>

<span data-ttu-id="84ac7-178">Značku `<typeparam>` používáte stejně jako značka, `<param>` ale pro obecné deklarace typu nebo metody k popisu obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="84ac7-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="84ac7-179">Přidejte do `Math` třídy rychlou obecnou metodu a zkontrolujte, zda je jedno množství větší než jiné.</span><span class="sxs-lookup"><span data-stu-id="84ac7-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="84ac7-180">\<paramref></span><span class="sxs-lookup"><span data-stu-id="84ac7-180">\<paramref></span></span>

<span data-ttu-id="84ac7-181">Někdy můžete být uprostřed popisu toho, co metoda dělá `<summary>` v čem by mohla být značka, a možná budete chtít vytvořit odkaz na parametr.</span><span class="sxs-lookup"><span data-stu-id="84ac7-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="84ac7-182">Značka `<paramref>` je skvělá právě pro toto.</span><span class="sxs-lookup"><span data-stu-id="84ac7-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="84ac7-183">Pojďme aktualizovat souhrn naší dvojité `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="84ac7-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="84ac7-184">Podobně `<param>` jako značka je název parametru zadán v **požadovaném** `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-184">Like the `<param>` tag, the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="84ac7-185">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="84ac7-185">\<typeparamref></span></span>

<span data-ttu-id="84ac7-186">Značku `<typeparamref>` používáte stejně jako značka, `<paramref>` ale pro obecné deklarace typu nebo metody k popisu obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="84ac7-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="84ac7-187">Můžete použít stejnou obecnou metodu, kterou jste dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="84ac7-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="84ac7-188">\<seznam></span><span class="sxs-lookup"><span data-stu-id="84ac7-188">\<list></span></span>

<span data-ttu-id="84ac7-189">`<list>` Značka slouží k formátování informací o dokumentaci jako uspořádaný seznam, neuspořádaný seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="84ac7-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list, or table.</span></span> <span data-ttu-id="84ac7-190">Vytvořte neuspořádaný seznam všech `Math` matematických operací, které vaše knihovna podporuje.</span><span class="sxs-lookup"><span data-stu-id="84ac7-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="84ac7-191">Seřazený seznam nebo tabulku `type` můžete `number` `table`vytvořit změnou atributu nebo .</span><span class="sxs-lookup"><span data-stu-id="84ac7-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

## <a name="inheritdoc"></a><span data-ttu-id="84ac7-192">\<inheritdoc></span><span class="sxs-lookup"><span data-stu-id="84ac7-192">\<inheritdoc></span></span>

<span data-ttu-id="84ac7-193">`<inheritdoc>` Značku můžete použít k dědění komentářů XML ze základních tříd, rozhraní a podobných metod.</span><span class="sxs-lookup"><span data-stu-id="84ac7-193">You can use the `<inheritdoc>` tag to inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="84ac7-194">Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky udržuje komentáře XML synchronizované.</span><span class="sxs-lookup"><span data-stu-id="84ac7-194">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a><span data-ttu-id="84ac7-195">Spojení všech součástí dohromady</span><span class="sxs-lookup"><span data-stu-id="84ac7-195">Put it all together</span></span>

<span data-ttu-id="84ac7-196">Pokud jste postupovali podle tohoto kurzu a v případě potřeby použili značky na váš kód, váš kód by teď měl vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="84ac7-196">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="84ac7-197">Z vašeho kódu můžete vygenerovat podrobný web dokumentace s křížovými odkazy, na které lze kliknout.</span><span class="sxs-lookup"><span data-stu-id="84ac7-197">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="84ac7-198">Ale jste konfrontováni s dalším problémem: váš kód se stal těžko čitelným.</span><span class="sxs-lookup"><span data-stu-id="84ac7-198">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="84ac7-199">Je tu tolik informací prosít přes to bude noční můra pro každého vývojáře, který chce přispět k tomuto kódu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-199">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="84ac7-200">Naštěstí existuje značka XML, která vám pomůže s tímto problémem:</span><span class="sxs-lookup"><span data-stu-id="84ac7-200">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="84ac7-201">\<patří></span><span class="sxs-lookup"><span data-stu-id="84ac7-201">\<include></span></span>

<span data-ttu-id="84ac7-202">Značka `<include>` umožňuje odkazovat na komentáře v samostatném souboru XML, které popisují typy a členy ve zdrojovém kódu, na rozdíl od umístění komentářů dokumentace přímo do souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-202">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="84ac7-203">Nyní přesunete všechny značky XML do samostatného `docs.xml`souboru XML s názvem .</span><span class="sxs-lookup"><span data-stu-id="84ac7-203">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="84ac7-204">Nebojte se pojmenovat soubor, co chcete.</span><span class="sxs-lookup"><span data-stu-id="84ac7-204">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="84ac7-205">Ve výše uvedeném xml se komentáře dokumentace každého člena zobrazují přímo uvnitř značky pojmenované podle toho, co dělají.</span><span class="sxs-lookup"><span data-stu-id="84ac7-205">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="84ac7-206">Můžete si vybrat vlastní strategii.</span><span class="sxs-lookup"><span data-stu-id="84ac7-206">You can choose your own strategy.</span></span>
<span data-ttu-id="84ac7-207">Teď, když máte komentáře XML v samostatném souboru, podívejme se, jak `<include>` může být váš kód čitelnější pomocí značky:</span><span class="sxs-lookup"><span data-stu-id="84ac7-207">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="84ac7-208">A tady to máte: náš kód je zpět čitelný a žádné informace o dokumentaci nebyly ztraceny.</span><span class="sxs-lookup"><span data-stu-id="84ac7-208">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="84ac7-209">Atribut `file` představuje název souboru XML obsahujícího dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="84ac7-209">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="84ac7-210">Atribut `path` představuje dotaz [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) `tag name` k přítomnosti `file`v zadaném .</span><span class="sxs-lookup"><span data-stu-id="84ac7-210">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="84ac7-211">Atribut `name` představuje specifikátor názvu ve značce, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="84ac7-211">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="84ac7-212">Atribut, `id` který lze použít místo `name`, představuje ID pro značku, která předchází komentáře.</span><span class="sxs-lookup"><span data-stu-id="84ac7-212">The `id` attribute, which can be used in place of `name`, represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="84ac7-213">Uživatelem definované značky</span><span class="sxs-lookup"><span data-stu-id="84ac7-213">User-defined tags</span></span>

<span data-ttu-id="84ac7-214">Všechny výše uvedené značky představují ty, které jsou rozpoznány kompilátorem Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="84ac7-214">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="84ac7-215">Uživatel však může definovat své vlastní značky.</span><span class="sxs-lookup"><span data-stu-id="84ac7-215">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="84ac7-216">Nástroje, jako je Sandcastle, [ \<](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) přinášejí podporu pro další značky, jako jsou>událostí a [ \<poznámka>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), a dokonce podporují [dokumentování jmenných prostorů](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="84ac7-216">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="84ac7-217">Vlastní nebo interní nástroje pro generování dokumentace lze také použít se standardními značkami a lze podporovat více výstupních formátů z HTML do PDF.</span><span class="sxs-lookup"><span data-stu-id="84ac7-217">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="84ac7-218">Doporučení</span><span class="sxs-lookup"><span data-stu-id="84ac7-218">Recommendations</span></span>

<span data-ttu-id="84ac7-219">Dokumentování kódu se doporučuje z mnoha důvodů.</span><span class="sxs-lookup"><span data-stu-id="84ac7-219">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="84ac7-220">Co bude následovat, jsou některé osvědčené postupy, obecné scénáře případu použití a věci, které byste měli vědět při použití značek dokumentace XML v kódu Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="84ac7-220">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="84ac7-221">Z důvodu konzistence by měly být zdokumentovány všechny veřejně viditelné typy a jejich členy.</span><span class="sxs-lookup"><span data-stu-id="84ac7-221">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="84ac7-222">Když to musíš udělat, udělej to všechno.</span><span class="sxs-lookup"><span data-stu-id="84ac7-222">If you must do it, do it all.</span></span>
- <span data-ttu-id="84ac7-223">Soukromé členy lze také zdokumentovat pomocí komentářů XML.</span><span class="sxs-lookup"><span data-stu-id="84ac7-223">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="84ac7-224">Tím se však zpřístupní vnitřní (potenciálně důvěrné) fungování knihovny.</span><span class="sxs-lookup"><span data-stu-id="84ac7-224">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="84ac7-225">Na minimum, typy a jejich členové `<summary>` by měli mít značku, protože jeho obsah je potřeba pro IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="84ac7-225">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="84ac7-226">Text dokumentace by měl být napsán pomocí úplných vět končících úplnými zastávkami.</span><span class="sxs-lookup"><span data-stu-id="84ac7-226">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="84ac7-227">Částečné třídy jsou plně podporovány a informace o dokumentaci budou zřetězeny do jedné položky pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="84ac7-227">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="84ac7-228">Kompilátor `<exception>`ověří syntaxi značek `<include>` `<param>`, `<see>` `<seealso>`, `<typeparam>` , , a.</span><span class="sxs-lookup"><span data-stu-id="84ac7-228">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="84ac7-229">Kompilátor ověřuje parametry, které obsahují cesty k souborům a odkazy na jiné části kódu.</span><span class="sxs-lookup"><span data-stu-id="84ac7-229">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="84ac7-230">Viz také</span><span class="sxs-lookup"><span data-stu-id="84ac7-230">See also</span></span>

- [<span data-ttu-id="84ac7-231">Dokumentační komentáře XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="84ac7-231">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="84ac7-232">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="84ac7-232">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
