---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803232"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel: ve výchozím nastavení se zjistily změny v konfiguraci v době běhu.

Kestrel nyní reaguje na změny v `Kestrel` části `IConfiguration` instance projektu (například *appsettings.json*) v době běhu. Další informace o tom, jak nakonfigurovat Kestrel pomocí *appsettings.jsna*, najdete v *appsettings.js* v tématu [Konfigurace koncového bodu](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).

Kestrel bude při reakci na tyto změny konfigurace navazovat, odpojit a znovu vytvořit vazbu koncových bodů.

Diskuzi najdete v tématu problém [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="old-behavior"></a>Staré chování

Před ASP.NET Core 5,0 Preview 6 nepodporuje Kestrel změnu konfigurace v době běhu.

V ASP.NET Core 5,0 Preview 6 se můžete vyjádřit jako výchozí chování při provádění změn konfigurace v době běhu. Ruční konfigurace Kestrel vazeb v konfiguraci:

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a>Nové chování

Kestrel ve výchozím nastavení reaguje na změny konfigurace v době běhu. Pro podporu této změny <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> volání `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` ve výchozím nastavení.

#### <a name="reason-for-change"></a>Důvod změny

Změna byla provedena za účelem podpory opětovné konfigurace koncového bodu v době běhu bez úplného restartování serveru. Na rozdíl od úplného restartování serveru nejsou nezměněné koncové body bez dočasné vazby.

#### <a name="recommended-action"></a>Doporučená akce

* Ve většině scénářů, ve kterých výchozí konfigurační oddíl Kestrel se nezmění v době běhu, tato změna nemá žádný vliv a není nutné provádět žádnou akci.
* Ve scénářích, ve kterých se výchozí konfigurační oddíl Kestrel mění v době běhu a Kestrel by na ni měl reagovat, je teď to výchozí chování.
* U scénářů, ve kterých se výchozí konfigurační oddíl Kestrel mění v době běhu a Kestrel by na něj neměli reagovat, můžete odhlásit následujícím způsobem:

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

**Poznámky:**

Tato změna nemění chování `KestrelServerOptions.Configure(IConfiguration)` přetížení, které je stále výchozím `reloadOnChange: false` chováním.

Je také důležité se ujistit, že zdroj konfigurace podporuje opětovné načtení. U zdrojů JSON je opakované načítání konfigurováno voláním `AddJsonFile(path, reloadOnChange: true)` . Opětovné načítání je již ve výchozím nastavení nakonfigurováno pro *appsettings.jsv* a *appSettings. { Environment}. JSON*.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
