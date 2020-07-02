---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620017"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Přerušení pro vrácení z různých generování SQL 4,5 na jednodušší 4,0 generování SQL

#### <a name="details"></a>Podrobnosti

Dotazy, které tvoří příkazy spojení a obsahují volání omezující operace bez předchozího použití OrderBy nyní poskytují jednodušší SQL. Po upgradu na verzi .NET Framework 4,5 tyto dotazy vytvořily složitější SQL než předchozí verze.

#### <a name="suggestion"></a>Návrh

Tato funkce je ve výchozím nastavení zakázaná. Pokud Entity Framework generuje nadbytečné příkazy spojení, které způsobují snížení výkonu, můžete tuto funkci povolit přidáním následujícího záznamu do <code>&lt;appSettings&gt;</code> oddílu konfiguračního souboru aplikace (app.config):<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Průhlednost|
|Verze|4.5.2|
|Typ|Modul runtime|
