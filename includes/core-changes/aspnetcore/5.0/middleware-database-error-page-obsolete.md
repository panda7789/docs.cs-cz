---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811257"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a>Middleware: chybová stránka databáze je označena jako zastaralá.

[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) a související metody rozšíření byly označeny jako zastaralé v ASP.NET Core 5,0. Middleware a metody rozšíření budou odebrány v ASP.NET Core 6,0. Funkce se místo toho poskytne pomocí `DatabaseDeveloperPageExceptionFilter` a jeho rozšiřujících metod.

Diskuzi najdete v tématu věnovaném problému GitHubu v [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).

#### <a name="version-introduced"></a>Představená verze

5,0 RC 1

#### <a name="old-behavior"></a>Staré chování

`DatabaseErrorPageMiddleware` a přidružené metody rozšíření se zastaraly.

#### <a name="new-behavior"></a>Nové chování

`DatabaseErrorPageMiddleware` a přidružené metody rozšíření jsou zastaralé.

#### <a name="reason-for-change"></a>Důvod změny

`DatabaseErrorPageMiddleware` bylo migrováno na rozšiřitelné rozhraní API pro [stránku výjimky pro vývojáře](/aspnet/core/fundamentals/error-handling#developer-exception-page). Další informace o rozšiřitelném rozhraní API najdete v tématu problém GitHubu [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).

#### <a name="recommended-action"></a>Doporučená akce

Dokončete následující kroky:

1. Ukončete používání `DatabaseErrorPageMiddleware` v projektu. Například odeberte `UseDatabaseErrorPage` volání metody z `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. Přidejte do projektu stránku výjimky pro vývojáře. Například volejte <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> metodu v `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. Do kolekce služeb přidejte filtr výjimky stránky pro vývojáře databáze. Například volejte `AddDatabaseDeveloperPageExceptionFilter` metodu v `Startup.ConfigureServices` :

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
