---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901940"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="322cb-101">Lokalizace: ResourceManagerWithCultureStringLocalizer a WithCulture označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="322cb-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="322cb-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) třídy a [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) člen rozhraní jsou často zdrojem nejasností `IStringLocalizer` pro uživatele lokalizace, zejména při vytváření vlastní implementace.</span><span class="sxs-lookup"><span data-stu-id="322cb-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="322cb-103">Tyto položky dávají uživateli `IStringLocalizer` dojem, že instance je "podle jazyka, podle prostředku".</span><span class="sxs-lookup"><span data-stu-id="322cb-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="322cb-104">Ve skutečnosti by instance měly být pouze "na prostředek".</span><span class="sxs-lookup"><span data-stu-id="322cb-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="322cb-105">Vyhledávaný jazyk je `CultureInfo.CurrentUICulture` určen časem spuštění.</span><span class="sxs-lookup"><span data-stu-id="322cb-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="322cb-106">Chcete-li odstranit zdroj nejasností, byla v ASP.NET core 3.0 Preview 3 označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="322cb-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="322cb-107">Api budou odebrány v budoucí verzi.</span><span class="sxs-lookup"><span data-stu-id="322cb-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="322cb-108">Kontext naleznete [v tématu dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="322cb-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="322cb-109">Diskuse naleznete [v tématu dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="322cb-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="322cb-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="322cb-110">Version introduced</span></span>

<span data-ttu-id="322cb-111">3.0</span><span class="sxs-lookup"><span data-stu-id="322cb-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="322cb-112">Staré chování</span><span class="sxs-lookup"><span data-stu-id="322cb-112">Old behavior</span></span>

<span data-ttu-id="322cb-113">Metody nebyly označeny `Obsolete`jako .</span><span class="sxs-lookup"><span data-stu-id="322cb-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="322cb-114">Nové chování</span><span class="sxs-lookup"><span data-stu-id="322cb-114">New behavior</span></span>

<span data-ttu-id="322cb-115">Metody jsou `Obsolete`označeny .</span><span class="sxs-lookup"><span data-stu-id="322cb-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="322cb-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="322cb-116">Reason for change</span></span>

<span data-ttu-id="322cb-117">Api představovalpřípad použití, který není doporučeno.</span><span class="sxs-lookup"><span data-stu-id="322cb-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="322cb-118">Tam byl zmatek o návrhu lokalizace.</span><span class="sxs-lookup"><span data-stu-id="322cb-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="322cb-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="322cb-119">Recommended action</span></span>

<span data-ttu-id="322cb-120">Doporučení je použít `ResourceManagerStringLocalizer` místo.</span><span class="sxs-lookup"><span data-stu-id="322cb-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="322cb-121">Nechť je jazyková verze nastavena souborem `CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="322cb-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="322cb-122">Pokud to není možnost, vytvořte a použijte kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="322cb-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="322cb-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="322cb-123">Category</span></span>

<span data-ttu-id="322cb-124">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="322cb-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="322cb-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="322cb-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
