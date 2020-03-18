---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902036"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="4c6d5-101">Identita: Konstruktor SignInManager přijímá nový parametr.</span><span class="sxs-lookup"><span data-stu-id="4c6d5-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="4c6d5-102">Počínaje ASP.NET Jádrem 3.0 `IUserConfirmation<TUser>` byl do `SignInManager` konstruktoru přidán nový parametr.</span><span class="sxs-lookup"><span data-stu-id="4c6d5-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="4c6d5-103">Další informace naleznete [v tématu dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="4c6d5-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4c6d5-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="4c6d5-104">Version introduced</span></span>

<span data-ttu-id="4c6d5-105">3.0</span><span class="sxs-lookup"><span data-stu-id="4c6d5-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4c6d5-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4c6d5-106">Reason for change</span></span>

<span data-ttu-id="4c6d5-107">Motivací pro změnu bylo přidat podporu pro nové e-mailové / potvrzovací toky v Identity.</span><span class="sxs-lookup"><span data-stu-id="4c6d5-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c6d5-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4c6d5-108">Recommended action</span></span>

<span data-ttu-id="4c6d5-109">Pokud ručně vytváření `SignInManager`, poskytují implementaci `IUserConfirmation` nebo uchopit jeden z vkládání závislostí poskytnout.</span><span class="sxs-lookup"><span data-stu-id="4c6d5-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="4c6d5-110">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4c6d5-110">Category</span></span>

<span data-ttu-id="4c6d5-111">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4c6d5-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c6d5-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4c6d5-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
