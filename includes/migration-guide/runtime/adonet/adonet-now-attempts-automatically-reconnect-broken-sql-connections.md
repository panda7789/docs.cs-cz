---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619945"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="8e007-101">ADO.NET se teď pokusí automaticky znovu připojit k přerušeným připojením SQL.</span><span class="sxs-lookup"><span data-stu-id="8e007-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="8e007-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8e007-102">Details</span></span>

<span data-ttu-id="8e007-103">Počínaje .NET Framework 4.5.1 se .NET Framework pokusí automaticky znovu připojit přerušená připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="8e007-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="8e007-104">I když se tím obvykle aplikace spolehlivější, existují hraniční případy, ve kterých aplikace potřebuje znát, že připojení bylo ztraceno, aby mohlo při opětovném připojení provést nějakou akci.</span><span class="sxs-lookup"><span data-stu-id="8e007-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8e007-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="8e007-105">Suggestion</span></span>

<span data-ttu-id="8e007-106">Pokud je tato funkce nežádoucí kvůli problémům s kompatibilitou, může být zakázána nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> vlastnosti připojovacího řetězce (nebo <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> ) na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="8e007-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="8e007-107">Name</span><span class="sxs-lookup"><span data-stu-id="8e007-107">Name</span></span>    | <span data-ttu-id="8e007-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8e007-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8e007-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8e007-109">Scope</span></span>   |<span data-ttu-id="8e007-110">Edge</span><span class="sxs-lookup"><span data-stu-id="8e007-110">Edge</span></span>|
|<span data-ttu-id="8e007-111">Verze</span><span class="sxs-lookup"><span data-stu-id="8e007-111">Version</span></span>|<span data-ttu-id="8e007-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8e007-112">4.5.1</span></span>|
|<span data-ttu-id="8e007-113">Typ</span><span class="sxs-lookup"><span data-stu-id="8e007-113">Type</span></span>|<span data-ttu-id="8e007-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8e007-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8e007-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8e007-115">Affected APIs</span></span>

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
