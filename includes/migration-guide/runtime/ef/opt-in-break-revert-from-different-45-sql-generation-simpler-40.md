---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803164"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="fe9c0-101">Opt-in break pro návrat z různých 4.5 SQL generace na jednodušší 4.0 SQL generace</span><span class="sxs-lookup"><span data-stu-id="fe9c0-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fe9c0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fe9c0-102">Details</span></span>|<span data-ttu-id="fe9c0-103">Dotazy, které vytvářejí příkazy JOIN a obsahují volání omezující operace bez předchozího použití OrderBy nyní vytvořit jednodušší SQL.</span><span class="sxs-lookup"><span data-stu-id="fe9c0-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="fe9c0-104">Po upgradu na rozhraní .NET Framework 4.5 tyto dotazy vytvořily složitější SQL než předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="fe9c0-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="fe9c0-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="fe9c0-105">Suggestion</span></span>|<span data-ttu-id="fe9c0-106">Tato funkce je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="fe9c0-106">This feature is disabled by default.</span></span> <span data-ttu-id="fe9c0-107">Pokud entity Framework generuje další příkazy JOIN, které způsobují snížení výkonu, <code>&lt;appSettings&gt;</code> můžete tuto funkci povolit přidáním následující položky do části souboru konfigurace aplikace (app.config):</span><span class="sxs-lookup"><span data-stu-id="fe9c0-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="fe9c0-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="fe9c0-108">Scope</span></span>|<span data-ttu-id="fe9c0-109">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="fe9c0-109">Transparent</span></span>|
|<span data-ttu-id="fe9c0-110">Version</span><span class="sxs-lookup"><span data-stu-id="fe9c0-110">Version</span></span>|<span data-ttu-id="fe9c0-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="fe9c0-111">4.5.2</span></span>|
|<span data-ttu-id="fe9c0-112">Typ</span><span class="sxs-lookup"><span data-stu-id="fe9c0-112">Type</span></span>|<span data-ttu-id="fe9c0-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="fe9c0-113">Runtime</span></span>|
