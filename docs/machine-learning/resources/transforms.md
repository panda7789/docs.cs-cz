---
title: Transformace dat
description: Prozkoumejte funkce engineering součásti, které jsou podporované v ML.NET.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 7ea06e19b4651017079a6ae57136f033e0ce981c
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65558017"
---
# <a name="data-transformations"></a>Transformace dat

Transformace dat slouží k přípravě dat pro trénování modelu. Transformace v této příručce vracejí třídy, které implementují [IEstimator](xref:Microsoft.ML.IEstimator%601) rozhraní. Transformace dat je možné zřetězit. Každá transformace očekává, že a vytvoří data konkrétní typy a formáty, které jsou určené v propojených referenční dokumentaci.

Některé transformace dat vyžadují trénovací data vypočítat své parametry. Příklad: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer vypočítá průměr a odchylky trénovacích dat během `Fit()` operace a používá tyto parametry v `Transform()` operace. 

Další transformací dat nevyžadují trénovací data. Příklad: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> můžete provádět transformaci `Transform()` operaci bez nutnosti vidět všechny trénovacích dat během `Fit()` operace.

## <a name="column-mapping-and-grouping"></a>Mapování sloupců a seskupování

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Zřetězit nejmíň jeden vstupní sloupce do nového sloupce výstupu |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Zkopírujte a přejmenujte nejmíň jeden vstupní sloupce |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Vyřadit nejmíň jeden vstupní sloupce |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Vyberte jeden nebo více sloupců, aby ze vstupních dat |

## <a name="normalization-and-scaling"></a>Normalizace a škálování

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Odečte střední (trénovacích dat) a dělit odchylku (trénovacích dat) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normalizovat podle logaritmus trénovacích dat |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Škálování vstupním Vektorům podle jejich [lp norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), kde p je 1, 2 nebo nekonečno. Výchozí hodnota je norm (Euclidean vzdálenost) l2 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Škálování každé hodnoty v řádku tak, že se střední řádek dat a dělení podle buď směrodatnou odchylku nebo l2 – normály (řádek dat) a vynásobit konfigurovatelné měřítko (výchozí 2) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Vstupní hodnota přiřadit bin index a dělit počet intervalů k vytvoření hodnoty typu float mezi 0 a 1. Hranice bin se počítají a trénovací data rovnoměrně distribuuje mezi přihrádky |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Vstupní hodnota přiřadit přihrádky podle jeho korelace s popisek sloupce |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Rozdíl mezi minimální a maximální hodnoty v trénovacích dat můžete škálovat vstupu |

## <a name="conversions-between-data-types"></a>Převody mezi datovými typy

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Typ vstupní sloupec převést na nový typ |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | Mapování hodnot klíče (kategorie) podle zadaného slovníku mapování |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | Mapování hodnot na klíče (kategorie) tak, že vytvoříte mapování ze vstupních dat |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | Převést zpět na původní hodnoty klíče |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | Převést zpět na původní hodnoty vektory klíče |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | Převést zpět na binární vektor původní hodnoty klíče |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | Hodnota hash hodnotu ve vstupním sloupci |

## <a name="text-transformations"></a>Transformace textu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | Transformovat sloupec text do pole typu float normalizované ngrams a počty char g | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | Rozdělit jeden nebo více textové sloupce na jednotlivá slova |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | Rozdělit jeden nebo více textové sloupce na float jednotlivých znaků v rámci sady témata |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | Změnit velikost písmen, odeberte diakritická znaménka, interpunkční znaménka a čísla |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | Transformovat textový sloupec na kontejner počty ngrams (posloupnosti po sobě jdoucích slov)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | Kontejner počty ngrams vektor transformován textového sloupce |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | Transformovat textový sloupec jako vektor hashované ngram počty |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | Transformace textu sloupce do kontejneru objektů a dat hash ngram součtů |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | Odebrání výchozí nevýznamová slova pro určený jazyk vstupní sloupce |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | Odebere zadané nevýznamová slova ze vstupní sloupce |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | Transformace dokumentů (reprezentovány jako vektor hodnot float) jako vektor hodnot float v rámci sady témata |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | Převést vektory větu pomocí předem vytrénovaných modelu vektory text tokenů |

## <a name="image-transformations"></a>Obrázek transformace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | Převedení obrázku na stupně šedé |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | Převést Vektor obrazových bodů <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | Převést na pixelech ze vstupního obrázku vektor čísel |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | Načíst obrázky ze složky do paměti |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | Změna velikosti obrázků |

## <a name="categorical-data-transformations"></a>Transformace data zařazená do kategorií

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | Převést do jednoho nebo více sloupců text [horkou jeden](https://en.wikipedia.org/wiki/One-hot) kódovaný vektorů |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | Převést jeden další textové sloupce na základě algoritmu hash horkou jeden kódovaného vektorů |

## <a name="missing-values"></a>Chybějící hodnoty

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | Vytvoří nový sloupec logický výstup, jehož hodnota je true, při chybí hodnota v sloupci vstupní |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | Vytvoří nový sloupec výstup, jehož hodnota nastavena na výchozí hodnotu, pokud je hodnota chybí vstupní sloupec a vstupní hodnota jinak |

## <a name="feature-selection"></a>Výběr funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | Zvolte funkce, jejichž jiné než výchozí hodnoty jsou větší než prahová hodnota |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | Vyberte funkce, v nichž je největší závislé data ve sloupci popisek |

## <a name="custom-transformations"></a>Vlastní transformace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | Transformace existujících sloupců do nových pomocí uživatelem definované mapování |
