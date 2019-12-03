---
title: Volání pověření – gRPC pro vývojáře WCF
description: Jak implementovat a používat přihlašovací údaje volání gRPC v ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 01f21f58ed4235f45509c948c84653cd99d35618
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711539"
---
# <a name="call-credentials"></a><span data-ttu-id="22f37-103">Přihlašovací údaje volání</span><span class="sxs-lookup"><span data-stu-id="22f37-103">Call credentials</span></span>

<span data-ttu-id="22f37-104">Přihlašovací údaje volání jsou všechny na základě tokenu předaného v metadatech s každým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="22f37-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="22f37-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="22f37-105">WS-Federation</span></span>

<span data-ttu-id="22f37-106">ASP.NET Core podporuje WS-Federation pomocí balíčku NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="22f37-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="22f37-107">WS-Federation je nejbližší dostupná alternativa ověřování systému Windows, která není podporována přes protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="22f37-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="22f37-108">Uživatelé se ověřují pomocí Active Directory Federation Services (AD FS) (AD FS), která poskytuje token, který se dá použít k ověřování ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="22f37-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="22f37-109">Další informace o tom, jak začít s touto metodou ověřování, najdete [v tématu ověřování uživatelů pomocí WS-Federation v ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span><span class="sxs-lookup"><span data-stu-id="22f37-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="22f37-110">Tokeny nosiče JWT</span><span class="sxs-lookup"><span data-stu-id="22f37-110">JWT Bearer tokens</span></span>

<span data-ttu-id="22f37-111">Standard [JSON web token](https://jwt.io) (Jwt) poskytuje způsob, jak zakódovat informace o uživateli a jejich deklaracích v zakódovaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="22f37-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="22f37-112">Poskytuje také způsob, jak token podepsat, aby příjemce mohl ověřit integritu tokenu pomocí kryptografie s veřejným klíčem.</span><span class="sxs-lookup"><span data-stu-id="22f37-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="22f37-113">K ověřování uživatelů a generování tokenů OpenID Connect (OIDC) pro použití s rozhraními API gRPC a HTTP můžete použít různé služby, například IdentityServer4.</span><span class="sxs-lookup"><span data-stu-id="22f37-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="22f37-114">ASP.NET Core 3,0 může zpracovávat JWTs pomocí balíčku nosiče JWT.</span><span class="sxs-lookup"><span data-stu-id="22f37-114">ASP.NET Core 3.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="22f37-115">Konfigurace je přesně stejná pro aplikaci gRPC, protože je pro aplikaci ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="22f37-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="22f37-116">Tady se zaměříme na tokeny JWT nosiče, protože je snazší je vyvíjet s výjimkou WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="22f37-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="22f37-117">Přidat ověřování a autorizaci na server</span><span class="sxs-lookup"><span data-stu-id="22f37-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="22f37-118">Balíček nosiče JWT není ve výchozím nastavení součástí ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="22f37-118">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="22f37-119">Do své aplikace nainstalujte balíček NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) .</span><span class="sxs-lookup"><span data-stu-id="22f37-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="22f37-120">Přidejte ověřovací službu do třídy po spuštění a nakonfigurujte obslužnou rutinu JWT nosiče:</span><span class="sxs-lookup"><span data-stu-id="22f37-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="22f37-121">Vlastnost `IssuerSigningKey` vyžaduje implementaci `Microsoft.IdentityModels.Tokens.SecurityKey` s kryptografickými daty potřebnými k ověření podepsaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="22f37-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="22f37-122">Tento token bezpečně uložte na *tajných serverech*, jako je Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="22f37-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="22f37-123">Pak přidejte autorizační službu, která řídí přístup k systému:</span><span class="sxs-lookup"><span data-stu-id="22f37-123">Next, add the Authorization service, which controls access to the system:</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="22f37-124">Ověřování a autorizace jsou dva samostatné kroky.</span><span class="sxs-lookup"><span data-stu-id="22f37-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="22f37-125">Pomocí ověřování určíte identitu uživatele.</span><span class="sxs-lookup"><span data-stu-id="22f37-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="22f37-126">Můžete použít autorizaci k rozhodnutí, jestli má tento uživatel povolený přístup k různým částem systému.</span><span class="sxs-lookup"><span data-stu-id="22f37-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="22f37-127">Nyní do kanálu ASP.NET Core v metodě `Configure` přidejte middleware pro ověřování a autorizaci:</span><span class="sxs-lookup"><span data-stu-id="22f37-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="22f37-128">Nakonec použijte atribut `[Authorize]` pro všechny služby nebo metody, které mají být zabezpečeny, a pomocí vlastnosti `User` z podkladového `HttpContext` Ověřte oprávnění.</span><span class="sxs-lookup"><span data-stu-id="22f37-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="22f37-129">Zadání přihlašovacích údajů volání v klientské aplikaci</span><span class="sxs-lookup"><span data-stu-id="22f37-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="22f37-130">Až obdržíte token JWT ze serveru identity, můžete ho použít k ověření volání gRPC z klienta, a to tak, že ho přidáte jako hlavičku metadat pro volání následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="22f37-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="22f37-131">Teď jste zabezpečili službu gRPC pomocí tokenů JWT nosiče jako přihlašovacích údajů volání.</span><span class="sxs-lookup"><span data-stu-id="22f37-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="22f37-132">Verze [ukázek portfolia gRPC s přidaným ověřováním a autorizací](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) je na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="22f37-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="22f37-133">[Předchozí](security.md)
>[Další](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="22f37-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
