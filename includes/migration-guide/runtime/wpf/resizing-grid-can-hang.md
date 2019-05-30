---
ms.openlocfilehash: 5df5afec17d400ed14fe9b4c03c2f754895f0dd7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378777"
---
### <a name="resizing-a-grid-can-cause-an-application-to-become-unresponsive"></a>Změně velikosti mřížky může způsobit, že aplikace přestane reagovat

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka se můžou objevit během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:<ul><li>Definice řádku obsahovat dva *-rows, obě deklarace MinHeight a MaxHeight.</li><li>Obsah *-řádků nepřekračuje odpovídající MaxHeight</li><li>K dispozici výška mřížky je překročena první MinHeight (a jakékoli jiné pevné nebo Auto řádků)</li><li>Aplikace cílí na .NET Framework 4.7 nebo vyjádřit výslovný souhlas pro algoritmus 4.7 přidělení nastavením <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčky by také mohlo dojít s více než dva řádky nebo v případě podobných pro sloupce. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7.1.  Případně není nutné algoritmus 4.7 přidělení můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|Type|Modul runtime|
