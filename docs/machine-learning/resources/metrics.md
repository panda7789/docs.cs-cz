---
title: ML.NET metriky
description: Pochopení metrik, které se používají k vyhodnocení výkonu ML.NET modelu
ms.date: 12/17/2019
author: natke
ms.author: nakersha
ms.openlocfilehash: b154c88281b65730c107a52034dfa40a45d4e367
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347756"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Vyhodnocení modelu ML.NET pomocí metrik

Pochopení metrik používané k vyhodnocení modelu ML.NET.

Metriky vyhodnocení jsou specifické pro typ úlohy strojového učení, kterou model provádí.

Například pro úlohu klasifikace je model vyhodnocován pomocí měření, jak dobře předpokládaná kategorie odpovídá aktuální kategorii. A pro clustering se hodnocení vychází z toho, jak se vzájemně dostanou clusterované položky, a kolik jich mezi clustery existuje.

## <a name="evaluation-metrics-for-binary-classification"></a>Metriky vyhodnocení pro binární klasifikaci

| Metriky   |      Popis      |  Vyhledejte |
|-----------|-----------------------|-----------|
| **Údajů** |  [Přesnost](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) je poměr správného předpovědi se sadou testů dat. Je to poměr počtu správných předpovědi k celkovému počtu vstupních vzorků. Funguje dobře, pokud existuje podobný počet vzorků patřících ke každé třídě.| **Nejblíže k 1,00, tím lépe**. Ale přesně 1,00 označuje problém (obvykle se jedná o netěsné úniky popisků, převzetí služeb při selhání nebo testování pomocí školicích dat). Pokud jsou testovací data nevyvážená (kde většina instancí patří do jedné z tříd), je datová sada malá nebo má skóre přístup 0,00 nebo 1,00, pak přesnost nezachycuje efektivitu klasifikátoru a potřebujete zkontrolovat další metriky. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) nebo *plocha pod křivkou* měří oblast pod křivkou, která je vytvořená vykreslením skutečné kladné míry a falešně pozitivních sazeb.  |   **Nejblíže k 1,00, tím lépe**. Měl by být větší než 0,50, aby bylo možné model akceptovat. Model s AUC 0,50 nebo méně je bezcenné. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) nebo *plocha pod křivkou křivky přesnosti odvolání*: užitečná míra úspěšnosti předpovědi, pokud jsou třídy nevyrovnané (vysoce zkreslené datové sady). |  **Nejblíže k 1,00, tím lépe**. Vysoká skóre blízko až 1,00 ukazují, že klasifikátor vrací přesné výsledky (vysoká přesnost) a vrací většinu všech pozitivních výsledků (vysoké odvolání). |
| **F1 – skóre** | [Skóre F1](https://en.wikipedia.org/wiki/F1_score) se také označuje jako *vyrovnané f-skore nebo f-Measure*. Je to harmonický význam přesnosti a odvolání. Skóre F1 je užitečné, pokud chcete vyhledat rovnováhu mezi přesností a odvoláním.| **Nejblíže k 1,00, tím lépe**.  Skóre F1 dosáhne své nejlepší hodnoty na 1,00 a nejhorší skóre v 0,00. Dozvíte se, jak přesně je třídění. |

Další podrobnosti o binárních metrikách klasifikace najdete v následujících článcích:

- [Přesnost, přesnost, odvolání nebo F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Třída binárních metrik klasifikace](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Vztah mezi přesností a odvoláním a ROC křivky](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Metriky vyhodnocení pro klasifikaci více tříd

| Metriky   |      Popis      |  Vyhledejte |
|-----------|-----------------------|-----------|
| **Mikropřesnost** |  [Střední hodnota přesnosti](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agreguje příspěvky všech tříd k výpočtu průměrné metriky. Jedná se o zlomek nesprávně vypředpokládaných instancí. Střední hodnota mikroprůměru nebere v úvahu členství třídy. V podstatě každá dvojice vzorových tříd přispívá stejně jako metrika přesnosti. | **Nejblíže k 1,00, tím lépe**. V rámci úlohy klasifikace s více třídami je mikropřesnost vhodnější než přesnost v makrech, pokud máte podezření, že může dojít k nerovnováze třídy (tj. je možné, že máte mnoho dalších příkladů jedné třídy než jiné třídy).|
| **Přesnost maker** | [Makro – Průměrná přesnost](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) je průměrná přesnost na úrovni třídy. Je vypočítána přesnost pro každou třídu a přesnost makra je průměrem z těchto přesností. V podstatě každá třída přispívá stejně jako metrika přesnosti. Minoritní třídy mají stejnou váhu jako větší třídy. Makro – Průměrná metrika poskytuje stejnou váhu jednotlivým třídám, bez ohledu na to, kolik instancí z této třídy datová sada obsahuje. |  **Nejblíže k 1,00, tím lépe**.  Počítá metriku nezávisle pro každou třídu a pak bere průměr (proto se všechny třídy zpracovávají stejně). |
| **Protokol – ztráta**| [Logaritmická ztráta](http://wiki.fast.ai/index.php/Log_Loss) měří výkon klasifikačního modelu, kde vstupní předpověď je pravděpodobnostní hodnota mezi 0,00 a 1,00. Ztráta protokolu se zvyšuje, protože předpokládaná pravděpodobnost se liší od skutečného popisku. | **Nejblíže k 0,00, tím lépe**. Dokonalý model by měl mít za následek ztrátu protokolu 0,00. Cílem našich modelů strojového učení je minimalizovat tuto hodnotu.|
| **Omezení ztrát protokolu** | [Snížení logaritmických ztrát](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) může být interpretováno jako výhoda klasifikátoru na náhodné předpovědi.| **Rozsahy od-inf a 1,00, kde 1,00 je perfektní předpovědi a 0,00 znamená střední předpovědi**. Například pokud se hodnota rovná 0,20, může být interpretována jako "pravděpodobnost správné předpovědi je 20% lepší než náhodné odhadování"|

Mikropřesnost je všeobecně lepší v souladu s podnikovými požadavky předpovědi ML. Pokud chcete vybrat jednu metriku pro výběr kvality úlohy klasifikace s více třídami, měla by obvykle být mikropřesnost.

Příklad pro úlohu klasifikace lístků podpory: (mapuje příchozí lístky na podporu týmů)

- Mikropřesnost – jak často se příchozí lístek klasifikuje do správného týmu?
- Přesnost makra – pro průměrnou tým, jak často je příchozí lístek správný pro svůj tým?

V tomto příkladu jsou předané malé týmy s přesností maker. malý tým, který získá jenom 10 lístků za rok, se počítá jako velký tým s 10 000 lístky za rok. Mikropřesnost v tomto případě je lépe koreluje s potřebnou firmou. "kolik času a peněz může společnost ukládat pomocí automatizace procesu směrování lístku".

Další podrobnosti o metrikách klasifikace s více třídami najdete v následujících článcích:

- [Mikroa makro – průměr přesnosti, odvolání a F-skore](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Klasifikace více tříd s nevyváženou datovou sadou](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Metriky vyhodnocení pro regresi a doporučení

Úkoly regrese i doporučení předpovídá číslo. V případě regrese může být číslo výstupní vlastností, která je ovlivněna vstupními vlastnostmi. Pro doporučení je číslo obvykle hodnota hodnocení (například mezi 1 a 5 příkladem) nebo doporučení ano/ne (reprezentované 1. a 0 v uvedeném pořadí).

| Metrika   |      Popis      |  Vyhledejte |
|----------|-----------------------|-----------|
| **R – čtvercový** |  [R-kvadrát (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)nebo *koeficienty stanovitelnosti* představují prediktivní sílu modelu jako hodnotu mezi-inf a 1,00. 1,00 znamená, že existuje dokonalé přizpůsobení a přizpůsobení může být libovolně špatné, takže skóre mohou být záporná. Skóre 0,00 znamená, že model odhaduje očekávanou hodnotu popisku. R2 měří způsob, jakým se hodnoty skutečných testovacích dat blíží předpokládaným hodnotám. | **Lepší kvalita je blíže k 1,00**. Někdy ale nízké hodnoty R-Square (například 0,50) můžou být pro váš scénář zcela normální nebo dostatečně dobré a vysoké hodnoty R-čtverce nejsou vždy dobré a jsou podezřelé. |
| **Absolutní ztráta** |  [Absolutní ztráta](https://en.wikipedia.org/wiki/Mean_absolute_error) nebo *střední absolutní chyba (Mae)* měří způsob, jakým se předpovědi blíží skutečným výsledkům. Jedná se o průměr všech chyb modelů, kde chyba modelu je absolutní vzdálenost mezi předpovězenou hodnotou popisku a správnou hodnotou popisku. Tato chyba předpovědi je vypočítána pro každý záznam sady dat testu. Nakonec se pro všechny zaznamenané absolutní chyby vypočítá střední hodnota.| **Lepší kvalita je blíže k 0,00.** Střední absolutní chyba používá stejné měřítko jako měřená data (není normalizována na konkrétní rozsah). Absolutní ztráta, čtvercová ztráta a ztráta RMS lze použít pouze k porovnání modelů pro stejnou datovou sadu nebo datovou sadu s podobnou distribucí hodnoty popisku. |
| **Kvadratická ztráta** |  [Čtvercová ztráta](https://en.wikipedia.org/wiki/Mean_squared_error) nebo *střední Chyba (MSE)* , označovaná také jako *střední odchylka (MSD)* , říká, jak blízko regresní čáry je sada hodnot testových dat, a to tak, že převezme vzdálenosti od bodů až po regresní čáru (tyto vzdálenosti jsou chyby E) a umocnění je. Umocnění poskytuje větší váhu většímu rozdílu. | Je vždycky nezáporné a **hodnoty blíž až 0,00 jsou lepší**. V závislosti na vašich datech nemusí být možné získat velmi malou hodnotu pro střední kvadratickou chybu.|
| **RMS – ztráta** |  Služba [RMS – ztráta](https://en.wikipedia.org/wiki/Root-mean-square_deviation) nebo *hlavní střední hodnota chyby (RMSE)* (označuje se také jako *Kořenová střední odchylka, RMSD*), měří rozdíl mezi hodnotami předpokládanými modelem a hodnotami zjištěnými z prostředí, které je právě modelováno. Služby RMS-ztráta je druhá odmocnina čtvercové ztráty a má stejné jednotky jako popisek, podobně jako u absolutní ztráty, a poskytuje větší váhu větším rozdílům. V climatology, předpovědi a regresní analýze se běžně používá chyba na kořenovém středním průměru k ověření experimentálních výsledků. | Je vždycky nezáporné a **hodnoty blíž až 0,00 jsou lepší**. RMSD je míra přesnosti, která umožňuje porovnat chyby prognózy různých modelů pro určitou datovou sadu a ne mezi datovými sadami, protože se jedná o závislé na škálování.|

Další podrobnosti o regresních metrikách najdete v následujících článcích:

- [Regresní analýza: Jak mohu interpretovat R-kvadrát a vyhodnotit dobré výsledky?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Jak interpretovat R-kvadrát v analýze regrese](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definice R-čtverce](https://www.investopedia.com/terms/r/r-squared.asp)
- [Střední hodnota čtverce v definici chyby](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Co znamená chyba na čtverci a hlavní střední hodnota chyby?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Metriky vyhodnocení pro clustering

| Metrika   |      Popis      |  Vyhledejte |
|----------|-----------------------|-----------|
|**Průměrná vzdálenost**|Průměr vzdálenosti mezi datovými body a centrem přiřazeného clusteru Průměrná vzdálenost je míra blízkosti datových bodů ke službě cluster centroids. Jedná se o míru, jak je cluster "těsný".|Hodnoty blíže k **0** jsou lepší. Hodnota bližší k nule znamená průměrnou vzdálenost, tím více je clusterovaných dat. Všimněte si ale, že tato metrika se po zvýšení počtu clusterů sníží a v extrémním případě (kde každá z různých datových bodů je vlastním clusterem) se rovná nule.
|**Davies Bouldin index**|Průměrný poměr vzdálenosti mezi clustery a vzdálenostmi mezi clustery. Čím užší je cluster a čím dál jsou clustery, tím nižší je hodnota.|Hodnoty blíže k **0** jsou lepší. Clustery, které jsou větší a méně rozptýlené, budou mít za následek lepší skóre.|
|**Normalizované vzájemné informace**|Dá se použít, když se školicí data, která se používají ke výuce modelu clusteringu, dodávají s popisky pravdy (tj. pod dohledem clusteringu). Normalizovaná metrika vzájemných informací měří, jestli se podobné datové body přiřazují ke stejnému clusteru a různorodé datové body se přiřazují k různým clusterům. Normalizované vzájemné informace jsou hodnoty mezi 0 a 1.|Hodnoty blížící se **1** jsou lepší.|

## <a name="evaluation-metrics-for-ranking"></a>Metriky vyhodnocení pro hodnocení

| Metrika   |      Popis      |  Vyhledejte |
|----------|-----------------------|-----------|
|**Zlevněné kumulativní zisky**|Zlevněný kumulativní zisk (DCG) je míra kvality hodnocení. Je odvozen ze dvou předpokladů. Jedna: vysoce relevantní položky jsou užitečnější, pokud se v pořadí podle pořadí seřazení zobrazuje výš. Dvě: užitečnost sleduje relevanci, to znamená větší relevanci, užitečnější položku. Zlevněný kumulativní zisk se počítá pro konkrétní pozici v pořadí řazení. Sečte stupeň relevance dělený logaritmem hodnocení podle pozice v zájmu. Počítá se pomocí $ \ sum_ {i = 0} ^ {p} \frac {rel_i} {\ log_ {e} {i + 1}} $ jsou k dispozici školicímu algoritmu řazení jako označení uzemněné pravdy. Jedna hodnota DCG je poskytována pro každou pozici v tabulce hodnocení, takže název se zlevněnými kumulativními **zisky**. |**Vyšší hodnoty jsou lepší**|
|**Normalizované zlevněné kumulativní zisky**|Normalizace DCG umožňuje porovnání metriky se seznamy řazení různých délek.|**Hodnoty blížící se 1 jsou lepší.**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Metriky vyhodnocení pro detekci anomálií

| Metrika   |      Popis      |  Vyhledejte |
|----------|-----------------------|-----------|
|**Plošný s křivkou ROC**|Oblast pod křivkou operátora přijímače měří, jak dobře model odděluje neobvyklé a běžné datové body.|**Hodnoty blížící se 1 jsou lepší**. Pouze hodnoty větší než 0,5 ukazují efektivitu modelu. Hodnoty 0,5 nebo nižší označují, že model není lepší než náhodné přidělování vstupů neobvyklé a obvyklým kategoriím.|
|**Rychlost detekce při nepravdivém kladném počtu**|Rychlost detekce při nepravdivém kladném počtu je poměr počtu správně identifikovaných anomálií na celkový počet anomálií v sadě testů indexovaných každou falešně pozitivním způsobem. To znamená, že pro každou falešně pozitivní položku existuje hodnota pro rychlost detekce v hodnotě falešně pozitivního počtu.|**Hodnoty blížící se 1 jsou lepší**. Pokud neexistují žádné falešně pozitivních hodnot, je tato hodnota 1.|
