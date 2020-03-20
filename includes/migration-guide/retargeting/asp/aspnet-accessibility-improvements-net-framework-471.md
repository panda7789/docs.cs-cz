---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887749"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>ASP.NET zlepšení přístupnosti v rozhraní .NET Framework 4.7.1

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7.1 ASP.NET vylepšilo způsob práce ASP.NET webových ovládacích prvků s technologií usnadnění v sadě Visual Studio, aby byla lépe ASP.NET zákazníkům.  Patří mezi ně následující změny:<ul><li>Změny pro implementaci chybějících vzorů usnadnění přístupu k rozhraní v ovládacích prvcích, jako je dialogové okno Přidat pole v průvodci zobrazením podrobností nebo dialogové okno Konfigurovat zobrazení seznamu průvodce listview.</li><li>Změny pro zlepšení zobrazení v režimu vysokého kontrastu, například editor polí datových stránek.</li><li>Změny pro zlepšení prostředí navigace pomocí klávesnice pro ovládací prvky, například dialogové okno Pole v průvodci Upravit pole operátoru ovládacího prvku DataPager, dialogové okno Konfigurovat kontext objektu nebo dialogové okno Konfigurovat selction dat průvodcem Konfigurovat zdroj dat.</li></ul>|
|Návrh|**Jak se přihlásit nebo odhlásit z těchto změn**<br>Aby visual studio návrháře těžit z těchto změn, musí běžet v rozhraní .NET Framework 4.7.1 nebo novější. Webová aplikace může těžit z těchto změn v některé z následujících způsobů:<ul><li>Nainstalujte Visual Studio 2017 15.3 nebo novější, který podporuje nové funkce usnadnění s následující AppContext Switch ve výchozím nastavení.</li><li>Odhlásit se z chování starší <code>Switch.UseLegacyAccessibilityFeatures</code> usnadnění přidáním <code>&lt;runtime&gt;</code> AppContext přepínač do sekce v devenv.exe.config souboru a nastavení na <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější a chtějí zachovat starší chování usnadnění <code>true</code>přístupu, se mohou přihlásit k použití starších funkcí usnadnění explicitním nastavením tohoto přepínače AppContext na .|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
