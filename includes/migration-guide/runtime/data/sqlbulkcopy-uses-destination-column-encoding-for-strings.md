---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619999"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="3cab9-101">SqlBulkCopy používá pro řetězce kódování cílového sloupce.</span><span class="sxs-lookup"><span data-stu-id="3cab9-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="3cab9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3cab9-102">Details</span></span>

<span data-ttu-id="3cab9-103">Při vkládání dat do sloupce <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> používá místo výchozího kódování pro a typy kódování cílového sloupce <code>VARCHAR</code> <code>CHAR</code> .</span><span class="sxs-lookup"><span data-stu-id="3cab9-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="3cab9-104">Tato změna eliminuje možnost poškození dat při použití výchozího kódování, pokud cílový sloupec nepoužívá výchozí kódování.</span><span class="sxs-lookup"><span data-stu-id="3cab9-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="3cab9-105">Ve výjimečných případech může existující aplikace vyvolat výjimku SqlException, pokud změna kódování vytvoří data, která jsou příliš velká, aby se vešla do cílového sloupce.</span><span class="sxs-lookup"><span data-stu-id="3cab9-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3cab9-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="3cab9-106">Suggestion</span></span>

<span data-ttu-id="3cab9-107">V <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> důsledku rozdílů v kódování se očekává, že už nebudou poškozená data.</span><span class="sxs-lookup"><span data-stu-id="3cab9-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="3cab9-108">Pokud se zkopírují řetězce v blízkosti limitu velikosti cílového sloupce, může být nutné buď předem kódovat data (aby bylo možné ověřit, že se data vejdou do cílového sloupce), nebo zachytit <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> s.</span><span class="sxs-lookup"><span data-stu-id="3cab9-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="3cab9-109">Name</span><span class="sxs-lookup"><span data-stu-id="3cab9-109">Name</span></span>    | <span data-ttu-id="3cab9-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3cab9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3cab9-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3cab9-111">Scope</span></span>   |<span data-ttu-id="3cab9-112">Edge</span><span class="sxs-lookup"><span data-stu-id="3cab9-112">Edge</span></span>|
|<span data-ttu-id="3cab9-113">Verze</span><span class="sxs-lookup"><span data-stu-id="3cab9-113">Version</span></span>|<span data-ttu-id="3cab9-114">4.5</span><span class="sxs-lookup"><span data-stu-id="3cab9-114">4.5</span></span>|
|<span data-ttu-id="3cab9-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3cab9-115">Type</span></span>|<span data-ttu-id="3cab9-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3cab9-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3cab9-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3cab9-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
