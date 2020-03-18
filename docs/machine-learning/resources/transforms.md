---
title: Transformace dat
description: Prozkoumejte součásti technické funkce podporované v ML.NET.
ms.date: 04/02/2019
ms.openlocfilehash: ca410b475c556db5ad4c3862fb79755b455d6830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398921"
---
# <a name="data-transformations"></a>Transformace dat

Transformace dat se používají k:

- připravit data pro modelové školení
- použití importovaného modelu ve formátu TensorFlow nebo ONNX
- údaje po zpracování poté, co byly předány modelem

Transformace v této příručce vrátit třídy, které implementují rozhraní [IEstimator.](xref:Microsoft.ML.IEstimator%601) Transformace dat lze zřetězit dohromady. Každá transformace očekává a vytváří data konkrétních typů a formátů, které jsou určeny v propojené referenční dokumentaci.

Některé transformace dat vyžadují trénovací data k výpočtu jejich parametrů. Například: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformátor vypočítá střední a rozptyl trénovacích dat během `Fit()` operace a `Transform()` použije tyto parametry v operaci.

Jiné transformace dat nevyžadují trénovací data. Například: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> transformace může `Transform()` provést operaci bez zobrazení dat `Fit()` školení během operace.

## <a name="column-mapping-and-grouping"></a>Mapování a seskupování sloupců

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Zřetězit jeden nebo více vstupních sloupců do nového výstupního sloupce |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Kopírování a přejmenování jednoho nebo více vstupních sloupců |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Přetažení jednoho nebo více vstupních sloupců |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Výběr jednoho nebo více sloupců, které chcete zachovat ze vstupních dat |

## <a name="normalization-and-scaling"></a>Normalizace a škálování

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Odečtěte průměr (tréninkových dat) a vydělte rozptylem (tréninkových dat) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normalizovat na základě logaritmu trénovacích dat |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Měřítko vstupních vektorů podle jejich [lp-normy](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), kde p je 1, 2 nebo nekonečno. Výchozí hodnota normy l2 (Euclidean distance) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Měřítko každé hodnoty v řádku odečtením střední hodnoty řádku dat a vydělit buď směrodatnou odchylkou nebo l2-normou (dat řádku) a vynásobit konfigurovatelným faktorem měřítka (výchozí 2) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Přiřaďte vstupní hodnotu k indexu přihrádky a vydělíte počtem přihrádek, abyste vytvořili plovoucí hodnotu mezi 0 a 1. Hranice přihrádky jsou vypočteny tak, aby rovnoměrně distribuovaly trénovací data mezi přihrádky. |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Přiřazení vstupní hodnoty k přihrádce na základě její korelace se sloupcem popisku |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Měřítko vstupu o rozdíl mezi minimální a maximální hodnotou v trénovacích datech |

## <a name="conversions-between-data-types"></a>Převody mezi datovými typy

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Převedení typu vstupního sloupce na nový typ |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue%2A> | Mapování hodnot na klíče (kategorie) na základě dodaného slovníku mapování |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> | Mapování hodnot na klíče (kategorie) vytvořením mapování ze vstupních dat |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A> | Převedení klíčů zpět na původní hodnoty |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector%2A> | Převést klíče zpět na vektory původních hodnot |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector%2A> | Převést klíče zpět na binární vektor původních hodnot |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A> | Hash hodnota ve vstupním sloupci |

## <a name="text-transformations"></a>Transformace textu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText%2A> | Transformace textového sloupce na plovoucí pole normalizovaných ngramů a počtu znakových gramů |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A> | Rozdělení jednoho nebo více sloupců textu na jednotlivá slova |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys%2A> | Rozdělení jednoho nebo více sloupců textu na jednotlivé znaky plovoucí přes sadu témat |
| <xref:Microsoft.ML.TextCatalog.NormalizeText%2A> | Změna případu, odstranění diakritických znamének, interpunkčních znamének a čísel |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams%2A> | Transformace textového sloupce na sáček s počty ngramů (sekvence po sobě jdoucích slov)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags%2A> | Transformace textového sloupce na sáček s počty ngramů vektoru |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams%2A> | Transformace textového sloupce na vektor počty zahasgovaných ngramů |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags%2A> | Transformace textového sloupce na sáček s počty zahashovaných ngramů |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords%2A>  | Odebrání výchozích stop slov pro zadaný jazyk ze vstupních sloupců |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords%2A> | Odebere zadaná slova stop ze vstupních sloupců. |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation%2A> | Transformace dokumentu (reprezentovaného jako vektor plováků) na vektor plováků nad sadou témat |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding%2A> | Převod vektorů textových tokenů na vektory vět pomocí předem trénovaného modelu |

