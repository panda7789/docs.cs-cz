---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394232"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="407fc-101">SPAServices a NodeServices označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="407fc-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="407fc-102">Obsah následujících balíčků NuGet byly všechny zbytečné od ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="407fc-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="407fc-103">V důsledku toho jsou následující balíčky označeny jako zastaralé:</span><span class="sxs-lookup"><span data-stu-id="407fc-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="407fc-104">Služby Microsoft.AspNetCore.SpaServices</span><span class="sxs-lookup"><span data-stu-id="407fc-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="407fc-105">Služby Microsoft.AspNetCore.NodeServices</span><span class="sxs-lookup"><span data-stu-id="407fc-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="407fc-106">Ze stejného důvodu jsou následující moduly npm označeny jako zastaralé:</span><span class="sxs-lookup"><span data-stu-id="407fc-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="407fc-107">aspnet-úhlové</span><span class="sxs-lookup"><span data-stu-id="407fc-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="407fc-108">aspnet-prerendering</span><span class="sxs-lookup"><span data-stu-id="407fc-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="407fc-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="407fc-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="407fc-110">aspnet-webpack-reagovat</span><span class="sxs-lookup"><span data-stu-id="407fc-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="407fc-111">úloha domény</span><span class="sxs-lookup"><span data-stu-id="407fc-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="407fc-112">Předchozí balíčky a moduly npm budou později odebrány v rozhraní .NET 5.</span><span class="sxs-lookup"><span data-stu-id="407fc-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="407fc-113">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="407fc-113">Version introduced</span></span>

<span data-ttu-id="407fc-114">3.0</span><span class="sxs-lookup"><span data-stu-id="407fc-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="407fc-115">Staré chování</span><span class="sxs-lookup"><span data-stu-id="407fc-115">Old behavior</span></span>

<span data-ttu-id="407fc-116">Zastaralé balíčky a moduly npm byly určeny k integraci ASP.NET Core s různými jednostránkovými aplikačními (SPA) rámci.</span><span class="sxs-lookup"><span data-stu-id="407fc-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="407fc-117">Mezi takové rámce patří Angular, React a React with Redux.</span><span class="sxs-lookup"><span data-stu-id="407fc-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="407fc-118">Nové chování</span><span class="sxs-lookup"><span data-stu-id="407fc-118">New behavior</span></span>

<span data-ttu-id="407fc-119">V balíčku [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet existuje nový mechanismus integrace.</span><span class="sxs-lookup"><span data-stu-id="407fc-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="407fc-120">Balíček zůstává základem šablon projektu Angular a React od ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="407fc-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="407fc-121">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="407fc-121">Reason for change</span></span>

<span data-ttu-id="407fc-122">ASP.NET Core podporuje integraci s různými jednostránkovými rozhraními aplikace (SPA), včetně Angular, React a React with Redux.</span><span class="sxs-lookup"><span data-stu-id="407fc-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="407fc-123">Zpočátku integrace s těmito rámci bylo dosaženo s ASP.NET komponenty specifické pro jádro, které zpracovávaly scénáře, jako je předběžné vykreslování na straně serveru a integrace s webpack.</span><span class="sxs-lookup"><span data-stu-id="407fc-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="407fc-124">Jak šel čas, průmyslové standardy se měnily.</span><span class="sxs-lookup"><span data-stu-id="407fc-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="407fc-125">Každý z spa rámců vydal vlastní standardní rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="407fc-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="407fc-126">Například úhlové CLI a create-react-app.</span><span class="sxs-lookup"><span data-stu-id="407fc-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="407fc-127">Když byl v květnu 2018 vydán ASP.NET Core 2.1, tým reagoval na změnu standardů.</span><span class="sxs-lookup"><span data-stu-id="407fc-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="407fc-128">Byl zajištěn novější a jednodušší způsob integrace s vlastními řetězci nástrojů spa frameworků.</span><span class="sxs-lookup"><span data-stu-id="407fc-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="407fc-129">Nový integrační mechanismus `Microsoft.AspNetCore.SpaServices.Extensions` existuje v balíčku a zůstává základem šablon projektu Angular a React od ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="407fc-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="407fc-130">Chcete-li objasnit, že starší ASP.NET komponenty specifické pro jádro jsou irelevantní a nedoporučuje se:</span><span class="sxs-lookup"><span data-stu-id="407fc-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="407fc-131">Integrační mechanismus pre-2.1 je označen jako zastaralý.</span><span class="sxs-lookup"><span data-stu-id="407fc-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="407fc-132">Podpůrné balíčky npm jsou označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="407fc-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="407fc-133">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="407fc-133">Recommended action</span></span>

<span data-ttu-id="407fc-134">Pokud používáte tyto balíčky, aktualizujte aplikace tak, aby používaly tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="407fc-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="407fc-135">V `Microsoft.AspNetCore.SpaServices.Extensions` balíčku.</span><span class="sxs-lookup"><span data-stu-id="407fc-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="407fc-136">Poskytované spa frameworky, které používáte</span><span class="sxs-lookup"><span data-stu-id="407fc-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="407fc-137">Chcete-li povolit funkce, jako je předběžné vykreslování na straně serveru a opětovné načtení horkého modulu, přečtěte si dokumentaci k příslušnému rozhraní SPA.</span><span class="sxs-lookup"><span data-stu-id="407fc-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="407fc-138">Funkce v `Microsoft.AspNetCore.SpaServices.Extensions` in *není* zastaralá a bude i nadále podporována.</span><span class="sxs-lookup"><span data-stu-id="407fc-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="407fc-139">Kategorie</span><span class="sxs-lookup"><span data-stu-id="407fc-139">Category</span></span>

<span data-ttu-id="407fc-140">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="407fc-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="407fc-141">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="407fc-141">Affected APIs</span></span>

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
