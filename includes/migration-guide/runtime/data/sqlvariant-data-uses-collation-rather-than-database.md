---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620005"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="3c7df-101">Sql_variant dat používá místo řazení databáze sql_variant kolaci.</span><span class="sxs-lookup"><span data-stu-id="3c7df-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="3c7df-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3c7df-102">Details</span></span>

<span data-ttu-id="3c7df-103"><code>sql_variant</code>data používají <code>sql_variant</code> řazení místo řazení databáze.</span><span class="sxs-lookup"><span data-stu-id="3c7df-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3c7df-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="3c7df-104">Suggestion</span></span>

<span data-ttu-id="3c7df-105">Tato změna řeší možné poškození dat, pokud se řazení databáze liší od <code>sql_variant</code> řazení.</span><span class="sxs-lookup"><span data-stu-id="3c7df-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="3c7df-106">Aplikace využívající poškozená data mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="3c7df-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="3c7df-107">Name</span><span class="sxs-lookup"><span data-stu-id="3c7df-107">Name</span></span>    | <span data-ttu-id="3c7df-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c7df-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3c7df-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3c7df-109">Scope</span></span>   |<span data-ttu-id="3c7df-110">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="3c7df-110">Transparent</span></span>|
|<span data-ttu-id="3c7df-111">Verze</span><span class="sxs-lookup"><span data-stu-id="3c7df-111">Version</span></span>|<span data-ttu-id="3c7df-112">4.5</span><span class="sxs-lookup"><span data-stu-id="3c7df-112">4.5</span></span>|
|<span data-ttu-id="3c7df-113">Typ</span><span class="sxs-lookup"><span data-stu-id="3c7df-113">Type</span></span>|<span data-ttu-id="3c7df-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3c7df-114">Runtime</span></span>|
