---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620014"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="1d35c-101">Různé zpracování výjimek pro metody ObjectContext. CreateDatabase a DbProviderServices. CreateDatabase</span><span class="sxs-lookup"><span data-stu-id="1d35c-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="1d35c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1d35c-102">Details</span></span>

<span data-ttu-id="1d35c-103">Počínaje .NET Framework 4,5, pokud se vytvoření databáze nezdaří, <code>CreateDatabase</code> metody se pokusí odstranit prázdnou databázi.</span><span class="sxs-lookup"><span data-stu-id="1d35c-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="1d35c-104">Pokud je tato operace úspěšná, <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> bude rozšířena původní (místo toho <xref:System.InvalidOperationException?displayProperty=fullName> , který byl vždy vyvolán v .NET Framework 4,0).</span><span class="sxs-lookup"><span data-stu-id="1d35c-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1d35c-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="1d35c-105">Suggestion</span></span>

<span data-ttu-id="1d35c-106">Při zachycení <xref:System.InvalidOperationException?displayProperty=fullName> při spuštění <xref:System.Data.Objects.ObjectContext.CreateDatabase> nebo <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> SQLExceptions by nyní mělo být zachyceno také.</span><span class="sxs-lookup"><span data-stu-id="1d35c-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="1d35c-107">Name</span><span class="sxs-lookup"><span data-stu-id="1d35c-107">Name</span></span>    | <span data-ttu-id="1d35c-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1d35c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1d35c-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1d35c-109">Scope</span></span>   |<span data-ttu-id="1d35c-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="1d35c-110">Minor</span></span>|
|<span data-ttu-id="1d35c-111">Verze</span><span class="sxs-lookup"><span data-stu-id="1d35c-111">Version</span></span>|<span data-ttu-id="1d35c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1d35c-112">4.5</span></span>|
|<span data-ttu-id="1d35c-113">Typ</span><span class="sxs-lookup"><span data-stu-id="1d35c-113">Type</span></span>|<span data-ttu-id="1d35c-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1d35c-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1d35c-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1d35c-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
