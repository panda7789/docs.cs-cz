---
title: Transformace dat
description: Prozkoumejte komponenty pro inženýry funkcí podporované v ML.NET.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: cb191b1688dce8f703bdabcd220eb39efe68fd48
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977237"
---
# <a name="data-transformations"></a>Transformace dat

Transformace dat slouží k těmto akcím:

- Příprava dat pro školení modelů
- použití importovaného modelu ve formátu TensorFlow nebo ONNX
- data po zpracování poté, co byla předána pomocí modelu

Transformace v této příručce vracejí třídy, které implementují rozhraní [IEstimator](xref:Microsoft.ML.IEstimator%601) . Transformace dat se dají zřetězit dohromady. Každá transformace očekává a vytvoří data specifických typů a formátů, které jsou zadány v referenční dokumentaci s odkazem.

Některé transformace dat vyžadují k výpočtu jejich parametrů školicí data. Například: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformátor vypočítá průměr a rozptyl školicích dat během operace `Fit()` a použije tyto parametry v operaci `Transform()`.

Další transformace dat nevyžadují školicí data. Například: transformace <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> může provést operaci `Transform()`, aniž by během operace `Fit()` viděli žádná školicí data.

## <a name="column-mapping-and-grouping"></a>Mapování sloupců a seskupení

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Zřetězí jeden nebo více vstupních sloupců do nového výstupního sloupce. |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Zkopírování a přejmenování jednoho nebo více vstupních sloupců |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Odstranit jeden nebo více vstupních sloupců |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Vyberte jeden nebo více sloupců, které chcete zachovat ze vstupních dat. |

## <a name="normalization-and-scaling"></a>Normalizace a škálování

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Odečte střední hodnotu (ze školicích dat) a vydělí odchylku (data školení). |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normalizovat podle logaritmu dat školení |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Škálujte vstupní vektory podle jejich hodnoty [LP-norma](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), kde p je 1, 2 nebo nekonečno. Výchozí hodnota pro normu L2 (Euclidean distance) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Škálujte každou hodnotu v řádku odečtením střední hodnoty řádkových dat a rozdělte je směrodatnou odchylkou nebo L2-normou (data řádku) a vynásobte je konfigurovatelnou hodnotou měřítka (výchozí 2). |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Přiřaďte vstupní hodnotu k indexu přihrádky a rozdělte je počtem přihrádek, aby se vytvořila hodnota typu float mezi 0 a 1. Hranice přihrádky jsou vypočítány tak, aby rovnoměrně rozdělují školicí data napříč přihrádkami. |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Přiřazení vstupní hodnoty k přihrádce na základě korelace se sloupcem popisek |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Škálování vstupu na rozdíl mezi minimální a maximální hodnotou v školicích datech |

## <a name="conversions-between-data-types"></a>Převody mezi datovými typy

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Převést typ vstupního sloupce na nový typ |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | Mapování hodnot na klíče (kategorie) na základě zadaného slovníku mapování |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | Mapování hodnot na klíče (kategorie) vytvořením mapování ze vstupních dat |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | Převést klíče zpátky na původní hodnoty |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | Převést klíče zpět na vektory původních hodnot |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | Převod klíčů zpět na binární vektor původních hodnot |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | Hodnota hash hodnoty ve sloupci Input |

## <a name="text-transformations"></a>Transformace textu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | Transformace textového sloupce na pole typu float normalizovaných ngrams a počtu znaků-gramů |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | Rozdělení jednoho nebo více textových sloupců na jednotlivá slova |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | Rozdělení jednoho nebo více textových sloupců na jednotlivé znaky Floaty přes sadu témat |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | Změnit velikost písmen, odebrat diakritická znaménka, interpunkční znaménka a číslice |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | Transformovat textový sloupec na penaltu počtů ngrams (posloupnosti po sobě jdoucích slov)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | Transformovat textový sloupec do kontejneru počtů ngrams Vector |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | Transformovat text do vektoru ngram počtů hash |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | Transformovat textový sloupec do kontejneru ngram počtů hash |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | Odebrat výchozí slova stop pro zadaný jazyk ze vstupních sloupců |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | Odstraní zadaná slova stop ze vstupních sloupců. |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | Transformace dokumentu (reprezentovaného jako vektorové Floaty) na vektory Floaty přes sadu témat |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | Převod vektorů textových tokenů na vektory vět pomocí předem připraveného modelu |

