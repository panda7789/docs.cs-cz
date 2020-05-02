---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728337"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="33370-101">Lokalizace: ResourceManagerWithCultureStringLocalizer a WithCulture označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="33370-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="33370-102">Člen třídy [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) a rozhraní [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) jsou často zdrojem nejasností pro uživatele lokalizace, zejména při vytváření vlastní `IStringLocalizer` implementace.</span><span class="sxs-lookup"><span data-stu-id="33370-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="33370-103">Tyto položky přidávají uživateli dojem, že je `IStringLocalizer` instance "na jazyk, podle prostředků".</span><span class="sxs-lookup"><span data-stu-id="33370-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="33370-104">Ve skutečnosti by měly být instance pouze "za prostředek".</span><span class="sxs-lookup"><span data-stu-id="33370-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="33370-105">Hledaný jazyk je určen `CultureInfo.CurrentUICulture` v době spuštění.</span><span class="sxs-lookup"><span data-stu-id="33370-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="33370-106">Aby se vyloučil zdroj nejasností, rozhraní API byla v ASP.NET Core 3,0 Preview 3 označená jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="33370-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="33370-107">Rozhraní API se v budoucí verzi odeberou.</span><span class="sxs-lookup"><span data-stu-id="33370-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="33370-108">Pro kontext viz [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="33370-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="33370-109">Diskuzi najdete v tématu [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="33370-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="33370-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="33370-110">Version introduced</span></span>

<span data-ttu-id="33370-111">3.0</span><span class="sxs-lookup"><span data-stu-id="33370-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="33370-112">Staré chování</span><span class="sxs-lookup"><span data-stu-id="33370-112">Old behavior</span></span>

<span data-ttu-id="33370-113">Metody nebyly označeny jako `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="33370-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="33370-114">Nové chování</span><span class="sxs-lookup"><span data-stu-id="33370-114">New behavior</span></span>

<span data-ttu-id="33370-115">Metody jsou označeny `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="33370-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="33370-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="33370-116">Reason for change</span></span>

<span data-ttu-id="33370-117">Rozhraní API představovaly případ použití, který se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="33370-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="33370-118">Při návrhu lokalizace došlo k nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="33370-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="33370-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="33370-119">Recommended action</span></span>

<span data-ttu-id="33370-120">Doporučujeme místo toho použít `ResourceManagerStringLocalizer` .</span><span class="sxs-lookup"><span data-stu-id="33370-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="33370-121">Povolit jazykovou verzi nastavením `CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="33370-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="33370-122">Pokud to není možnost, vytvořte a použijte kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="33370-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="33370-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="33370-123">Category</span></span>

<span data-ttu-id="33370-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33370-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="33370-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="33370-125">Affected APIs</span></span>

- [<span data-ttu-id="33370-126">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="33370-126">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [<span data-ttu-id="33370-127">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="33370-127">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
