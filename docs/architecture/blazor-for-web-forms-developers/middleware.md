---
title: Moduly, obslužné rutiny a middleware
description: Přečtěte si o zpracování požadavků HTTP pomocí modulů, obslužných rutin a middlewaru.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 10/11/2019
ms.openlocfilehash: 639755dd78892df1b70ea5245a9584e575fbf691
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267877"
---
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="b1da5-103">Moduly, obslužné rutiny a middleware</span><span class="sxs-lookup"><span data-stu-id="b1da5-103">Modules, handlers, and middleware</span></span>

<span data-ttu-id="b1da5-104">Aplikace ASP.NET Core je postavená na řadě *middlewaru*.</span><span class="sxs-lookup"><span data-stu-id="b1da5-104">An ASP.NET Core app is built upon a series of *middleware*.</span></span> <span data-ttu-id="b1da5-105">Middleware jsou obslužné rutiny, které jsou uspořádány do kanálu pro zpracování požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="b1da5-105">Middleware is handlers that are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="b1da5-106">V aplikaci webového formuláře obslužné rutiny a moduly HTTP vyřeší podobné problémy.</span><span class="sxs-lookup"><span data-stu-id="b1da5-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="b1da5-107">V ASP.NET Core jsou moduly, obslužné rutiny, *Global.asax.cs*a životní cyklus aplikace nahrazeny middlewarem.</span><span class="sxs-lookup"><span data-stu-id="b1da5-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="b1da5-108">V této kapitole se dozvíte, jaký middleware v kontextu Blazor aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1da5-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="b1da5-109">Přehled</span><span class="sxs-lookup"><span data-stu-id="b1da5-109">Overview</span></span>

<span data-ttu-id="b1da5-110">Kanál žádostí o ASP.NET Core se skládá z posloupnosti delegátů požadavků, který se nazývá jedna po druhé.</span><span class="sxs-lookup"><span data-stu-id="b1da5-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="b1da5-111">Následující diagram znázorňuje koncept.</span><span class="sxs-lookup"><span data-stu-id="b1da5-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="b1da5-112">Vlákno provádění následuje za černými šipkami.</span><span class="sxs-lookup"><span data-stu-id="b1da5-112">The thread of execution follows the black arrows.</span></span>

