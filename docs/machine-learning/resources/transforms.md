---
title: Transformace dat
description: Prozkoumejte funkce engineering součásti, které jsou podporované v ML.NET.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: d3261f88a8e52c71f8ddf4d3d5c90b2e2b22b620
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636556"
---
# <a name="data-transformations"></a><span data-ttu-id="98435-103">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="98435-103">Data transformations</span></span>

<span data-ttu-id="98435-104">Transformace dat slouží k přípravě dat pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="98435-104">Data transformations are used to prepare data for model training.</span></span> <span data-ttu-id="98435-105">Transformace v této příručce vracejí třídy, které implementují [IEstimator](xref:Microsoft.ML.IEstimator`1) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98435-105">The transformations in this guide return classes that implement the [IEstimator](xref:Microsoft.ML.IEstimator`1) interface.</span></span> <span data-ttu-id="98435-106">Transformace dat je možné zřetězit.</span><span class="sxs-lookup"><span data-stu-id="98435-106">Data transformations can be chained together.</span></span> <span data-ttu-id="98435-107">Každá transformace očekává, že a vytvoří data konkrétní typy a formáty, které jsou určené v propojených referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="98435-107">Each transformation both expects and produces data of specific types and formats, which are specified in the linked reference documentation.</span></span>

<span data-ttu-id="98435-108">Některé transformace dat vyžadují trénovací data vypočítat své parametry.</span><span class="sxs-lookup"><span data-stu-id="98435-108">Some data transformations require training data to calculate their parameters.</span></span> <span data-ttu-id="98435-109">Příklad: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer vypočítá průměr a odchylky trénovacích dat během `Fit()` operace a používá tyto parametry v `Transform()` operace.</span><span class="sxs-lookup"><span data-stu-id="98435-109">For example: the <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer calculates the mean and variance of the training data during the `Fit()` operation, and uses those parameters in the `Transform()` operation.</span></span> 

<span data-ttu-id="98435-110">Další transformací dat nevyžadují trénovací data.</span><span class="sxs-lookup"><span data-stu-id="98435-110">Other data transformations don't require training data.</span></span> <span data-ttu-id="98435-111">Příklad: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> můžete provádět transformaci `Transform()` operaci bez nutnosti vidět všechny trénovacích dat během `Fit()` operace.</span><span class="sxs-lookup"><span data-stu-id="98435-111">For example: the <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> transformation can perform the `Transform()` operation without having seen any training data during the `Fit()` operation.</span></span>

## <a name="column-mapping-and-grouping"></a><span data-ttu-id="98435-112">Mapování sloupců a seskupování</span><span class="sxs-lookup"><span data-stu-id="98435-112">Column mapping and grouping</span></span>

| <span data-ttu-id="98435-113">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-113">Transform</span></span> | <span data-ttu-id="98435-114">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-114">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | <span data-ttu-id="98435-115">Zřetězit nejmíň jeden vstupní sloupce do nového sloupce výstupu</span><span class="sxs-lookup"><span data-stu-id="98435-115">Concatenate one or more input columns into a new output column</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | <span data-ttu-id="98435-116">Zkopírujte a přejmenujte nejmíň jeden vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="98435-116">Copy and rename one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | <span data-ttu-id="98435-117">Vyřadit nejmíň jeden vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="98435-117">Drop one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | <span data-ttu-id="98435-118">Vyberte jeden nebo více sloupců, aby ze vstupních dat</span><span class="sxs-lookup"><span data-stu-id="98435-118">Select one or more columns to keep from the input data</span></span> |

## <a name="normalization-and-scaling"></a><span data-ttu-id="98435-119">Normalizace a škálování</span><span class="sxs-lookup"><span data-stu-id="98435-119">Normalization and scaling</span></span>

