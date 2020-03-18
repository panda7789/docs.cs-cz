---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198404"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="0ef70-101">Ukládání do mezipaměti: Microsoft.Extensions.Caching.SqlServer používá nový balíček SqlClient</span><span class="sxs-lookup"><span data-stu-id="0ef70-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="0ef70-102">Balíček `Microsoft.Extensions.Caching.SqlServer` bude používat `Microsoft.Data.SqlClient` nový `System.Data.SqlClient` balíček namísto balíčku.</span><span class="sxs-lookup"><span data-stu-id="0ef70-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="0ef70-103">Tato změna může způsobit mírné změny chování lámání.</span><span class="sxs-lookup"><span data-stu-id="0ef70-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="0ef70-104">Další informace naleznete [v tématu Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="0ef70-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0ef70-105">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0ef70-105">Version introduced</span></span>

<span data-ttu-id="0ef70-106">3.0</span><span class="sxs-lookup"><span data-stu-id="0ef70-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0ef70-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0ef70-107">Old behavior</span></span>

<span data-ttu-id="0ef70-108">Balíček `Microsoft.Extensions.Caching.SqlServer` použil `System.Data.SqlClient` balíček.</span><span class="sxs-lookup"><span data-stu-id="0ef70-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0ef70-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0ef70-109">New behavior</span></span>

<span data-ttu-id="0ef70-110">`Microsoft.Extensions.Caching.SqlServer`nyní používá `Microsoft.Data.SqlClient` balíček.</span><span class="sxs-lookup"><span data-stu-id="0ef70-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0ef70-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0ef70-111">Reason for change</span></span>

<span data-ttu-id="0ef70-112">`Microsoft.Data.SqlClient`je nový balíček, který `System.Data.SqlClient`je postaven mimo .</span><span class="sxs-lookup"><span data-stu-id="0ef70-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="0ef70-113">To je místo, kde všechny nové funkce práce bude provedeno od nynějška.</span><span class="sxs-lookup"><span data-stu-id="0ef70-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0ef70-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0ef70-114">Recommended action</span></span>

<span data-ttu-id="0ef70-115">Zákazníci by se neměli obávat této narušující změny, pokud nepoužívali typy vrácené `Microsoft.Extensions.Caching.SqlServer` balíčkem a přetypovali je na `System.Data.SqlClient` typy.</span><span class="sxs-lookup"><span data-stu-id="0ef70-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="0ef70-116">Například pokud někdo byl `DbConnection` přetypování na [starý typ SqlConnection](xref:System.Data.SqlClient.SqlConnection), budou `Microsoft.Data.SqlClient.SqlConnection` muset změnit přetypování na nový typ.</span><span class="sxs-lookup"><span data-stu-id="0ef70-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="0ef70-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0ef70-117">Category</span></span>

<span data-ttu-id="0ef70-118">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0ef70-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0ef70-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0ef70-119">Affected APIs</span></span>

<span data-ttu-id="0ef70-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="0ef70-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
