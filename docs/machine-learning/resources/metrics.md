---
title: ML.NET metriky
description: Pochopit metriky, které se používají k vyhodnocení výkonu ML.NET modelu
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399215"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Vyhodnoťte svůj ML.NET model pomocí metrik

Seznamte se s metrikami použitými k vyhodnocení ML.NET modelu.

Metriky hodnocení jsou specifické pro typ úlohy strojového učení, kterou model provádí.

Například pro úkol klasifikace je model vyhodnocen měřením, jak dobře předpovídaná kategorie odpovídá skutečné kategorii. A pro clustering hodnocení je založena na tom, jak blízko clusterované položky jsou k sobě navzájem a kolik oddělení je mezi clustery.

## <a name="evaluation-metrics-for-binary-classification"></a>Hodnotící metriky pro binární klasifikaci

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **Přesnost** |  [Přesnost](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) je podíl správných předpovědí se sadou testovacích dat. Jedná se o poměr počtu správných předpovědí k celkovému počtu vstupních vzorků. Funguje dobře, pokud existuje podobný počet vzorků, které patří do každé třídy.| **Čím blíže k 1,00, tím lépe**. Ale přesně 1,00 označuje problém (obvykle: label/target leakleak, over-fitting nebo testing with training data). Pokud jsou testovací data nevyvážená (kde většina instancí patří do jedné z tříd), datová sada je malá nebo skóre přístup 0,00 nebo 1,00, pak přesnost není ve skutečnosti zachytit účinnost třídění a je třeba zkontrolovat další metriky. |
| **Auc** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) nebo *Oblast pod křivkou* měří plochu pod křivkou vytvořenou zametáním skutečné kladné míry vs. falešně pozitivní rychlost.  |   **Čím blíže k 1,00, tím lépe**. Pro přijatelný by měl být model větší než 0,50. Model s AUC 0,50 nebo méně je bezcenný. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) nebo *oblast pod křivkou precision-recall křivky*: Užitečné měřítko úspěšnosti predikce, když jsou třídy nevyvážené (vysoce zkosené datové sady). |  **Čím blíže k 1,00, tím lépe**. Vysoké skóre téměř 1,00 ukazují, že třídění vrací přesné výsledky (vysoká přesnost), stejně jako vrácení většiny všech pozitivních výsledků (vysoké odvolání). |
| **F1-skóre** | [F1 skóre](https://en.wikipedia.org/wiki/F1_score) také známé jako *vyvážené F-skóre nebo F-míra*. Je to harmonický průměr přesnosti a odvolání. F1 Skóre je užitečné, pokud chcete najít rovnováhu mezi Precision a Recall.| **Čím blíže k 1,00, tím lépe**.  Skóre F1 dosahuje své nejlepší hodnoty na 1,00 a nejhorší skóre na 0,00. To vám řekne, jak přesné je váš třídění. |

Další podrobnosti o binárníklasifikaci metriky přečtěte si následující články:

- [Přesnost, přesnost, odvolání nebo F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Binární klasifikace Metriky třídy](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Vztah mezi křivkami precision-recall a ROC](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Hodnotící metriky pro klasifikaci více tříd

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **Mikropřesnost** |  [Mikroprůměrná přesnost](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agreguje příspěvky všech tříd pro výpočet průměrné metriky. Jedná se o zlomek správně předpovídaných instancí. Mikro-průměr nebere v úvahu členství ve třídě. V podstatě každý pár třídy vzorku přispívá stejně k metrike přesnosti. | **Čím blíže k 1,00, tím lépe**. Při vícestupňové klasifikaci je mikropřesnost vhodnější než makropřesnost, pokud máte podezření, že může existovat nerovnováha třídy (tj. můžete mít mnohem více příkladů jedné třídy než jiných tříd).|
| **Makropřesnost** | [Makroprůměrná přesnost](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) je průměrná přesnost na úrovni třídy. Přesnost pro každou třídu je vypočítána a přesnost maker je průměr těchto přesností. V podstatě každá třída přispívá stejně k metrike přesnosti. Menšinové třídy mají stejnou váhu jako větší třídy. Makroprůměrná metrika poskytuje stejnou váhu každé třídě bez ohledu na to, kolik instancí z této třídy datová sada obsahuje. |  **Čím blíže k 1,00, tím lépe**.  Vypočítá metriku nezávisle pro každou třídu a pak vezme průměr (tedy zacházet se všemi třídami stejně) |
| **Ztráta protokolu**| [Logaritmická ztráta](http://wiki.fast.ai/index.php/Log_Loss) měří výkon klasifikačního modelu, kde vstup předpovědi je hodnota pravděpodobnosti mezi 0,00 a 1,00. Ztráta protokolu se zvyšuje, protože předpokládaná pravděpodobnost se liší od skutečného popisku. | **Čím blíže k 0,00, tím lépe**. Perfektní model by měl log-loss 0,00. Cílem našich modelů strojového učení je minimalizovat tuto hodnotu.|
| **Snížení ztráty protokolu** | [Logaritmické snížení ztráty](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) lze interpretovat jako výhodu třídění přes náhodné předpověď.| **V rozsahu od -inf a 1,00, kde 1,00 je perfektní předpovědi a 0,00 označuje střední předpovědi**. Například pokud se hodnota rovná 0,20, může být interpretována jako "pravděpodobnost správné předpovědi je o 20 % lepší než náhodné odhadování"|

Mikropřesnost je obecně lépe v souladu s obchodními potřebami předpovědí ML. Pokud chcete vybrat jednu metriku pro výběr kvality úlohy klasifikace více tříd, měla by být obvykle mikropřesnost.

Příklad pro úkol klasifikace lístků podpory: (mapuje příchozí vstupenky podpůrným týmům)

- Mikropřesnost - jak často se příchozí jízdenka dostane do správného týmu?
- Makro-přesnost - pro průměrný tým, jak často je příchozí lístek správný pro jejich tým?

Makropřesnost má v tomto příkladu nadváhu malých týmů. malý tým, který dostane pouze 10 vstupenek ročně se počítá stejně jako velký tým s 10k vstupenky za rok. Mikro-přesnost v tomto případě koreluje lépe s obchodní potřebou, "kolik času / peněz může společnost ušetřit automatizací mého procesu směrování vstupenek".

Další podrobnosti o metrikách klasifikace více tříd načtou následující články:

- [Mikroprůměr přesnosti, odvolání a f-skóre](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Klasifikace více tříd s nevyváženou datovou sadou](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Hodnotící metriky pro regresi a doporučení

Regrese a doporučení úkoly předpovědět číslo. V případě regrese může být číslo libovolnou výstupní vlastností, která je ovlivněna vstupními vlastnostmi. Pro doporučení je číslo obvykle hodnota hodnocení (například mezi 1 a 5) nebo doporučení ano/ne (reprezentované 1 a 0).

| Metrika   |      Popis      |  Hledat |
|----------|-----------------------|-----------|
| **R-na druhou** |  [R-kvadrát (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)nebo *koeficient stanovení* představuje prediktivní sílu modelu jako hodnotu mezi -inf a 1,00. 1.00 znamená, že je perfektní fit, a fit může být libovolně špatná, takže skóre může být negativní. Skóre 0,00 znamená, že model je hádat očekávanou hodnotu pro popisek. R2 měří, jak blízko jsou hodnoty skutečných testovacích dat předpovídaným hodnotám. | **Čím blíže k 1,00, tím lepší kvalita**. Někdy však nízké hodnoty na druhou R (například 0,50) může být zcela normální nebo dost dobré pro váš scénář a vysoké hodnoty na druhou R nejsou vždy dobré a podezřelé. |
| **Absolutní ztráta** |  [Absolutní ztráta](https://en.wikipedia.org/wiki/Mean_absolute_error) nebo *střední absolutní chyba (MAE)* měří, jak blízko jsou předpovědi ke skutečným výsledkům. Jedná se o průměr všech chyb modelu, kde chyba modelu je absolutní vzdálenost mezi předpokládanou hodnotou popisku a správnou hodnotou popisku. Tato chyba předpověď se vypočítá pro každý záznam testovací datové sady. Nakonec se vypočítá střední hodnota pro všechny zaznamenané absolutní chyby.| **Čím blíže k 0,00, tím lepší kvalitu.** Průměrná absolutní chyba používá stejné měřítko jako měřená data (není normalizována na konkrétní rozsah). Absolutní ztráta, kvadrátální ztráta a ztráta RMS lze použít pouze k porovnání mezi modely pro stejnou datovou sadu nebo datovou sadu s podobným rozložením hodnoty popisku. |
| **Kvadrač-ztráta** |  [Kvadratická nebo](https://en.wikipedia.org/wiki/Mean_squared_error) *střední kvadratická chyba (MSE)*, také nazývaná *střední kvadratická odchylka (MSD),* vám řekne, jak blízko je regresní čára k sadě hodnot testovacích dat tím, že vezme vzdálenosti od bodů k regresní čáře (tyto vzdálenosti jsou chyby E) a kvadraturu je. Kvadratura dává větší váhu větším rozdílům. | Je vždy nezáporná a **hodnoty blíže k 0,00 jsou lepší**. V závislosti na vašich datech může být nemožné získat velmi malou hodnotu pro střední kvadratorovou chybu.|
| **RMS-ztráta** |  [RMS-loss](https://en.wikipedia.org/wiki/Root-mean-square_deviation) nebo *Root Mean SquareD Error (RMSE)* (také nazývaný *Kořenová střední kvadratická odchylka, RMSD*), měří rozdíl mezi hodnotami předpovězenými modelem a hodnotami pozorovanými z prostředí, které je modelováno. RMS-ztráta je druhá odmocnina squared-ztráta a má stejné jednotky jako štítek, podobně jako absolutní-ztráta i když dává větší váhu větší rozdíly. Střední kvadratická chyba kořene se běžně používá v klimatologii, prognózách a regresní analýze k ověření experimentálních výsledků. | Je vždy nezáporná a **hodnoty blíže k 0,00 jsou lepší**. RMSD je míra přesnosti, porovnat chyby prognózy různých modelů pro konkrétní datové sady a nikoli mezi datovými sadami, protože je závislé na měřítku.|

Další podrobnosti o regresní metriky, přečtěte si následující články:

- [Regresní analýza: Jak interpretuji R-kvadratou a posoudit dobrotu fit?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Jak interpretovat R-kvadratý v regresní analýze](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R-kvadrát definice](https://www.investopedia.com/terms/r/r-squared.asp)
- [Definice střední kvadraté chyby](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Co jsou střední kvadratří chyba a střední kvadratická chyba kořenového adresáře?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Metriky hodnocení clusteringu

| Metrika   |      Popis      |  Hledat |
|----------|-----------------------|-----------|
|**Průměrná vzdálenost**|Průměr vzdálenosti mezi datovými body a středem přiřazeného clusteru. Průměrná vzdálenost je mírou blízkosti datových bodů k centroidům clusteru. Je to míra toho, jak 'těsný' cluster je.|Hodnoty blíže k **0** jsou lepší. Čím blíže k nule je průměrná vzdálenost, tím více seskupených dat je. Všimněte si však, že tato metrika se sníží, pokud se zvýší počet clusterů a v extrémním případě (kde každý odlišný datový bod je vlastní cluster) se bude rovnat nule.
|**Davies Bouldin Index**|Průměrný poměr vzdáleností v rámci clusteru k mezikupami. Čím těsnější cluster u ta je, tím nižší je tato hodnota.|Hodnoty blíže k **0** jsou lepší. Clustery, které jsou dále od sebe a méně rozptýlené bude mít za následek lepší skóre.|
|**Normalizované vzájemné informace**|Lze použít, když trénovací data použitá k trénování modelu clusteringu také přichází s popisky pravdy země (to znamená, že pod dohledem clustering). Metrika Normalizované vzájemné informace měří, zda se podobné datové body přiřadí ke stejnému clusteru a nesourodé datové body se přiřadí do různých clusterů. Normalizované vzájemné informace je hodnota mezi 0 a 1|Hodnoty blíže k **1** jsou lepší|

## <a name="evaluation-metrics-for-ranking"></a>Hodnotící metriky pro hodnocení

| Metrika   |      Popis      |  Hledat |
|----------|-----------------------|-----------|
|**Diskontované kumulativní zisky**|Diskontovaný kumulativní zisk (DCG) je měřítkem kvality hodnocení. Je odvozen ze dvou předpokladů. První: Vysoce relevantní položky jsou užitečnější, když se objevují vyšší v pořadí. Za druhé: Užitečnost sleduje relevanci, která je, čím vyšší je relevance, tím užitečnější je položka. Diskontovaný kumulativní zisk se vypočítá pro konkrétní pozici v pořadí. Shrnuje klasifikaci relevance dělenou logaritmem žebříčku indexu až do pozice zájmu. Vypočítá se pomocí $\sum_{i=0}^{p} \frac {rel_i} {\log_{e}{i+1}}$ Stupně relevance jsou k dispozici algoritmu hodnocení školení jako pozemní popisky pravdy. Pro každou pozici v tabulce pořadí je uvedena jedna hodnota DCG, proto je uveden název Diskontované kumulativní **zisky**. |**Vyšší hodnoty jsou lepší**|
|**Normalizované diskontované kumulativní zisky**|Normalizace DCG umožňuje porovnat metriku pro pořadníky různých délek|**Hodnoty blíže k 1 jsou lepší**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Metriky vyhodnocení pro detekci anomálií

| Metrika   |      Popis      |  Hledat |
|----------|-----------------------|-----------|
|**Plocha pod křivkou ROC**|Plocha pod křivkou operátora přijímače měří, jak dobře model odděluje neobvyklé a obvyklé datové body.|**Hodnoty blíže k 1 jsou lepší**. Účinnost modelu demonstrují pouze hodnoty větší než 0,5. Hodnoty 0,5 nebo nižší označují, že model není o nic lepší než náhodné přidělování vstupů do neobvyklých a obvyklých kategorií|
|**Míra detekce při falešně pozitivním počtu**|Míra detekce při falešně pozitivním počtu je poměr počtu správně identifikovaných anomálií k celkovému počtu anomálií v testovací sadě indexovaných jednotlivými falešně pozitivními. To znamená, že je hodnota pro zjišťování rychlost při falešně pozitivní počet pro každou falešně pozitivní položku.|**Hodnoty blíže k 1 jsou lepší**. Pokud nejsou k dispozici žádné falešně pozitivní výsledky, je tato hodnota 1|
