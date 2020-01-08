---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344279"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: kompilace za běhu byla přesunuta do balíčku

Podpora pro kompilaci za běhu zobrazení Razor a Razor Pages se přesunula do samostatného balíčku.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Kompilace za běhu je k dispozici bez nutnosti dalších balíčků.

#### <a name="new-behavior"></a>Nové chování

Funkce se přesunula do balíčku [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) .

Následující rozhraní API byly dříve k dispozici v `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pro podporu kompilace modulu runtime. Rozhraní API jsou nyní k dispozici prostřednictvím `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders` je teď `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` je teď `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Kromě toho se odebral `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange`. Opětovná kompilace při změnách souborů je ve výchozím nastavení povolená odkazem na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla nutná pro odebrání závislostí sdíleného rozhraní ASP.NET Core v Roslyn.

#### <a name="recommended-action"></a>Doporučená akce

Aplikace, které vyžadují kompilaci za běhu nebo opětovnou kompilaci souborů Razor, by měly provést následující kroky:

1. Přidejte odkaz na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.
1. Aktualizujte metodu `Startup.ConfigureServices` projektu tak, aby zahrnovala volání `AddRazorRuntimeCompilation`. Příklad:

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
