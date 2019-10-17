---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394232"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Jednostránkové: SpaServices a NodeServices označené jako zastaralé

Obsah následujících balíčků NuGet byl od ASP.NET Core 2,1 zbytečný. V důsledku toho jsou následující balíčky označeny jako zastaralé:

- [Microsoft. AspNetCore. SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft. AspNetCore. NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Ze stejného důvodu jsou následující moduly npm označeny jako zastaralé:

- [ASPNET – úhlová](https://www.npmjs.com/package/aspnet-angular)
- [ASPNET – předběžné vykreslování](https://www.npmjs.com/package/aspnet-prerendering)
- [ASPNET – Webpack](https://www.npmjs.com/package/aspnet-webpack)
- [ASPNET – Webpack – reakce](https://www.npmjs.com/package/aspnet-webpack-react)
- [Doména – úloha](https://www.npmjs.com/package/domain-task)

Předchozí balíčky a moduly npm budou později odebrány v rozhraní .NET 5.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Zastaralé balíčky a moduly npm byly určeny k integraci ASP.NET Core s různými architekturami jednostránkové aplikace (SPA). Mezi takové architektury patří úhlová, reakce a reakce na Redux.

#### <a name="new-behavior"></a>Nové chování

V balíčku NuGet [Microsoft. AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) existuje nový integrační mechanismus. Balíček zůstává základem úhlů a Reagujecích šablon projektů od ASP.NET Core 2,1.

#### <a name="reason-for-change"></a>Důvod změny

ASP.NET Core podporuje integraci s různými architekturami jednostránkové aplikace (SPA), včetně úhlů, reakce a reakce na Redux. Zpočátku se integrace s těmito rozhraními provedla s ASP.NET Core specifickými komponentami, které zpracovávají scénáře jako předběžné vykreslování na straně serveru a integraci s nástrojem Webpack. V době, kdy došlo k úpravě, se oborové standardy změnily. Každé rozhraní zabezpečeného ověřování hesla uvolnilo vlastní standardní rozhraní příkazového řádku. Například úhlové CLI a vytvořit reakci-aplikace.

Po vydání ASP.NET Core 2,1 do května 2018 tým odpověděl na změnu v normách. Byl poskytnut novější a jednodušší způsob, jak integrovat s vlastními sady nástrojů architekturou SPA. Nový integrační mechanismus existuje v balíčku `Microsoft.AspNetCore.SpaServices.Extensions` a zůstává základem úhlů a reakci šablon projektů od ASP.NET Core 2,1.

Pro objasnění, že starší součásti specifické pro ASP.NET Core jsou důležité a nedoporučuje se:

- Mechanismus Integration pre-2,1 je označený jako zastaralý.
- Podpůrné balíčky npm jsou označeny jako zastaralé.

#### <a name="recommended-action"></a>Doporučená akce

Pokud tyto balíčky používáte, aktualizujte aplikace tak, aby používaly tyto funkce:

- V balíčku `Microsoft.AspNetCore.SpaServices.Extensions`.
- Poskytované rozhraními zabezpečeného hesla, které používáte

Pokud chcete povolit funkce, jako je například předběžné vykreslení na straně serveru a Hot Module reload, přečtěte si dokumentaci pro odpovídající architekturu SPA. Funkce v @no__t- *0 není zastaralá* a bude nadále podporována.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
