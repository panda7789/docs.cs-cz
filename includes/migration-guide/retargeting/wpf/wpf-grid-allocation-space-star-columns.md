---
ms.openlocfilehash: 3709b9e694011666cebcb0ae09fbc838f65967af
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614562"
---
### <a name="wpf-grid-allocation-of-space-to-star-columns"></a>Přidělování prostoru v mřížce WPF do hvězdiček – sloupce

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,7, WPF nahradí algoritmus, který <xref:System.Windows.Controls.Grid> používá k přidělení prostoru pro \* sloupce. Tato akce změní skutečnou šířku přiřazenou ke \* sloupcům v několika případech:

- Pokud má jeden nebo více \* sloupců také minimální nebo maximální šířku, která přepíše proporcionální přidělení pro tento slo. (Minimální šířka se může odvozovat z explicitní deklarace MinWidth nebo z implicitního minima získaného z obsahu sloupce. Maximální šířku lze definovat pouze explicitně z deklarace MaxWidth.)
- Pokud jeden nebo více \* sloupců deklaruje extrémně velkou \* váhu, větší než 10 ^ 298.
- Pokud \* jsou závaží dostatečně odlišná, aby narazila na nestabilitu plovoucí desetinné čárky (přetečení, podtečení, ztráta přesnosti).
- Když je povoleno zaoblení rozložení a efektivní zobrazení DPI je dostatečně vysoké.
V prvních dvou případech může být šířka vytvořená novým algoritmem výrazně odlišná od těch, které vytvořil starý algoritmus. v posledním případě bude rozdíl maximálně jeden nebo dva pixely.<p/>Nový algoritmus opravuje několik chyb ve starém algoritmu:

- Celkový počet přidělení na sloupce může překročit šířku mřížky. K tomu může dojít při přidělování prostoru do sloupce, jehož proporcionální podíl je menší než minimální velikost. Algoritmus přiděluje minimální velikost, která snižuje místo dostupného pro ostatní sloupce. Pokud neexistují žádné \* sloupce, které by bylo možné přidělit, celkový počet přidělení bude příliš velký.
- Celkový počet přidělení může být nižší než šířka mřížky. Jedná se o duální problém, který je #1, což znamená při přidělování do sloupce, jehož proporcionální podíl je větší než jeho maximální velikost, takže \* nezbývá, aby se zabrala časová rezerva.
- Dva \* sloupce můžou získat přidělení neúměrné jejich \* závaží. Toto je mírná verze #1/#2, která vzniká při přidělování na \* sloupce a, B a C (v tomto pořadí), kde hodnota b poměrná sdílená položka je v rozporu s omezením (nebo max). Jak je uvedeno výše, mění se místo dostupné pro sloupec C, který získá méně (nebo více) proporční přidělování, než bylo provedeno,
- Sloupce s extrémně velkým závažím ( &gt; 10 ^ 298) se považují za, jako kdyby měly 10 ^ 298. Poměrná rozdíl mezi nimi (a mezi sloupci s mírně menším závažím) nejsou dodrženy.
- Sloupce s tloušťkou inifinte se nezpracovávají správně. [Ve skutečnosti nemůžete nastavit váhu na nekonečno, ale toto je umělé omezení. Alokační kód se snažil ho zpracovat, ale provádí špatnou úlohu.]
- Několik menších problémů při předcházení přetečení, podtečení, ztráty přesnosti a podobné problémy s plovoucí desetinnou čárkou.
- Úpravy pro zaokrouhlování rozložení jsou nesprávné při dostatečně vysokém rozlišení DPI.
Nový algoritmus vytvoří výsledky, které splňují následující kritéria:<p/>A. Skutečná šířka přiřazená ke sloupci * není nikdy menší než minimální šířka ani větší než maximální šířka.<br/>B. Každému <em>sloupci, který nemá přiřazenou minimální nebo maximální šířku, je přiřazena šířka přiměřená na <em>váhu. V případě, že jsou dva sloupce deklarovány s šířkou x</em> a y</em> a pokud žádný ze sloupců neobdrží minimální nebo maximální šířku, mají skutečné šířky v a w přiřazené sloupce ve stejném poměru: v/w = = x/y.<br/>C. Celková šířka přidělená pro &quot; proporcionální &quot; \* sloupce se rovná volnému prostoru, který je k dispozici po přidělení na sloupce s omezením (pevné, automatické a \* -sloupce, které mají přidělenu minimální nebo maximální šířku). Tato hodnota může být nulová, například pokud součet minimálních šířek překračuje šířku availbable mřížky.<br/>D. Všechny tyto příkazy jsou interpretovány s ohledem na &quot; ideální &quot; rozložení. Když je navýšení rozložení platné, skutečné šířky se mohou lišit od ideální šířky až do velikosti jednoho pixelu.<br/>Starý algoritmus dodržoval (A), ale nedokázal přijmout další kritéria v případech uvedených výše.<p/>Vše uvedené o sloupcích a šířkách v tomto článku se vztahuje i na řádky a výšky.

#### <a name="suggestion"></a>Návrh

Ve výchozím nastavení se v aplikacích, které cílí na verze .NET Framework od .NET Framework 4,7, zobrazí nový algoritmus, zatímco aplikace cílené na .NET Framework 4.6.2 nebo starší verze uvidí starý algoritmus.<p/>Pokud chcete přepsat výchozí nastavení, použijte následující nastavení konfigurace:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Hodnota `true` vybere starý algoritmus a `false` vybere nový algoritmus.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,7         |
| Typ    | Změna cílení |
