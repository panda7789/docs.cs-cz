---
ms.openlocfilehash: 63101fb127c84de21d165994bba85a2753e97344
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236590"
---
### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížky může přestat reagovat

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka se můžou objevit během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:<ul><li>Definice řádku obsahovat dva *-rows, obě deklarace MinHeight a MaxHeight.</li><li>Obsah *-řádků nepřekračuje odpovídající MaxHeight</li><li>K dispozici výška mřížky je překročena první MinHeight (a jakékoli jiné pevné nebo Auto řádků)</li><li>Aplikace cílí na .NET Framework 4.7 nebo vyjádřit výslovný souhlas pro algoritmus 4.7 přidělení nastavením <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčky by také mohlo dojít s více než dva řádky nebo v případě podobných pro sloupce. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7.1.  Případně není nutné algoritmus 4.7 přidělení můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Type|Modul runtime|
