---
title: Přihlašovací údaje kanálu – gRPC pro vývojáře WCF
description: Postup implementace a použití přihlašovacích údajů gRPC kanálu v ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: b424db49337a2dc6e3d0245d36349e3f408cdf6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967951"
---
# <a name="channel-credentials"></a>Přihlašovací údaje kanálu

Jak název naznačuje, jsou přihlašovací údaje kanálu připojené k základnímu gRPC kanálu. Standardní forma přihlašovacích údajů kanálu používá ověřování klientským certifikátem, kde klient poskytuje certifikát TLS při navazování připojení, které se ověří serverem před tím, než povolí provedení jakýchkoli volání.

Přihlašovací údaje kanálu můžou být kombinovány s přihlašovacími údaji volání, aby poskytovaly komplexní zabezpečení pro službu gRPC. Pověření kanálu prokáže, že klientská aplikace má povolen přístup ke službě a přihlašovací údaje volání poskytují informace o osobě pomocí klientské aplikace.

Ověřování klientským certifikátem funguje pro gRPC stejným způsobem jako při práci s ASP.NET Core. Proces konfigurace se tady shrnuje, ale další informace najdete v článku [Konfigurace ověřování certifikátů v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .

Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale v produkčním prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.

## <a name="adding-certificate-authentication-to-the-server"></a>Přidání ověřování certifikátu na server

Ověřování certifikátu je třeba nakonfigurovat na úrovni hostitele, například na serveru Kestrel, a v kanálu ASP.NET Core.

### <a name="configuring-certificate-validation-on-kestrel"></a>Konfigurace ověřování certifikátů v Kestrel

Kestrel ASP.NET Core (Server HTTP Server) můžete nakonfigurovat tak, aby vyžadovala klientský certifikát, a případně provést nějaké ověření poskytnutého certifikátu před přijetím příchozích připojení. Tato konfigurace se provádí v metodě `CreateWebHostBuilder` `Program` třídy, nikoli v `Startup`.

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

Nastavení `ClientCertificateMode.RequireCertificate` způsobí, že Kestrel okamžitě odmítne všechny žádosti o připojení, které neposkytují klientský certifikát, ale certifikát neověří. Přidání zpětného volání `ClientCertificateValidation` umožňuje Kestrel ověřit certifikát klienta (v tomto případě zajistěte, aby byl vydán stejnou *certifikační autoritou* jako certifikát serveru) v okamžiku, kdy se připojení provedlo, před zapojením kanálu ASP.NET Core.

### <a name="adding-aspnet-core-certificate-authentication"></a>Přidání ověřování certifikátů ASP.NET Core

Ověřování certifikátu zajišťuje balíček NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .

Přidejte službu ověřování certifikátů v metodě `ConfigureServices` a do kanálu ASP.NET Core v metodě `Configure` přidejte ověřování a autorizaci.

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

Při použití balíčku `Grpc.Net.Client` se certifikáty konfigurují na instanci služby <xref:System.Net.Http.HttpClient>, která je k dispozici pro `GrpcChannel` používané pro připojení.

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

K poskytnutí ChannelCredentials i CallCredentials na straně klienta použijte metodu `ChannelCredentials.Create` pro použití přihlašovacích údajů volání. Ověřování certifikátů je stále nutné použít pomocí <xref:System.Net.Http.HttpClient> instance: Pokud předáte argumenty konstruktoru `SslCredentials`, interní kód klienta vyvolá výjimku. Parametr `SslCredentials` je zahrnutý jenom v metodě `Create` `Grpc.Net.Client` balíčku, aby se zachovala kompatibilita s `Grpc.Core` balíčkem.

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
> Metodu `ChannelCredentials.Create` pro klienta bez ověřování certifikátů můžete použít jako užitečný způsob, jak předat přihlašovací údaje tokenu při každém volání na kanálu.

Verze [ukázkové FullStockTicker aplikace gRPC s přidaným certifikátovým ověřováním](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.

>[!div class="step-by-step"]
>[Předchozí](call-credentials.md)
>[Další](encryption.md)
