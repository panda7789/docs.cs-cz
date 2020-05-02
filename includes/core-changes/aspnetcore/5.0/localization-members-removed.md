---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728300"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="2d1e6-101">Lokalizace: odebral se člen rozhraní třídy ResourceManagerWithCultureStringLocalizer a WithCulture.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="2d1e6-102">Metoda třídy [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) a [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) byla odebrána v rozhraní .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="2d1e6-103">Kontext najdete v tématu [ASPNET/oznámení # 346](https://github.com/aspnet/Announcements/issues/346) a [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="2d1e6-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="2d1e6-104">Diskuzi o této změně najdete v tématu [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="2d1e6-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2d1e6-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2d1e6-105">Version introduced</span></span>

<span data-ttu-id="2d1e6-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="2d1e6-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2d1e6-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="2d1e6-107">Old behavior</span></span>

<span data-ttu-id="2d1e6-108">`ResourceManagerWithCultureStringLocalizer` Třída a `ResourceManagerStringLocalizer.WithCulture` metoda jsou [zastaralé v rozhraní .NET Core 3,0 Preview 3 a novější](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="2d1e6-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2d1e6-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="2d1e6-109">New behavior</span></span>

<span data-ttu-id="2d1e6-110">`ResourceManagerWithCultureStringLocalizer` Třída a `ResourceManagerStringLocalizer.WithCulture` metoda byly odebrány v rozhraní .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="2d1e6-111">Inventář provedených změn najdete v žádosti o získání dat v [dotnet/rozšířeních # 2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="2d1e6-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2d1e6-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="2d1e6-112">Reason for change</span></span>

<span data-ttu-id="2d1e6-113">Metoda [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) a [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) byla často zdrojem nejasností pro uživatele lokalizace.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="2d1e6-114">Při vytváření vlastní <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementace byla obzvláště vysoká nejasnost.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="2d1e6-115">Tato třída a metoda dává spotřebitelům dojem, že `IStringLocalizer` se očekává, že instance bude "na jazyk, podle prostředků".</span><span class="sxs-lookup"><span data-stu-id="2d1e6-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="2d1e6-116">Ve skutečnosti by instance měla být pouze "za prostředek".</span><span class="sxs-lookup"><span data-stu-id="2d1e6-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="2d1e6-117">V době běhu Určuje <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost jazyk, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2d1e6-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2d1e6-118">Recommended action</span></span>

<span data-ttu-id="2d1e6-119">Ukončete používání `ResourceManagerWithCultureStringLocalizer` třídy a `ResourceManagerStringLocalizer.WithCulture` metody.</span><span class="sxs-lookup"><span data-stu-id="2d1e6-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="2d1e6-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2d1e6-120">Category</span></span>

<span data-ttu-id="2d1e6-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2d1e6-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2d1e6-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2d1e6-122">Affected APIs</span></span>

- [<span data-ttu-id="2d1e6-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="2d1e6-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="2d1e6-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="2d1e6-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
