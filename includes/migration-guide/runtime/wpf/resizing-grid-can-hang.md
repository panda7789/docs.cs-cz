---
ms.openlocfilehash: 1e4c0ac1f0f9011f4b8fc136ec2e383d38567355
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83435405"
---
### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížky může zavěsit

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka může nastat během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:<ul><li>Definice řádků obsahují dva \* řádky, deklaruje MinHeight a MaxHeight.</li><li>Obsah \* řádků nepřekračuje odpovídající MaxHeight</li><li>Dostupná výška mřížky se překročí prvním MinHeight (a dalšími pevnými nebo automatickými řádky).</li><li>Cíle aplikace .NET Framework 4,7 nebo výslovný na algoritmus alokace 4,7 nastavením<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčka by také probíhala s více než dvěma řádky nebo v podobných případech pro sloupce. Problém je vyřešen .NET Framework 4.7.1.|
|Návrh|Upgradujte na .NET Framework 4.7.1.  Případně, pokud nepotřebujete algoritmus přidělování 4,7, můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Verze|4,7|
|Typ|Modul runtime|
