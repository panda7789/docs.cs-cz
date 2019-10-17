---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394065"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="1a621-101">Autorizace: přetížení AddAuthorization se přesunulo do jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a621-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="1a621-102">Základní metody `AddAuthorization`, které se nacházejí v `Microsoft.AspNetCore.Authorization`, byly přejmenovány na `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="1a621-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="1a621-103">Staré metody `AddAuthorization` stále existují, ale místo toho jsou v balíčku `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="1a621-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` package instead.</span></span> <span data-ttu-id="1a621-104">U aplikací, které používají obě metody, by se měl zobrazit žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="1a621-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="1a621-105">Aplikace, které balíček zásad nepoužívaly, se musí přepnout na použití `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="1a621-105">Apps that weren't using the policy package must switch to using `AddAuthorizationCore`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1a621-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="1a621-106">Version introduced</span></span>

<span data-ttu-id="1a621-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1a621-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1a621-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="1a621-108">Old behavior</span></span>

<span data-ttu-id="1a621-109">v `Microsoft.AspNetCore.Authorization` existovaly metody `AddAuthorization`.</span><span class="sxs-lookup"><span data-stu-id="1a621-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1a621-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="1a621-110">New behavior</span></span>

<span data-ttu-id="1a621-111">v `Microsoft.AspNetCore.Authorization.Policy` existují metody `AddAuthorization`.</span><span class="sxs-lookup"><span data-stu-id="1a621-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="1a621-112">`AddAuthorizationCore` je nový název pro staré metody.</span><span class="sxs-lookup"><span data-stu-id="1a621-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1a621-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="1a621-113">Reason for change</span></span>

<span data-ttu-id="1a621-114">`AddAuthorization` je lepší název metody pro přidání všech běžných služeb potřebných pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="1a621-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1a621-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1a621-115">Recommended action</span></span>

<span data-ttu-id="1a621-116">Buď přidejte odkaz na `Microsoft.AspNetCore.Authorization.Policy`, nebo použijte místo toho `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="1a621-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="1a621-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1a621-117">Category</span></span>

<span data-ttu-id="1a621-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1a621-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a621-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1a621-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
