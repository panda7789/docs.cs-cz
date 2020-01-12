---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902036"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="3639f-101">Identita: konstruktor SignInManager akceptuje nový parametr.</span><span class="sxs-lookup"><span data-stu-id="3639f-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="3639f-102">Počínaje ASP.NET Core 3,0 byl do konstruktoru `SignInManager` přidán nový parametr `IUserConfirmation<TUser>`.</span><span class="sxs-lookup"><span data-stu-id="3639f-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="3639f-103">Další informace naleznete v tématu [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="3639f-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3639f-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="3639f-104">Version introduced</span></span>

<span data-ttu-id="3639f-105">3,0</span><span class="sxs-lookup"><span data-stu-id="3639f-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3639f-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="3639f-106">Reason for change</span></span>

<span data-ttu-id="3639f-107">Motivací pro změnu byla přidání podpory pro nové toky e-mailu a potvrzení identity.</span><span class="sxs-lookup"><span data-stu-id="3639f-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3639f-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3639f-108">Recommended action</span></span>

<span data-ttu-id="3639f-109">Pokud je ručně vytvořen `SignInManager`, Poskytněte implementaci `IUserConfirmation` nebo předejte od injektáže závislosti k poskytnutí.</span><span class="sxs-lookup"><span data-stu-id="3639f-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="3639f-110">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3639f-110">Category</span></span>

<span data-ttu-id="3639f-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3639f-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3639f-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3639f-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
