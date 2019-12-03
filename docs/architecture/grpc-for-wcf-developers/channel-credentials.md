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
# <a name="channel-credentials"></a><span data-ttu-id="98702-103">Přihlašovací údaje kanálu</span><span class="sxs-lookup"><span data-stu-id="98702-103">Channel credentials</span></span>

<span data-ttu-id="98702-104">Jak název naznačuje, jsou přihlašovací údaje kanálu připojené k základnímu gRPC kanálu.</span><span class="sxs-lookup"><span data-stu-id="98702-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="98702-105">Standardní forma přihlašovacích údajů kanálu používá ověřování klientským certifikátem.</span><span class="sxs-lookup"><span data-stu-id="98702-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="98702-106">V tomto procesu klient poskytuje certifikát TLS při navazování připojení a potom tento server ověří před tím, než povolí provedení jakýchkoli volání.</span><span class="sxs-lookup"><span data-stu-id="98702-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="98702-107">K zajištění komplexního zabezpečení služby gRPC můžete kombinovat přihlašovací údaje kanálu s přihlašovacími údaji volání.</span><span class="sxs-lookup"><span data-stu-id="98702-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="98702-108">Pověření kanálu prokáže, že klientská aplikace má povolen přístup ke službě a přihlašovací údaje volání poskytují informace o osobě, která používá klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="98702-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="98702-109">Ověřování klientským certifikátem funguje pro gRPC stejným způsobem jako při práci s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="98702-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="98702-110">Další informace najdete v tématu [Konfigurace ověřování certifikátů v ASP.NET Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="98702-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="98702-111">Pro účely vývoje můžete použít certifikát podepsaný svým držitelem, ale v produkčním prostředí byste měli použít správný certifikát HTTPS podepsaný důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="98702-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="98702-112">Přidat ověřování certifikátu na server</span><span class="sxs-lookup"><span data-stu-id="98702-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="98702-113">Nakonfigurujte ověřování certifikátů na úrovni hostitele (například na serveru Kestrel) a v kanálu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="98702-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="98702-114">Konfigurace ověření certifikátu v Kestrel</span><span class="sxs-lookup"><span data-stu-id="98702-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="98702-115">Kestrel ASP.NET Core (Server HTTP Server) můžete nakonfigurovat tak, aby vyžadovala klientský certifikát, a případně provést nějaké ověření poskytnutého certifikátu před přijetím příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="98702-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="98702-116">To provedete v metodě `CreateWebHostBuilder` `Program` třídy, nikoli v `Startup`.</span><span class="sxs-lookup"><span data-stu-id="98702-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="98702-117">Nastavení `ClientCertificateMode.RequireCertificate` způsobí, že Kestrel okamžitě odmítne všechny žádosti o připojení, které neposkytují klientský certifikát, ale toto nastavení sám o sobě neověří certifikát, který je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="98702-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="98702-118">Přidejte `ClientCertificateValidation` zpětné volání, aby bylo možné povolit Kestrel ověřování klientského certifikátu v okamžiku, kdy se připojení provedlo, než se zapojí kanál ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="98702-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="98702-119">(V tomto případě zpětné volání zajistí, že byla vydána stejnou *certifikační autoritou* jako certifikát serveru.)</span><span class="sxs-lookup"><span data-stu-id="98702-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span> 

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="98702-120">Přidat ověřování certifikátů ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="98702-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="98702-121">Balíček NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) zajišťuje ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="98702-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="98702-122">Přidejte službu ověřování certifikátů v metodě `ConfigureServices` a do kanálu ASP.NET Core v metodě `Configure` přidejte ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="98702-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="98702-123">Zadání přihlašovacích údajů kanálu v klientské aplikaci</span><span class="sxs-lookup"><span data-stu-id="98702-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="98702-124">Pomocí balíčku `Grpc.Net.Client` nakonfigurujete certifikáty pro <xref:System.Net.Http.HttpClient> instanci, která je k dispozici pro `GrpcChannel` používané pro připojení.</span><span class="sxs-lookup"><span data-stu-id="98702-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="98702-125">Kombinování ChannelCredentials a CallCredentials</span><span class="sxs-lookup"><span data-stu-id="98702-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="98702-126">Server můžete nakonfigurovat tak, aby používal ověřování pomocí certifikátu i tokenu.</span><span class="sxs-lookup"><span data-stu-id="98702-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="98702-127">Provedete to tak, že použijete změny certifikátu na server Kestrel a pomocí middlewaru JWT nosiče v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="98702-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="98702-128">Chcete-li v klientovi poskytnout `ChannelCredentials` i `CallCredentials`, použijte k použití přihlašovacích údajů volání metodu `ChannelCredentials.Create`.</span><span class="sxs-lookup"><span data-stu-id="98702-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="98702-129">I nadále je nutné použít ověřování certifikátů pomocí <xref:System.Net.Http.HttpClient> instance.</span><span class="sxs-lookup"><span data-stu-id="98702-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="98702-130">Pokud předáte argumenty `SslCredentials` konstruktoru, interní kód klienta vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="98702-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="98702-131">Parametr `SslCredentials` je zahrnutý jenom v metodě `Create` `Grpc.Net.Client` balíčku, aby se zachovala kompatibilita s `Grpc.Core` balíčkem.</span><span class="sxs-lookup"><span data-stu-id="98702-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="98702-132">Metodu `ChannelCredentials.Create` můžete použít pro klienta bez ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="98702-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="98702-133">Toto je užitečný způsob, jak předat přihlašovací údaje tokenu při každém volání na kanálu.</span><span class="sxs-lookup"><span data-stu-id="98702-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="98702-134">Verze [ukázkové FullStockTicker aplikace gRPC s přidaným certifikátovým ověřováním](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) je na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="98702-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="98702-135">[Předchozí](call-credentials.md)
>[Další](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="98702-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
