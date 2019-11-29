---
title: IdentityServer pro nativní cloudové aplikace
description: Architekt cloudových nativních aplikací .NET pro Azure | IdentityServer
ms.date: 06/30/2019
ms.openlocfilehash: e96395766d1a4b63815c10c2c90e35a8f7f9159d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568469"
---
# <a name="identityserver-for-cloud-native-applications"></a>IdentityServer pro cloudové nativní aplikace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

IdentityServer je Open Source Server pro ověřování, který implementuje standardy OpenID Connect (OIDC) a OAuth 2,0 pro ASP.NET Core. Je navržený tak, aby poskytoval běžný způsob, jak ověřovat požadavky na všechny vaše aplikace, ať už jsou to webové, nativní, mobilní nebo koncové body rozhraní API. IdentityServer se dá použít k implementaci jednotného přihlašování (SSO) pro více aplikací a typů aplikací. Dá se použít k ověření skutečných uživatelů pomocí formulářů pro přihlášení a podobných uživatelských rozhraní i ověřování na základě služby, které obvykle zahrnuje vystavení, ověřování a obnovování tokenů bez uživatelského rozhraní. IdentityServer je navržený tak, aby bylo přizpůsobitelné řešení. Každá instance se obvykle přizpůsobí konkrétní organizaci a/nebo sadě požadavků aplikací.

## <a name="common-web-app-scenarios"></a>Běžné scénáře webových aplikací

Aplikace obvykle potřebují podporovat některé nebo všechny z následujících scénářů:

- Lidé, kteří přistupují k webovým aplikacím pomocí prohlížeče.
- Uživatelé, kteří získávají přístup k webovým rozhraním API back-endu z aplikací založených na prohlížeči.
- Uživatelé s mobilními nebo nativními klienty, kteří přistupují k back-endové webové rozhraní API.
- Jiné aplikace přistupující do back-endové webové rozhraní API (bez aktivního uživatele nebo uživatelského rozhraní).
- Každá aplikace může potřebovat interakci s dalšími webovými rozhraními API, pomocí vlastní identity nebo delegování identitě uživatele.

![typy a scénáře aplikace](./media/application-types.png)
**obrázek 8-1**. Typy a scénáře aplikace

V každém z těchto scénářů musí být vystavené funkce zabezpečené před neoprávněným použitím. Minimálně to obvykle vyžaduje ověření uživatele nebo objektu zabezpečení, který vytváří požadavek na prostředek. Toto ověřování může používat jeden z několika běžných protokolů, jako je SAML2p, WS-doOpenID nebo Connect. Komunikace s rozhraními API obvykle používá protokol OAuth2 a jeho podporu pro tokeny zabezpečení. Oddělení těchto důležitých otázek zabezpečení a jejich prováděcích detailů od samotných aplikací zajišťuje konzistenci a zlepšuje zabezpečení a udržovatelnost. Použití těchto otázek pro vyhrazený produkt, jako je IdentityServer, pomáhá požadavek každé aplikace tyto problémy vyřešit sami.

IdentityServer poskytuje middleware, který běží v aplikaci ASP.NET Core a přidává podporu pro OpenID Connect a OAuth2 (viz článek [podporované specifikace](http://docs.identityserver.io/en/latest/intro/specs.html)). Organizace vytvoří svou vlastní aplikaci ASP.NET Core s využitím middlewaru IdentityServer k tomu, aby fungovala jako STS pro všechny protokoly zabezpečení založené na tokenech. Middleware IdentityServer zpřístupňuje koncové body pro podporu standardních funkcí, včetně:

- Autorizovat (ověření koncového uživatele)
- Token (žádost o token prostřednictvím kódu programu)
- Zjišťování (metadata o serveru)
- Informace o uživateli (získat informace o uživateli pomocí platného přístupového tokenu)
- Autorizace zařízení (používá se ke spuštění autorizace toku zařízení)
- Introspekce (ověření tokenu)
- Odvolání (odvolání tokenu)
- Ukončit relaci (aktivovat jednotné odhlašování napříč všemi aplikacemi)

## <a name="getting-started"></a>Začínáme

IdentityServer4 je open source a zdarma ho použít. Můžete ji přidat do svých aplikací pomocí svých balíčků NuGet. Hlavní balíček je [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) , který se stáhl více než 4 000 000 krát. Základní balíček neobsahuje žádný kód uživatelského rozhraní a podporuje se jenom v konfiguraci paměti. Pokud ho chcete použít s databází, budete také chtít poskytovatele dat, jako je [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) , který používá Entity Framework Core k ukládání konfiguračních a provozních dat pro IdentityServer. V případě uživatelského rozhraní můžete zkopírovat soubory z [úložiště uživatelského rozhraní pro rychlé](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) zprovoznění do aplikace ASP.NET Core MVC a přidat podporu pro přihlášení a odhlášení pomocí middlewaru IdentityServer.

## <a name="configuration"></a>Konfigurace

IdentityServer podporuje různé druhy protokolů a poskytovatele pro sociální ověřování, které se dají konfigurovat jako součást každé vlastní instalace. To se obvykle provádí v `Startup` třídě ASP.NET Core aplikace v metodě `ConfigureServices`. Konfigurace zahrnuje určení podporovaných protokolů a cest k serverům a koncovým bodům, které budou použity. Obrázek 8-2 ukazuje ukázkovou konfiguraci pořízenou z projektu uživatelského rozhraní rychlého startu IdentityServer4:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

**Obrázek 8-2**. Konfigurace IdentityServer.

IdentityServer také hostuje veřejnou ukázkovou lokalitu, která se dá použít k otestování různých protokolů a konfigurací. Je umístěný na [https://demo.identityserver.io/](https://demo.identityserver.io/) a obsahuje informace o tom, jak nakonfigurovat své chování na základě `client_id`, které mu jsou k dispozici.

## <a name="javascript-clients"></a>Klienti JavaScriptu

Mnoho cloudových nativních aplikací využívá na front-endu rozhraní API na straně serveru a bohatých klientských aplikacích (jednostránkové). IdentityServer dodává [JavaScriptový klient](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html) (`oidc-client.js`) prostřednictvím NPM, který se dá přidat do jednostránkové a povolit tak použití IdentityServer pro přihlášení, odhlášení a ověřování webových rozhraní API na základě tokenu.

## <a name="references"></a>Reference

- [Dokumentace k IdentityServer](http://docs.identityserver.io/en/latest/)
- [Typy aplikací](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [Klient OIDC JavaScript](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html)

>[!div class="step-by-step"]
>[Předchozí](azure-active-directory.md)
>[Další](security.md)
