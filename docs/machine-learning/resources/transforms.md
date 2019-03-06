---
title: Strojové učení transformací dat - ML.NET
description: Prozkoumejte funkce engineering součásti, které jsou podporované v ML.NET.
author: JRAlexander
ms.custom: seodec18
ms.date: 01/14/2019
ms.openlocfilehash: e649c9a27f0409cb9cdfb554963b5c0e732991f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355403"
---
# <a name="machine-learning-data-transforms---mlnet"></a>Strojové učení transformací dat - ML.NET

Následující tabulky obsahují informace o všech transformace dat v ML.NET podporována.

> [!NOTE]
> ML.NET je aktuálně ve verzi Preview. Ne všechny transformace dat se aktuálně nepodporuje. Chcete-li odeslat žádost o určitých transformace, otevřete problém ve službě [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) úložiště GitHub.

## <a name="combiners-and-segregators"></a>Combiners a segregators

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | Skupiny hodnoty pro skalární sloupec jako vektor podle ID souvislých skupiny. |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | Zrušení skupiny vektorové sloupce do sekvence řádků, inverzní funkce k transformaci skupiny. |

## <a name="conversions"></a>Převody

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | Hodnoty hash jednotného Vážíme si toho sloupce nebo vektorové sloupce. Pro vektor sloupce vytvoří hodnotu hash každý slot samostatně. Můžete ho hash textové hodnoty nebo hodnoty klíče. |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | Převede více hodnot sloupců do hodnoty hash. Tato transformace přijímá číselné a textové vstupů, jednu i s hodnotou vektoru sloupce. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | Převede klíč na sloupec binární vektoru. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | Využívá KeyValues metadat pro mapování klíčů indexů na odpovídající hodnoty v metadatech KeyValues. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | Převede klíč na sloupec vektoru. |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | Změny základní typ sloupce za předpokladu, že typ lze převést. |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | Převede vstupní hodnoty (slova, čísla, atd.) do indexu ve slovníku. |

## <a name="deep-learning"></a>Obsáhlý learning

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Poskytuje data do existujícího modelu ONNX a vrátí skóre (předpověď). |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Můžete buď skóre, které je předem vytrénované TensorFlow modelu nebo programovém přeučení modelů TensorFlow. |

## <a name="feature-extraction"></a>Extrakce funkce

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | Odebere zadaný seznam stop slov porovnání jednotlivých tokenů (porovnání velká a malá písmena) stopwords.|
| <xref:Microsoft.ML.ImageAnalytics.ImageGrayscaleTransform> | Přijímá jeden nebo více sloupců ImageType a převede je na stupně šedé reprezentace stejnou bitovou kopii.|
| <xref:Microsoft.ML.ImageAnalytics.ImageLoaderTransform> | Vezme jeden nebo více sloupců ReadOnlyMemory a načte jako ImageType. |
| <xref:Microsoft.ML.ImageAnalytics.ImagePixelExtractorTransform> | Přijímá jeden nebo více sloupců ImageType a převede je na reprezentaci vektoru.|
| <xref:Microsoft.ML.ImageAnalytics.ImageResizerTransform> | Vezme jeden nebo více sloupců ImageType a přizpůsobí svou velikost je zadaná výšku a šířku.|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | Implementuje LightLDA stavu nejmodernější provádění latentní Dirichletův přidělení.|
| <xref:Microsoft.ML.Transforms.LoadTransform> | Načte konkrétní transformace ze souboru zadaného modelu. Umožňuje "vybírání" transformací z serializovaný řetězec nebo použití předem vytrénovaných transformace na zobrazení dat různých (ale stále kompatibilní). |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | Vytvoří kontejner počty ngrams (pořadí po sobě jdoucích hodnoty o délce 1-n) v dané vektor klíče. Dělá to tak vytváření slovník ngrams a jako index v kontejneru a s použitím id ve slovníku. |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | Změní sadu tokenizovaná text (vector ReadOnlyMemory) nebo vektorů klíčů vektory čísly. Funkce vektory jsou počty ngrams (pořadí po sobě jdoucích tokeny - slova nebo klíče - o délce 1-n). |
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | Zapne kolekci tokenizovaná textu (vector ReadOnlyMemory) do čísla vektory pomocí algoritmu hash. |
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | Vytvoří kontejner počty ngrams (posloupnosti po sobě jdoucích slov o délce 1-n) v daného textu. |
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | Převede hodnotu zařazené do kategorií na indikátor pole tak, že vytváření slovník kategorií na základě dat a s použitím id ve slovníku jako index v poli |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | Vypočítá projekce vektoru funkce na volné místo nízké hodnocení. |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | Používá model které je předem vytrénované mínění ke stanovení skóre vstupního řetězce. |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | Odstraní konkrétní jazyk seznam stop slov (Nejčastější slova) a porovnejte jednotlivé tokeny (porovnání velká a malá písmena) stopwords. |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | Vytvoří kontejner počty ngrams (posloupnosti po sobě jdoucích slov) v daného textu. Dělá to tak vytváření slovník ngrams a jako index v kontejneru a s použitím id ve slovníku. |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | Vytvoří kontejner počty ngrams (posloupnosti po sobě jdoucích slov o délce 1-n) v daného textu. Dělá to tak hashování každý ngram a používají hodnoty hash jako index v kontejneru a. |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | Rozdělí text na slova pomocí znaky oddělovače. |


