---
title: Machine Learning Glosář
description: Glosář termínů machine learning.
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: b7690eb6931f4a491b1a03812fe3f2d8a64cfcd4
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208312"
---
# <a name="machine-learning-glossary"></a>Machine learning Glosář

V následujícím seznamu je kompilací důležité machine learning podmínky, které jsou užitečné při sestavování vlastní modely.

## <a name="accuracy"></a>Přesnost

V [klasifikace](#classification), přesnost je počet správně klasifikovaný položek oddělených celkový počet položek v sadě testů. Rozmezí od 0 (nejméně přesné) na hodnotu 1 (nejpřesnější). Přesnost je jedním z vyhodnocení metriky výkonu modelu. Zvažte ve spojení s [přesnost](#precision), [odvolání](#recall), a [F – score](#f-score).

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.

## <a name="area-under-the-curve-auc"></a>Oblast pod křivkou (AUC)

V [binární klasifikace](#binary-classification), metriku hodnocení, která je hodnota oblasti pod křivkou, která ukazuje zeměpisný true pozitivních rychlost (na ose y) proti falešně pozitivních rychlost (na ose x). Rozsahy z 0,5 (nejhorší) na hodnotu 1 (doporučené). Oblasti se taky říká pod křivka ROC, tedy příjemce operační charakteristik křivky. Další informace najdete v tématu [příjemce operační vlastnosti](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) článku na webu Wikipedia.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.

## <a name="binary-classification"></a>binární klasifikace

A [klasifikace](#classification) případ where [popisek](#label) je jenom jednu z dvě třídy. Další informace najdete v tématu [binární klasifikace](tasks.md#binary-classification) části [strojového učení úlohy](tasks.md) tématu.

## <a name="classification"></a>klasifikace

Pokud data se používají k předvídání kategorii, [počítač učení se supervizí](#supervised-machine-learning) je volána úloha, klasifikace. [Binární klasifikace](#binary-classification) odkazuje na predikci pouze dvě kategorie (například klasifikace bitovou kopii jako obrázek 'cat' nebo 'PSA). [Více třídami klasifikace](#multiclass-classification) odkazuje na predikci více kategorií (například při klasifikaci bitovou kopii jako obrázek konkrétní druh PSA).

## <a name="coefficient-of-determination"></a>Koeficient spolehlivosti

V [regrese](#regression), metriku hodnocení, která určuje, jak dobře dat odpovídá modelu. Rozmezí od 0 do 1. Hodnota 0 znamená, že data jsou náhodných nebo jinak se nemůže vejít do modelu. Hodnota 1 znamená, že model přesně odpovídá data. To se často označuje jako r<sup>2</sup>, R<sup>2</sup>, nebo spolehlivosti.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.

## <a name="feature"></a>Funkce

Měřitelné vlastnosti jevu měřenou, obvykle číselnou hodnotu (double). Více funkcí se označují jako **funkce vector** a obvykle se uloží jako `double[]`. Funkce definovat důležité charakteristiky se měří jevu. Další informace najdete v tématu [funkce](https://en.wikipedia.org/wiki/Feature_(machine_learning)) článku na webu Wikipedia.

## <a name="feature-engineering"></a>Funkce inženýrství

Funkce inženýrství je proces, který zahrnuje definování sady [funkce](#feature) a vývoji softwaru, který vytváří vektory funkce z dostupných jevu dat, tedy funkce extrakce. Další informace najdete v tématu [konstruování](https://en.wikipedia.org/wiki/Feature_engineering) článku na webu Wikipedia.

## <a name="f-score"></a>F – score

V [klasifikace](#classification), vyhodnocení metrika, který vyrovnává [přesnost](#precision) a [odvolání](#recall).

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.

## <a name="hyperparameter"></a>Hyperparameter

Parametr algoritmu strojového učení. Mezi příklady patří počet stromy další v doménové struktuře rozhodnutí nebo velikost kroku v algoritmus klesání přechodu. Hodnoty z *Hyperparameters* jsou nastavené před tréninku modelu a řídit proces hledání parametry funkce předpovědi, například porovnání body v rozhodovacím stromu nebo vah ve model lineární regrese . Další informace najdete v tématu [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) článku na webu Wikipedia.

## <a name="label"></a>Popisek

Elementu, který chcete předpovědět s model strojového učení. Například se druh pes nebo budoucí uložených cena.

## <a name="log-loss"></a>Ztráta protokolu

V [klasifikace](#classification), metriku hodnocení, která charakterizuje přesnost třídění. Menší ztrátě protokolu je, tím přesnější třídění.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.

## <a name="mean-absolute-error-mae"></a>Střední absolutní chyba (MAE)

V [regrese](#regression), metriku hodnocení, která je průměr všech modelu chyb, kde chybu modelu je vzdálenost mezi předpokládaných [popisek](#label) hodnota a hodnota správný popisek.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.

## <a name="model"></a>Model

Obvyklým parametry pro funkci předpovědi. Například vah ve model lineární regrese nebo body rozdělení v rozhodovacím stromu. V ML.NET, model obsahuje všechny informace potřebné k předpovědi [popisek](#label) objektu domény (například obrázek nebo text). To znamená, že ML.NET modely zahrnout featurization kroky, které jsou nezbytné, a také parametry pro funkci předpovědi.

## <a name="multiclass-classification"></a>více třídami klasifikace

A [klasifikace](#classification) případ where [popisek](#label) je jedním z tři nebo více tříd. Další informace najdete v tématu [více třídami klasifikace](tasks.md#multiclass-classification) části [strojového učení úlohy](tasks.md) tématu.

## <a name="n-gram"></a>N-gram

Funkce extrakce schéma pro data textu: žádné pořadí N slova se změní [funkce](#feature) hodnotu.

## <a name="numerical-feature-vector"></a>Numerické funkce vector

A [funkce](#feature) vektor, který se skládá pouze z číselné hodnoty. Toto je podobná `double[]`.

## <a name="pipeline"></a>Kanál

Všechny operace, je potřeba podle modelu pro datové sady. Kanál se skládá z importu dat, transformaci, featurization a učení kroky. Jakmile je vycvičena kanál, změní se do modelu.

## <a name="precision"></a>Přesnost

V [klasifikace](#classification), přesnost pro třídu je počet položek správně předpovědět jako patřící do této třídy dělený celkový počet položek předpovědět jako náležící k třídě.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.

## <a name="recall"></a>Odvolat

V [klasifikace](#classification), odvolání pro třídu je počet položek správně předpovědět jako patřící do této třídy dělený celkový počet položek, které ve skutečnosti patří do třídy.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.

## <a name="regression"></a>Regrese

A [počítač učení se supervizí](#supervised-machine-learning) úloh, kde výstup je skutečné hodnoty, například, double. Mezi příklady patří predikci uložených ceny. Další informace najdete v tématu [regrese](tasks.md#regression) části [strojového učení úlohy](tasks.md) tématu.

## <a name="relative-absolute-error"></a>Relativní absolutní chyba

V [regrese](#regression), metriku hodnocení, která je součet hodnot všech absolutních chyb dělený součet vzdálenosti mezi správné [popisek](#label) hodnotami a průměrem všech opravte popisek hodnoty.

## <a name="relative-squared-error"></a>Relativní kvadratická chyba

V [regrese](#regression), metriku hodnocení, která je součet všech spolehlivosti absolutních chyb a součtu kvadratických vzdálenosti mezi správné [popisek](#label) hodnotami a průměrem všech opravte popisek hodnoty.

## <a name="root-of-mean-squared-error-rmse"></a>Kořenové střední spolehlivosti chyby (RMSE)

V [regrese](#regression), vyhodnocení metriky, která je druhá odmocnina průměru kvadratických chyb.

Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.

## <a name="supervised-machine-learning"></a>Strojového učení

Podtřídou třídy strojového učení, ve kterém požadované modelu předpovídá popisek pro ještě neviditelný data. Mezi příklady patří klasifikaci, regresi a strukturovaných předpovědi. Další informace najdete v tématu [učení se Supervizí](https://en.wikipedia.org/wiki/Supervised_learning) článku na webu Wikipedia.

## <a name="training"></a>Školení

Proces identifikace [modelu](#model) pro danou trénovací datové sady. Pro model lineární to znamená, že hledání vah. Pro strom zahrnuje identifikace body rozdělení.

## <a name="transform"></a>Transformace

A [kanálu](#pipeline) komponenty, která transformuje data. Například z text vector čísel.

## <a name="unsupervised-machine-learning"></a>Bez dohledu machine learning

Podtřídou třídy strojového učení, ve kterém požadované modelu najde struktura skrytá (nebo latentní) v datech. Mezi příklady patří clustering, tématu modelování a snížení dimenzionalitu. Další informace najdete v tématu [Supervize](https://en.wikipedia.org/wiki/Unsupervised_learning) článku na webu Wikipedia.
