---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041656"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="dd1c0-101">Identita: uživatelské rozhraní používá funkci statických webových prostředků.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="dd1c0-102">ASP.NET Core 3,0 zavedlo funkci statického webového prostředku a uživatelské rozhraní identity ho přijalo.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dd1c0-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="dd1c0-103">Change description</span></span>

<span data-ttu-id="dd1c0-104">Následkem toho, že uživatelské rozhraní identity přijímá funkci statických webových prostředků:</span><span class="sxs-lookup"><span data-stu-id="dd1c0-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="dd1c0-105">Výběr architektury se dá provést pomocí vlastnosti `IdentityUIFrameworkVersion` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="dd1c0-106">Výchozím rozhraním uživatelského rozhraní identity je Bootstrap 4.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="dd1c0-107">Spouštěcí rutina 3 dosáhla konce životnosti a měli byste zvážit migraci na podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dd1c0-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="dd1c0-108">Version introduced</span></span>

<span data-ttu-id="dd1c0-109">3.0</span><span class="sxs-lookup"><span data-stu-id="dd1c0-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dd1c0-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="dd1c0-110">Old behavior</span></span>

<span data-ttu-id="dd1c0-111">Výchozí architektura uživatelského rozhraní pro uživatelské rozhraní identity byla **bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="dd1c0-112">ROZHRANÍ .NET Framework může být nakonfigurováno pomocí parametru pro volání metody `AddDefaultUI` v `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dd1c0-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="dd1c0-113">New behavior</span></span>

<span data-ttu-id="dd1c0-114">Výchozí architektura uživatelského rozhraní pro uživatelské rozhraní identity je **bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="dd1c0-115">ROZHRANÍ .NET Framework musí být nakonfigurováno v souboru projektu místo ve volání metody `AddDefaultUI`.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dd1c0-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="dd1c0-116">Reason for change</span></span>

<span data-ttu-id="dd1c0-117">Při přijetí funkce statických webových prostředků se vyžaduje, aby se konfigurace architektury uživatelského rozhraní přesunula na MSBuild.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="dd1c0-118">Rozhodnutí, na které rozhraní vkládat, je rozhodnutí o době sestavení, ne rozhodnutí za běhu.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dd1c0-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="dd1c0-119">Recommended action</span></span>

<span data-ttu-id="dd1c0-120">Zkontrolujte uživatelské rozhraní lokality a ujistěte se, že jsou nové součásti s rutinou Bootstrap 4 kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="dd1c0-121">V případě potřeby použijte vlastnost `IdentityUIFrameworkVersion` MSBuild a vraťte se k rutině Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="dd1c0-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="dd1c0-122">Přidejte vlastnost do prvku `<PropertyGroup>` v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="dd1c0-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="dd1c0-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="dd1c0-123">Category</span></span>

<span data-ttu-id="dd1c0-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd1c0-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dd1c0-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dd1c0-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
