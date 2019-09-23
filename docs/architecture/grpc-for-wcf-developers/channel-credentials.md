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
# <a name="channel-credentials"></a><span data-ttu-id="44a9e-103">Přihlašovací údaje kanálu</span><span class="sxs-lookup"><span data-stu-id="44a9e-103">Channel credentials</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="44a9e-104">Jak název naznačuje, jsou přihlašovací údaje kanálu připojené k základnímu gRPC kanálu.</span><span class="sxs-lookup"><span data-stu-id="44a9e-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="44a9e-105">Standardní forma přihlašovacích údajů kanálu používá ověřování klientským certifikátem, kde klient poskytuje certifikát TLS při navazování připojení, které se ověří serverem před tím, než povolí provedení jakýchkoli volání.</span><span class="sxs-lookup"><span data-stu-id="44a9e-105">The standard form of channel credentials uses Client Certificate authentication, where the client provides a TLS certificate when it's making the connection, which is verified by the server before allowing any calls to be made.</span></span>

<span data-ttu-id="44a9e-106">Přihlašovací údaje kanálu můžou být kombinovány s přihlašovacími údaji volání, aby poskytovaly komplexní zabezpečení pro službu gRPC.</span><span class="sxs-lookup"><span data-stu-id="44a9e-106">Channel credentials can be combined with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="44a9e-107">Pověření kanálu prokáže, že klientská aplikace má povolen přístup ke službě a přihlašovací údaje volání poskytují informace o osobě pomocí klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="44a9e-107">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person using the client application.</span></span>

<span data-ttu-id="44a9e-108">Ověřování klientským certifikátem funguje pro gRPC stejným způsobem jako při práci s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a9e-108">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="44a9e-109">Proces konfigurace se tady shrnuje, ale další informace najdete v článku [Konfigurace ověřování certifikátů v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="44a9e-109">The configuration process will be summarized here, but more information is available in the [Configure certificate authentication in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) article.</span></span>

<span data-ttu-id="44a9e-110">Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale v produkčním prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="44a9e-110">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="adding-certificate-authentication-to-the-server"></a><span data-ttu-id="44a9e-111">Přidání ověřování certifikátu na server</span><span class="sxs-lookup"><span data-stu-id="44a9e-111">Adding certificate authentication to the server</span></span>

<span data-ttu-id="44a9e-112">Ověřování certifikátu je třeba nakonfigurovat na úrovni hostitele, například na serveru Kestrel, a v kanálu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a9e-112">You need to configure certificate authentication both at the host level, for example on the Kestrel server, and in the ASP.NET Core pipeline.</span></span>

### <a name="configuring-certificate-validation-on-kestrel"></a><span data-ttu-id="44a9e-113">Konfigurace ověřování certifikátů v Kestrel</span><span class="sxs-lookup"><span data-stu-id="44a9e-113">Configuring certificate validation on Kestrel</span></span>

<span data-ttu-id="44a9e-114">Kestrel ASP.NET Core (Server HTTP Server) můžete nakonfigurovat tak, aby vyžadovala klientský certifikát, a případně provést nějaké ověření poskytnutého certifikátu před přijetím příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="44a9e-114">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate before accepting incoming connections.</span></span> <span data-ttu-id="44a9e-115">Tato konfigurace se provádí v `CreateWebHostBuilder` metodě `Program` třídy, nikoli v `Startup`.</span><span class="sxs-lookup"><span data-stu-id="44a9e-115">This configuration is done in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="44a9e-116">`ClientCertificateMode.RequireCertificate` Nastavení způsobí, že Kestrel okamžitě odmítne všechny žádosti o připojení, které neposkytují klientský certifikát, ale certifikát neověří.</span><span class="sxs-lookup"><span data-stu-id="44a9e-116">The `ClientCertificateMode.RequireCertificate` setting will cause Kestrel to immediately reject any connection request that doesn't provide a client certificate, but it won't validate the certificate.</span></span> <span data-ttu-id="44a9e-117">Přidání zpětného volání umožňuje Kestrel ověřit klientský certifikát (v tomto případě zajistí, že byl vydán stejnou *certifikační autoritou* jako certifikát serveru) v okamžiku, kdy se připojení nastavilo, před ASP.NET Core `ClientCertificateValidation` kanál se zapojí.</span><span class="sxs-lookup"><span data-stu-id="44a9e-117">Adding the `ClientCertificateValidation` callback enables Kestrel to validate the client certificate (in this case, ensuring that it was issued by the same *Certificate Authority* as the server certificate) at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span>

