---
title: Glosář strojového učení
description: Glosář důležitých termínů strojového učení, které jsou užitečné při vytváření vlastních modelů v ML.NET.
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: 32ccb6df1cb08db45ebd25a0d1c0ea4396a6c50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398935"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Glosář strojového učení důležitých pojmů

Následující seznam je kompilací důležitých termínů strojového učení, které jsou užitečné při vytváření vlastních modelů v ML.NET.

## <a name="accuracy"></a>Přesnost

V [klasifikaci](#classification)je přesnost počet správně klasifikovaných položek vydělený celkovým počtem položek v testovací sadě. Rozsah y od 0 (nejméně přesné) do 1 (nejpřesnější). Přesnost je jednou z metrik hodnocení výkonu modelu. Vezměme si to ve spojení s [přesností](#precision), [odvolání](#recall), a [F-skóre](#f-score).

## <a name="area-under-the-curve-auc"></a>Plocha pod křivkou (AUC)

V [binární klasifikaci](#binary-classification)je metrika vyhodnocení, která je hodnotou oblasti pod křivkou, která vykresluje skutečnou kladnou míru (na ose y) proti míře falešně pozitivních hodnot (na ose x). Pohybuje se od 0,5 (nejhorší) do 1 (nejlepší). Také známý jako oblast pod křivkou ROC, tj. Další informace naleznete v článku [o provozní chodu příjemce](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) na Wikipedii.

## <a name="binary-classification"></a>Binární klasifikace

Případ [klasifikace,](#classification) kdy [popisek](#label) je pouze jeden ze dvou tříd. Další informace naleznete [v](tasks.md#binary-classification) části Binární klasifikace v tématu [úkoly strojového učení.](tasks.md)

## <a name="calibration"></a>Kalibrace

Kalibrace je proces mapování nezpracovaného skóre na členství ve třídě pro binární a vícetřídní klasifikaci. Některé ML.NET trenéři `NonCalibrated` mají příponu. Tyto algoritmy vytvořit nezpracované skóre, které pak musí být mapovány na pravděpodobnost třídy.

## <a name="catalog"></a>Katalog

V ML.NET je katalog kolekce rozšiřujících funkcí seskupených podle společného účelu.

Například každý úkol strojového učení (binární klasifikace, regrese, pořadí atd.) má katalog dostupných algoritmů strojového učení (školitelů). Katalog pro binární klasifikace školitelů je: <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>.

## <a name="classification"></a>Classification

Při použití dat k předvídání kategorie se úkol [strojového učení pod dohledem](#supervised-machine-learning) nazývá klasifikace. [Binární klasifikace](#binary-classification) odkazuje na předpovídání pouze dvou kategorií (například klasifikace obrázku jako obrázku "kočky" nebo "psa"). [Klasifikace více tříd](#multiclass-classification) odkazuje na předpovídání více kategorií (například při klasifikaci obrázku jako obrázku určitého plemene psa).

## <a name="coefficient-of-determination"></a>Koeficient stanovení

V [regresi](#regression)metrika vyhodnocení, která označuje, jak dobře data vejde model. Rozsah od 0 do 1. Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu. Hodnota 1 znamená, že model přesně odpovídá datům. To je často označováno jako r<sup>2</sup>, R<sup>2</sup>nebo r-squared.

## <a name="data"></a>Data

Data jsou zásadní pro všechny aplikace strojového učení. V ML.NET jsou <xref:Microsoft.ML.IDataView> data reprezentována objekty. Objekty zobrazení dat:

- jsou tvořeny sloupci a řádky
- jsou líně vyhodnocovány, to znamená, že načítají data pouze tehdy, když operace volá
- obsahují schéma, které definuje typ, formát a délku každého sloupce

## <a name="estimator"></a>Odhad

Třída v ML.NET, která <xref:Microsoft.ML.IEstimator%601> implementuje rozhraní.

Odhad je specifikace transformace (transformace přípravy dat a transformace trénování modelu strojového učení). Odhady lze zřetězit do kanálu transformací. Parametry odhadu nebo potrubí odhadců se učí, když <xref:Microsoft.ML.IEstimator%601.Fit%2A> je volána. Výsledkem <xref:Microsoft.ML.IEstimator%601.Fit%2A> je [Transformer](#transformer).

## <a name="extension-method"></a>Metoda rozšíření

Metoda .NET, která je součástí třídy, ale je definována mimo třídu. První parametr metody rozšíření je `this` statický odkaz na třídu, do které patří metoda rozšíření.

Rozšiřující metody se ve velké míře používají v ML.NET k vytvoření instancí [odhadů](#estimator).

## <a name="feature"></a>Funkce

Měřitelná vlastnost měřeného jevu, obvykle číselná (dvojitá) hodnota. Více funkcí se označuje jako **vektor funkce** `double[]`a obvykle se ukládá jako . Vlastnosti definují důležité charakteristiky měřeného jevu. Další informace naleznete v článku [Funkce](https://en.wikipedia.org/wiki/Feature_(machine_learning)) na Wikipedii.

## <a name="feature-engineering"></a>Návrh funkcí

Funkce inženýrství je proces, který zahrnuje definování sadu [funkcí](#feature) a vývoj softwaru, který vytváří vektory funkcí z dostupných jevů dat, tj. Další informace naleznete v článku [o funkci na](https://en.wikipedia.org/wiki/Feature_engineering) Wikipedii.

## <a name="f-score"></a>F-skóre

V [klasifikaci](#classification)metrika hodnocení , která vyvažuje [přesnost](#precision) a [vyvolání .](#recall)

## <a name="hyperparameter"></a>Hyperparametr

Parametr algoritmu strojového učení. Příklady zahrnují počet stromů, které se mají učit v rozhodovací doménové struktuře, nebo velikost kroku v algoritmu sestupu přechodu. Hodnoty *Hyperparameters* jsou nastaveny před trénování modelu a řídí proces hledání parametrů funkce předpověď, například porovnávací body ve stromu rozhodnutí nebo váhy v modelu lineární regrese. Další informace naleznete v článku [hyperparametry](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) na Wikipedii.

## <a name="label"></a>Popisek

Prvek, který má být předpovězen pomocí modelu strojového učení. Například plemeno psa nebo budoucí cena akcií.

## <a name="log-loss"></a>Ztráta protokolu

V [klasifikaci](#classification)metrika hodnocení, která charakterizuje přesnost třídění. Menší ztráta protokolu je přesnější třídění je.

## <a name="loss-function"></a>Funkce ztráty

Funkce ztráty je rozdíl mezi hodnotami popisku školení a předpověď provedené modelem. Parametry modelu se odhadují minimalizací funkce ztráty.

Různé trenéři mohou být konfigurovány s různými funkcemi ztráty.

## <a name="mean-absolute-error-mae"></a>Průměrná absolutní chyba (MAE)

V [regresi](#regression)metrika vyhodnocení, která je průměrem všech chyb modelu, kde chyba modelu je vzdálenost mezi předpovídanou hodnotou [popisku](#label) a správnou hodnotou popisku.

## <a name="model"></a>Model

Tradičně parametry pro předpověď funkce. Například váhy v modelu lineární regrese nebo rozdělené body ve stromu rozhodnutí. V ML.NET model obsahuje všechny informace potřebné k předvídání [popisku](#label) objektu domény (například obrázek nebo text). To znamená, že ML.NET modely zahrnují nezbytné kroky featurization, stejně jako parametry pro funkci předpověď.

## <a name="multiclass-classification"></a>Klasifikace více tříd

Případ [klasifikace,](#classification) kdy [popisek](#label) je jeden ze tří nebo více tříd. Další informace najdete v části [Klasifikace více tříd](tasks.md#multiclass-classification) v tématu [Úkoly strojového učení.](tasks.md)

## <a name="n-gram"></a>N-gram

Schéma extrakce prvků pro textová data: libovolná sekvence N slov se změní na hodnotu [prvku.](#feature)

## <a name="normalization"></a>Normalizace

Normalizace je proces škálování dat s plovoucí desetinnou tálicí na hodnoty mezi 0 a 1. Mnoho trénovacích algoritmů používaných v ML.NET vyžaduje normalizovat data vstupních funkcí. ML.NET poskytuje řadu [transformací pro normalizaci](transforms.md#normalization-and-scaling)

## <a name="numerical-feature-vector"></a>Vektor číselných prvků

Vektor [prvku,](#feature) který se skládá pouze z číselných hodnot. To je `double[]`podobné .

## <a name="pipeline"></a>Kanál

Všechny operace potřebné k přizpůsobení modelu datové sadě. Kanál se skládá z importu dat, transformace, featurization a učení kroky. Jakmile je potrubí trénované, změní se na model.

## <a name="precision"></a>Přesnost

V [klasifikaci](#classification)je přesnost pro třídu počet položek správně předpovězených jako položky do této třídy vydělený celkovým počtem položek, které byly předpovězeny jako položky patřící do třídy.

## <a name="recall"></a>Úplnost

V [klasifikaci](#classification)je odvolání pro třídu počet položek správně předpovězených jako položky patřící do této třídy vydělený celkovým počtem položek, které skutečně patří do třídy.

## <a name="regularization"></a>Regularizace

 Regularizace penalizuje lineární model za to, že je příliš komplikovaný. Existují dva typy regularizace:

- $L_1$ regularizace nuly váhy pro nevýznamné funkce. Velikost uloženého modelu může být po tomto typu regularizace menší.
- $L_2$ minimalizuje hmotnostní rozsah pro nevýznamné funkce. Jedná se o obecnější proces a je méně citlivý na odlehlé hodnoty.

## <a name="regression"></a>Regrese

Úkol [strojového učení pod dohledem,](#supervised-machine-learning) kde je výstup skutečnou hodnotou, například double. Příklady zahrnují předpovídání cen akcií. Další informace najdete v části [Regrese](tasks.md#regression) v tématu [Úlohy strojového učení.](tasks.md)

## <a name="relative-absolute-error"></a>Relativní absolutní chyba

V [regresi](#regression)metrika vyhodnocení, která je součtem všech absolutních chyb děleno součtem vzdáleností mezi hodnotami [správných popisků](#label) a průměrem všech správných hodnot popisků.

## <a name="relative-squared-error"></a>Relativní vyrovnaná chyba

V [regresi](#regression)metrika vyhodnocení, která je součtem všech kvadratických absolutních chyb děleno součtem kvadratických vzdáleností mezi správnými hodnotami [popisků](#label) a průměrem všech správných hodnot popisků.

## <a name="root-of-mean-squared-error-rmse"></a>Odmocnina střední kvadratózní chyby (RMSE)

V [regresi](#regression), metrika vyhodnocení, která je druhou odmocninou průměru druhých mocnin chyb.

## <a name="scoring"></a>Vyhodnocování

Vyhodnocování je proces použití nových dat na trénovaný model strojového učení a generování předpovědí. Bodování se také označuje jako odvození. V závislosti na typu modelu může být skóre nezpracovaná hodnota, pravděpodobnost nebo kategorie.

## <a name="supervised-machine-learning"></a>Strojové učení pod dohledem

Podtřída strojového učení, ve kterém požadovaný model předpovídá popisek pro dosud neviditelná data. Příklady zahrnují klasifikaci, regrese a strukturované předpovědi. Další informace naleznete v článku [Učení pod dohledem](https://en.wikipedia.org/wiki/Supervised_learning) na Wikipedii.

## <a name="training"></a>Školení

Proces identifikace [modelu](#model) pro danou sadu dat školení. Pro lineární model to znamená nalezení závaží. Pro strom zahrnuje identifikaci rozdělených bodů.

## <a name="transformer"></a>Transformátor

ML.NET třídy, která <xref:Microsoft.ML.ITransformer> implementuje rozhraní.

Transformátor transformuje jeden <xref:Microsoft.ML.IDataView> do druhého. Transformátor je vytvořen školením [odhadu](#estimator)nebo kanálu odhadu.

## <a name="unsupervised-machine-learning"></a>Strojové učení bez dohledu

Podtřída strojového učení, ve kterém požadovaný model najde skrytou (nebo latentní) strukturu v datech. Příklady zahrnují clustering, modelování témat a snížení dimenzionality. Další informace naleznete v článku [učení bez dozoru](https://en.wikipedia.org/wiki/Unsupervised_learning) na Wikipedii.
