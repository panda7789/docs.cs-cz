---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100819"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="f7425-101">Autorizace: AddAuthorization přetížení přesunuta do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="f7425-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="f7425-102">Základní `AddAuthorization` metody, které se `Microsoft.AspNetCore.Authorization` používaly k `AddAuthorizationCore`pobývání v byly přejmenovány na .</span><span class="sxs-lookup"><span data-stu-id="f7425-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="f7425-103">Staré `AddAuthorization` metody stále existují, ale `Microsoft.AspNetCore.Authorization.Policy` jsou v sestavení místo.</span><span class="sxs-lookup"><span data-stu-id="f7425-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="f7425-104">Aplikace používající obě metody by neměly mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="f7425-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="f7425-105">Všimněte `Microsoft.AspNetCore.Authorization.Policy` si, že nyní dodává ve sdíleném rámci spíše než samostatný balíček, jak je popsáno ve [sdílené masce: Sestavení odebrána z Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="f7425-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f7425-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="f7425-106">Version introduced</span></span>

<span data-ttu-id="f7425-107">3.0</span><span class="sxs-lookup"><span data-stu-id="f7425-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f7425-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="f7425-108">Old behavior</span></span>
<span data-ttu-id="f7425-109">`AddAuthorization`metody existovaly `Microsoft.AspNetCore.Authorization`v .</span><span class="sxs-lookup"><span data-stu-id="f7425-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f7425-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="f7425-110">New behavior</span></span>

<span data-ttu-id="f7425-111">`AddAuthorization`existují metody `Microsoft.AspNetCore.Authorization.Policy`v .</span><span class="sxs-lookup"><span data-stu-id="f7425-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="f7425-112">`AddAuthorizationCore`je nový název pro staré metody.</span><span class="sxs-lookup"><span data-stu-id="f7425-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f7425-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f7425-113">Reason for change</span></span>

<span data-ttu-id="f7425-114">`AddAuthorization`je lepší název metody pro přidání všech běžných služeb potřebných pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="f7425-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f7425-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f7425-115">Recommended action</span></span>

<span data-ttu-id="f7425-116">Buď přidejte `Microsoft.AspNetCore.Authorization.Policy` odkaz `AddAuthorizationCore` na nebo použijte místo.</span><span class="sxs-lookup"><span data-stu-id="f7425-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="f7425-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f7425-117">Category</span></span>

<span data-ttu-id="f7425-118">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f7425-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7425-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f7425-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
