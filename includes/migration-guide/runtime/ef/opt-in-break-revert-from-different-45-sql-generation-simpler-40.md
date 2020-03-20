---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803164"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Opt-in break pro návrat z různých 4.5 SQL generace na jednodušší 4.0 SQL generace

|   |   |
|---|---|
|Podrobnosti|Dotazy, které vytvářejí příkazy JOIN a obsahují volání omezující operace bez předchozího použití OrderBy nyní vytvořit jednodušší SQL. Po upgradu na rozhraní .NET Framework 4.5 tyto dotazy vytvořily složitější SQL než předchozí verze.|
|Návrh|Tato funkce je ve výchozím nastavení zakázána. Pokud entity Framework generuje další příkazy JOIN, které způsobují snížení výkonu, <code>&lt;appSettings&gt;</code> můžete tuto funkci povolit přidáním následující položky do části souboru konfigurace aplikace (app.config):<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Průhlednost|
|Version|4.5.2|
|Typ|Modul runtime|
