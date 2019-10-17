---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394365"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="30055-101">Identita: konstruktor SignInManager akceptuje nový parametr.</span><span class="sxs-lookup"><span data-stu-id="30055-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="30055-102">Počínaje ASP.NET Core 3,0 byl do konstruktoru `SignInManager` přidán nový parametr `IUserConfirmation<TUser>`.</span><span class="sxs-lookup"><span data-stu-id="30055-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="30055-103">Další informace najdete v tématu [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="30055-103">For more information, see [aspnet/AspNetCore#8356](https://github.com/aspnet/AspNetCore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30055-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="30055-104">Version introduced</span></span>

<span data-ttu-id="30055-105">3.0</span><span class="sxs-lookup"><span data-stu-id="30055-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="30055-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="30055-106">Reason for change</span></span>

<span data-ttu-id="30055-107">Motivací pro změnu byla přidání podpory pro nové toky e-mailu a potvrzení identity.</span><span class="sxs-lookup"><span data-stu-id="30055-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30055-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="30055-108">Recommended action</span></span>

<span data-ttu-id="30055-109">Pokud je ručně vytvořen `SignInManager`, Poskytněte implementaci `IUserConfirmation` nebo jeden ze vkládání závislostí k poskytnutí.</span><span class="sxs-lookup"><span data-stu-id="30055-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="30055-110">Kategorie</span><span class="sxs-lookup"><span data-stu-id="30055-110">Category</span></span>

<span data-ttu-id="30055-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30055-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30055-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="30055-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
