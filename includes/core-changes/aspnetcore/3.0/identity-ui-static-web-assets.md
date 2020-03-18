---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041656"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="764ee-101">Identita: Uživatelské uživatelské zařízení používá funkci statických webových datových zdrojů</span><span class="sxs-lookup"><span data-stu-id="764ee-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="764ee-102">ASP.NET Core 3.0 představil statickou funkci webových datových zdrojů a uživatelské uživatelské uživatelské číslo identity ji přijalo.</span><span class="sxs-lookup"><span data-stu-id="764ee-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="764ee-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="764ee-103">Change description</span></span>

<span data-ttu-id="764ee-104">V důsledku identity uživatelského uživatelského prvku přijetí statické webové datové zdroje funkce:</span><span class="sxs-lookup"><span data-stu-id="764ee-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="764ee-105">Výběr architektury se provádí `IdentityUIFrameworkVersion` pomocí vlastnosti v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="764ee-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="764ee-106">Bootstrap 4 je výchozí rozhraní ui pro rozhraní identity.</span><span class="sxs-lookup"><span data-stu-id="764ee-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="764ee-107">Bootstrap 3 dosáhl konce životnosti a měli byste zvážit migraci na podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="764ee-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="764ee-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="764ee-108">Version introduced</span></span>

<span data-ttu-id="764ee-109">3.0</span><span class="sxs-lookup"><span data-stu-id="764ee-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="764ee-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="764ee-110">Old behavior</span></span>

<span data-ttu-id="764ee-111">Výchozí rozhraní ui pro identity ui byl **Bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="764ee-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="764ee-112">Rozhraní ui lze nakonfigurovat pomocí `AddDefaultUI` parametru `Startup.ConfigureServices`volání metody v .</span><span class="sxs-lookup"><span data-stu-id="764ee-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="764ee-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="764ee-113">New behavior</span></span>

<span data-ttu-id="764ee-114">Výchozí rozhraní ui pro identity ui je **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="764ee-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="764ee-115">Rozhraní ui musí být nakonfigurovánv souboru `AddDefaultUI` projektu, nikoli ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="764ee-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="764ee-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="764ee-116">Reason for change</span></span>

<span data-ttu-id="764ee-117">Přijetí funkce statické webové datové zdroje vyžaduje, aby konfigurace rozhraní rozhraní přesunout do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="764ee-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="764ee-118">Rozhodnutí, na kterém rámci vložit je sestavení rozhodnutí, nikoli runtime rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="764ee-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="764ee-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="764ee-119">Recommended action</span></span>

<span data-ttu-id="764ee-120">Zkontrolujte své rozhraní webu, abyste se ujistili, že nové komponenty Bootstrap 4 jsou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="764ee-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="764ee-121">V případě potřeby `IdentityUIFrameworkVersion` použijte msbuild vlastnost vrátit do Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="764ee-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="764ee-122">Přidejte vlastnost `<PropertyGroup>` do prvku v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="764ee-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="764ee-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="764ee-123">Category</span></span>

<span data-ttu-id="764ee-124">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="764ee-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="764ee-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="764ee-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
