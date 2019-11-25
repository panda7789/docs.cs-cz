---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74100819"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="a198d-101">Autorizace: přetížení AddAuthorization se přesunulo do jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a198d-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="a198d-102">Základní metody `AddAuthorization`, které se nacházejí v `Microsoft.AspNetCore.Authorization`, byly přejmenovány na `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="a198d-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="a198d-103">Staré metody `AddAuthorization` stále existují, ale jsou místo toho v sestavení `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="a198d-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="a198d-104">U aplikací, které používají obě metody, by se měl zobrazit žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="a198d-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="a198d-105">Všimněte si, že `Microsoft.AspNetCore.Authorization.Policy` nyní dodává do sdíleného rozhraní, nikoli jako samostatný balíček, jak je popsáno v tématu [Shared Framework: sestavení byla odebrána z Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="a198d-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a198d-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a198d-106">Version introduced</span></span>

<span data-ttu-id="a198d-107">3.0</span><span class="sxs-lookup"><span data-stu-id="a198d-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a198d-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="a198d-108">Old behavior</span></span>
<span data-ttu-id="a198d-109">v `Microsoft.AspNetCore.Authorization` existovaly metody `AddAuthorization`.</span><span class="sxs-lookup"><span data-stu-id="a198d-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a198d-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="a198d-110">New behavior</span></span>

<span data-ttu-id="a198d-111">v `Microsoft.AspNetCore.Authorization.Policy` existují metody `AddAuthorization`.</span><span class="sxs-lookup"><span data-stu-id="a198d-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="a198d-112">`AddAuthorizationCore` je nový název pro staré metody.</span><span class="sxs-lookup"><span data-stu-id="a198d-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a198d-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="a198d-113">Reason for change</span></span>

<span data-ttu-id="a198d-114">`AddAuthorization` je lepší název metody pro přidání všech běžných služeb potřebných pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="a198d-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a198d-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a198d-115">Recommended action</span></span>

<span data-ttu-id="a198d-116">Buď přidejte odkaz na `Microsoft.AspNetCore.Authorization.Policy`, nebo použijte místo toho `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="a198d-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="a198d-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a198d-117">Category</span></span>

<span data-ttu-id="a198d-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a198d-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a198d-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a198d-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
