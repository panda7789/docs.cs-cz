---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803251"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="b63de-101">Kestrel: výchozí podporované verze protokolu TLS se změnily</span><span class="sxs-lookup"><span data-stu-id="b63de-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="b63de-102">Kestrel nyní používá výchozí verze protokolu TLS pro systém místo omezení připojení k protokolům TLS 1,1 a TLS 1,2, jako jste předtím.</span><span class="sxs-lookup"><span data-stu-id="b63de-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="b63de-103">Tato změna umožňuje:</span><span class="sxs-lookup"><span data-stu-id="b63de-103">This change allows:</span></span>

* <span data-ttu-id="b63de-104">TLS 1,3, který se ve výchozím nastavení použije v prostředích, která ho podporují.</span><span class="sxs-lookup"><span data-stu-id="b63de-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="b63de-105">TLS 1,0, který se má použít v některých prostředích (například Windows Server 2016 ve výchozím nastavení), což obvykle [není žádoucí](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="b63de-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="b63de-106">Diskuzi najdete v tématu problém [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="b63de-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b63de-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b63de-107">Version introduced</span></span>

<span data-ttu-id="b63de-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="b63de-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b63de-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="b63de-109">Old behavior</span></span>

<span data-ttu-id="b63de-110">Kestrel vyžaduje, aby připojení ve výchozím nastavení používala TLS 1,1 nebo TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="b63de-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b63de-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="b63de-111">New behavior</span></span>

<span data-ttu-id="b63de-112">Kestrel umožňuje operačnímu systému zvolit nejlepší protokol, který se má použít, a zablokovat nezabezpečené protokoly.</span><span class="sxs-lookup"><span data-stu-id="b63de-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="b63de-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> Teď je ve výchozím nastavení `SslProtocols.None` místo `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="b63de-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b63de-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="b63de-114">Reason for change</span></span>

<span data-ttu-id="b63de-115">Tato změna byla provedena za účelem podpory protokolu TLS 1,3 a budoucích verzí TLS ve výchozím nastavení, jakmile budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b63de-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b63de-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b63de-116">Recommended action</span></span>

<span data-ttu-id="b63de-117">Pokud vaše aplikace nemá konkrétní důvod, měli byste použít nové výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b63de-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="b63de-118">Ověřte, že je systém nakonfigurovaný tak, aby povoloval jenom zabezpečené protokoly.</span><span class="sxs-lookup"><span data-stu-id="b63de-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="b63de-119">Pokud chcete zakázat starší protokoly, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b63de-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="b63de-120">Zakažte starší protokoly, jako je třeba TLS 1,0, a postupujte podle [pokynů pro Windows](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="b63de-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="b63de-121">V současné době je ve všech verzích systému Windows povolená ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="b63de-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="b63de-122">V kódu ručně vyberte protokoly, které chcete podporovat, následovně:</span><span class="sxs-lookup"><span data-stu-id="b63de-122">Manually select which protocols you want to support in code as follows:</span></span>

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

<span data-ttu-id="b63de-123">Bohužel není k dispozici žádné rozhraní API pro vyloučení konkrétních protokolů.</span><span class="sxs-lookup"><span data-stu-id="b63de-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="b63de-124">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b63de-124">Category</span></span>

<span data-ttu-id="b63de-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b63de-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b63de-126">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b63de-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
