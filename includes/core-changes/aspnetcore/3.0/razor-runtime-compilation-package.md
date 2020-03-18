---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344279"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: Runtime kompilace přesunuta do balíčku

Podpora pro runtime kompilaci zobrazení Razor a Razor Pages se přesunula do samostatného balíčku.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Runtime kompilace je k dispozici bez nutnosti další balíčky.

#### <a name="new-behavior"></a>Nové chování

Funkce byla přesunuta do balíčku [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)

Následující rozhraní API byly `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` dříve k dispozici pro podporu kompilace za běhu. Rozhraní API jsou nyní `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`k dispozici prostřednictvím aplikace .

- `RazorViewEngineOptions.FileProviders`je nyní`MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences`je nyní`MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Kromě toho `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` byl odstraněn. Rekompilace na změny souborů je ve `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` výchozím nastavení povolena odkazem na balíček.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla nezbytná k odebrání ASP.NET závislost na sdíleném rámci Core na Roslyn.

#### <a name="recommended-action"></a>Doporučená akce

Aplikace, které vyžadují kompilaci runtime nebo rekompilaci souborů Razor, by měly provést následující kroky:

1. Přidejte odkaz `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` na balíček.
1. Aktualizujte `Startup.ConfigureServices` metodu projektu tak, `AddRazorRuntimeCompilation`aby zahrnovala volání aplikace . Například:

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