| <span data-ttu-id="98435-120">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-120">Transform</span></span> | <span data-ttu-id="98435-121">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-121">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | <span data-ttu-id="98435-122">Odečte střední (trénovacích dat) a dělit odchylku (trénovacích dat)</span><span class="sxs-lookup"><span data-stu-id="98435-122">Subtract the mean (of the training data) and divide by the variance (of the training data)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | <span data-ttu-id="98435-123">Normalizovat podle logaritmus trénovacích dat</span><span class="sxs-lookup"><span data-stu-id="98435-123">Normalize based on the logarithm of the training data</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | <span data-ttu-id="98435-124">Škálování vstupním Vektorům podle jejich [lp norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), kde p je 1, 2 nebo nekonečno.</span><span class="sxs-lookup"><span data-stu-id="98435-124">Scale input vectors by their [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), where p is 1, 2 or infinity.</span></span> <span data-ttu-id="98435-125">Výchozí hodnota je norm (Euclidean vzdálenost) l2</span><span class="sxs-lookup"><span data-stu-id="98435-125">Defaults to the l2 (Euclidean distance) norm</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | <span data-ttu-id="98435-126">Škálování každé hodnoty v řádku tak, že se střední řádek dat a dělení podle buď směrodatnou odchylku nebo l2 – normály (řádek dat) a vynásobit konfigurovatelné měřítko (výchozí 2)</span><span class="sxs-lookup"><span data-stu-id="98435-126">Scale each value in a row by subtracting the mean of the row data and divide by either the standard deviation or l2-norm (of the row data), and multiply by a configurable scale factor (default 2)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | <span data-ttu-id="98435-127">Vstupní hodnota přiřadit bin index a dělit počet intervalů k vytvoření hodnoty typu float mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="98435-127">Assign the input value to a bin index and divide by the number of bins to produce a float value between 0 and 1.</span></span> <span data-ttu-id="98435-128">Hranice bin se počítají a trénovací data rovnoměrně distribuuje mezi přihrádky</span><span class="sxs-lookup"><span data-stu-id="98435-128">The bin boundaries are calculated to evenly distribute the training data across bins</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | <span data-ttu-id="98435-129">Vstupní hodnota přiřadit přihrádky podle jeho korelace s popisek sloupce</span><span class="sxs-lookup"><span data-stu-id="98435-129">Assign the input value to a bin based on its correlation with label column</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | <span data-ttu-id="98435-130">Rozdíl mezi minimální a maximální hodnoty v trénovacích dat můžete škálovat vstupu</span><span class="sxs-lookup"><span data-stu-id="98435-130">Scale the input by the difference between the minimum and maximum values in the training data</span></span> |

## <a name="conversions-between-data-types"></a><span data-ttu-id="98435-131">Převody mezi datovými typy</span><span class="sxs-lookup"><span data-stu-id="98435-131">Conversions between data types</span></span>

| <span data-ttu-id="98435-132">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-132">Transform</span></span> | <span data-ttu-id="98435-133">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-133">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | <span data-ttu-id="98435-134">Typ vstupní sloupec převést na nový typ</span><span class="sxs-lookup"><span data-stu-id="98435-134">Convert the type of an input column to a new type</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | <span data-ttu-id="98435-135">Mapování hodnot klíče (kategorie) podle zadaného slovníku mapování</span><span class="sxs-lookup"><span data-stu-id="98435-135">Map values to keys (categories) based on the supplied dictionary of mappings</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | <span data-ttu-id="98435-136">Mapování hodnot na klíče (kategorie) tak, že vytvoříte mapování ze vstupních dat</span><span class="sxs-lookup"><span data-stu-id="98435-136">Map values to keys (categories) by creating the mapping from the input data</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | <span data-ttu-id="98435-137">Převést zpět na původní hodnoty klíče</span><span class="sxs-lookup"><span data-stu-id="98435-137">Convert keys back to their original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | <span data-ttu-id="98435-138">Převést zpět na původní hodnoty vektory klíče</span><span class="sxs-lookup"><span data-stu-id="98435-138">Convert keys back to vectors of original values</span></span> |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | <span data-ttu-id="98435-139">Převést zpět na binární vektor původní hodnoty klíče</span><span class="sxs-lookup"><span data-stu-id="98435-139">Convert keys back to a binary vector of original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | <span data-ttu-id="98435-140">Hodnota hash hodnotu ve vstupním sloupci</span><span class="sxs-lookup"><span data-stu-id="98435-140">Hash the value in the input column</span></span> |

