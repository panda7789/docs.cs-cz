---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957680"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="73297-101">Razor: rozhraní API RazorTemplateEngine bylo odebráno</span><span class="sxs-lookup"><span data-stu-id="73297-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="73297-102">Rozhraní API [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) se odebralo a nahradilo <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .</span><span class="sxs-lookup"><span data-stu-id="73297-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="73297-103">Diskuzi najdete v tématu problém GitHubu [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).</span><span class="sxs-lookup"><span data-stu-id="73297-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73297-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="73297-104">Version introduced</span></span>

<span data-ttu-id="73297-105">3,0</span><span class="sxs-lookup"><span data-stu-id="73297-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="73297-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="73297-106">Old behavior</span></span>

<span data-ttu-id="73297-107">Modul šablon lze vytvořit a použít k analýze a generování kódu pro soubory Razor.</span><span class="sxs-lookup"><span data-stu-id="73297-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="73297-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="73297-108">New behavior</span></span>

<span data-ttu-id="73297-109">`RazorProjectEngine` lze vytvořit a poskytnout stejný typ informací pro `RazorTemplateEngine` analýzu a generování kódu pro soubory Razor.</span><span class="sxs-lookup"><span data-stu-id="73297-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="73297-110">`RazorProjectEngine` poskytuje také dodatečné úrovně konfigurace.</span><span class="sxs-lookup"><span data-stu-id="73297-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="73297-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="73297-111">Reason for change</span></span>

<span data-ttu-id="73297-112">`RazorTemplateEngine` byl příliš pevně spojen s existující implementací.</span><span class="sxs-lookup"><span data-stu-id="73297-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="73297-113">Toto těsné spojení vedlo k dalším otázkám při pokusu o správnou konfiguraci kanálu analýzy/generování Razor.</span><span class="sxs-lookup"><span data-stu-id="73297-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73297-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="73297-114">Recommended action</span></span>

<span data-ttu-id="73297-115">`RazorProjectEngine`Místo použijte `RazorTemplateEngine` .</span><span class="sxs-lookup"><span data-stu-id="73297-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="73297-116">Vezměte v úvahu následující příklady.</span><span class="sxs-lookup"><span data-stu-id="73297-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="73297-117">Vytvoření a konfigurace RazorProjectEngine</span><span class="sxs-lookup"><span data-stu-id="73297-117">Create and configure the RazorProjectEngine</span></span>

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="73297-118">Vygenerovat kód pro soubor Razor</span><span class="sxs-lookup"><span data-stu-id="73297-118">Generate code for a Razor file</span></span>

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a><span data-ttu-id="73297-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="73297-119">Category</span></span>

<span data-ttu-id="73297-120">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="73297-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73297-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="73297-121">Affected APIs</span></span>

- [<span data-ttu-id="73297-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="73297-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="73297-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="73297-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
