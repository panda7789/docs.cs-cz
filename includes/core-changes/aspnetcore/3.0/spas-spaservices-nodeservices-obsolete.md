---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394232"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="2b100-101">Jednostránkové: SpaServices a NodeServices označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="2b100-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="2b100-102">Obsah následujících balíčků NuGet byl od ASP.NET Core 2,1 zbytečný.</span><span class="sxs-lookup"><span data-stu-id="2b100-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="2b100-103">V důsledku toho jsou následující balíčky označeny jako zastaralé:</span><span class="sxs-lookup"><span data-stu-id="2b100-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="2b100-104">Microsoft. AspNetCore. SpaServices</span><span class="sxs-lookup"><span data-stu-id="2b100-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="2b100-105">Microsoft. AspNetCore. NodeServices</span><span class="sxs-lookup"><span data-stu-id="2b100-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="2b100-106">Ze stejného důvodu jsou následující moduly npm označeny jako zastaralé:</span><span class="sxs-lookup"><span data-stu-id="2b100-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="2b100-107">ASPNET – úhlová</span><span class="sxs-lookup"><span data-stu-id="2b100-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="2b100-108">ASPNET – předběžné vykreslování</span><span class="sxs-lookup"><span data-stu-id="2b100-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="2b100-109">ASPNET – Webpack</span><span class="sxs-lookup"><span data-stu-id="2b100-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="2b100-110">ASPNET – Webpack – reakce</span><span class="sxs-lookup"><span data-stu-id="2b100-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="2b100-111">Doména – úloha</span><span class="sxs-lookup"><span data-stu-id="2b100-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="2b100-112">Předchozí balíčky a moduly npm budou později odebrány v rozhraní .NET 5.</span><span class="sxs-lookup"><span data-stu-id="2b100-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b100-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2b100-113">Version introduced</span></span>

<span data-ttu-id="2b100-114">3.0</span><span class="sxs-lookup"><span data-stu-id="2b100-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2b100-115">Staré chování</span><span class="sxs-lookup"><span data-stu-id="2b100-115">Old behavior</span></span>

<span data-ttu-id="2b100-116">Zastaralé balíčky a moduly npm byly určeny k integraci ASP.NET Core s různými architekturami jednostránkové aplikace (SPA).</span><span class="sxs-lookup"><span data-stu-id="2b100-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="2b100-117">Mezi takové architektury patří úhlová, reakce a reakce na Redux.</span><span class="sxs-lookup"><span data-stu-id="2b100-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2b100-118">Nové chování</span><span class="sxs-lookup"><span data-stu-id="2b100-118">New behavior</span></span>

<span data-ttu-id="2b100-119">V balíčku NuGet [Microsoft. AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) existuje nový integrační mechanismus.</span><span class="sxs-lookup"><span data-stu-id="2b100-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="2b100-120">Balíček zůstává základem úhlů a Reagujecích šablon projektů od ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="2b100-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2b100-121">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="2b100-121">Reason for change</span></span>

<span data-ttu-id="2b100-122">ASP.NET Core podporuje integraci s různými architekturami jednostránkové aplikace (SPA), včetně úhlů, reakce a reakce na Redux.</span><span class="sxs-lookup"><span data-stu-id="2b100-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="2b100-123">Zpočátku se integrace s těmito rozhraními provedla s ASP.NET Core specifickými komponentami, které zpracovávají scénáře jako předběžné vykreslování na straně serveru a integraci s nástrojem Webpack.</span><span class="sxs-lookup"><span data-stu-id="2b100-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="2b100-124">V době, kdy došlo k úpravě, se oborové standardy změnily.</span><span class="sxs-lookup"><span data-stu-id="2b100-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="2b100-125">Každé rozhraní zabezpečeného ověřování hesla uvolnilo vlastní standardní rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2b100-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="2b100-126">Například úhlové CLI a vytvořit reakci-aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b100-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="2b100-127">Po vydání ASP.NET Core 2,1 do května 2018 tým odpověděl na změnu v normách.</span><span class="sxs-lookup"><span data-stu-id="2b100-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="2b100-128">Byl poskytnut novější a jednodušší způsob, jak integrovat s vlastními sady nástrojů architekturou SPA.</span><span class="sxs-lookup"><span data-stu-id="2b100-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="2b100-129">Nový integrační mechanismus existuje v balíčku `Microsoft.AspNetCore.SpaServices.Extensions` a zůstává základem úhlů a reakci šablon projektů od ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="2b100-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="2b100-130">Pro objasnění, že starší součásti specifické pro ASP.NET Core jsou důležité a nedoporučuje se:</span><span class="sxs-lookup"><span data-stu-id="2b100-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="2b100-131">Mechanismus Integration pre-2,1 je označený jako zastaralý.</span><span class="sxs-lookup"><span data-stu-id="2b100-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="2b100-132">Podpůrné balíčky npm jsou označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2b100-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b100-133">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2b100-133">Recommended action</span></span>

<span data-ttu-id="2b100-134">Pokud tyto balíčky používáte, aktualizujte aplikace tak, aby používaly tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="2b100-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="2b100-135">V balíčku `Microsoft.AspNetCore.SpaServices.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="2b100-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="2b100-136">Poskytované rozhraními zabezpečeného hesla, které používáte</span><span class="sxs-lookup"><span data-stu-id="2b100-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="2b100-137">Pokud chcete povolit funkce, jako je například předběžné vykreslení na straně serveru a Hot Module reload, přečtěte si dokumentaci pro odpovídající architekturu SPA.</span><span class="sxs-lookup"><span data-stu-id="2b100-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="2b100-138">Funkce v @no__t- *0 není zastaralá* a bude nadále podporována.</span><span class="sxs-lookup"><span data-stu-id="2b100-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="2b100-139">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2b100-139">Category</span></span>

<span data-ttu-id="2b100-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2b100-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b100-141">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2b100-141">Affected APIs</span></span>

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
