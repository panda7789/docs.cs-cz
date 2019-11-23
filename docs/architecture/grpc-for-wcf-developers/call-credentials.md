---
title: Volání pověření – gRPC pro vývojáře WCF
description: Jak implementovat a používat přihlašovací údaje volání gRPC v ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 2588fe3590a63ea6071b85ff29b3685efbfa25db
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967989"
---
# <a name="call-credentials"></a><span data-ttu-id="aeeef-103">Přihlašovací údaje volání</span><span class="sxs-lookup"><span data-stu-id="aeeef-103">Call credentials</span></span>

<span data-ttu-id="aeeef-104">Přihlašovací údaje volání jsou všechny na základě určitého druhu tokenu předaného v metadatech s každou žádostí.</span><span class="sxs-lookup"><span data-stu-id="aeeef-104">Call credentials are all based on some kind of token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="aeeef-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="aeeef-105">WS-Federation</span></span>

<span data-ttu-id="aeeef-106">ASP.NET Core podporuje WS-Federation pomocí balíčku NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="aeeef-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="aeeef-107">WS-Federation je nejbližší dostupná alternativa ověřování systému Windows, která není podporována přes protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="aeeef-107">WS-Federation is the closest available alternative to Windows Authentication, which is not supported over HTTP/2.</span></span> <span data-ttu-id="aeeef-108">Uživatelé se ověřují pomocí Active Directory Federation Services (AD FS) (ADFS), která poskytuje token, který se dá použít k ověřování pomocí ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aeeef-108">Users are authenticated using Active Directory Federation Services (ADFS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="aeeef-109">Další informace o tom, jak začít s touto metodou ověřování, najdete v článku [ověřování uživatelů pomocí protokolu WS-Federation v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="aeeef-109">For more information on how to get started with this authentication method, see the [Authenticate users with WS-Federation in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) article.</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="aeeef-110">Tokeny nosiče JWT</span><span class="sxs-lookup"><span data-stu-id="aeeef-110">JWT Bearer tokens</span></span>

<span data-ttu-id="aeeef-111">[JSON web token](https://jwt.io) Standard poskytuje způsob, jak kódovat informace o uživateli a jejich deklaracích do kódovaného řetězce, a podepsat tento token takovým způsobem, že příjemce může ověřit integritu tokenu pomocí kryptografie s veřejným klíčem.</span><span class="sxs-lookup"><span data-stu-id="aeeef-111">The [JSON Web Token](https://jwt.io) standard provides a way to encode information about a user and their claims in an encoded string, and to sign that token in such a way that the consumer can verify the integrity of the token using public key cryptography.</span></span> <span data-ttu-id="aeeef-112">K ověřování uživatelů a generování tokenů OpenID Connect (OIDC) pro použití s rozhraními API gRPC a HTTP můžete použít různé služby, například IdentityServer4.</span><span class="sxs-lookup"><span data-stu-id="aeeef-112">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="aeeef-113">ASP.NET Core 3,0 může zpracovávat webové tokeny JSON pomocí balíčku nosiče JWT.</span><span class="sxs-lookup"><span data-stu-id="aeeef-113">ASP.NET Core 3.0 can handle JSON Web Tokens using the JWT Bearer package.</span></span> <span data-ttu-id="aeeef-114">Konfigurace je přesně stejná jako aplikace gRPC jako aplikace ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="aeeef-114">The configuration is exactly the same for a gRPC application as an ASP.NET Core MVC application.</span></span>

<span data-ttu-id="aeeef-115">Tato kapitola se zaměřuje na tokeny JWT nosiče, protože je snazší je vyvíjet s výjimkou WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="aeeef-115">This chapter will focus on JWT Bearer tokens as they're easier to develop with than WS-Federation.</span></span>

## <a name="adding-authentication-and-authorization-to-the-server"></a><span data-ttu-id="aeeef-116">Přidání ověřování a autorizace na server</span><span class="sxs-lookup"><span data-stu-id="aeeef-116">Adding authentication and authorization to the server</span></span>

<span data-ttu-id="aeeef-117">Balíček nosiče JWT není ve výchozím nastavení součástí ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="aeeef-117">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="aeeef-118">Do své aplikace nainstalujte balíček NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) .</span><span class="sxs-lookup"><span data-stu-id="aeeef-118">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="aeeef-119">Přidejte ověřovací službu do třídy po spuštění a nakonfigurujte obslužnou rutinu JWT nosiče.</span><span class="sxs-lookup"><span data-stu-id="aeeef-119">Add the Authentication service in the Startup class and configure the JWT Bearer handler.</span></span>

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

<span data-ttu-id="aeeef-120">Vlastnost `IssuerSigningKey` vyžaduje implementaci `Microsoft.IdentityModels.Tokens.SecurityKey` s kryptografickými daty potřebnými k ověření podepsaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="aeeef-120">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="aeeef-121">Tento token by měl být bezpečně uložený na *tajných serverech* , jako je Azure klíčů trezor.</span><span class="sxs-lookup"><span data-stu-id="aeeef-121">This token should be stored securely in a *secrets server* like Azure KeyVault.</span></span>

<span data-ttu-id="aeeef-122">Dále přidejte autorizační službu, která řídí přístup k systému.</span><span class="sxs-lookup"><span data-stu-id="aeeef-122">Next add the Authorization service, which controls access to the system.</span></span>

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
> <span data-ttu-id="aeeef-123">Ověřování a autorizace jsou dva samostatné kroky.</span><span class="sxs-lookup"><span data-stu-id="aeeef-123">Authentication and Authorization are two separate steps.</span></span> <span data-ttu-id="aeeef-124">Ověřování se používá k určení identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="aeeef-124">Authentication is used to determine the user's identity.</span></span> <span data-ttu-id="aeeef-125">Autorizace rozhoduje, jestli má tento uživatel povolený přístup k různým částem systému.</span><span class="sxs-lookup"><span data-stu-id="aeeef-125">Authorization decides whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="aeeef-126">Nyní do kanálu ASP.NET Core v metodě `Configure` přidejte middleware pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="aeeef-126">Now add the Authentication and Authorization middleware to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

<span data-ttu-id="aeeef-127">Nakonec použijte atribut `[Authorize]` pro všechny služby nebo metody, které mají být zabezpečeny, a pomocí vlastnosti `User` z podkladového `HttpContext` Ověřte oprávnění.</span><span class="sxs-lookup"><span data-stu-id="aeeef-127">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

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

## <a name="providing-call-credentials-in-the-client-application"></a><span data-ttu-id="aeeef-128">Poskytování přihlašovacích údajů volání v klientské aplikaci</span><span class="sxs-lookup"><span data-stu-id="aeeef-128">Providing call credentials in the client application</span></span>

<span data-ttu-id="aeeef-129">Jakmile obdržíte token JWT ze serveru identity, můžete ho použít k ověření volání gRPC od klienta, a to tak, že ho přidáte jako hlavičku metadat pro volání následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="aeeef-129">Once you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

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

<span data-ttu-id="aeeef-130">Teď jste zabezpečili službu gRPC pomocí nosných tokenů JWT jako přihlašovacích údajů volání.</span><span class="sxs-lookup"><span data-stu-id="aeeef-130">Now, you've secured your gRPC service using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="aeeef-131">Verze [ukázek portfolia gRPC s přidaným ověřováním a autorizací](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) je na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="aeeef-131">A version of the [Portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="aeeef-132">[Předchozí](security.md)
>[Další](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="aeeef-132">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
