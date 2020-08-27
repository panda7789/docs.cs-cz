---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957680"
---
### <a name="razor-razortemplateengine-api-removed"></a>Razor: rozhraní API RazorTemplateEngine bylo odebráno

Rozhraní API [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) se odebralo a nahradilo <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .

Diskuzi najdete v tématu problém GitHubu [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Modul šablon lze vytvořit a použít k analýze a generování kódu pro soubory Razor.

#### <a name="new-behavior"></a>Nové chování

`RazorProjectEngine` lze vytvořit a poskytnout stejný typ informací pro `RazorTemplateEngine` analýzu a generování kódu pro soubory Razor. `RazorProjectEngine` poskytuje také dodatečné úrovně konfigurace.

#### <a name="reason-for-change"></a>Důvod změny

`RazorTemplateEngine` byl příliš pevně spojen s existující implementací. Toto těsné spojení vedlo k dalším otázkám při pokusu o správnou konfiguraci kanálu analýzy/generování Razor.

#### <a name="recommended-action"></a>Doporučená akce

`RazorProjectEngine`Místo použijte `RazorTemplateEngine` . Vezměte v úvahu následující příklady.

##### <a name="create-and-configure-the-razorprojectengine"></a>Vytvoření a konfigurace RazorProjectEngine

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

##### <a name="generate-code-for-a-razor-file"></a>Vygenerovat kód pro soubor Razor

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

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [RazorTemplateEngineOptions](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
