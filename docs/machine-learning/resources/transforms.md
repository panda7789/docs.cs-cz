---
title: Transformace dat | ML.NET
description: Prozkoumejte funkce engineering součásti, které jsou podporované v ML.NET.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 506abcc826059f4d252378b1bde0b852949a42e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019136"
---
# <a name="data-transformations"></a><span data-ttu-id="f9f04-103">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="f9f04-103">Data transformations</span></span>

<span data-ttu-id="f9f04-104">Transformace dat slouží k přípravě dat pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="f9f04-104">Data transformations are used to prepare data for model training.</span></span> <span data-ttu-id="f9f04-105">Transformace v této příručce vracejí třídy, které implementují [IEstimator](xref:Microsoft.ML.IEstimator`1) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9f04-105">The transformations in this guide return classes that implement the [IEstimator](xref:Microsoft.ML.IEstimator`1) interface.</span></span> <span data-ttu-id="f9f04-106">Transformace dat je možné zřetězit.</span><span class="sxs-lookup"><span data-stu-id="f9f04-106">Data transformations can be chained together.</span></span> <span data-ttu-id="f9f04-107">Každá transformace očekává, že a vytvoří data konkrétní typy a formáty, které jsou určené v propojených referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="f9f04-107">Each transformation both expects and produces data of specific types and formats, which are specified in the linked reference documentation.</span></span>

<span data-ttu-id="f9f04-108">Některé transformace dat vyžadují trénovací data vypočítat své parametry.</span><span class="sxs-lookup"><span data-stu-id="f9f04-108">Some data transformations require training data to calculate their parameters.</span></span> <span data-ttu-id="f9f04-109">Příklad: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer vypočítá průměr a odchylky trénovacích dat během `Fit()` operace a používá tyto parametry v `Transform()` operace.</span><span class="sxs-lookup"><span data-stu-id="f9f04-109">For example: the <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer calculates the mean and variance of the training data during the `Fit()` operation, and uses those parameters in the `Transform()` operation.</span></span> 

<span data-ttu-id="f9f04-110">Další transformací dat nevyžadují trénovací data.</span><span class="sxs-lookup"><span data-stu-id="f9f04-110">Other data transformations don't require training data.</span></span> <span data-ttu-id="f9f04-111">Příklad: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> můžete provádět transformaci `Transform()` operaci bez nutnosti vidět všechny trénovacích dat během `Fit()` operace.</span><span class="sxs-lookup"><span data-stu-id="f9f04-111">For example: the <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> transformation can perform the `Transform()` operation without having seen any training data during the `Fit()` operation.</span></span>

## <a name="column-mapping-and-grouping"></a><span data-ttu-id="f9f04-112">Mapování sloupců a seskupování</span><span class="sxs-lookup"><span data-stu-id="f9f04-112">Column mapping and grouping</span></span>

| <span data-ttu-id="f9f04-113">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-113">Transform</span></span> | <span data-ttu-id="f9f04-114">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-114">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | <span data-ttu-id="f9f04-115">Zřetězit nejmíň jeden vstupní sloupce do nového sloupce výstupu</span><span class="sxs-lookup"><span data-stu-id="f9f04-115">Concatenate one or more input columns into a new output column</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | <span data-ttu-id="f9f04-116">Zkopírujte a přejmenujte nejmíň jeden vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="f9f04-116">Copy and rename one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | <span data-ttu-id="f9f04-117">Vyřadit nejmíň jeden vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="f9f04-117">Drop one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | <span data-ttu-id="f9f04-118">Vyberte jeden nebo více sloupců, aby ze vstupních dat</span><span class="sxs-lookup"><span data-stu-id="f9f04-118">Select one or more columns to keep from the input data</span></span> |

## <a name="normalization-and-scaling"></a><span data-ttu-id="f9f04-119">Normalizace a škálování</span><span class="sxs-lookup"><span data-stu-id="f9f04-119">Normalization and scaling</span></span>

