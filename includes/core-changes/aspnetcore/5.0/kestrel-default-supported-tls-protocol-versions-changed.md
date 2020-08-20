---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803251"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a>Kestrel: výchozí podporované verze protokolu TLS se změnily

Kestrel nyní používá výchozí verze protokolu TLS pro systém místo omezení připojení k protokolům TLS 1,1 a TLS 1,2, jako jste předtím.

Tato změna umožňuje:

* TLS 1,3, který se ve výchozím nastavení použije v prostředích, která ho podporují.
* TLS 1,0, který se má použít v některých prostředích (například Windows Server 2016 ve výchozím nastavení), což obvykle [není žádoucí](/security/engineering/solving-tls1-problem).

Diskuzi najdete v tématu problém [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 6

#### <a name="old-behavior"></a>Staré chování

Kestrel vyžaduje, aby připojení ve výchozím nastavení používala TLS 1,1 nebo TLS 1,2.

#### <a name="new-behavior"></a>Nové chování

Kestrel umožňuje operačnímu systému zvolit nejlepší protokol, který se má použít, a zablokovat nezabezpečené protokoly. <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> Teď je ve výchozím nastavení `SslProtocols.None` místo `SslProtocols.Tls12 | SslProtocols.Tls11` .

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla provedena za účelem podpory protokolu TLS 1,3 a budoucích verzí TLS ve výchozím nastavení, jakmile budou k dispozici.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše aplikace nemá konkrétní důvod, měli byste použít nové výchozí hodnoty. Ověřte, že je systém nakonfigurovaný tak, aby povoloval jenom zabezpečené protokoly.

Pokud chcete zakázat starší protokoly, proveďte jednu z následujících akcí:

* Zakažte starší protokoly, jako je třeba TLS 1,0, a postupujte podle [pokynů pro Windows](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry). V současné době je ve všech verzích systému Windows povolená ve výchozím nastavení.
* V kódu ručně vyberte protokoly, které chcete podporovat, následovně:

    ```csharp
    using System.Security.Authentication;
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
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

Bohužel není k dispozici žádné rozhraní API pro vyloučení konkrétních protokolů.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
