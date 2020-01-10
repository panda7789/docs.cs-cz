---
title: Transformace dat
description: Prozkoumejte komponenty pro inženýry funkcí podporované v ML.NET.
ms.date: 04/02/2019
ms.openlocfilehash: ca410b475c556db5ad4c3862fb79755b455d6830
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739586"
---
# <a name="data-transformations"></a>Transformace dat

Transformace dat slouží k těmto akcím:

- Příprava dat pro školení modelů
- použití importovaného modelu ve formátu TensorFlow nebo ONNX
- data po zpracování poté, co byla předána pomocí modelu

Transformace v této příručce vracejí třídy, které implementují rozhraní [IEstimator](xref:Microsoft.ML.IEstimator%601) . Transformace dat se dají zřetězit dohromady. Každá transformace očekává a vytvoří data specifických typů a formátů, které jsou zadány v referenční dokumentaci s odkazem.

Některé transformace dat vyžadují k výpočtu jejich parametrů školicí data. Například: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformátor vypočítá průměr a rozptyl školicích dat během operace `Fit()` a použije tyto parametry v operaci `Transform()`.

Další transformace dat nevyžadují školicí data. Například: transformace <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> může provést operaci `Transform()`, aniž by během operace `Fit()` viděli žádná školicí data.

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
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue%2A> | Mapování hodnot na klíče (kategorie) na základě zadaného slovníku mapování |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> | Mapování hodnot na klíče (kategorie) vytvořením mapování ze vstupních dat |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A> | Převést klíče zpátky na původní hodnoty |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector%2A> | Převést klíče zpět na vektory původních hodnot |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector%2A> | Převod klíčů zpět na binární vektor původních hodnot |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A> | Hodnota hash hodnoty ve sloupci Input |

## <a name="text-transformations"></a>Transformace textu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText%2A> | Transformace textového sloupce na pole typu float normalizovaných ngrams a počtu znaků-gramů |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A> | Rozdělení jednoho nebo více textových sloupců na jednotlivá slova |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys%2A> | Rozdělení jednoho nebo více textových sloupců na jednotlivé znaky Floaty přes sadu témat |
| <xref:Microsoft.ML.TextCatalog.NormalizeText%2A> | Změnit velikost písmen, odebrat diakritická znaménka, interpunkční znaménka a číslice |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams%2A> | Transformovat textový sloupec na penaltu počtů ngrams (posloupnosti po sobě jdoucích slov)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags%2A> | Transformovat textový sloupec do kontejneru počtů ngrams Vector |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams%2A> | Transformovat text do vektoru ngram počtů hash |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags%2A> | Transformovat textový sloupec do kontejneru ngram počtů hash |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords%2A>  | Odebrat výchozí slova stop pro zadaný jazyk ze vstupních sloupců |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords%2A> | Odstraní zadaná slova stop ze vstupních sloupců. |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation%2A> | Transformace dokumentu (reprezentovaného jako vektorové Floaty) na vektory Floaty přes sadu témat |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding%2A> | Převod vektorů textových tokenů na vektory vět pomocí předem připraveného modelu |

## <a name="image-transformations"></a>Transformace obrázků

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> | Převést obrázek na stupně šedi |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage%2A> | Převod vektoru pixelů na <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A> | Převést pixely ze vstupní image na vektor čísel |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A> | Načtení imagí ze složky do paměti |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A> | Změna velikosti obrázků |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage%2A> | Použije předem vyškolený model DNN (neuronové Network) pro transformaci vstupní image na vektor funkce. |

## <a name="categorical-data-transformations"></a>Transformace dat kategorií

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A> | Převod jednoho nebo více textových sloupců na [jeden aktivní](https://en.wikipedia.org/wiki/One-hot) kódovaný vektor |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding%2A> | Převod jednoho nebo více textových sloupců na aktivní kódované vektory založené na algoritmu hash |

## <a name="time-series-data-transformations"></a>Transformace dat časové řady

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn%2A> | Zjištění anomálií v datech vstupních časových řad pomocí algoritmu spektrálního zbytku (SR) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa%2A> | Zjištění bodů změn v datech časových řad pomocí analýzy pro jednotné spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint%2A> | Zjištění bodů změny v nezávislá a rovnoměrně distribuovaných datech (IID) časových řad pomocí adaptivního odhadu hustoty jádra a hodnocení Martingale |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa%2A> | Prognózování dat časových řad pomocí analýzy pro jednotné spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa%2A> | Detekce špiček v datech časových řad pomocí analýzy pro jednotné spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike%2A> | Zjišťovat špičky v nezávislá a rovnoměrně distribuovaných datech (IID) časových řad pomocí adaptivního odhadu hustoty jádra a Martingale skóre |

## <a name="missing-values"></a>Chybějící hodnoty

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues%2A> | Vytvoří nový logický výstupní sloupec, jehož hodnota je true, pokud chybí hodnota ve vstupním sloupci. |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A> | Vytvoří nový výstupní sloupec, hodnota, která je nastavená na výchozí hodnotu, pokud hodnota ve vstupním sloupci chybí, a vstupní hodnota jinak. |

## <a name="feature-selection"></a>Výběr součástí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount%2A> | Vyberte funkce, jejichž jiné než výchozí hodnoty jsou větší než prahová hodnota. |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation%2A> | Vyberte funkce, na kterých jsou data ve sloupci popisek nejvíce závislá. |

## <a name="feature-transformations"></a>Transformace funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap%2A> | Namapujte jednotlivé vstupní vektory na méně dimenzionální prostor funkcí, kde vnitřní produkty přibližně vyhodnotí funkci jádra, aby se funkce mohly používat jako vstupy lineárních algoritmů. |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents%2A> | Zmenšení rozměrů vektoru vstupní funkce použitím algoritmu analýzy hlavní součásti |

## <a name="explainability-transformations"></a>Transformace pro vysvětlení

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution%2A> | Vypočítat skóre příspěvků pro každý prvek vektoru funkce |

## <a name="calibration-transformations"></a>Transformace kalibrací

| Transformace | Definice |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Transformuje nezpracované skóre v binárním třídění na pravděpodobnost třídy pomocí logistické regrese s parametry odhadovanými pomocí školicích dat. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Transformuje binární skóre nezpracovaného třídění na pravděpodobnost třídy pomocí logistické regrese s pevnými parametry. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive%2A> | Umožňuje transformovat nezpracované skóre binárního třídění na pravděpodobnost třídy přiřazením skóre k přihrádkám a výpočtem pravděpodobnosti na základě distribuce mezi přihrádkami. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic%2A> | Transformuje binární skóre nezpracovaného třídění na pravděpodobnost třídy přiřazením skóre k přihrádkám, kde je pozice hranic a velikost přihrádek odhadované pomocí školicích dat.  |

## <a name="deep-learning-transformations"></a>Transformace hloubkového učení

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A> | Transformace vstupních dat pomocí importovaného modelu ONNX |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel%2A> | Transformace vstupních dat pomocí importovaného modelu TensorFlow |

## <a name="custom-transformations"></a>Vlastní transformace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping%2A> | Transformovat existující sloupce na nové s uživatelem definovaným mapováním |
