---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394232"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>SPAServices a NodeServices označené jako zastaralé

Obsah následujících balíčků NuGet byly všechny zbytečné od ASP.NET Core 2.1. V důsledku toho jsou následující balíčky označeny jako zastaralé:

- [Služby Microsoft.AspNetCore.SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Služby Microsoft.AspNetCore.NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Ze stejného důvodu jsou následující moduly npm označeny jako zastaralé:

- [aspnet-úhlové](https://www.npmjs.com/package/aspnet-angular)
- [aspnet-prerendering](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-reagovat](https://www.npmjs.com/package/aspnet-webpack-react)
- [úloha domény](https://www.npmjs.com/package/domain-task)

Předchozí balíčky a moduly npm budou později odebrány v rozhraní .NET 5.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Zastaralé balíčky a moduly npm byly určeny k integraci ASP.NET Core s různými jednostránkovými aplikačními (SPA) rámci. Mezi takové rámce patří Angular, React a React with Redux.

#### <a name="new-behavior"></a>Nové chování

V balíčku [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet existuje nový mechanismus integrace. Balíček zůstává základem šablon projektu Angular a React od ASP.NET Core 2.1.

#### <a name="reason-for-change"></a>Důvod změny

ASP.NET Core podporuje integraci s různými jednostránkovými rozhraními aplikace (SPA), včetně Angular, React a React with Redux. Zpočátku integrace s těmito rámci bylo dosaženo s ASP.NET komponenty specifické pro jádro, které zpracovávaly scénáře, jako je předběžné vykreslování na straně serveru a integrace s webpack. Jak šel čas, průmyslové standardy se měnily. Každý z spa rámců vydal vlastní standardní rozhraní příkazového řádku. Například úhlové CLI a create-react-app.

Když byl v květnu 2018 vydán ASP.NET Core 2.1, tým reagoval na změnu standardů. Byl zajištěn novější a jednodušší způsob integrace s vlastními řetězci nástrojů spa frameworků. Nový integrační mechanismus `Microsoft.AspNetCore.SpaServices.Extensions` existuje v balíčku a zůstává základem šablon projektu Angular a React od ASP.NET Core 2.1.

Chcete-li objasnit, že starší ASP.NET komponenty specifické pro jádro jsou irelevantní a nedoporučuje se:

- Integrační mechanismus pre-2.1 je označen jako zastaralý.
- Podpůrné balíčky npm jsou označeny jako zastaralé.

#### <a name="recommended-action"></a>Doporučená akce

Pokud používáte tyto balíčky, aktualizujte aplikace tak, aby používaly tyto funkce:

- V `Microsoft.AspNetCore.SpaServices.Extensions` balíčku.
- Poskytované spa frameworky, které používáte

Chcete-li povolit funkce, jako je předběžné vykreslování na straně serveru a opětovné načtení horkého modulu, přečtěte si dokumentaci k příslušnému rozhraní SPA. Funkce v `Microsoft.AspNetCore.SpaServices.Extensions` in *není* zastaralá a bude i nadále podporována.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

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
