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
# <a name="modules-handlers-and-middleware"></a>Moduly, obslužné rutiny a middleware

Aplikace ASP.NET Core je postavená na řadě *middlewaru*. Middleware jsou obslužné rutiny, které jsou uspořádány do kanálu pro zpracování požadavků a odpovědí. V aplikaci webového formuláře obslužné rutiny a moduly HTTP vyřeší podobné problémy. V ASP.NET Core jsou moduly, obslužné rutiny, *Global.asax.cs*a životní cyklus aplikace nahrazeny middlewarem. V této kapitole se dozvíte, jaký middleware v kontextu Blazor aplikace.

## <a name="overview"></a>Přehled

Kanál žádostí o ASP.NET Core se skládá z posloupnosti delegátů požadavků, který se nazývá jedna po druhé. Následující diagram znázorňuje koncept. Vlákno provádění následuje za černými šipkami.

![kanálu](media/middleware/request-delegate-pipeline.png)

V předchozím diagramu chybí koncept událostí životního cyklu. Tento koncept je základem způsobu, jakým jsou zpracovávány požadavky webových formulářů ASP.NET. Tento systém usnadňuje důvod k tomu, ke kterému procesu dochází, a umožňuje vkládat middleware do libovolného místa. Middleware se spustí v pořadí, ve kterém se přidá do kanálu požadavků. Jsou také přidány v kódu místo konfiguračních souborů, obvykle v *Startup.cs*.

## <a name="katana"></a>Katana

Čtenáři obeznámené s Katana se budou dobře cítit ASP.NET Core. Ve skutečnosti Katana je rozhraní, ze kterého je odvozen ASP.NET Core. Zavedly podobné vzory middlewaru a kanálu pro ASP.NET 4. x. Middleware určené pro Katana se dají přizpůsobit pro práci s kanálem ASP.NET Core.

## <a name="common-middleware"></a>Společný middlewarový

ASP.NET 4. x zahrnuje mnoho modulů. Podobným způsobem má ASP.NET Core také mnoho dostupných součástí middlewaru. Moduly IIS se můžou v některých případech použít ASP.NET Core. V jiných případech může být k dispozici nativní ASP.NET Core middleware.

V následující tabulce jsou uvedeny náhradní middleware a součásti v ASP.NET Core.

|Modul                 |ASP.NET 4. x – modul           |Možnost ASP.NET Core|
|-----------------------|-----------------------------|-------------------|
|Chyby protokolu HTTP            |`CustomErrorModule`          |[Middleware stránky stavového kódu](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|Výchozí dokument       |`DefaultDocumentModule`      |[Middleware výchozích souborů](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|Procházení adresářů     |`DirectoryListingModule`     |[Middleware procházení adresářů](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|Dynamická komprese    |`DynamicCompressionModule`   |[Middleware pro kompresi odpovědí](/aspnet/core/performance/response-compression)|
|Trasování chybných žádostí|`FailedRequestsTracingModule`|[Protokolování ASP.NET Core](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|Ukládání souborů do mezipaměti           |`FileCacheModule`            |[Middleware pro ukládání odpovědí do mezipaměti](/aspnet/core/performance/caching/middleware)|
|Ukládání HTTP do mezipaměti           |`HttpCacheModule`            |[Middleware pro ukládání odpovědí do mezipaměti](/aspnet/core/performance/caching/middleware)|
|Protokolování HTTP           |`HttpLoggingModule`          |[Protokolování ASP.NET Core](/aspnet/core/fundamentals/logging/index)|
|Přesměrování protokolu HTTP       |`HttpRedirectionModule`      |[Middleware pro přepis adres URL](/aspnet/core/fundamentals/url-rewriting)|
|Filtry ISAPI          |`IsapiFilterModule`          |[Middleware](/aspnet/core/fundamentals/middleware/index)|
|ISAPI                  |`IsapiModule`                |[Middleware](/aspnet/core/fundamentals/middleware/index)|
|Filtrování žádostí      |`RequestFilteringModule`     |[Přepis adres URL IRule middlewaru](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|&#8224; přepsání adresy URL   |`RewriteModule`              |[Middleware pro přepis adres URL](/aspnet/core/fundamentals/url-rewriting)|
|Statická komprese     |`StaticCompressionModule`    |[Middleware pro kompresi odpovědí](/aspnet/core/performance/response-compression)|
|Statický obsah         |`StaticFileModule`           |[Middleware statických souborů](/aspnet/core/fundamentals/static-files)|
|Autorizace URL      |`UrlAuthorizationModule`     |[ASP.NET Core identity](/aspnet/core/security/authentication/identity)|

Tento seznam není vyčerpávající, ale měl by poskytnout představu o tom, jaké mapování existuje mezi oběma rozhraními. Podrobnější seznam najdete v tématu [moduly IIS s ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).

## <a name="custom-middleware"></a>Vlastní middleware

Předdefinovaný middleware nemusí zpracovávat všechny scénáře nutné pro aplikaci. V takových případech má smysl vytvořit vlastní middlewarový přístup. Existuje několik způsobů, jak definovat middleware, nejjednodušší je jednoduchého delegáta. Vezměte v úvahu následující middleware, které akceptují požadavek na jazykovou verzi z řetězce dotazu:

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

Middleware může být také definována jako třída, buď implementací `IMiddleware` rozhraní nebo podle konvence middlewaru. Další informace najdete v tématu [zápis vlastního middlewaru ASP.NET Core](/aspnet/core/fundamentals/middleware/write).

>[!div class="step-by-step"]
>[Předchozí](data.md) 
> [Další](config.md)
