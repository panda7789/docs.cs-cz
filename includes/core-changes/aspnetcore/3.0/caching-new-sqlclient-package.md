---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198404"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="14062-101">Ukládání do mezipaměti: Microsoft. Extensions. Caching. SqlServer používá nový balíček SqlClient.</span><span class="sxs-lookup"><span data-stu-id="14062-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="14062-102">Balíček `Microsoft.Extensions.Caching.SqlServer` použije nový balíček `Microsoft.Data.SqlClient` místo balíčku `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="14062-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="14062-103">Tato změna by mohla způsobit mírné změny v chování.</span><span class="sxs-lookup"><span data-stu-id="14062-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="14062-104">Další informace najdete v tématu [představení nového Microsoft. data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="14062-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="14062-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="14062-105">Version introduced</span></span>

<span data-ttu-id="14062-106">3.0</span><span class="sxs-lookup"><span data-stu-id="14062-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="14062-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="14062-107">Old behavior</span></span>

<span data-ttu-id="14062-108">Balíček `Microsoft.Extensions.Caching.SqlServer` použil balíček `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="14062-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="14062-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="14062-109">New behavior</span></span>

<span data-ttu-id="14062-110">`Microsoft.Extensions.Caching.SqlServer` nyní používá balíček `Microsoft.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="14062-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="14062-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="14062-111">Reason for change</span></span>

<span data-ttu-id="14062-112">`Microsoft.Data.SqlClient` je nový balíček, který je vytvořen z `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="14062-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="14062-113">Je to místo, kde se všechny nové funkce budou dělat hned na.</span><span class="sxs-lookup"><span data-stu-id="14062-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="14062-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="14062-114">Recommended action</span></span>

<span data-ttu-id="14062-115">Zákazníci by se neměli muset starat o tuto zásadní změnu, pokud nepoužívali typy vrácené balíčkem `Microsoft.Extensions.Caching.SqlServer` a přetypování do `System.Data.SqlClient` typů.</span><span class="sxs-lookup"><span data-stu-id="14062-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="14062-116">Pokud někdo například přetypování `DbConnection` na [starý typ SqlConnection](xref:System.Data.SqlClient.SqlConnection), museli byste přetypování změnit na nový typ `Microsoft.Data.SqlClient.SqlConnection`.</span><span class="sxs-lookup"><span data-stu-id="14062-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="14062-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="14062-117">Category</span></span>

<span data-ttu-id="14062-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="14062-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14062-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="14062-119">Affected APIs</span></span>

<span data-ttu-id="14062-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="14062-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
