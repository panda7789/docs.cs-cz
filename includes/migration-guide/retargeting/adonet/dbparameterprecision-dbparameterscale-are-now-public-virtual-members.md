---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616046"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="5dfdd-101">DbParameter. Precision a DbParameter. Scale jsou teď veřejné virtuální členy.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="5dfdd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5dfdd-102">Details</span></span>

<span data-ttu-id="5dfdd-103"><xref:System.Data.Common.DbParameter.Precision>a <xref:System.Data.Common.DbParameter.Scale> jsou implementovány jako veřejné virtuální vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="5dfdd-104">Nahrazují odpovídající explicitní implementace rozhraní <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> a <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale> .</span><span class="sxs-lookup"><span data-stu-id="5dfdd-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5dfdd-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="5dfdd-105">Suggestion</span></span>

<span data-ttu-id="5dfdd-106">Při opětovném sestavování poskytovatele databáze ADO.NET budou tyto rozdíly vyžadovat, aby klíčové slovo override bylo použito pro vlastnosti Precision a Scale.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="5dfdd-107">To je nutné pouze při opětovném sestavování komponent. existující binární soubory budou fungovat i nadále.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="5dfdd-108">Name</span><span class="sxs-lookup"><span data-stu-id="5dfdd-108">Name</span></span>    | <span data-ttu-id="5dfdd-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5dfdd-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5dfdd-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5dfdd-110">Scope</span></span>   | <span data-ttu-id="5dfdd-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="5dfdd-111">Minor</span></span>       |
| <span data-ttu-id="5dfdd-112">Verze</span><span class="sxs-lookup"><span data-stu-id="5dfdd-112">Version</span></span> | <span data-ttu-id="5dfdd-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5dfdd-113">4.5.1</span></span>       |
| <span data-ttu-id="5dfdd-114">Typ</span><span class="sxs-lookup"><span data-stu-id="5dfdd-114">Type</span></span>    | <span data-ttu-id="5dfdd-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="5dfdd-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5dfdd-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5dfdd-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
