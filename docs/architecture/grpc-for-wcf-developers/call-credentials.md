---
title: Volání pověření – gRPC pro vývojáře WCF
description: Jak implementovat a používat přihlašovací údaje volání gRPC v ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 483f540a0ed3849883c07cc70f0e3d45a6b121ad
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184594"
---
# <a name="call-credentials"></a>Zavolat přihlašovací údaje

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Přihlašovací údaje volání jsou všechny na základě určitého druhu tokenu předaného v metadatech s každou žádostí.

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core podporuje WS-Federation pomocí balíčku NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) . WS-Federation je nejbližší dostupná alternativa ověřování systému Windows, která není podporována přes protokol HTTP/2. Uživatelé se ověřují pomocí Active Directory Federation Services (AD FS) (ADFS), která poskytuje token, který se dá použít k ověřování pomocí ASP.NET Core.

Další informace o tom, jak začít s touto metodou ověřování, najdete v článku [ověřování uživatelů pomocí protokolu WS-Federation v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) .

## <a name="jwt-bearer-tokens"></a>Tokeny nosiče JWT

[JSON web token](https://jwt.io) Standard poskytuje způsob, jak kódovat informace o uživateli a jejich deklaracích do kódovaného řetězce, a podepsat tento token takovým způsobem, že příjemce může ověřit integritu tokenu pomocí kryptografie s veřejným klíčem. K ověřování uživatelů a generování tokenů OpenID Connect (OIDC) pro použití s rozhraními API gRPC a HTTP můžete použít různé služby, například IdentityServer4.

ASP.NET Core 3,0 může zpracovávat webové tokeny JSON pomocí balíčku nosiče JWT. Konfigurace je přesně stejná jako aplikace gRPC jako aplikace ASP.NET Core MVC.

Tato kapitola se zaměřuje na tokeny JWT nosiče, protože je snazší je vyvíjet s výjimkou WS-Federation.

## <a name="adding-authentication-and-authorization-to-the-server"></a>Přidání ověřování a autorizace na server

Balíček nosiče JWT není ve výchozím nastavení součástí ASP.NET Core 3,0. Do své aplikace nainstalujte balíček NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) .

Přidejte ověřovací službu do třídy po spuštění a nakonfigurujte obslužnou rutinu JWT nosiče.

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

`IssuerSigningKey` Vlastnost vyžaduje`Microsoft.IdentityModels.Tokens.SecurityKey` implementaci s kryptografickými daty potřebnými k ověření podepsaných tokenů. Tento token by měl být bezpečně uložený na *tajných serverech* , jako je Azure klíčů trezor.

Dále přidejte autorizační službu, která řídí přístup k systému.

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
> Ověřování a autorizace jsou dva samostatné kroky. Ověřování se používá k určení identity uživatele. Autorizace rozhoduje, jestli má tento uživatel povolený přístup k různým částem systému.

Nyní do kanálu ASP.NET Core v `Configure` metodě přidejte middleware pro ověřování a autorizaci.

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

Nakonec použijte `User` `HttpContext` atribut na všechny služby nebo metody, které mají být zabezpečeny, a pomocí vlastnosti z podkladové metody ověřte oprávnění. `[Authorize]`

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

## <a name="providing-call-credentials-in-the-client-application"></a>Poskytování přihlašovacích údajů volání v klientské aplikaci

Jakmile obdržíte token JWT ze serveru identity, můžete ho použít k ověření volání gRPC od klienta, a to tak, že ho přidáte jako hlavičku metadat pro volání následujícím způsobem:

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

Teď jste zabezpečili službu gRPC pomocí nosných tokenů JWT jako přihlašovacích údajů volání. Verze [ukázek portfolia gRPC s přidaným ověřováním a autorizací](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) je na GitHubu.

>[!div class="step-by-step"]
>[Předchozí](security.md)
>[Další](channel-credentials.md)