![kanálu](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="b1da5-114">V předchozím diagramu chybí koncept událostí životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="b1da5-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="b1da5-115">Tento koncept je základem způsobu, jakým jsou zpracovávány požadavky webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b1da5-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="b1da5-116">Tento systém usnadňuje důvod k tomu, ke kterému procesu dochází, a umožňuje vkládat middleware do libovolného místa.</span><span class="sxs-lookup"><span data-stu-id="b1da5-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="b1da5-117">Middleware se spustí v pořadí, ve kterém se přidá do kanálu požadavků.</span><span class="sxs-lookup"><span data-stu-id="b1da5-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="b1da5-118">Jsou také přidány v kódu místo konfiguračních souborů, obvykle v *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="b1da5-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="b1da5-119">Katana</span><span class="sxs-lookup"><span data-stu-id="b1da5-119">Katana</span></span>

<span data-ttu-id="b1da5-120">Čtenáři obeznámené s Katana se budou dobře cítit ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1da5-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="b1da5-121">Ve skutečnosti Katana je rozhraní, ze kterého je odvozen ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1da5-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="b1da5-122">Zavedly podobné vzory middlewaru a kanálu pro ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="b1da5-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="b1da5-123">Middleware určené pro Katana se dají přizpůsobit pro práci s kanálem ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1da5-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="b1da5-124">Společný middlewarový</span><span class="sxs-lookup"><span data-stu-id="b1da5-124">Common middleware</span></span>

<span data-ttu-id="b1da5-125">ASP.NET 4. x zahrnuje mnoho modulů.</span><span class="sxs-lookup"><span data-stu-id="b1da5-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="b1da5-126">Podobným způsobem má ASP.NET Core také mnoho dostupných součástí middlewaru.</span><span class="sxs-lookup"><span data-stu-id="b1da5-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="b1da5-127">Moduly IIS se můžou v některých případech použít ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1da5-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="b1da5-128">V jiných případech může být k dispozici nativní ASP.NET Core middleware.</span><span class="sxs-lookup"><span data-stu-id="b1da5-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="b1da5-129">V následující tabulce jsou uvedeny náhradní middleware a součásti v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1da5-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="b1da5-130">Modul</span><span class="sxs-lookup"><span data-stu-id="b1da5-130">Module</span></span>                 |<span data-ttu-id="b1da5-131">ASP.NET 4. x – modul</span><span class="sxs-lookup"><span data-stu-id="b1da5-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="b1da5-132">Možnost ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1da5-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="b1da5-133">Chyby protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="b1da5-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="b1da5-134">Middleware stránky stavového kódu</span><span class="sxs-lookup"><span data-stu-id="b1da5-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="b1da5-135">Výchozí dokument</span><span class="sxs-lookup"><span data-stu-id="b1da5-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="b1da5-136">Middleware výchozích souborů</span><span class="sxs-lookup"><span data-stu-id="b1da5-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="b1da5-137">Procházení adresářů</span><span class="sxs-lookup"><span data-stu-id="b1da5-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="b1da5-138">Middleware procházení adresářů</span><span class="sxs-lookup"><span data-stu-id="b1da5-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="b1da5-139">Dynamická komprese</span><span class="sxs-lookup"><span data-stu-id="b1da5-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="b1da5-140">Middleware pro kompresi odpovědí</span><span class="sxs-lookup"><span data-stu-id="b1da5-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="b1da5-141">Trasování chybných žádostí</span><span class="sxs-lookup"><span data-stu-id="b1da5-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="b1da5-142">Protokolování ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1da5-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="b1da5-143">Ukládání souborů do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b1da5-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="b1da5-144">Middleware pro ukládání odpovědí do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b1da5-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="b1da5-145">Ukládání HTTP do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b1da5-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="b1da5-146">Middleware pro ukládání odpovědí do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b1da5-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="b1da5-147">Protokolování HTTP</span><span class="sxs-lookup"><span data-stu-id="b1da5-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="b1da5-148">Protokolování ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1da5-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="b1da5-149">Přesměrování protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="b1da5-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="b1da5-150">Middleware pro přepis adres URL</span><span class="sxs-lookup"><span data-stu-id="b1da5-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="b1da5-151">Filtry ISAPI</span><span class="sxs-lookup"><span data-stu-id="b1da5-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="b1da5-152">Middleware</span><span class="sxs-lookup"><span data-stu-id="b1da5-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="b1da5-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="b1da5-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="b1da5-154">Middleware</span><span class="sxs-lookup"><span data-stu-id="b1da5-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="b1da5-155">Filtrování žádostí</span><span class="sxs-lookup"><span data-stu-id="b1da5-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="b1da5-156">Přepis adres URL IRule middlewaru</span><span class="sxs-lookup"><span data-stu-id="b1da5-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="b1da5-157">&#8224; přepsání adresy URL</span><span class="sxs-lookup"><span data-stu-id="b1da5-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="b1da5-158">Middleware pro přepis adres URL</span><span class="sxs-lookup"><span data-stu-id="b1da5-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="b1da5-159">Statická komprese</span><span class="sxs-lookup"><span data-stu-id="b1da5-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="b1da5-160">Middleware pro kompresi odpovědí</span><span class="sxs-lookup"><span data-stu-id="b1da5-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="b1da5-161">Statický obsah</span><span class="sxs-lookup"><span data-stu-id="b1da5-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="b1da5-162">Middleware statických souborů</span><span class="sxs-lookup"><span data-stu-id="b1da5-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="b1da5-163">Autorizace URL</span><span class="sxs-lookup"><span data-stu-id="b1da5-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="b1da5-164">ASP.NET Core identity</span><span class="sxs-lookup"><span data-stu-id="b1da5-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="b1da5-165">Tento seznam není vyčerpávající, ale měl by poskytnout představu o tom, jaké mapování existuje mezi oběma rozhraními.</span><span class="sxs-lookup"><span data-stu-id="b1da5-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="b1da5-166">Podrobnější seznam najdete v tématu [moduly IIS s ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span><span class="sxs-lookup"><span data-stu-id="b1da5-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="b1da5-167">Vlastní middleware</span><span class="sxs-lookup"><span data-stu-id="b1da5-167">Custom middleware</span></span>

<span data-ttu-id="b1da5-168">Předdefinovaný middleware nemusí zpracovávat všechny scénáře nutné pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b1da5-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="b1da5-169">V takových případech má smysl vytvořit vlastní middlewarový přístup.</span><span class="sxs-lookup"><span data-stu-id="b1da5-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="b1da5-170">Existuje několik způsobů, jak definovat middleware, nejjednodušší je jednoduchého delegáta.</span><span class="sxs-lookup"><span data-stu-id="b1da5-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="b1da5-171">Vezměte v úvahu následující middleware, které akceptují požadavek na jazykovou verzi z řetězce dotazu:</span><span class="sxs-lookup"><span data-stu-id="b1da5-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

<span data-ttu-id="b1da5-172">Middleware může být také definována jako třída, buď implementací `IMiddleware` rozhraní nebo podle konvence middlewaru.</span><span class="sxs-lookup"><span data-stu-id="b1da5-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="b1da5-173">Další informace najdete v tématu [zápis vlastního middlewaru ASP.NET Core](/aspnet/core/fundamentals/middleware/write).</span><span class="sxs-lookup"><span data-stu-id="b1da5-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b1da5-174">[Předchozí](data.md) 
> [Další](config.md)</span><span class="sxs-lookup"><span data-stu-id="b1da5-174">[Previous](data.md)
[Next](config.md)</span></span>
