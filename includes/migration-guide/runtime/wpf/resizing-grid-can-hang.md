---
ms.openlocfilehash: 86169b5c9a20678647153c951550e590a5bce588
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622236"
---
### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížky může zavěsit

#### <a name="details"></a>Podrobnosti

Nekonečná smyčka může nastat během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:<ul><li>Definice řádků obsahují dva \* řádky, deklaruje MinHeight a MaxHeight.</li><li>Obsah \* řádků nepřekračuje odpovídající MaxHeight</li><li>Dostupná výška mřížky se překročí prvním MinHeight (a dalšími pevnými nebo automatickými řádky).</li><li>Cíle aplikace .NET Framework 4,7 nebo výslovný na algoritmus alokace 4,7 nastavením<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčka by také probíhala s více než dvěma řádky nebo v podobných případech pro sloupce. Problém je vyřešen .NET Framework 4.7.1.

#### <a name="suggestion"></a>Návrh

Upgradujte na .NET Framework 4.7.1.  Případně, pokud nepotřebujete algoritmus přidělování 4,7, můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4,7|
|Typ|Modul runtime|