## <a name="image-model-featurizers"></a>Obrázek modelu featurizers

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | Toto je metodu rozšíření, která se použije <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> aby bylo možné používat pretrained [AlexNet](https://en.wikipedia.org/wiki/AlexNet) modelu. NuGet, který obsahuje toto rozšíření také je zaručeno, že k binárnímu modelu soubor k zahrnutí. |
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | Toto je metodu rozšíření, která se použije <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> použití pretrained ResNet18 modelu. NuGet, který obsahuje toto rozšíření také je zaručeno, že k binárnímu modelu soubor k zahrnutí. |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | Toto je metodu rozšíření, která se použije <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> používat pretrained ResNet50model. NuGet, který obsahuje toto rozšíření také je zaručeno, že k binárnímu modelu soubor k zahrnutí. |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | Toto je metodu rozšíření, která se použije <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> použití pretrained ResNet101 modelu. NuGet, který obsahuje toto rozšíření také je zaručeno, že k binárnímu modelu soubor k zahrnutí. |

## <a name="label-parsing"></a>Popisek analýza kódu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  Převede popisky. |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | Změní víc tříd popisky na binární hodnotu True, False popisky, především pro použití s OVA.|

## <a name="missing-values"></a>Chybějící hodnoty

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | Zahodí, chybějící hodnoty ze sloupce. |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | Vytvoří logickou výstupního sloupce se stejný počet slotů jako vstupní sloupec, kde je výstupní hodnota true Pokud chybí hodnota ve vstupním sloupci. |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | Zpracování chybějící hodnoty tak, že nahradíte s výchozí hodnotu nebo hodnotu mean/min/max (netextovými pouze pro sloupce). |

## <a name="normalization"></a>Normalizace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | Transformace normalizace LP-Norm (vector/row-wise). |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | Vypočítá průměr a odchylky pro sloupec Vážíme si toho vektoru. Sleduje aktuální průměr a M2 (součet kvadratických rozdíly od střední hodnoty), počet hodnoty NaN a počet prvků nenulové. |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | Vypočítá průměr a odchylky pro sloupec Vážíme si toho vektoru. Sleduje aktuální průměr a M2 (součet kvadratických rozdíly od střední hodnoty), počet hodnoty NaN a počet prvků nenulové. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | Sleduje min, max, počet hodnot nezhuštěný (vCount) a počet volání ProcessValue() (trainCount) pro sloupec Vážíme si toho vektoru. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | Standardizuje funkce rozsahy. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |Standardizuje funkce rozsahy. |

## <a name="onnx"></a>Onnx

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Skóre, které se předem vytrénovaných modely ONNX využívající standardní v1.2 ONNX |

## <a name="preprocessing"></a>Předběžné zpracování
| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | Aproximuje bootstrap vzorkování pomocí vzorkování Poissonovo rozdělení. |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | Vytvoří náhodný Fourierova funkce. |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Znak objektově orientovaný tokenizátor, ve kterém se text je považován za posloupnost znaků. |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | Zjednodušuje optimalizace jako pomoc s identifikací váhy. |

## <a name="row-filters"></a>Filtry řádků

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | Podle okolí posouvá náhodnou kurzoru se pokusil provést pomocí fondu zadaný počet řádků.  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | Umožňuje omezit vstup na podmnožinu řádků přeskočením počet řádků. |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | Umožňuje omezení vstup na podmnožinu řádků volitelné posunem. Můžete použít k implementaci stránkování na data. Při vytvoření se SkipTakeFilter.SkipArguments chová jako `SkipFilter`.
| <xref:Microsoft.ML.Transforms.TakeFilter> | Umožňuje omezení vstup na podmnožinu řádků provedením prvních N řádků. |


## <a name="schema"></a>Schéma

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | Duplicitní sloupce z datové sady.|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | Vybere sadu sloupce, které chcete vyřadit nebo zabránit daný vstup. |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | Sloty Přetahované sloupce.|
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | Vytvoří nový sloupec se zadaným typem a výchozí hodnoty. |
| <xref:Microsoft.ML.Transforms.RangeFilter> | Filtry pro zobrazení dat na sloupce typu Single, Double nebo klíč (souvislé). Uchovává hodnoty, které jsou v rozsahu zadaného min/max. Hodnoty NaN vždy filtrují. Pokud je vstup typ klíče, min/max jsou považovány za procenta počet hodnot. |

## <a name="tensorflow"></a>TensorFlow

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Buď skóre, pomocí které je předem vytrénované TensorFlow model nebo retrains TensorFlow modelu. |

## <a name="text-processing-and-featurization"></a>Snadné a zpracování textu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | Normalizace transformace textu, který umožňuje normalizace písmen, odebírání diakritická znaménka, interpunkční znaménka a/nebo čísla. Transformací, která funguje na textové zadání, stejně jako vektor tokeny/text (vector ReadOnlyMemory). |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Znak objektově orientovaný tokenizátor, ve kterém se text je považován za posloupnost znaků. |

## <a name="time-series"></a>Časové řady

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesProcessing.ExponentialAverageTransform> | Přijímá vážený průměr hodnot: ExpAvg(y_t) = a * y_t + (1-a) * ExpAvg(y_(t-1)). |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidChangePointDetector> | Implementuje transformace detektor změnu bodu pro i.i.d. pořadí na základě odhadu hustota adaptivní jádra a martingales (náhodného vzorku). |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidSpikeDetector> | Implementuje detektor zásobníku transformovat i.i.d. pořadí podle hustoty odhad adaptivní jádra (náhodného vzorku). |
| <xref:Microsoft.ML.TimeSeriesProcessing.MovingAverageTransform> | Poskytuje vážený průměr hodnot posuvné okno. |
| <xref:Microsoft.ML.TimeSeriesProcessing.PercentileThresholdTransform> | Určuje, zda aktuální hodnota časové řady patří do posuvného okna nejvyšší hodnoty. percentilu. |
| <xref:Microsoft.ML.TimeSeriesProcessing.PValueTransform> | Vypočítá řady aktuální empirical p hodnoty na základě jiných hodnot v posuvné okno. |
| <xref:Microsoft.ML.TimeSeriesProcessing.SlidingWindowTransform> | Vypíše posuvné okno v časové řadě typu Single. |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaChangePointDetector> | Implementuje transformace detektor bodu změnit podle singulární spektra modelování časových řad. |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaSpikeDetector> | Implementuje detektor transformace (špičky) podle singulární spektra modelování časových řad. |

## <a name="miscellaneous"></a>Různé

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | Vytvoří složené DataTransform. |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | Generuje další sloupce do zadané `IDataView`. Nedojde ke změně počtu řádků a uvidíte v důsledku použití funkce uživatele pro každý řádek vstupní data.|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | Přidá sloupec s generované čísel pořadí. |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | Sloupec s ID bodu kurzoru vytváří jako sloupec. |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | Generuje náhodné číslo. |