| <span data-ttu-id="f9f04-120">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-120">Transform</span></span> | <span data-ttu-id="f9f04-121">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-121">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | <span data-ttu-id="f9f04-122">Odečte střední (trénovacích dat) a dělit odchylku (trénovacích dat)</span><span class="sxs-lookup"><span data-stu-id="f9f04-122">Subtract the mean (of the training data) and divide by the variance (of the training data)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | <span data-ttu-id="f9f04-123">Normalizovat podle logaritmus trénovacích dat</span><span class="sxs-lookup"><span data-stu-id="f9f04-123">Normalize based on the logarithm of the training data</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | <span data-ttu-id="f9f04-124">Škálování vstupním Vektorům podle jejich [lp norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), kde p je 1, 2 nebo nekonečno.</span><span class="sxs-lookup"><span data-stu-id="f9f04-124">Scale input vectors by their [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), where p is 1, 2 or infinity.</span></span> <span data-ttu-id="f9f04-125">Výchozí hodnota je norm (Euclidean vzdálenost) l2</span><span class="sxs-lookup"><span data-stu-id="f9f04-125">Defaults to the l2 (Euclidean distance) norm</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | <span data-ttu-id="f9f04-126">Škálování každé hodnoty v řádku tak, že se střední řádek dat a dělení podle buď směrodatnou odchylku nebo l2 – normály (řádek dat) a vynásobit konfigurovatelné měřítko (výchozí 2)</span><span class="sxs-lookup"><span data-stu-id="f9f04-126">Scale each value in a row by subtracting the mean of the row data and divide by either the standard deviation or l2-norm (of the row data), and multiply by a configurable scale factor (default 2)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | <span data-ttu-id="f9f04-127">Vstupní hodnota přiřadit bin index a dělit počet intervalů k vytvoření hodnoty typu float mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="f9f04-127">Assign the input value to a bin index and divide by the number of bins to produce a float value between 0 and 1.</span></span> <span data-ttu-id="f9f04-128">Hranice bin se počítají a trénovací data rovnoměrně distribuuje mezi přihrádky</span><span class="sxs-lookup"><span data-stu-id="f9f04-128">The bin boundaries are calculated to evenly distribute the training data across bins</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | <span data-ttu-id="f9f04-129">Vstupní hodnota přiřadit přihrádky podle jeho korelace s popisek sloupce</span><span class="sxs-lookup"><span data-stu-id="f9f04-129">Assign the input value to a bin based on its correlation with label column</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | <span data-ttu-id="f9f04-130">Rozdíl mezi minimální a maximální hodnoty v trénovacích dat můžete škálovat vstupu</span><span class="sxs-lookup"><span data-stu-id="f9f04-130">Scale the input by the difference between the minimum and maximum values in the training data</span></span> |

## <a name="conversions-between-data-types"></a><span data-ttu-id="f9f04-131">Převody mezi datovými typy</span><span class="sxs-lookup"><span data-stu-id="f9f04-131">Conversions between data types</span></span>

| <span data-ttu-id="f9f04-132">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-132">Transform</span></span> | <span data-ttu-id="f9f04-133">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-133">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | <span data-ttu-id="f9f04-134">Typ vstupní sloupec převést na nový typ</span><span class="sxs-lookup"><span data-stu-id="f9f04-134">Convert the type of an input column to a new type</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | <span data-ttu-id="f9f04-135">Mapování hodnot klíče (kategorie) podle zadaného slovníku mapování</span><span class="sxs-lookup"><span data-stu-id="f9f04-135">Map values to keys (categories) based on the supplied dictionary of mappings</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | <span data-ttu-id="f9f04-136">Mapování hodnot na klíče (kategorie) tak, že vytvoříte mapování ze vstupních dat</span><span class="sxs-lookup"><span data-stu-id="f9f04-136">Map values to keys (categories) by creating the mapping from the input data</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | <span data-ttu-id="f9f04-137">Převést zpět na původní hodnoty klíče</span><span class="sxs-lookup"><span data-stu-id="f9f04-137">Convert keys back to their original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | <span data-ttu-id="f9f04-138">Převést zpět na původní hodnoty vektory klíče</span><span class="sxs-lookup"><span data-stu-id="f9f04-138">Convert keys back to vectors of original values</span></span> |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | <span data-ttu-id="f9f04-139">Převést zpět na binární vektor původní hodnoty klíče</span><span class="sxs-lookup"><span data-stu-id="f9f04-139">Convert keys back to a binary vector of original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | <span data-ttu-id="f9f04-140">Hodnota hash hodnotu ve vstupním sloupci</span><span class="sxs-lookup"><span data-stu-id="f9f04-140">Hash the value in the input column</span></span> |

