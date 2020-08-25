---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811257"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="37747-101">Middleware: chybová stránka databáze je označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="37747-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="37747-102">[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) a související metody rozšíření byly označeny jako zastaralé v ASP.NET Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="37747-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="37747-103">Middleware a metody rozšíření budou odebrány v ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="37747-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="37747-104">Funkce se místo toho poskytne pomocí `DatabaseDeveloperPageExceptionFilter` a jeho rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="37747-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="37747-105">Diskuzi najdete v tématu věnovaném problému GitHubu v [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).</span><span class="sxs-lookup"><span data-stu-id="37747-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="37747-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="37747-106">Version introduced</span></span>

<span data-ttu-id="37747-107">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="37747-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="37747-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="37747-108">Old behavior</span></span>

<span data-ttu-id="37747-109">`DatabaseErrorPageMiddleware` a přidružené metody rozšíření se zastaraly.</span><span class="sxs-lookup"><span data-stu-id="37747-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="37747-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="37747-110">New behavior</span></span>

<span data-ttu-id="37747-111">`DatabaseErrorPageMiddleware` a přidružené metody rozšíření jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="37747-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="37747-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="37747-112">Reason for change</span></span>

<span data-ttu-id="37747-113">`DatabaseErrorPageMiddleware` bylo migrováno na rozšiřitelné rozhraní API pro [stránku výjimky pro vývojáře](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span><span class="sxs-lookup"><span data-stu-id="37747-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="37747-114">Další informace o rozšiřitelném rozhraní API najdete v tématu problém GitHubu [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="37747-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="37747-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="37747-115">Recommended action</span></span>

<span data-ttu-id="37747-116">Dokončete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="37747-116">Complete the following steps:</span></span>

1. <span data-ttu-id="37747-117">Ukončete používání `DatabaseErrorPageMiddleware` v projektu.</span><span class="sxs-lookup"><span data-stu-id="37747-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="37747-118">Například odeberte `UseDatabaseErrorPage` volání metody z `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="37747-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="37747-119">Přidejte do projektu stránku výjimky pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="37747-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="37747-120">Například volejte <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> metodu v `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="37747-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="37747-121">Do kolekce služeb přidejte filtr výjimky stránky pro vývojáře databáze.</span><span class="sxs-lookup"><span data-stu-id="37747-121">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="37747-122">Například volejte `AddDatabaseDeveloperPageExceptionFilter` metodu v `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="37747-122">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="37747-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="37747-123">Category</span></span>

<span data-ttu-id="37747-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37747-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="37747-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="37747-125">Affected APIs</span></span>

- [<span data-ttu-id="37747-126">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="37747-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="37747-127">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="37747-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
