---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997586"
---
### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížky může zavěsit

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka může dojít <code>T:System.Windows.Controls.Grid</code> při rozvržení za následujících okolností:<ul><li>Definice řádků obsahují dva *-řádky, oba deklaruje MinHeight a MaxHeight.</li><li>Obsah *-řádků nepřesahuje odpovídající MaxHeight</li><li>Dostupná výška mřížky je překročena prvním MinHeightem (plus všechny ostatní pevné nebo automatické řádky)</li><li>Aplikace cílí na rozhraní .NET Framework 4.7 nebo se přihlásí k algoritmu přidělení 4.7 nastavením<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčka by také dojít s více než dva řádky, nebo v podobném případě pro sloupce. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Návrh|Upgrade na rozhraní .NET Framework 4.7.1.  Případně, pokud nepotřebujete algoritmus přidělení 4.7, můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Modul runtime|
