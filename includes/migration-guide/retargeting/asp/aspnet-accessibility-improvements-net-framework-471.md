---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887749"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Vylepšení přístupnosti ASP.NET v .NET Framework 4.7.1

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.7.1, ASP.NET zlepšila, jak webové ovládací prvky ASP.NET pracují s technologiemi usnadnění v aplikaci Visual Studio, aby lépe podporovaly ASP.NET zákazníky.  Mezi ně patří tyto změny:<ul><li>Změny pro implementaci chybějících vzorů přístupnosti uživatelského rozhraní v ovládacích prvcích, jako je dialogové okno Přidat pole v průvodci zobrazení podrobností nebo dialogové okno Konfigurovat ListView Průvodce ListView.</li><li>Změny pro zlepšení zobrazení v režimu Vysoký kontrast, jako je například editor polí datového pageru.</li><li>Změny pro zlepšení prostředí navigace klávesnicí pro ovládací prvky, jako je dialogové okno pole v průvodci úpravou polí stránkování ovládacího prvku DataPager, dialogové okno Konfigurovat ObjectContext nebo dialogové okno Konfigurovat data Selction v Průvodci konfigurací zdroje dat.</li></ul>|
|Doporučení|**Jak vyjádřit nebo odhlásit tyto změny**<br>Aby mohl Návrhář sady Visual Studio těžit z těchto změn, musí běžet na .NET Framework 4.7.1 nebo novějším. Webová aplikace může tyto změny využít v jednom z následujících způsobů:<ul><li>Nainstalujte Visual Studio 2017 15,3 nebo novější, které ve výchozím nastavení podporují nové funkce usnadnění s následujícím přepínačem AppContext.</li><li>Odhlaste se se starším chováním přístupnosti, a to přidáním <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext do oddílu <code>&lt;runtime&gt;</code> v souboru devenv. exe. config a nastavením na <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikace, které cílí na .NET Framework 4.7.1 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na <code>true</code>.|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