## <a name="image-transformations"></a>Transformace obrázků

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | Převést obrázek na stupně šedi |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | Převod vektoru pixelů na <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | Převést pixely ze vstupní image na vektor čísel |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | Načtení imagí ze složky do paměti |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | Změna velikosti obrázků |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage*> | Použije předem vyškolený model DNN (neuronové Network) pro transformaci vstupní image na vektor funkce. |

## <a name="categorical-data-transformations"></a>Transformace dat kategorií

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | Převod jednoho nebo více textových sloupců na [jeden aktivní](https://en.wikipedia.org/wiki/One-hot) kódovaný vektor |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | Převod jednoho nebo více textových sloupců na aktivní kódované vektory založené na algoritmu hash |

## <a name="time-series-data-transformations"></a>Transformace dat časové řady

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn*> | Zjištění anomálií v datech vstupních časových řad pomocí algoritmu spektrálního zbytku (SR) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa*> | Zjištění bodů změn v datech časových řad pomocí analýzy pro jednotné spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint*> | Zjištění bodů změny v nezávislá a rovnoměrně distribuovaných datech (IID) časových řad pomocí adaptivního odhadu hustoty jádra a hodnocení Martingale |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*> | Prognózování dat časových řad pomocí analýzy pro jednotné spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa*> | Detekce špiček v datech časových řad pomocí analýzy pro jednotné spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike*> | Zjišťovat špičky v nezávislá a rovnoměrně distribuovaných datech (IID) časových řad pomocí adaptivního odhadu hustoty jádra a Martingale skóre |

## <a name="missing-values"></a>Chybějící hodnoty

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | Vytvoří nový logický výstupní sloupec, jehož hodnota je true, pokud chybí hodnota ve vstupním sloupci. |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | Vytvoří nový výstupní sloupec, hodnota, která je nastavená na výchozí hodnotu, pokud hodnota ve vstupním sloupci chybí, a vstupní hodnota jinak. |

## <a name="feature-selection"></a>Výběr funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | Vyberte funkce, jejichž jiné než výchozí hodnoty jsou větší než prahová hodnota. |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | Vyberte funkce, na kterých jsou data ve sloupci popisek nejvíce závislá. |

## <a name="feature-transformations"></a>Transformace funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap*> | Namapujte jednotlivé vstupní vektory na méně dimenzionální prostor funkcí, kde vnitřní produkty přibližně vyhodnotí funkci jádra, aby se funkce mohly používat jako vstupy lineárních algoritmů. |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents*> | Zmenšení rozměrů vektoru vstupní funkce použitím algoritmu analýzy hlavní součásti |

## <a name="explainability-transformations"></a>Transformace pro vysvětlení

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution*> | Vypočítat skóre příspěvků pro každý prvek vektoru funkce |

## <a name="calibration-transformations"></a>Transformace kalibrací

| Transformace | Definice |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Transformuje nezpracované skóre v binárním třídění na pravděpodobnost třídy pomocí logistické regrese s parametry odhadovanými pomocí školicích dat. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Transformuje binární skóre nezpracovaného třídění na pravděpodobnost třídy pomocí logistické regrese s pevnými parametry. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive*> | Umožňuje transformovat nezpracované skóre binárního třídění na pravděpodobnost třídy přiřazením skóre k přihrádkám a výpočtem pravděpodobnosti na základě distribuce mezi přihrádkami. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic*> | Transformuje binární skóre nezpracovaného třídění na pravděpodobnost třídy přiřazením skóre k přihrádkám, kde je pozice hranic a velikost přihrádek odhadované pomocí školicích dat.  |

## <a name="deep-learning-transformations"></a>Transformace hloubkového učení

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*> | Transformace vstupních dat pomocí importovaného modelu ONNX |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel*> | Transformace vstupních dat pomocí importovaného modelu TensorFlow |

## <a name="custom-transformations"></a>Vlastní transformace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | Transformovat existující sloupce na nové s uživatelem definovaným mapováním |
