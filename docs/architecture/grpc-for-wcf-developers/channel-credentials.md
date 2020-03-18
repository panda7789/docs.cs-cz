---
title: Pověření kanálu - gRPC pro vývojáře WCF
description: Jak implementovat a používat pověření kanálu gRPC v ASP.NET Core 3.0.
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148202"
---
# <a name="channel-credentials"></a>Přihlašovací údaje kanálu

Jak název napovídá, pověření kanálu jsou připojeny k podkladovému kanálu gRPC. Standardní forma pověření kanálu používá ověřování klientského certifikátu. V tomto procesu klient poskytuje certifikát TLS při vytváření připojení a pak server ověří před povolením všechna volání.

Můžete kombinovat pověření kanálu s pověřeními volání a zajistit tak komplexní zabezpečení služby gRPC. Pověření kanálu prokázat, že klientská aplikace je povolen přístup ke službě a pověření volání poskytují informace o osobě, která používá klientskou aplikaci.

Ověřování klientského certifikátu funguje pro gRPC stejným způsobem jako pro ASP.NET Core. Další informace naleznete [v tématu Konfigurace ověřování certifikátů v ASP.NET core](/aspnet/core/security/authentication/certauth).

Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale pro produkční prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.

## <a name="add-certificate-authentication-to-the-server"></a>Přidání ověřování certifikátu na server

Nakonfigurujte ověřování certifikátů na úrovni hostitele (například na serveru Kestrel) i v kanálu ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Konfigurace ověření certifikátu v kestrelu

Kestrel (ASP.NET core HTTP server) můžete nakonfigurovat tak, aby vyžadoval klientský certifikát a volitelně provedl ověření zadaného certifikátu před přijetím příchozích připojení. To provést v `CreateWebHostBuilder` metodě `Program` třídy, `Startup`nikoli v .

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

Nastavení `ClientCertificateMode.RequireCertificate` způsobí, že Kestrel okamžitě odmítne jakýkoli požadavek na připojení, který neposkytuje klientský certifikát, ale toto nastavení samo o sobě neověří certifikát, který je k dispozici. Přidejte `ClientCertificateValidation` zpětné volání, které umožní Kestrelovi ověřit klientský certifikát v okamžiku nastokovaného připojení před připojením kanálu ASP.NET Core. (V tomto případě zpětné volání zajišťuje, že byl vydán stejnou *certifikační autoritou* jako certifikát serveru.)

### <a name="add-aspnet-core-certificate-authentication"></a>Přidání ASP.NET ověřování základního certifikátu

Balíček [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet poskytuje ověřování certifikátů.

Přidejte službu ověřování `ConfigureServices` certifikátů do metody a přidejte ověřování `Configure` a autorizaci do kanálu ASP.NET Core v metodě.

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

## <a name="provide-channel-credentials-in-the-client-application"></a>Zadejte pověření kanálu v klientské aplikaci

S `Grpc.Net.Client` balíčkem nakonfigurujete certifikáty <xref:System.Net.Http.HttpClient> na `GrpcChannel` instanci, která je k dispozici pro připojení.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Kombinovat channelcredentials a callcredentials

Server můžete nakonfigurovat tak, aby používal ověřování certifikátů i tokenů. To provést použitím změny certifikátu na serveru Kestrel a pomocí JWT nosič middleware v ASP.NET Core.

Chcete-li `ChannelCredentials` `CallCredentials` poskytnout oba a `ChannelCredentials.Create` na straně klienta, použijte metodu použít pověření volání. Stále je třeba použít ověřování <xref:System.Net.Http.HttpClient> certifikátu pomocí instance. Pokud předáte všechny argumenty `SslCredentials` konstruktoru, vnitřní kód klienta vyvolá výjimku. Parametr `SslCredentials` je součástí pouze `Grpc.Net.Client` `Create` metody balíčku pro zachování `Grpc.Core` kompatibility s balíčkem.

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
> Metodu `ChannelCredentials.Create` můžete použít pro klienta bez ověření certifikátu. Toto je užitečný způsob, jak předat pověření tokenu s každým voláním v kanálu.

Verze [ukázkové ukázky FullStockTicker gRPC s přidaným ověřováním certifikátu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.

>[!div class="step-by-step"]
>[Předchozí](call-credentials.md)
>[další](encryption.md)
