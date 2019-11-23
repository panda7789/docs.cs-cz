---
title: Moduly, obslužné rutiny a middleware
description: Přečtěte si o zpracování požadavků HTTP pomocí modulů, obslužných rutin a middlewaru.
author: danroth27
ms.author: daroth
ms.date: 10/11/2019
ms.openlocfilehash: b0be6109b9226bddbb9cbe4cebf114fd2b2a6114
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291152"
---
# <a name="modules-handlers-and-middleware"></a>Moduly, obslužné rutiny a middleware

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace ASP.NET Core je postavená na řadě middlewaru. Middleware jsou obslužné rutiny, které jsou uspořádány do kanálu pro zpracování požadavků a odpovědí. V aplikaci webového formuláře obslužné rutiny a moduly HTTP vyřeší podobné problémy. V ASP.NET Core jsou moduly, obslužné rutiny, *Global.asax.cs*a životní cyklus aplikace nahrazeny middlewarem. V této kapitole se dozvíte, jaký middleware v kontextu aplikace Blazor.

## <a name="overview"></a>Přehled

Kanál požadavků ASP.NET Core se skládá z posloupnosti delegátů požadavku a volají se jeden po druhém. Následující diagram znázorňuje tento koncept. Vlákno provádění postupuje po směru černé šipky.

![Kanálu](media/middleware/request-delegate-pipeline.png)

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
|procházení adresářů     |`DirectoryListingModule`     |[Middleware procházení adresářů](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|Dynamická komprese    |`DynamicCompressionModule`   |[Middleware pro kompresi odpovědí](/aspnet/core/performance/response-compression)|
|Trasování chybných žádostí|`FailedRequestsTracingModule`|[Protokolování ASP.NET Core](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|Ukládání souborů do mezipaměti           |`FileCacheModule`            |[Middleware pro ukládání odpovědí do mezipaměti](/aspnet/core/performance/caching/middleware)|
|Ukládání HTTP do mezipaměti           |`HttpCacheModule`            |[Middleware pro ukládání odpovědí do mezipaměti](/aspnet/core/performance/caching/middleware)|
|Protokolování HTTP           |`HttpLoggingModule`          |[Protokolování ASP.NET Core](/aspnet/core/fundamentals/logging/index)|
|Přesměrování protokolu HTTP       |`HttpRedirectionModule`      |[Middleware pro přepis adres URL](/aspnet/core/fundamentals/url-rewriting)|
|filtry ISAPI          |`IsapiFilterModule`          |[Middleware](/aspnet/core/fundamentals/middleware/index)|
|ISAPI                  |`IsapiModule`                |[Middleware](/aspnet/core/fundamentals/middleware/index)|
|Filtrování žádostí      |`RequestFilteringModule`     |[Přepis adres URL IRule middlewaru](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|Přepsání adresy URL&#8224;   |`RewriteModule`              |[Middleware pro přepis adres URL](/aspnet/core/fundamentals/url-rewriting)|
|Statická komprese     |`StaticCompressionModule`    |[Middleware pro kompresi odpovědí](/aspnet/core/performance/response-compression)|
|Statický obsah         |`StaticFileModule`           |[Middleware statických souborů](/aspnet/core/fundamentals/static-files)|
|Autorizace adres URL      |`UrlAuthorizationModule`     |[ASP.NET Core identity](/aspnet/core/security/authentication/identity)|

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

Middleware může být také definována jako třída, buď implementací rozhraní `IMiddleware` nebo podle konvence middlewaru. Další informace najdete v tématu [zápis vlastního middlewaru ASP.NET Core](/aspnet/core/fundamentals/middleware/write).

>[!div class="step-by-step"]
>[Předchozí](data.md)
>[Další](config.md)
