---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997586"
---
### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížky může zavěsit

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka může nastat během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:<ul><li>Definice řádků obsahují dva řádky, které jsou deklarovány jako MinHeight a MaxHeight.</li><li>Obsah řádků *-Rows nepřekračuje odpovídající MaxHeight.</li><li>Dostupná výška mřížky se překročí prvním MinHeight (a dalšími pevnými nebo automatickými řádky).</li><li>Cíle aplikace .NET Framework 4,7 nebo výslovný na algoritmus alokace 4,7 nastavením<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčka by také probíhala s více než dvěma řádky nebo v podobných případech pro sloupce. Problém je vyřešen .NET Framework 4.7.1.|
|Doporučení|Upgradujte na .NET Framework 4.7.1.  Případně, pokud nepotřebujete algoritmus přidělování 4,7, můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|type|Modul runtime|
