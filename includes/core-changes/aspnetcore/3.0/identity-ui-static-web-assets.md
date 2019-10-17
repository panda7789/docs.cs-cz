---
ms.openlocfilehash: 8d7942ef6c36c01a9ae7ae2a9739f26dfcda5813
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394358"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="7a3ed-101">Identita: uživatelské rozhraní používá funkci statických webových prostředků.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="7a3ed-102">ASP.NET Core 3,0 zavedlo funkci statického webového prostředku a uživatelské rozhraní identity ho přijalo.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7a3ed-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="7a3ed-103">Change description</span></span>

<span data-ttu-id="7a3ed-104">Následkem toho, že uživatelské rozhraní identity přijímá funkci statických webových prostředků:</span><span class="sxs-lookup"><span data-stu-id="7a3ed-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="7a3ed-105">Výběr architektury se dá provést pomocí vlastnosti `IdentityUIFrameworkVersion` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="7a3ed-106">Výchozím rozhraním uživatelského rozhraní identity je Bootstrap 4.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="7a3ed-107">Spouštěcí rutina 3 dosáhla konce životnosti a měli byste zvážit migraci na podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a3ed-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7a3ed-108">Version introduced</span></span>

<span data-ttu-id="7a3ed-109">3.0</span><span class="sxs-lookup"><span data-stu-id="7a3ed-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7a3ed-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="7a3ed-110">Old behavior</span></span>

<span data-ttu-id="7a3ed-111">Výchozí architektura uživatelského rozhraní pro uživatelské rozhraní identity byla **bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="7a3ed-112">ROZHRANÍ .NET Framework může být nakonfigurováno pomocí parametru pro volání metody `AddIdentityUI` v `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-112">The UI framework could be configured using a parameter to the `AddIdentityUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7a3ed-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="7a3ed-113">New behavior</span></span>

<span data-ttu-id="7a3ed-114">Výchozí architektura uživatelského rozhraní pro uživatelské rozhraní identity je **bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="7a3ed-115">ROZHRANÍ .NET Framework musí být nakonfigurováno v souboru projektu namísto volání metody `AddIdentityUI`.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-115">The UI framework must be configured in your project file, instead of in the `AddIdentityUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7a3ed-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="7a3ed-116">Reason for change</span></span>

<span data-ttu-id="7a3ed-117">Při přijetí funkce statických webových prostředků se vyžaduje, aby se konfigurace architektury uživatelského rozhraní přesunula na MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="7a3ed-118">Rozhodnutí, na které rozhraní vkládat, je rozhodnutí o době sestavení, ne rozhodnutí za běhu.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a3ed-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7a3ed-119">Recommended action</span></span>

<span data-ttu-id="7a3ed-120">Zkontrolujte uživatelské rozhraní lokality a ujistěte se, že jsou nové součásti s rutinou Bootstrap 4 kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="7a3ed-121">V případě potřeby použijte vlastnost `IdentityUIFrameworkVersion` MSBuild a vraťte se k rutině Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="7a3ed-122">Přidejte vlastnost do prvku `<PropertyGroup>` v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="7a3ed-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="7a3ed-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7a3ed-123">Category</span></span>

<span data-ttu-id="7a3ed-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a3ed-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a3ed-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7a3ed-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)`

-->
