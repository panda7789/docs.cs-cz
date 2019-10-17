---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394428"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: kompilace za běhu byla přesunuta do balíčku

Podpora pro kompilaci za běhu zobrazení Razor a Razor Pages se přesunula do samostatného balíčku.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Kompilace za běhu je k dispozici bez nutnosti dalších balíčků.

#### <a name="new-behavior"></a>Nové chování

Funkčnost byla přesunuta do balíčku `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

Následující rozhraní API byly dříve k dispozici v `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pro podporu kompilace modulu runtime. Rozhraní API jsou nyní k dispozici prostřednictvím `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Kromě toho se odebrala `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange`. Opětovná kompilace při změnách souborů je ve výchozím nastavení povolená odkazem na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla nutná pro odebrání závislostí sdíleného rozhraní ASP.NET Core v Roslyn.

#### <a name="recommended-action"></a>Doporučená akce

Aplikace, které vyžadují kompilaci za běhu nebo opětovnou kompilaci souborů Razor, by měly provést následující kroky:

1. Přidejte odkaz na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.
1. Aktualizujte metodu `Startup.ConfigureServices` projektu tak, aby zahrnovala volání `AddMvcRazorRuntimeCompilation`. Například v `Startup.ConfigureServices`:

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
