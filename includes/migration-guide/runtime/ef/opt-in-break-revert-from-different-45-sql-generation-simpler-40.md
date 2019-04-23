---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774251"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="40bf7-101">Konec vyjádřit výslovný souhlas se vrátit z různých 4.5 generování SQL pro jednodušší 4.0 generování SQL</span><span class="sxs-lookup"><span data-stu-id="40bf7-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="40bf7-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="40bf7-102">Details</span></span>|<span data-ttu-id="40bf7-103">Dotazy, které vytvářejí Příkazy JOIN a obsahovat volání limitující operace, aniž byste nejdřív pomocí OrderBy nyní vytvořit jednodušší SQL.</span><span class="sxs-lookup"><span data-stu-id="40bf7-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="40bf7-104">Po upgradu na rozhraní .NET Framework 4.5, vytváří tyto dotazy SQL složitější než předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="40bf7-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="40bf7-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="40bf7-105">Suggestion</span></span>|<span data-ttu-id="40bf7-106">Tato funkce je ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="40bf7-106">This feature is disabled by default.</span></span> <span data-ttu-id="40bf7-107">Pokud rozhraní Entity Framework generuje dodatečné příkazy JOIN, které způsobují snížení výkonu, můžete tuto funkci povolíte tak, že přidáte následující položky <code>&lt;appSettings&gt;</code> souboru konfigurace (app.config) aplikace:</span><span class="sxs-lookup"><span data-stu-id="40bf7-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="40bf7-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="40bf7-108">Scope</span></span>|<span data-ttu-id="40bf7-109">Transparentní</span><span class="sxs-lookup"><span data-stu-id="40bf7-109">Transparent</span></span>|
|<span data-ttu-id="40bf7-110">Version</span><span class="sxs-lookup"><span data-stu-id="40bf7-110">Version</span></span>|<span data-ttu-id="40bf7-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="40bf7-111">4.5.2</span></span>|
|<span data-ttu-id="40bf7-112">Type</span><span class="sxs-lookup"><span data-stu-id="40bf7-112">Type</span></span>|<span data-ttu-id="40bf7-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="40bf7-113">Runtime</span></span>|
