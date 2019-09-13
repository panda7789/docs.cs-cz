---
title: Glosář strojového učení
description: Glosář důležitých termínů strojového učení, které jsou užitečné při sestavování vlastních modelů v ML.NET.
ms.custom: seodec18
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: 4d4bb80c6582facbcb11664309fde230bcfa4e7b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929271"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Glosář strojového učení s důležitými podmínkami

Následující seznam je kompilace důležitých podmínek strojového učení, které jsou užitečné při sestavování vlastních modelů v ML.NET.

## <a name="accuracy"></a>údajů

V [klasifikaci](#classification)je přesnost počet správně klasifikovaných položek dělený celkovým počtem položek v sadě testů. Rozsahy od 0 (nejméně přesný) po 1 (nejpřesnější). Přesnost je jednou ze zkušebních metrik výkonu modelu. Zvažte, jestli je ve spojení s [přesností](#precision), [odvoláním](#recall)a [F-skore](#f-score).

## <a name="area-under-the-curve-auc"></a>Oblast pod křivkou (AUC)

V [binární klasifikaci](#binary-classification)je vyhodnocena metrika, která je hodnotou oblasti pod křivkou, která vykreslí skutečnou kladovou sazbu (na ose y) proti falešně pozitivním sazbám (na ose x). Rozsahy od 0,5 (nejhorší) po 1 (nejlepší). Označuje se také jako oblast pod křivkou ROC, tj. křivka s provozní charakteristikou přijímače. Další informace najdete v článku věnovaném [provozním charakteristikám přijímače](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) na Wikipedii.

## <a name="binary-classification"></a>Binární klasifikace

Případ [klasifikace](#classification) , kde [popisek](#label) je pouze jeden ze dvou tříd. Další informace najdete v části [binární klasifikace](tasks.md#binary-classification) v tématu [úlohy strojového učení](tasks.md) .

## <a name="calibration"></a>Kalibrac

Kalibrace je proces mapování nezpracovaného skóre na členství ve třídě pro binární a více třídové klasifikace. Některé ml.NET školitele mají `NonCalibrated` příponu. Tyto algoritmy vytvoří nezpracované skóre, které pak musí být namapovány na pravděpodobnost třídy. 

## <a name="catalog"></a>Katalog 

Katalog je v ML.NET kolekce funkcí rozšíření, které se seskupují podle společného účelu.

Každý úkol strojového učení (binární klasifikace, regrese, řazení atd.) má například katalog dostupných algoritmů strojového učení (školitele). Katalog školitele binární klasifikace je: <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>.

## <a name="classification"></a>Klasifikace

Když se data použijí pro předpověď kategorie, je [pod dohledem úlohy strojového učení](#supervised-machine-learning) označována jako klasifikace. [Binární klasifikace](#binary-classification) odkazuje na předpověď pouze dvou kategorií (například klasifikaci obrázku jako obrázku "Cat" nebo "pes"). [Klasifikace s více třídami](#multiclass-classification) odkazuje na předpověď více kategorií (například při klasifikaci obrázku jako obrázku konkrétního druhu pes).

## <a name="coefficient-of-determination"></a>Koeficient určení

V [regresi](#regression)je vyhodnocena metrika, která indikuje, jak dobře data vyhovují modelu. Rozsah od 0 do 1. Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu. Hodnota 1 znamená, že model přesně odpovídá datům. To se často označuje jako r<sup>2</sup>, r<sup>2</sup>nebo r-Saurashtra.

## <a name="data"></a>Data

Data jsou centrálně k libovolné aplikaci strojového učení. V ml.NET data jsou reprezentována <xref:Microsoft.ML.IDataView> objekty. Objekty zobrazení dat:

- jsou tvořeny sloupci a řádky
- jsou vyhodnoceny jako laxně vytvářená, které načítají data pouze při volání operace.
- obsahuje schéma definující typ, formát a délku každého sloupce.

## <a name="estimator"></a>Estimator

Třída v ml.NET, která implementuje <xref:Microsoft.ML.IEstimator%601> rozhraní.

Estimator je specifikace transformace (transformace přípravy dat i převod výuky modelů strojového učení). Odhady se dají zřetězit dohromady do kanálu transformací. Parametry Estimator nebo kanálu odhady se označují při <xref:Microsoft.ML.IEstimator`1.Fit*> volání metody. Výsledkem <xref:Microsoft.ML.IEstimator`1.Fit*> je [transformátor](#transformer).

## <a name="extension-method"></a>Metoda rozšíření

Metoda .NET, která je součástí třídy, ale je definována mimo třídu. První parametr metody rozšíření je statický `this` odkaz na třídu, do které patří rozšiřující metoda.

Metody rozšíření jsou v ML.NET používány rozsáhle k vytváření instancí [odhady](#estimator).

## <a name="feature"></a>Funkce

Měřitelná vlastnost neměřeného jevu, obvykle číselná (dvojitá) hodnota. Více funkcí je označováno jako **vektor funkce** a obvykle je uloženo jako `double[]`. Funkce definují důležité charakteristiky pro měřený jev. Další informace najdete v článku [funkce](https://en.wikipedia.org/wiki/Feature_(machine_learning)) na Wikipedii.

## <a name="feature-engineering"></a>Návrh funkcí

Inženýr funkcí je proces, který zahrnuje definování sady [funkcí](#feature) a vývoj softwaru, který vytváří vektory funkcí z dostupných dat pro jev, tj. extrakce funkcí. Další informace najdete v článku věnovaném [inženýrům funkcí](https://en.wikipedia.org/wiki/Feature_engineering) na Wikipedii.

## <a name="f-score"></a>Skóre F

V [klasifikaci](#classification)je metrika vyhodnocení, která vyvažuje [přesnost](#precision) a [odvolání](#recall).

## <a name="hyperparameter"></a>Parametr

Parametr algoritmu strojového učení. Příklady zahrnují počet stromů, které se naučí v doménové struktuře rozhodnutí nebo velikost kroku v algoritmu prostupného přechodu. Hodnoty *parametrů* jsou nastaveny před školením modelu a řízení procesu hledání parametrů funkce předpovědi, například porovnávacích bodů v rozhodovacím stromu nebo závaží v modelu lineární regrese. Další informace najdete [v článku na](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) Wikipedii.

## <a name="label"></a>Popisek

Prvek, který má být předpovězen modelu Machine Learning. Například druh psa nebo budoucí cena za zásobu.

## <a name="log-loss"></a>Protokolovat ztráty

V [klasifikaci](#classification)je vyhodnocena metrika, která charakterizuje přesnost třídění. Menší ztráta protokolu je přesnější klasifikátor.

## <a name="loss-function"></a>Funkce ztráty

Funkce ztráty je rozdíl mezi hodnotami školicích popisků a předpovědi provedenou modelem. Parametry modelu jsou odhadované minimalizací funkce ztráty.

U různých školitelů se dá nakonfigurovat jiné funkce ztráty.

## <a name="mean-absolute-error-mae"></a>Střední absolutní chyba (MAE)

V [regresi](#regression)vyhodnocuje metrika, která je průměrem všech chyb modelů, kde chyba modelu je vzdálenost mezi předpovězenou hodnotou [popisku](#label) a správnou hodnotou popisku.

## <a name="model"></a>Model

Tradičně parametry pro funkci předpovědi. Například váhy v modelu lineární regrese nebo v místech rozdělení v rozhodovacím stromu. V ML.NET model obsahuje všechny informace potřebné pro předpověď [popisku](#label) doménového objektu (například obrázku nebo textu). To znamená, že modely ML.NET zahrnují potřebné kroky featurization a také parametry pro funkci předpovědi.

## <a name="multiclass-classification"></a>Klasifikace s více třídami

Případ [klasifikace](#classification) , kde [popisek](#label) představuje jednu ze tří nebo více tříd. Další informace najdete v části [klasifikace více tříd](tasks.md#multiclass-classification) v tématu [úlohy strojového učení](tasks.md) .

## <a name="n-gram"></a>N-gram

Schéma extrakce funkce pro textová data: jakákoli sekvence N slov přepíná na hodnotu [funkce](#feature) .

## <a name="normalization"></a>Normalizace

Normalizace je proces škálování dat s plovoucí desetinnou čárkou na hodnoty mezi 0 a 1. Mnohé z školicích algoritmů používaných v ML.NET vyžadují, aby byla vstupní data funkce normalizovaná. ML.NET poskytuje řadu [transformací pro normalizaci](transforms.md#normalization-and-scaling) .

## <a name="numerical-feature-vector"></a>Vektor číselné funkce

Vektor [funkce](#feature) skládající se pouze z číselných hodnot. To je podobné `double[]`.

## <a name="pipeline"></a>Kanál

Všechny operace potřebné k přizpůsobení modelu datové sadě. Kanál se skládá z kroků importu, transformace, featurization a učení dat. Jakmile je kanál vyškolen, změní se na model.

## <a name="precision"></a>Přesnost

V [klasifikaci](#classification), přesnost pro třídu je počet položek, které byly správně předpovězeny, jako patřící do této třídy dělené celkovým počtem položek, které byly předpovězeny jako patřící do třídy.

## <a name="recall"></a>Svolat

V [klasifikaci](#classification)je odvolání pro třídu počet položek, které byly správně předpovězeny, jako patřící do této třídy, dělený celkovým počtem položek, které skutečně patří do třídy.

## <a name="regularization"></a>Regularizace

 Pravidelný postih je lineárním modelem, který je příliš složitý. Existují dva typy pravidelnosti:

- $L _1 $ regularing pro nevýznamné funkce vynulová váhy. Velikost uloženého modelu může být po tomto typu depravidelnosti menší.
- Pravidelná na$L _2 $ minimalizuje rozsah váhy pro nevýznamné funkce, jedná se o obecnější proces a méně citlivá na odlehlé hodnoty.

## <a name="regression"></a>Regrese

Úkol [strojového učení pod dohledem](#supervised-machine-learning) , kde výstup je skutečná hodnota, například Double. Mezi příklady patří předpověď cen akcií. Další informace najdete v části [regrese](tasks.md#regression) v tématu [úlohy strojového učení](tasks.md) .

## <a name="relative-absolute-error"></a>Relativní absolutní chyba

V [regresi](#regression)je vyhodnocena metrika, která představuje součet všech absolutních chyb dělený součtem vzdálenosti mezi správnými hodnotami [popisku](#label) a průměrem všech správných hodnot popisku.

## <a name="relative-squared-error"></a>Relativní čtvercová chyba

V [regresi](#regression)je vyhodnocena metrika, která je součtem všech kvadratických absolutních chyb dělený součtem čtvercových vzdáleností mezi správnými hodnotami [popisku](#label) a průměrem všech správných hodnot popisku.

## <a name="root-of-mean-squared-error-rmse"></a>Kořen průměrného čtverce chyby (RMSE)

V [regresi](#regression)vyhodnocuje metrika, která je druhou odmocninou průměru čtverců chyb.

## <a name="scoring"></a>Vzorec

Bodování je proces použití nových dat na školený model strojového učení a generování předpovědi. Bodování se také označuje jako Inferencing. V závislosti na typu modelu může být skóre neupravená hodnota, pravděpodobnost nebo kategorie.

## <a name="supervised-machine-learning"></a>Pod dohledem strojového učení

Podtřída strojového učení, ve které požadovaný model předpovídá popisek pro dosud nepřesná data. Mezi příklady patří klasifikace, regrese a strukturovaná předpověď. Další informace najdete v článku věnovaném [učení](https://en.wikipedia.org/wiki/Supervised_learning) na Wikipedii.

## <a name="training"></a>Školení

Proces identifikace [modelu](#model) pro danou sadu dat školení. Pro lineární model to znamená hledání vah. Ve stromové struktuře zahrnuje identifikaci rozdělení bodů.

## <a name="transformer"></a>Transformer

Třída ml.NET, která implementuje <xref:Microsoft.ML.ITransformer> rozhraní.

Transformátor transformuje jeden <xref:Microsoft.ML.IDataView> do jiného. Transformátor se vytvoří prostřednictvím školení [Estimator](#estimator)nebo kanálu Estimator. 

## <a name="unsupervised-machine-learning"></a>Strojové učení bez dohledu

Podtřídou strojového učení, ve kterém požadovaný model najde skrytou (nebo latentní) strukturu v datech. Mezi příklady patří clustering, modelování témat a snížení rozměru. Další informace najdete v článku o [výukovém kurzu, který není pod dohledem](https://en.wikipedia.org/wiki/Unsupervised_learning) na Wikipedii.