## <a name="text-transformations"></a><span data-ttu-id="98435-141">Transformace textu</span><span class="sxs-lookup"><span data-stu-id="98435-141">Text transformations</span></span>

| <span data-ttu-id="98435-142">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-142">Transform</span></span> | <span data-ttu-id="98435-143">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-143">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | <span data-ttu-id="98435-144">Transformovat sloupec text do pole typu float normalizované ngrams a počty char g</span><span class="sxs-lookup"><span data-stu-id="98435-144">Transform a text column into a float array of normalized ngrams and char-grams counts</span></span> | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | <span data-ttu-id="98435-145">Rozdělit jeden nebo více textové sloupce na jednotlivá slova</span><span class="sxs-lookup"><span data-stu-id="98435-145">Split one or more text columns into individual words</span></span> |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | <span data-ttu-id="98435-146">Rozdělit jeden nebo více textové sloupce na float jednotlivých znaků v rámci sady témata</span><span class="sxs-lookup"><span data-stu-id="98435-146">Split one or more text columns into individual characters floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | <span data-ttu-id="98435-147">Změnit velikost písmen, odeberte diakritická znaménka, interpunkční znaménka a čísla</span><span class="sxs-lookup"><span data-stu-id="98435-147">Change case, remove diacritical marks, punctuation marks and numbers</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | <span data-ttu-id="98435-148">Transformovat textový sloupec na kontejner počty ngrams (posloupnosti po sobě jdoucích slov)</span><span class="sxs-lookup"><span data-stu-id="98435-148">Transform text column into a bag of counts of ngrams (sequences of consecutive words)</span></span>|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | <span data-ttu-id="98435-149">Kontejner počty ngrams vektor transformován textového sloupce</span><span class="sxs-lookup"><span data-stu-id="98435-149">Transform text column into a bag of counts of ngrams vector</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | <span data-ttu-id="98435-150">Transformovat textový sloupec jako vektor hashované ngram počty</span><span class="sxs-lookup"><span data-stu-id="98435-150">Transform text column into a vector of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | <span data-ttu-id="98435-151">Transformace textu sloupce do kontejneru objektů a dat hash ngram součtů</span><span class="sxs-lookup"><span data-stu-id="98435-151">Transform text column into a bag of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | <span data-ttu-id="98435-152">Odebrání výchozí nevýznamová slova pro určený jazyk vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="98435-152">Remove default stop words for the specified language from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | <span data-ttu-id="98435-153">Odebere zadané nevýznamová slova ze vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="98435-153">Removes specified stop words from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | <span data-ttu-id="98435-154">Transformace dokumentů (reprezentovány jako vektor hodnot float) jako vektor hodnot float v rámci sady témata</span><span class="sxs-lookup"><span data-stu-id="98435-154">Transform a document (represented as a vector of floats) into a vector of floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | <span data-ttu-id="98435-155">Převést vektory větu pomocí předem vytrénovaných modelu vektory text tokenů</span><span class="sxs-lookup"><span data-stu-id="98435-155">Convert vectors of text tokens into sentence vectors using a pre-trained model</span></span> |

## <a name="image-transformations"></a><span data-ttu-id="98435-156">Obrázek transformace</span><span class="sxs-lookup"><span data-stu-id="98435-156">Image transformations</span></span>

| <span data-ttu-id="98435-157">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-157">Transform</span></span> | <span data-ttu-id="98435-158">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-158">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | <span data-ttu-id="98435-159">Převedení obrázku na stupně šedé</span><span class="sxs-lookup"><span data-stu-id="98435-159">Convert an image to grayscale</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | <span data-ttu-id="98435-160">Převést Vektor obrazových bodů <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span><span class="sxs-lookup"><span data-stu-id="98435-160">Convert a vector of pixels to <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | <span data-ttu-id="98435-161">Převést na pixelech ze vstupního obrázku vektor čísel</span><span class="sxs-lookup"><span data-stu-id="98435-161">Convert pixels from input image into a vector of numbers</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | <span data-ttu-id="98435-162">Načíst obrázky ze složky do paměti</span><span class="sxs-lookup"><span data-stu-id="98435-162">Load images from a folder into memory</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | <span data-ttu-id="98435-163">Změna velikosti obrázků</span><span class="sxs-lookup"><span data-stu-id="98435-163">Resize images</span></span> |

