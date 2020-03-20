---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859208"
---
### <a name="wpf-pointer-based-touch-stack"></a>Dotykový zásobník založený na ukazatelích WPF

|   |   |
|---|---|
|Podrobnosti|Tato změna přidá možnost povolit volitelné WM_POINTER založené WPF touch/stylus zásobníku.  Vývojáři, kteří to explicitně nepovolují, by měli vidět žádnou změnu v chování dotykového a stylusu WPF. Aktuální známé problémy S volitelným WM_POINTER založeného zásobníku dotykového stylu:<ul><li>Žádná podpora pro rukopis v reálném čase.</li><li>Zatímco rukopis a StylusPlugins bude i nadále fungovat, budou zpracovány na vlákno uživatelského rozhraní, což může vést ke špatnému výkonu.</li><li>Změny chování v důsledku změn v propagaci z touch/stylus událostí na události myši</li><li>Manipulace se může chovat jinak</li><li>Přetažení mne nezobrazí odpovídající zpětnou vazbu pro dotykové ovládání.</li><li>To nemá vliv na vstup pera</li><li>Přetažení již nelze spustit při událostech dotykového ovládání/pera</li><li>To může potenciálně zavěsit aplikaci, dokud není zjištěn vstup myši.</li><li>Místo toho by vývojáři měli zahájit přetahování z událostí myši.</li></ul>|
|Návrh|Vývojáři, kteří chtějí povolit tento zásobník, mohou do souboru App.config své aplikace přidat nebo sloučit následující:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Odebrání maže nebo nastavení hodnoty na hodnotu false vypne tento volitelný zásobník. Všimněte si, že tento zásobník je k dispozici pouze na Windows 10 Creators Update a výše.|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna cílení|