## <a name="text-transformations"></a><span data-ttu-id="f9f04-141">Transformace textu</span><span class="sxs-lookup"><span data-stu-id="f9f04-141">Text transformations</span></span>

| <span data-ttu-id="f9f04-142">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-142">Transform</span></span> | <span data-ttu-id="f9f04-143">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-143">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | <span data-ttu-id="f9f04-144">Transformovat sloupec text do pole typu float normalizované ngrams a počty char g</span><span class="sxs-lookup"><span data-stu-id="f9f04-144">Transform a text column into a float array of normalized ngrams and char-grams counts</span></span> | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | <span data-ttu-id="f9f04-145">Rozdělit jeden nebo více textové sloupce na jednotlivá slova</span><span class="sxs-lookup"><span data-stu-id="f9f04-145">Split one or more text columns into individual words</span></span> |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | <span data-ttu-id="f9f04-146">Rozdělit jeden nebo více textové sloupce na float jednotlivých znaků v rámci sady témata</span><span class="sxs-lookup"><span data-stu-id="f9f04-146">Split one or more text columns into individual characters floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | <span data-ttu-id="f9f04-147">Změnit velikost písmen, odeberte diakritická znaménka, interpunkční znaménka a čísla</span><span class="sxs-lookup"><span data-stu-id="f9f04-147">Change case, remove diacritical marks, punctuation marks and numbers</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | <span data-ttu-id="f9f04-148">Transformovat textový sloupec na kontejner počty ngrams (posloupnosti po sobě jdoucích slov)</span><span class="sxs-lookup"><span data-stu-id="f9f04-148">Transform text column into a bag of counts of ngrams (sequences of consecutive words)</span></span>|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | <span data-ttu-id="f9f04-149">Kontejner počty ngrams vektor transformován textového sloupce</span><span class="sxs-lookup"><span data-stu-id="f9f04-149">Transform text column into a bag of counts of ngrams vector</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | <span data-ttu-id="f9f04-150">Transformovat textový sloupec jako vektor hashované ngram počty</span><span class="sxs-lookup"><span data-stu-id="f9f04-150">Transform text column into a vector of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | <span data-ttu-id="f9f04-151">Transformace textu sloupce do kontejneru objektů a dat hash ngram součtů</span><span class="sxs-lookup"><span data-stu-id="f9f04-151">Transform text column into a bag of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | <span data-ttu-id="f9f04-152">Odebrání výchozí nevýznamová slova pro určený jazyk vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="f9f04-152">Remove default stop words for the specified language from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | <span data-ttu-id="f9f04-153">Odebere zadané nevýznamová slova ze vstupní sloupce</span><span class="sxs-lookup"><span data-stu-id="f9f04-153">Removes specified stop words from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | <span data-ttu-id="f9f04-154">Transformace dokumentů (reprezentovány jako vektor hodnot float) jako vektor hodnot float v rámci sady témata</span><span class="sxs-lookup"><span data-stu-id="f9f04-154">Transform a document (represented as a vector of floats) into a vector of floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | <span data-ttu-id="f9f04-155">Převést vektory větu pomocí předem vytrénovaných modelu vektory text tokenů</span><span class="sxs-lookup"><span data-stu-id="f9f04-155">Convert vectors of text tokens into sentence vectors using a pre-trained model</span></span> |

## <a name="image-transformations"></a><span data-ttu-id="f9f04-156">Obrázek transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-156">Image transformations</span></span>

