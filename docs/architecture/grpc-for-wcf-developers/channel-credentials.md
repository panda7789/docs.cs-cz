---
title: Přihlašovací údaje kanálu – gRPC pro vývojáře WCF
description: Postup implementace a použití přihlašovacích údajů gRPC kanálu v ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 133de2c732e72844f249f11bfe22b5980b828b89
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711495"
---
# <a name="channel-credentials"></a>Přihlašovací údaje kanálu

Jak název naznačuje, jsou přihlašovací údaje kanálu připojené k základnímu gRPC kanálu. Standardní forma přihlašovacích údajů kanálu používá ověřování klientským certifikátem. V tomto procesu klient poskytuje certifikát TLS při navazování připojení a potom tento server ověří před tím, než povolí provedení jakýchkoli volání.

K zajištění komplexního zabezpečení služby gRPC můžete kombinovat přihlašovací údaje kanálu s přihlašovacími údaji volání. Pověření kanálu prokáže, že klientská aplikace má povolen přístup ke službě a přihlašovací údaje volání poskytují informace o osobě, která používá klientskou aplikaci.

Ověřování klientským certifikátem funguje pro gRPC stejným způsobem jako při práci s ASP.NET Core. Další informace najdete v tématu [Konfigurace ověřování certifikátů v ASP.NET Core](/aspnet/core/security/authentication/certauth).

Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale v produkčním prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.

## <a name="add-certificate-authentication-to-the-server"></a>Přidat ověřování certifikátu na server

Nakonfigurujte ověřování certifikátů na úrovni hostitele (například na serveru Kestrel) a v kanálu ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Konfigurace ověření certifikátu v Kestrel

Kestrel ASP.NET Core (Server HTTP Server) můžete nakonfigurovat tak, aby vyžadovala klientský certifikát, a případně provést nějaké ověření poskytnutého certifikátu před přijetím příchozích připojení. To provedete v metodě `CreateWebHostBuilder` `Program` třídy, nikoli v `Startup`.

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

Nastavení `ClientCertificateMode.RequireCertificate` způsobí, že Kestrel okamžitě odmítne všechny žádosti o připojení, které neposkytují klientský certifikát, ale toto nastavení sám o sobě neověří certifikát, který je k dispozici. Přidejte `ClientCertificateValidation` zpětné volání, aby bylo možné povolit Kestrel ověřování klientského certifikátu v okamžiku, kdy se připojení provedlo, než se zapojí kanál ASP.NET Core. (V tomto případě zpětné volání zajistí, že byla vydána stejnou *certifikační autoritou* jako certifikát serveru.) 

### <a name="add-aspnet-core-certificate-authentication"></a>Přidat ověřování certifikátů ASP.NET Core

Balíček NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) zajišťuje ověřování certifikátů.

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

## <a name="provide-channel-credentials-in-the-client-application"></a>Zadání přihlašovacích údajů kanálu v klientské aplikaci

Pomocí balíčku `Grpc.Net.Client` nakonfigurujete certifikáty pro <xref:System.Net.Http.HttpClient> instanci, která je k dispozici pro `GrpcChannel` používané pro připojení.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Kombinování ChannelCredentials a CallCredentials

Server můžete nakonfigurovat tak, aby používal ověřování pomocí certifikátu i tokenu. Provedete to tak, že použijete změny certifikátu na server Kestrel a pomocí middlewaru JWT nosiče v ASP.NET Core.

Chcete-li v klientovi poskytnout `ChannelCredentials` i `CallCredentials`, použijte k použití přihlašovacích údajů volání metodu `ChannelCredentials.Create`. I nadále je nutné použít ověřování certifikátů pomocí <xref:System.Net.Http.HttpClient> instance. Pokud předáte argumenty `SslCredentials` konstruktoru, interní kód klienta vyvolá výjimku. Parametr `SslCredentials` je zahrnutý jenom v metodě `Create` `Grpc.Net.Client` balíčku, aby se zachovala kompatibilita s `Grpc.Core` balíčkem.

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
> Metodu `ChannelCredentials.Create` můžete použít pro klienta bez ověření certifikátu. Toto je užitečný způsob, jak předat přihlašovací údaje tokenu při každém volání na kanálu.

Verze [ukázkové FullStockTicker aplikace gRPC s přidaným certifikátovým ověřováním](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.

>[!div class="step-by-step"]
>[Předchozí](call-credentials.md)
>[Další](encryption.md)
