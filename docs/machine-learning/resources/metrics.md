---
title: ML.NET metriky
description: Pochopení metrik, které se používají k vyhodnocení výkonu ML.NET modelu
ms.date: 04/29/2019
author: natke
ms.openlocfilehash: 362f2f382d050ff9ae246af2dffe3e15d22452eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460728"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>Metriky vyhodnocení modelu v ML.NET

## <a name="metrics-for-binary-classification"></a>Metriky pro binární klasifikaci

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **Údajů** |  [Přesnost](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) je poměr správného předpovědi se sadou testů dat. Je to poměr počtu správných předpovědi k celkovému počtu vstupních vzorků. Funguje správně pouze v případě, že existuje podobný počet vzorků patřících ke každé třídě.| **Nejblíže k 1,00, tím lépe**. Ale přesně 1,00 označuje problém (obvykle se jedná o netěsné úniky popisků, převzetí služeb při selhání nebo testování pomocí školicích dat). Pokud jsou testovací data nevyvážená (kde většina instancí patří do jedné z tříd), je datová sada velmi malá nebo má skóre přístup 0,00 nebo 1,00, takže přesnost nezachycuje efektivitu klasifikátoru a potřebujete zkontrolovat další metriky. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) nebo *plocha pod křivkou*: slouží k měření oblasti pod křivkou vytvořenou vyčištěním skutečné kladné míry a falešně pozitivní míry.  |   **Nejblíže k 1,00, tím lépe**. Měl by být větší než 0,50, aby bylo možné model akceptovat; model s AUC 0,50 nebo méně je bezcenné. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) nebo *plocha pod křivkou křivky přesnosti odvolání*: užitečná míra úspěšnosti předpovědi, pokud jsou třídy velmi nevyvážené (vysoce zkreslené datové sady). |  **Nejblíže k 1,00, tím lépe**. Vysoká skóre blízko až 1,00 ukazují, že klasifikátor vrací přesné výsledky (vysoká přesnost) a vrací většinu všech pozitivních výsledků (vysoké odvolání). |
| **F1 – skóre** | [Skóre F1](https://en.wikipedia.org/wiki/F1_score) se také označuje jako *vyrovnané f-skore nebo f-Measure*. Je to harmonický význam přesnosti a odvolání. Skóre F1 je užitečné, pokud chcete vyhledat rovnováhu mezi přesností a odvoláním.| **Nejblíže k 1,00, tím lépe**.  Skóre F1 dosáhne své nejlepší hodnoty na 1,00 a nejhorší skóre v 0,00. Dozvíte se, jak přesně je třídění. |

Další podrobnosti o binárních metrikách klasifikace najdete v následujících článcích:

- [Přesnost, přesnost, odvolání nebo F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Třída binárních metrik klasifikace](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Vztah mezi přesností a odvoláním a ROC křivky](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Metriky pro klasifikaci více tříd

| Metriky   |      Popis      |  Hledat |
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

## <a name="metrics-for-regression"></a>Metriky pro regresi

| Metriky   |      Popis      |  Hledat |
|-----------|-----------------------|-----------|
| **R – čtvercový** |  [R-kvadrát (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)nebo *koeficienty stanovitelnosti* představují prediktivní sílu modelu jako hodnotu mezi-inf a 1,00. 1,00 znamená, že existuje dokonalé přizpůsobení a přizpůsobení může být libovolně špatné, takže skóre mohou být záporná. Skóre 0,00 znamená, že model odhaduje očekávanou hodnotu popisku. R2 měří způsob, jakým se hodnoty skutečných testovacích dat blíží předpokládaným hodnotám. | **Lepší kvalita je blíže k 1,00**. Někdy ale nízké hodnoty R-Square (například 0,50) můžou být pro váš scénář zcela normální nebo dostatečně dobré a vysoké hodnoty R-čtverce nejsou vždy dobré a jsou podezřelé. |
| **Absolutní ztráta** |  [Absolutní ztráta](https://en.wikipedia.org/wiki/Mean_absolute_error) nebo *střední absolutní chyba (Mae)* měří způsob, jakým se předpovědi blíží skutečným výsledkům. Jedná se o průměr všech chyb modelů, kde chyba modelu je absolutní vzdálenost mezi předpovězenou hodnotou popisku a správnou hodnotou popisku. Tato chyba předpovědi je vypočítána pro každý záznam sady dat testu. Nakonec se pro všechny zaznamenané absolutní chyby vypočítá střední hodnota.| **Lepší kvalita je blíže k 0,00.** Všimněte si, že střední absolutní chyba používá stejnou škálu jako změřená data (není normalizována na konkrétní rozsah). Absolutní ztráta, čtvercová ztráta a ztráta RMS lze použít pouze k porovnání modelů pro stejnou datovou sadu nebo datovou sadu s podobnou distribucí hodnoty popisku. |
| **Kvadratická ztráta** |  [Čtvercová ztráta](https://en.wikipedia.org/wiki/Mean_squared_error) nebo *střední Chyba (MSE)* , označovaná také jako *střední odchylka (MSD)* , říká, jak blízko regresní přímky je sada hodnot testovacích dat. Provede to tím, že převezme vzdálenosti od bodů až po regresní čáru (tyto vzdálenosti jsou chyby E) a umocnění je. Umocnění poskytuje větší váhu většímu rozdílu. | Je vždycky nezáporné a **hodnoty blíž až 0,00 jsou lepší**. V závislosti na vašich datech nemusí být možné získat velmi malou hodnotu pro střední kvadratickou chybu.|
| **RMS – ztráta** |  Služba [RMS – ztráta](https://en.wikipedia.org/wiki/Root-mean-square_deviation) nebo *hlavní střední hodnota chyby (RMSE)* (označuje se také jako *Kořenová střední odchylka, RMSD*), měří rozdíl mezi hodnotami předpokládanými modelem a hodnotami skutečně zjištěnými z prostředí, které je právě modelováno. Služby RMS-ztráta je druhá odmocnina čtvercové ztráty a má stejné jednotky jako popisek, podobně jako u absolutní ztráty, a poskytuje větší váhu větším rozdílům. V climatology, předpovědi a regresní analýze se běžně používá chyba na kořenovém středním průměru k ověření experimentálních výsledků. | Je vždycky nezáporné a **hodnoty blíž až 0,00 jsou lepší**. RMSD je míra přesnosti, která umožňuje porovnat chyby prognózy různých modelů pro určitou datovou sadu a ne mezi datovými sadami, protože se jedná o závislé na škálování.|

Další podrobnosti o regresních metrikách najdete v následujících článcích:

- [Regresní analýza: Jak mohu interpretovat R-kvadrát a vyhodnotit dobré výsledky?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Jak interpretovat R-kvadrát v analýze regrese](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definice R-čtverce](https://www.investopedia.com/terms/r/r-squared.asp)
- [Střední hodnota čtverce v definici chyby](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Co znamená chyba na čtverci a hlavní střední hodnota chyby?](https://www.vernier.com/til/1014/)
