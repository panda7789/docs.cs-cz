---
ms.openlocfilehash: 2e870b8d7b8ed986863632f947223946a6604f89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802502"
---
### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížky může přestat reagovat

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka se můžou objevit během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:<ul><li>Definice řádku obsahovat dva *-rows, obě deklarace MinHeight a MaxHeight.</li><li>Obsah *-řádků nepřekračuje odpovídající MaxHeight</li><li>K dispozici výška mřížky je překročena první MinHeight (a jakékoli jiné pevné nebo Auto řádků)</li><li>Aplikace cílí na .NET Framework 4.7 nebo vyjádřit výslovný souhlas pro algoritmus 4.7 přidělení nastavením <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčky by také mohlo dojít s více než dva řádky nebo v případě podobných pro sloupce. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7.1.  Případně není nutné algoritmus 4.7 přidělení můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|type|Modul runtime|

