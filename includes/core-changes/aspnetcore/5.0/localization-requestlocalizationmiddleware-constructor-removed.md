---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281334"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>Lokalizace: v middlewari pro lokalizaci požadavků byl odebrán zastaralý konstruktor.

<xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Konstruktor, který postrádá parametr, <xref:Microsoft.Extensions.Logging.ILoggerFactory> byl [v tomto potvrzení](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)označen jako zastaralý. V ASP.NET Core 5,0 byl odebrán zastaralý konstruktor. Diskuzi najdete v tématu [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).

#### <a name="version-introduced"></a>Představená verze

5.0

#### <a name="old-behavior"></a>Staré chování

Zastaralý `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` konstruktor existuje.

#### <a name="new-behavior"></a>Nové chování

Zastaralý `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` konstruktor neexistuje.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna zajišťuje, že middleware lokalizace požadavků má vždycky přístup k protokolovacímu nástroje.

#### <a name="recommended-action"></a>Doporučená akce

Při ruční konstrukci instance třídy `RequestLocalizationMiddleware` předejte `ILoggerFactory` instanci v konstruktoru. Pokud `ILoggerFactory` v tomto kontextu není k dispozici platná instance, zvažte předání konstruktoru middleware <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instanci.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

[RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
