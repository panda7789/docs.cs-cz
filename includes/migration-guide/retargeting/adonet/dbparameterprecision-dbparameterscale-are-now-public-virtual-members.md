---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088470"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="e947d-101">DbParameter.Precision a DbParameter.Scale jsou teď virtuální veřejné členy</span><span class="sxs-lookup"><span data-stu-id="e947d-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e947d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e947d-102">Details</span></span>|<span data-ttu-id="e947d-103"><xref:System.Data.Common.DbParameter.Precision> a <xref:System.Data.Common.DbParameter.Scale> jsou implementovány jako virtuální veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e947d-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="e947d-104">Nahrazují odpovídající implementace explicitního rozhraní <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> a <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span><span class="sxs-lookup"><span data-stu-id="e947d-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>|
|<span data-ttu-id="e947d-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e947d-105">Suggestion</span></span>|<span data-ttu-id="e947d-106">Při opětovné sestavování databáze poskytovatele ADO.NET, bude vyžadovat tyto rozdíly – klíčové slovo 'override' má použít u vlastnosti hodnot Precision a Scale.</span><span class="sxs-lookup"><span data-stu-id="e947d-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="e947d-107">To je jenom nutné, když znovu sestavení součástí; existující binární soubory budou nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="e947d-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>|
|<span data-ttu-id="e947d-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e947d-108">Scope</span></span>|<span data-ttu-id="e947d-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e947d-109">Minor</span></span>|
|<span data-ttu-id="e947d-110">Version</span><span class="sxs-lookup"><span data-stu-id="e947d-110">Version</span></span>|<span data-ttu-id="e947d-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e947d-111">4.5.1</span></span>|
|<span data-ttu-id="e947d-112">Type</span><span class="sxs-lookup"><span data-stu-id="e947d-112">Type</span></span>|<span data-ttu-id="e947d-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e947d-113">Retargeting</span></span>|
|<span data-ttu-id="e947d-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e947d-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
