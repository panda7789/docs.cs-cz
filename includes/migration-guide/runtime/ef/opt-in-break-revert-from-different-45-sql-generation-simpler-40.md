---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620017"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="1b7c9-101">Přerušení pro vrácení z různých generování SQL 4,5 na jednodušší 4,0 generování SQL</span><span class="sxs-lookup"><span data-stu-id="1b7c9-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="1b7c9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1b7c9-102">Details</span></span>

<span data-ttu-id="1b7c9-103">Dotazy, které tvoří příkazy spojení a obsahují volání omezující operace bez předchozího použití OrderBy nyní poskytují jednodušší SQL.</span><span class="sxs-lookup"><span data-stu-id="1b7c9-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="1b7c9-104">Po upgradu na verzi .NET Framework 4,5 tyto dotazy vytvořily složitější SQL než předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="1b7c9-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b7c9-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="1b7c9-105">Suggestion</span></span>

<span data-ttu-id="1b7c9-106">Tato funkce je ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="1b7c9-106">This feature is disabled by default.</span></span> <span data-ttu-id="1b7c9-107">Pokud Entity Framework generuje nadbytečné příkazy spojení, které způsobují snížení výkonu, můžete tuto funkci povolit přidáním následujícího záznamu do <code>&lt;appSettings&gt;</code> oddílu konfiguračního souboru aplikace (app.config):</span><span class="sxs-lookup"><span data-stu-id="1b7c9-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1b7c9-108">Name</span><span class="sxs-lookup"><span data-stu-id="1b7c9-108">Name</span></span>    | <span data-ttu-id="1b7c9-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1b7c9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b7c9-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1b7c9-110">Scope</span></span>   |<span data-ttu-id="1b7c9-111">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="1b7c9-111">Transparent</span></span>|
|<span data-ttu-id="1b7c9-112">Verze</span><span class="sxs-lookup"><span data-stu-id="1b7c9-112">Version</span></span>|<span data-ttu-id="1b7c9-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1b7c9-113">4.5.2</span></span>|
|<span data-ttu-id="1b7c9-114">Typ</span><span class="sxs-lookup"><span data-stu-id="1b7c9-114">Type</span></span>|<span data-ttu-id="1b7c9-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1b7c9-115">Runtime</span></span>|
