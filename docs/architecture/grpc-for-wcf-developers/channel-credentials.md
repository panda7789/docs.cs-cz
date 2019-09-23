---
title: Přihlašovací údaje kanálu – gRPC pro vývojáře WCF
description: Postup implementace a použití přihlašovacích údajů gRPC kanálu v ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 61305ee47a2c09a0b2a0fd866beb9b7c102ffeaa
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184580"
---
# <a name="channel-credentials"></a>Přihlašovací údaje kanálu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak název naznačuje, jsou přihlašovací údaje kanálu připojené k základnímu gRPC kanálu. Standardní forma přihlašovacích údajů kanálu používá ověřování klientským certifikátem, kde klient poskytuje certifikát TLS při navazování připojení, které se ověří serverem před tím, než povolí provedení jakýchkoli volání.

Přihlašovací údaje kanálu můžou být kombinovány s přihlašovacími údaji volání, aby poskytovaly komplexní zabezpečení pro službu gRPC. Pověření kanálu prokáže, že klientská aplikace má povolen přístup ke službě a přihlašovací údaje volání poskytují informace o osobě pomocí klientské aplikace.

Ověřování klientským certifikátem funguje pro gRPC stejným způsobem jako při práci s ASP.NET Core. Proces konfigurace se tady shrnuje, ale další informace najdete v článku [Konfigurace ověřování certifikátů v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .

Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale v produkčním prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.

## <a name="adding-certificate-authentication-to-the-server"></a>Přidání ověřování certifikátu na server

Ověřování certifikátu je třeba nakonfigurovat na úrovni hostitele, například na serveru Kestrel, a v kanálu ASP.NET Core.

### <a name="configuring-certificate-validation-on-kestrel"></a>Konfigurace ověřování certifikátů v Kestrel

Kestrel ASP.NET Core (Server HTTP Server) můžete nakonfigurovat tak, aby vyžadovala klientský certifikát, a případně provést nějaké ověření poskytnutého certifikátu před přijetím příchozích připojení. Tato konfigurace se provádí v `CreateWebHostBuilder` metodě `Program` třídy, nikoli v `Startup`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

`ClientCertificateMode.RequireCertificate` Nastavení způsobí, že Kestrel okamžitě odmítne všechny žádosti o připojení, které neposkytují klientský certifikát, ale certifikát neověří. Přidání zpětného volání umožňuje Kestrel ověřit klientský certifikát (v tomto případě zajistí, že byl vydán stejnou *certifikační autoritou* jako certifikát serveru) v okamžiku, kdy se připojení nastavilo, před ASP.NET Core `ClientCertificateValidation` kanál se zapojí.

### <a name="adding-aspnet-core-certificate-authentication"></a>Přidání ověřování certifikátů ASP.NET Core

Ověřování certifikátu zajišťuje balíček NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .

Přidejte do `ConfigureServices` metody službu ověřování certifikátů a `Configure` v metodě přidejte do kanálu ASP.NET Core ověřování a autorizaci.

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="providing-channel-credentials-in-the-client-application"></a>Poskytování přihlašovacích údajů kanálu v klientské aplikaci

V balíčku se certifikáty konfigurují <xref:System.Net.Http.HttpClient> na instanci `GrpcChannel` , která je k dispozici pro použití pro připojení. `Grpc.Net.Client`

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combining-channelcredentials-and-callcredentials"></a>Kombinování ChannelCredentials a CallCredentials

Server můžete nakonfigurovat tak, aby používal ověřování pomocí certifikátu i tokenu, a to tak, že použije změny certifikátu na server Kestrel a použije middleware nosiče JWT v ASP.NET Core.

Chcete-li zadat jak ChannelCredentials, tak CallCredentials na straně klienta `ChannelCredentials.Create` , použijte metodu pro použití přihlašovacích údajů volání. Ověřování certifikátů je stále potřeba použít s použitím <xref:System.Net.Http.HttpClient> instance: Pokud předáte `SslCredentials` do konstruktoru nějaké argumenty, vyvolá kód interního klienta výjimku. Parametr je zahrnut pouze `Grpc.Net.Client` v `Create` metodě balíčku pro zachování kompatibility s `Grpc.Core` balíčkem. `SslCredentials`

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> `ChannelCredentials.Create` Metodu pro klienta bez ověřování certifikátů můžete použít jako užitečný způsob, jak předat přihlašovací údaje tokenu při každém volání v kanálu.

Verze [ukázkové FullStockTicker aplikace gRPC s přidaným certifikátovým ověřováním](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.

>[!div class="step-by-step"]
>[Předchozí](call-credentials.md)
>[Další](encryption.md)
