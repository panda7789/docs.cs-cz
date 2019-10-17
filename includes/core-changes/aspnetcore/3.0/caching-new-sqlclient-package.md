---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394277"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="625a4-101">Ukládání do mezipaměti: Microsoft. Extensions. Caching. SqlServer používá nový balíček SqlClient.</span><span class="sxs-lookup"><span data-stu-id="625a4-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="625a4-102">Balíček `Microsoft.Extensions.Caching.SqlServer` použije nový balíček `Microsoft.Data.SqlClient` místo balíčku `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="625a4-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="625a4-103">Tato změna by mohla způsobit mírné změny v chování.</span><span class="sxs-lookup"><span data-stu-id="625a4-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="625a4-104">Další informace najdete v tématu [představení nového Microsoft. data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="625a4-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="625a4-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="625a4-105">Version introduced</span></span>

<span data-ttu-id="625a4-106">3.0</span><span class="sxs-lookup"><span data-stu-id="625a4-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="625a4-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="625a4-107">Old behavior</span></span>

<span data-ttu-id="625a4-108">Balíček `Microsoft.Extensions.Caching.SqlServer` použil balíček `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="625a4-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="625a4-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="625a4-109">New behavior</span></span>

<span data-ttu-id="625a4-110">`Microsoft.Extensions.Caching.SqlServer` nyní používá balíček `Microsoft.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="625a4-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="625a4-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="625a4-111">Reason for change</span></span>

<span data-ttu-id="625a4-112">`Microsoft.Data.SqlClient` je nový balíček, který je vytvořen z `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="625a4-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="625a4-113">Je to místo, kde se všechny nové funkce budou dělat hned na.</span><span class="sxs-lookup"><span data-stu-id="625a4-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="625a4-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="625a4-114">Recommended action</span></span>

<span data-ttu-id="625a4-115">Zákazníci by se neměli muset starat o tuto zásadní změnu, pokud nepoužívali typy vrácené balíčkem `Microsoft.Extensions.Caching.SqlServer` a přetypování do `System.Data.SqlClient` typů.</span><span class="sxs-lookup"><span data-stu-id="625a4-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="625a4-116">Pokud někdo například přetypování `DbConnection` na [starý typ SqlConnection](xref:System.Data.SqlClient.SqlConnection), museli byste přetypování změnit na nový typ `Microsoft.Data.SqlClient.SqlConnection`.</span><span class="sxs-lookup"><span data-stu-id="625a4-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span> 

#### <a name="category"></a><span data-ttu-id="625a4-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="625a4-117">Category</span></span>

<span data-ttu-id="625a4-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="625a4-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="625a4-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="625a4-119">Affected APIs</span></span>

<span data-ttu-id="625a4-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="625a4-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