### <a name="adding-aspnet-core-certificate-authentication"></a><span data-ttu-id="44a9e-118">Přidání ověřování certifikátů ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="44a9e-118">Adding ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="44a9e-119">Ověřování certifikátu zajišťuje balíček NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .</span><span class="sxs-lookup"><span data-stu-id="44a9e-119">Certificate authentication is provided by the [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package.</span></span>

<span data-ttu-id="44a9e-120">Přidejte do `ConfigureServices` metody službu ověřování certifikátů a `Configure` v metodě přidejte do kanálu ASP.NET Core ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="44a9e-120">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="providing-channel-credentials-in-the-client-application"></a><span data-ttu-id="44a9e-121">Poskytování přihlašovacích údajů kanálu v klientské aplikaci</span><span class="sxs-lookup"><span data-stu-id="44a9e-121">Providing channel credentials in the client application</span></span>

<span data-ttu-id="44a9e-122">V balíčku se certifikáty konfigurují <xref:System.Net.Http.HttpClient> na instanci `GrpcChannel` , která je k dispozici pro použití pro připojení. `Grpc.Net.Client`</span><span class="sxs-lookup"><span data-stu-id="44a9e-122">With the `Grpc.Net.Client` package, certificates are configured on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combining-channelcredentials-and-callcredentials"></a><span data-ttu-id="44a9e-123">Kombinování ChannelCredentials a CallCredentials</span><span class="sxs-lookup"><span data-stu-id="44a9e-123">Combining ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="44a9e-124">Server můžete nakonfigurovat tak, aby používal ověřování pomocí certifikátu i tokenu, a to tak, že použije změny certifikátu na server Kestrel a použije middleware nosiče JWT v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a9e-124">You can configure your server to use both certificate and token authentication by applying the certificate changes to the Kestrel server and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="44a9e-125">Chcete-li zadat jak ChannelCredentials, tak CallCredentials na straně klienta `ChannelCredentials.Create` , použijte metodu pro použití přihlašovacích údajů volání.</span><span class="sxs-lookup"><span data-stu-id="44a9e-125">To provide both ChannelCredentials and CallCredentials on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="44a9e-126">Ověřování certifikátů je stále potřeba použít s použitím <xref:System.Net.Http.HttpClient> instance: Pokud předáte `SslCredentials` do konstruktoru nějaké argumenty, vyvolá kód interního klienta výjimku.</span><span class="sxs-lookup"><span data-stu-id="44a9e-126">Certificate authentication still needs to be applied using the <xref:System.Net.Http.HttpClient> instance: if you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="44a9e-127">Parametr je zahrnut pouze `Grpc.Net.Client` v `Create` metodě balíčku pro zachování kompatibility s `Grpc.Core` balíčkem. `SslCredentials`</span><span class="sxs-lookup"><span data-stu-id="44a9e-127">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="44a9e-128">`ChannelCredentials.Create` Metodu pro klienta bez ověřování certifikátů můžete použít jako užitečný způsob, jak předat přihlašovací údaje tokenu při každém volání v kanálu.</span><span class="sxs-lookup"><span data-stu-id="44a9e-128">You can use the `ChannelCredentials.Create` method for a client without certificate authentication, as a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="44a9e-129">Verze [ukázkové FullStockTicker aplikace gRPC s přidaným certifikátovým ověřováním](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="44a9e-129">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="44a9e-130">[Předchozí](call-credentials.md)
>[Další](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="44a9e-130">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