## <a name="image-transformations"></a>Transformace obrazu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> | Převedení obrazu na stupně šedi |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage%2A> | Převedení vektoru obrazových bodů na<xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A> | Převod obrazových bodů ze vstupního obrazu na vektor čísel |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A> | Načtení obrázků ze složky do paměti |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A> | Změna velikosti obrazů |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage%2A> | Použije předem trénovaný model hluboké neuronové sítě (DNN) k transformaci vstupního obrazu na vektor funkce. |

## <a name="categorical-data-transformations"></a>Kategorické transformace dat

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A> | Převod jednoho nebo více sloupců textu na [jednohorké](https://en.wikipedia.org/wiki/One-hot) kódované vektory |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding%2A> | Převedení jednoho nebo více sloupců textu na jednohorké kódované vektory založené na hash |

## <a name="time-series-data-transformations"></a>Transformace dat časových řad

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn%2A> | Detekce anomálií ve vstupních datech časových řad pomocí algoritmu Spektrální zbytkové (SR) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa%2A> | Detekce bodů změny v datech časových řad pomocí jednotné analýzy spektra (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint%2A> | Detekujte body změn v nezávislých a identicky distribuovaných (IID) datech časových řad pomocí adaptivních odhadů hustoty jádra a skóre martingale |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa%2A> | Data časových řad prognózy pomocí jednotné analýzy spektra (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa%2A> | Detekce špičky v datech časových řad pomocí jednotné analýzy spektra (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike%2A> | Detekujte špičky v nezávislých a identicky distribuovaných (IID) datech časových řad pomocí adaptivních odhadů hustoty jádra a skóre martingale |

## <a name="missing-values"></a>Chybějící hodnoty

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues%2A> | Vytvoření nového logického výstupního sloupce, jehož hodnota je true, pokud chybí hodnota ve vstupním sloupci |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A> | Vytvořte nový výstupní sloupec, jehož hodnota je nastavena na výchozí hodnotu, pokud ve vstupním sloupci chybí hodnota, a jinak vstupní hodnota |

## <a name="feature-selection"></a>Výběr funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount%2A> | Výběr funkcí, jejichž jiné než výchozí hodnoty jsou větší než prahová hodnota |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation%2A> | Vyberte funkce, na kterých jsou data ve sloupci popisku nejvíce závislá. |

## <a name="feature-transformations"></a>Transformace funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap%2A> | Namapujte každý vstupní vektor na prostor s nižšími rozměrovými funkcemi, kde se vnitřní produkty blíží funkci jádra, takže prvky mohou být použity jako vstupy k lineárním algoritmům |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents%2A> | Zmenšení rozměrů vektoru vstupních prvků použitím algoritmu Analýza hlavní součásti |

## <a name="explainability-transformations"></a>Vysvětlitelnost transformace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution%2A> | Výpočet skóre příspěvku pro každý prvek vektoru prvku |

## <a name="calibration-transformations"></a>Transformace kalibrace

| Transformace | Definice |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Transformuje binární třídění nezpracované skóre do pravděpodobnosti třídy pomocí logistické regrese s parametry odhadovanými pomocí trénovacích dat. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Transformuje binární třídění nezpracované skóre do třídy pravděpodobnost pomocí logistické regrese s pevnými parametry |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive%2A> | Transformuje nezpracované skóre binárního klasifikátoru na pravděpodobnost třídy přiřazením skóre do přihrádek a výpočtem pravděpodobnosti založené na rozdělení mezi přihrádky. |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic%2A> | Transformuje nezpracované skóre binárního klasifikátoru na pravděpodobnost třídy přiřazením skóre do přihrádek, kde se odhaduje umístění hranic a velikost přihrádek pomocí trénovacích dat.  |

## <a name="deep-learning-transformations"></a>Transformace hlubokého učení

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A> | Transformace vstupních dat s importovaným modelem ONNX |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel%2A> | Transformace vstupních dat s importovaným modelem TensorFlow |

## <a name="custom-transformations"></a>Vlastní transformace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping%2A> | Transformace existujících sloupců na nové pomocí uživatelem definovaného mapování |