| <span data-ttu-id="f9f04-157">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-157">Transform</span></span> | <span data-ttu-id="f9f04-158">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-158">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | <span data-ttu-id="f9f04-159">Převedení obrázku na stupně šedé</span><span class="sxs-lookup"><span data-stu-id="f9f04-159">Convert an image to grayscale</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | <span data-ttu-id="f9f04-160">Převést Vektor obrazových bodů <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span><span class="sxs-lookup"><span data-stu-id="f9f04-160">Convert a vector of pixels to <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | <span data-ttu-id="f9f04-161">Převést na pixelech ze vstupního obrázku vektor čísel</span><span class="sxs-lookup"><span data-stu-id="f9f04-161">Convert pixels from input image into a vector of numbers</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | <span data-ttu-id="f9f04-162">Načíst obrázky ze složky do paměti</span><span class="sxs-lookup"><span data-stu-id="f9f04-162">Load images from a folder into memory</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | <span data-ttu-id="f9f04-163">Změna velikosti obrázků</span><span class="sxs-lookup"><span data-stu-id="f9f04-163">Resize images</span></span> |

## <a name="categorical-data-transformations"></a><span data-ttu-id="f9f04-164">Transformace data zařazená do kategorií</span><span class="sxs-lookup"><span data-stu-id="f9f04-164">Categorical data transformations</span></span>

| <span data-ttu-id="f9f04-165">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-165">Transform</span></span> | <span data-ttu-id="f9f04-166">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-166">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | <span data-ttu-id="f9f04-167">Převést do jednoho nebo více sloupců text [horkou jeden](https://en.wikipedia.org/wiki/One-hot) kódovaný vektorů</span><span class="sxs-lookup"><span data-stu-id="f9f04-167">Convert one or more text columns into [one-hot](https://en.wikipedia.org/wiki/One-hot) encoded vectors</span></span> |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | <span data-ttu-id="f9f04-168">Převést jeden další textové sloupce na základě algoritmu hash horkou jeden kódovaného vektorů</span><span class="sxs-lookup"><span data-stu-id="f9f04-168">Convert one more text columns into hash-based one-hot encoded vectors</span></span> |

## <a name="missing-values"></a><span data-ttu-id="f9f04-169">Chybějící hodnoty</span><span class="sxs-lookup"><span data-stu-id="f9f04-169">Missing values</span></span>

| <span data-ttu-id="f9f04-170">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-170">Transform</span></span> | <span data-ttu-id="f9f04-171">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-171">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | <span data-ttu-id="f9f04-172">Vytvoří nový sloupec logický výstup, jehož hodnota je true, při chybí hodnota v sloupci vstupní</span><span class="sxs-lookup"><span data-stu-id="f9f04-172">Create a new boolean output column, the value of which is true when the value in the input column is missing</span></span> |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | <span data-ttu-id="f9f04-173">Vytvoří nový sloupec výstup, jehož hodnota nastavena na výchozí hodnotu, pokud je hodnota chybí vstupní sloupec a vstupní hodnota jinak</span><span class="sxs-lookup"><span data-stu-id="f9f04-173">Create a new output column, the value of which is set to a default value if the value is missing from the input column, and the input value otherwise</span></span> |

## <a name="feature-selection"></a><span data-ttu-id="f9f04-174">Výběr funkcí</span><span class="sxs-lookup"><span data-stu-id="f9f04-174">Feature selection</span></span>

| <span data-ttu-id="f9f04-175">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-175">Transform</span></span> | <span data-ttu-id="f9f04-176">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-176">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | <span data-ttu-id="f9f04-177">Zvolte funkce, jejichž jiné než výchozí hodnoty jsou větší než prahová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9f04-177">Select features whose non-default values are greater than a threshold</span></span> |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | <span data-ttu-id="f9f04-178">Vyberte funkce, v nichž je největší závislé data ve sloupci popisek</span><span class="sxs-lookup"><span data-stu-id="f9f04-178">Select the features on which the data in the label column is most dependent</span></span> |

## <a name="custom-transformations"></a><span data-ttu-id="f9f04-179">Vlastní transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-179">Custom transformations</span></span>

| <span data-ttu-id="f9f04-180">Transformace</span><span class="sxs-lookup"><span data-stu-id="f9f04-180">Transform</span></span> | <span data-ttu-id="f9f04-181">Definice</span><span class="sxs-lookup"><span data-stu-id="f9f04-181">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | <span data-ttu-id="f9f04-182">Transformace existujících sloupců do nových pomocí uživatelem definované mapování</span><span class="sxs-lookup"><span data-stu-id="f9f04-182">Transform existing columns onto new ones with a user-defined mapping</span></span> |
