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
# <a name="channel-credentials"></a><span data-ttu-id="c9de7-103">Přihlašovací údaje kanálu</span><span class="sxs-lookup"><span data-stu-id="c9de7-103">Channel credentials</span></span>

<span data-ttu-id="c9de7-104">Jak název napovídá, pověření kanálu jsou připojeny k podkladovému kanálu gRPC.</span><span class="sxs-lookup"><span data-stu-id="c9de7-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="c9de7-105">Standardní forma pověření kanálu používá ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c9de7-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="c9de7-106">V tomto procesu klient poskytuje certifikát TLS při vytváření připojení a pak server ověří před povolením všechna volání.</span><span class="sxs-lookup"><span data-stu-id="c9de7-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="c9de7-107">Můžete kombinovat pověření kanálu s pověřeními volání a zajistit tak komplexní zabezpečení služby gRPC.</span><span class="sxs-lookup"><span data-stu-id="c9de7-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="c9de7-108">Pověření kanálu prokázat, že klientská aplikace je povolen přístup ke službě a pověření volání poskytují informace o osobě, která používá klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9de7-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="c9de7-109">Ověřování klientského certifikátu funguje pro gRPC stejným způsobem jako pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9de7-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="c9de7-110">Další informace naleznete [v tématu Konfigurace ověřování certifikátů v ASP.NET core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="c9de7-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="c9de7-111">Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale pro produkční prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="c9de7-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="c9de7-112">Přidání ověřování certifikátu na server</span><span class="sxs-lookup"><span data-stu-id="c9de7-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="c9de7-113">Nakonfigurujte ověřování certifikátů na úrovni hostitele (například na serveru Kestrel) i v kanálu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9de7-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="c9de7-114">Konfigurace ověření certifikátu v kestrelu</span><span class="sxs-lookup"><span data-stu-id="c9de7-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="c9de7-115">Kestrel (ASP.NET core HTTP server) můžete nakonfigurovat tak, aby vyžadoval klientský certifikát a volitelně provedl ověření zadaného certifikátu před přijetím příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="c9de7-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="c9de7-116">To provést v `CreateWebHostBuilder` metodě `Program` třídy, `Startup`nikoli v .</span><span class="sxs-lookup"><span data-stu-id="c9de7-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="c9de7-117">Nastavení `ClientCertificateMode.RequireCertificate` způsobí, že Kestrel okamžitě odmítne jakýkoli požadavek na připojení, který neposkytuje klientský certifikát, ale toto nastavení samo o sobě neověří certifikát, který je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c9de7-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="c9de7-118">Přidejte `ClientCertificateValidation` zpětné volání, které umožní Kestrelovi ověřit klientský certifikát v okamžiku nastokovaného připojení před připojením kanálu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9de7-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="c9de7-119">(V tomto případě zpětné volání zajišťuje, že byl vydán stejnou *certifikační autoritou* jako certifikát serveru.)</span><span class="sxs-lookup"><span data-stu-id="c9de7-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="c9de7-120">Přidání ASP.NET ověřování základního certifikátu</span><span class="sxs-lookup"><span data-stu-id="c9de7-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="c9de7-121">Balíček [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet poskytuje ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="c9de7-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="c9de7-122">Přidejte službu ověřování `ConfigureServices` certifikátů do metody a přidejte ověřování `Configure` a autorizaci do kanálu ASP.NET Core v metodě.</span><span class="sxs-lookup"><span data-stu-id="c9de7-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="c9de7-123">Zadejte pověření kanálu v klientské aplikaci</span><span class="sxs-lookup"><span data-stu-id="c9de7-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="c9de7-124">S `Grpc.Net.Client` balíčkem nakonfigurujete certifikáty <xref:System.Net.Http.HttpClient> na `GrpcChannel` instanci, která je k dispozici pro připojení.</span><span class="sxs-lookup"><span data-stu-id="c9de7-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="c9de7-125">Kombinovat channelcredentials a callcredentials</span><span class="sxs-lookup"><span data-stu-id="c9de7-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="c9de7-126">Server můžete nakonfigurovat tak, aby používal ověřování certifikátů i tokenů.</span><span class="sxs-lookup"><span data-stu-id="c9de7-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="c9de7-127">To provést použitím změny certifikátu na serveru Kestrel a pomocí JWT nosič middleware v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9de7-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="c9de7-128">Chcete-li `ChannelCredentials` `CallCredentials` poskytnout oba a `ChannelCredentials.Create` na straně klienta, použijte metodu použít pověření volání.</span><span class="sxs-lookup"><span data-stu-id="c9de7-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="c9de7-129">Stále je třeba použít ověřování <xref:System.Net.Http.HttpClient> certifikátu pomocí instance.</span><span class="sxs-lookup"><span data-stu-id="c9de7-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="c9de7-130">Pokud předáte všechny argumenty `SslCredentials` konstruktoru, vnitřní kód klienta vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="c9de7-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="c9de7-131">Parametr `SslCredentials` je součástí pouze `Grpc.Net.Client` `Create` metody balíčku pro zachování `Grpc.Core` kompatibility s balíčkem.</span><span class="sxs-lookup"><span data-stu-id="c9de7-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="c9de7-132">Metodu `ChannelCredentials.Create` můžete použít pro klienta bez ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c9de7-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="c9de7-133">Toto je užitečný způsob, jak předat pověření tokenu s každým voláním v kanálu.</span><span class="sxs-lookup"><span data-stu-id="c9de7-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="c9de7-134">Verze [ukázkové ukázky FullStockTicker gRPC s přidaným ověřováním certifikátu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c9de7-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c9de7-135">[Předchozí](call-credentials.md)
>[další](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="c9de7-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
