---
title: Metriky ML.NET
description: Principy, která se používají k vyhodnocení výkonu modelu ML.NET
ms.date: 04/29/2019
author: natke
ms.openlocfilehash: 45176902a195906e7b5cffd24fc9da839406ad9d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410513"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>Model metrik v ML.NET

## <a name="metrics-for-binary-classification"></a>Metriky pro binární klasifikaci

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **Přesnost** |  [Přesnost](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) je poměr správné předpovědi s testovací datové sady. Je poměr počtu správné predikcí celkového počtu vstupních vzorků. To funguje dobře pouze pokud jsou podobné počet vzorků, které patří ke každé třídě.| **Blíže k 1,00, tím lepší**. Přesně 1,00 označuje potíže, ale (běžně: popisek/cílového únikům over-pass-the těsně a testování s trénovací data). Když jsou data testu nevyvážené uvozovky (kde většina instancí patří do jedné ze tříd), datové sady je velmi malý nebo skóre přístup 0,00 nebo 1,00, pak přesnost nezachytí skutečně efektivitu třídění a je potřeba zkontrolovat další metriky. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) nebo *oblasti pod křivkou*: To je měření oblasti pod křivkou vytvořené cílit na konkrétní hodnotu true kladné míra vs. míru falešně pozitivních výsledků.  |   **Blíže k 1,00, tím lepší**. By měla být větší než 0,50 modelu jako přijatelné; bezcenné. podstatné je model s AUC 0,50 nebo i rychleji. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) nebo *oblasti pod křivkou křivky přesnosti a úplnosti*: Užitečné měření úspěchu předpovědí při třídy jsou velmi imbalanced (s výrazně nerovnoměrnou distribucí datové sady). |  **Blíže k 1,00, tím lepší**. Vysoké hodnocení blížící se 1,00 zobrazení, třídění je vrácení přesné výsledky (vysoká přesnost), stejně jako vrácení většinou všechny pozitivních výsledků (vysoká odvolání). |
| **F1 skóre** | [Skóre F1](https://en.wikipedia.org/wiki/F1_score) označované také jako *balanced skóre F nebo F míru*. Je průměr přesnosti a odvolání. F1 skóre je užitečné, když chcete hledají rovnováhu mezi přesnosti a odvolání.| **Blíže k 1,00, tím lepší**.  Skóre F1 dosáhne jeho nejlepší poměr na 1,00 a nejhorší skóre v 0,00. Zjistíte, jak přesně je klasifikátoru. |

Další podrobnosti o binární klasifikace metrik najdete v následujících článcích:

- [Přesnost, zaokrouhlení, odvolání nebo stisknutím F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Binární klasifikace metriky třídy](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Vztah mezi přesnosti a úplnosti a křivky roc s více TŘÍDAMI](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Metriky pro klasifikace víc tříd

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **Micro-Accuracy** |  [Průměr Micro přesnost](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agreguje vaše příspěvky všechny třídy pro výpočet průměrné metriku. Jedná se o zlomek instance správně předpovědět. Průměr micro nepřijímá členství ve třídě v úvahu. V podstatě každá dvojice ukázkovou třídu přispívá stejně metriky přesnosti. | **Blíže k 1,00, tím lepší**. V rámci úlohy klasifikace roc micro přesnost je vhodnější než přes – makro přesnost Pokud máte podezření, že může být třída imbalance (např.) Možná budete muset mnoho dalších příkladů jedné třídy než jiné třídy).|
| **Macro-Accuracy** | [Average – makro přesnost](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) je průměrná přesností na úrovni třídy. Je vypočítán přesnost pro každou třídu a přesnost – makro je průměrem těchto přesností. V podstatě každá třída přispívá stejně metriky přesnosti. Třídy minority disponují stejnou váhu jako větší třídy. Metrika – makro průměr poskytuje stejnou váhou pro každou třídu, bez ohledu na to, kolik instancí od, který obsahuje třídu datové sady. |  **Blíže k 1,00, tím lepší**.  Vypočítá metrika nezávisle pro každou třídu a potom vezme v průměru (tedy. považuje všechny třídy stejně) |
| **Log-loss**| [Logaritmické ztrátu](http://wiki.fast.ai/index.php/Log_Loss) měří výkonnost model klasifikace, kde je hodnota pravděpodobnosti mezi 0,00 a 1,00 vstup předpovědi. Ztráta protokolu zvyšuje podle pravděpodobnost předpovězené diverges od skutečné popisku. | **Blíže k 0,00, tím lepší**. Ideální model by měla mít protokolu ztrátu 0,00. Cílem naší modelů strojového učení je minimalizovat tuto hodnotu.|
| **Omezení protokolu ztráty** | [Snížení logaritmické ztrátu](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) může být interpretován jako výhod třídění přes náhodné předpovědi.| **V rozsahu od -inf a 1,00, kde 1,00 je ideální předpovědi a 0,00 označuje střední predikcí**. Například pokud je hodnota 0.20 a novější, to může být interpretován tak "pravděpodobnost správného předpovědi je lepší než náhodných opakovaně uhodnout 20 %"|

Micro přesnost je obecně lepší v souladu s obchodní potřeby predikce ML. Pokud chcete vybrat jednu metriku pro výběr kvality úlohu klasifikace víc tříd, mělo by být obvykle micro přesnost.

Například pro úkol klasifikace lístku podpory: (mapuje příchozí lístky pro podporu týmů)

- Přesnost Micro – jak často lístek příchozí získat zařazených do správný tým?
- Přesnost – makro – průměrná týmu, jak často se lístek příchozí správnou pro jejich tým?

Malé týmy v tomto příkladu; overweights přesnost – makro malý tým, který získá jenom 10 lístky za rok se počítá tak, jak velký tým s 10 tisíc lístky za rok. Přesnost Micro v tomto případě koreluje lépe se obchodní potřeby, "kolik čas a peníze může společnost uložit tím, že automatizuje proces směrování lístku".

Další informace o klasifikaci roc metrik najdete v následujících článcích:

- [Micro – a – makro – průměr přesnost, odvolání a skóre F](http://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Klasifikace víc tříd s datovou sadou Imbalanced](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="metrics-for-regression"></a>Metriky pro regresní

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **Spolehlivosti R** |  [Plánovaná (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination), nebo *koeficient spolehlivosti* představuje výkon prediktivní model jako hodnotu mezi -inf a 1,00. 1,00 znamená, že se skvěle hodí, a přizpůsobit může být libovolně nízká, takže skóre může být záporné. Skóre 0,00 znamená, že model je opakovaně uhodnout očekávanou hodnotou pro popisek. R2 měří jak blízko skutečné testovací datové hodnoty jsou předpovězeným hodnotám. | **Blíže k 1,00, lepší kvalitu**. Ale někdy nízké hodnoty spolehlivosti (například 0,50) může být zcela normální nebo dostatečné pro váš scénář a vysoké spolehlivosti R hodnoty nejsou vždy dobré a dávejte pozor. |
| **Absolutní ztráty** |  [Absolutní ztrátu](https://en.wikipedia.org/wiki/Mean_absolute_error) nebo *střední absolutní chyba (MAE)* měří jak blízko předpovědi se skutečné výsledky. Je průměrem všechny chyby modelu, kde je chyba modelu absolutní vzdálenost mezi předpokládané popisek hodnotu a hodnotu správný popisek. Tato chyba predikcí se počítá pro každý záznam testovací datové sady. Nakonec se počítá střední hodnoty pro všechny nahrané absolutních chyb.| **Blíže k 0,00, lepší kvality.** Všimněte si, že střední absolutní chyba používá stejné měřítko jako data měří (není normalizovány na konkrétní rozsah). Absolutní ztráty, Squared ztráty a ztráty RMS jde použít jenom k porovnání mezi modely pro stejné datové sadě nebo datová sada se podobá distribuce hodnoty popisku. |
| **Spolehlivosti ztráty** |  [Squared ztrátu](https://en.wikipedia.org/wiki/Mean_squared_error) nebo *znamenat chyba spolehlivosti (MSE)* , označované také jako *znamenat spolehlivosti odchylka (program MSD)* , zjistíte, jak blízko řádku regrese do sady testů datových hodnot. Dělá to tak, že trvá daleko od bodů na regresní přímky (Tyto vzdálenosti se chyby E) a jejich umocnění na druhou. Umocňování poskytuje větší váhu k větší rozdíly. | Vždy je záporná, a **hodnoty blíže k 0,00 jsou lepší**. V závislosti na vašich dat může být možné získat velmi malou hodnotu pro střední kvadratické chyby.|
| **RMS-loss** |  [RMS při ztrátě](https://en.wikipedia.org/wiki/Root-mean-square_deviation) nebo *kořenové znamenat spolehlivosti chyby (RMSE)* (také nazývané *kořenové směrodatná odchylka, RMSD*), měří rozdíl mezi hodnotami předpovídané pomocí modelu a hodnotami ve skutečnosti zjištěnými z prostředí, které je právě modelovat. Ztráta RMS je odmocninu Squared ztráty a má stejné jednotky jako popisek, podobně jako absolutní ztrát v případě, že poskytuje větší váhu větší rozdíly. Průměrná kvadratická chyba se běžně používá v klimatologie, Prognózování a regresní analýzy ověřit výsledky. | Vždy je záporná, a **hodnoty blíže k 0,00 jsou lepší**. RMSD je míra přesnost porovnání Prognózování chyby z různých modelů pro konkrétní datové sady a není mezi datovými sadami, protože je závislé na škálování.|

Další podrobnosti týkající se metrik Regrese v následujících článcích:

- [Regresní analýzy: Jak interpretovat, spolehlivosti a posoudit ještě lepší-přizpůsobit zobrazení?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Jak interpretovat spolehlivosti R v regresní analýzy](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definice spolehlivosti R](https://www.investopedia.com/terms/r/r-squared.asp)
- [Znamenají kvadratická chyba definice](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Co jsou znamenat kvadratická chyba a kvadratická chyba znamenají kořenové?](https://www.vernier.com/til/1014/)