## <a name="categorical-data-transformations"></a><span data-ttu-id="98435-164">Transformace data zařazená do kategorií</span><span class="sxs-lookup"><span data-stu-id="98435-164">Categorical data transformations</span></span>

| <span data-ttu-id="98435-165">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-165">Transform</span></span> | <span data-ttu-id="98435-166">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-166">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | <span data-ttu-id="98435-167">Převést do jednoho nebo více sloupců text [horkou jeden](https://en.wikipedia.org/wiki/One-hot) kódovaný vektorů</span><span class="sxs-lookup"><span data-stu-id="98435-167">Convert one or more text columns into [one-hot](https://en.wikipedia.org/wiki/One-hot) encoded vectors</span></span> |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | <span data-ttu-id="98435-168">Převést jeden další textové sloupce na základě algoritmu hash horkou jeden kódovaného vektorů</span><span class="sxs-lookup"><span data-stu-id="98435-168">Convert one more text columns into hash-based one-hot encoded vectors</span></span> |

## <a name="missing-values"></a><span data-ttu-id="98435-169">Chybějící hodnoty</span><span class="sxs-lookup"><span data-stu-id="98435-169">Missing values</span></span>

| <span data-ttu-id="98435-170">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-170">Transform</span></span> | <span data-ttu-id="98435-171">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-171">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | <span data-ttu-id="98435-172">Vytvoří nový sloupec logický výstup, jehož hodnota je true, při chybí hodnota v sloupci vstupní</span><span class="sxs-lookup"><span data-stu-id="98435-172">Create a new boolean output column, the value of which is true when the value in the input column is missing</span></span> |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | <span data-ttu-id="98435-173">Vytvoří nový sloupec výstup, jehož hodnota nastavena na výchozí hodnotu, pokud je hodnota chybí vstupní sloupec a vstupní hodnota jinak</span><span class="sxs-lookup"><span data-stu-id="98435-173">Create a new output column, the value of which is set to a default value if the value is missing from the input column, and the input value otherwise</span></span> |

## <a name="feature-selection"></a><span data-ttu-id="98435-174">Výběr funkcí</span><span class="sxs-lookup"><span data-stu-id="98435-174">Feature selection</span></span>

| <span data-ttu-id="98435-175">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-175">Transform</span></span> | <span data-ttu-id="98435-176">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-176">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | <span data-ttu-id="98435-177">Zvolte funkce, jejichž jiné než výchozí hodnoty jsou větší než prahová hodnota</span><span class="sxs-lookup"><span data-stu-id="98435-177">Select features whose non-default values are greater than a threshold</span></span> |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | <span data-ttu-id="98435-178">Vyberte funkce, v nichž je největší závislé data ve sloupci popisek</span><span class="sxs-lookup"><span data-stu-id="98435-178">Select the features on which the data in the label column is most dependent</span></span> |

## <a name="custom-transformations"></a><span data-ttu-id="98435-179">Vlastní transformace</span><span class="sxs-lookup"><span data-stu-id="98435-179">Custom transformations</span></span>

| <span data-ttu-id="98435-180">Transformace</span><span class="sxs-lookup"><span data-stu-id="98435-180">Transform</span></span> | <span data-ttu-id="98435-181">Definice</span><span class="sxs-lookup"><span data-stu-id="98435-181">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | <span data-ttu-id="98435-182">Transformace existujících sloupců do nových pomocí uživatelem definované mapování</span><span class="sxs-lookup"><span data-stu-id="98435-182">Transform existing columns onto new ones with a user-defined mapping</span></span> |
