---
title: Transformace dat
description: Prozkoumejte různé datové transformace v ML.NET podporována.
ms.date: 08/08/2018
author: jralexander
ms.author: johalex
ms.openlocfilehash: 3c483f4a263052eb15435775a47f514893eee049
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397140"
---
# <a name="data-transforms"></a>Transformace dat

Následující tabulky obsahují informace o všech transformací dat nepodporuje v ML.NET (vyberte typ přejdete do příslušné tabulky transformovat data):

* [Zařazené do kategorií](#categorical)
* [Combiners a segregators](#combiners-and-segregators)
* [Výběr funkcí](#feature-selection)
* [Featurizers](#featurizers)
* [Popisek analýza kódu](#label-parsing)
* [Chybějící hodnoty](#missing-values)
* [Normalizace](#normalization)
* [Filtry řádků](#row-filters)
* [schéma](#schema)
* [Snadné a zpracování textu](#text-processing-and-featurization)
* [Různé](#miscellaneous)

> [!NOTE]
> ML.NET je aktuálně ve verzi Preview. Ne všechny transformace dat se aktuálně nepodporuje. Chcete-li odeslat žádost o určitých transformace, otevřete problém ve službě [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) úložiště GitHub.

## <a name="categorical"></a>Zařazené do kategorií

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CategoricalHashOneHotVectorizer> | Zakóduje proměnnou zařazené do kategorií pomocí algoritmu hash na základě kódování. |
| <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer> | Zakóduje zařazené do kategorií proměnnou s jedním hot kódování v závislosti na slovník termín. |

## <a name="combiners-and-segregators"></a>Combiners a segregators

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CombinerByContiguousGroupId> | Skupiny hodnoty pro skalární sloupec jako vektor podle ID souvislých skupiny. |
| <xref:Microsoft.ML.Transforms.FeatureCombiner> | Do sloupce jednu funkci k dispozici všechny funkce. |
| <xref:Microsoft.ML.Transforms.ManyHeterogeneousModelCombiner> | Kombinuje posloupnost TransformModels a PredictorModel do jednoho PredictorModel. |
| <xref:Microsoft.ML.Transforms.ModelCombiner> | Kombinuje posloupnost TransformModels do jednoho modelu. |
| <xref:Microsoft.ML.Transforms.Segregator> | Zruší seskupení sloupců vektor do sekvence řádků; inverzní funkce k transformaci skupiny. |
| <xref:Microsoft.ML.Transforms.TwoHeterogeneousModelCombiner> | Spojuje TransformModel a PredictorModel do jednoho PredictorModel. |

## <a name="feature-selection"></a>Výběr funkcí

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.FeatureSelectorByCount> | Vybere sloty, u kterých počet jiné než výchozí hodnoty je větší než nebo rovna prahové hodnoty. |
| <xref:Microsoft.ML.Transforms.FeatureSelectorByMutualInformation> | Vybere sloty nahoru k ve všech zadaných sloupcích seřazené podle jejich vzájemné informace o sloupci popisek. |

## <a name="featurizers"></a>Featurizers

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.HashConverter> | Hodnoty sloupců převádí hodnoty hash. Tato transformace přijímá číselné a textové vstupů, jednu i s hodnotou vektoru sloupce. |
| <xref:Microsoft.ML.Transforms.TreeLeafFeaturizer> | Trénovat komplet stromu, nebo načte ze souboru a potom mapuje číselné funkce vektor tří výstupy: 1. Vektor obsahující stromu jednotlivé výstupy komplet stromu. 2. Vektor označující listy, které funkce vector spadá do roku komplet stromu. 3. Vektor označující cesty, které funkce vector spadá do roku komplet stromu. Pokud jsou zadaná soubor modelu i trainer, vektoru použije soubor modelu. Pokud nejsou zadány žádné, bude výchozí model FastTree trénování vektoru. To může zpracovávat popisky kláves díky trénování regresní model směrem k jejich volitelně permutovanou funkci indexy. |

## <a name="label-parsing"></a>Popisek analýza kódu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Dictionarizer> | Převede vstupní hodnoty (slova, čísla, atd.) do indexu ve slovníku. |
| <xref:Microsoft.ML.Transforms.LabelColumnKeyBooleanConverter> | Transformuje popisku na klíč nebo bool (v případě potřeby) Chcete-li, že je vhodný pro klasifikaci. |
| <xref:Microsoft.ML.Transforms.LabelIndicator> | Používané soubory OVA remapper popisek. |
| <xref:Microsoft.ML.Transforms.LabelToFloatConverter> | Transformuje popisku na float, že je vhodný pro regrese. |
| <xref:Microsoft.ML.Transforms.PredictedLabelColumnOriginalValueConverter> | Transformuje předpokládané popisek sloupce na jeho původní hodnoty, pokud se nejedná o typ bool. |

## <a name="missing-values"></a>Chybějící hodnoty

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueHandler> | Zpracování chybějící hodnoty tak, že nahradíte s výchozí hodnotu nebo hodnotu mean/min/max (netextovými pouze pro sloupce). Sloupec ukazatele mohou být spojeny volitelně, pokud je typ vstupní sloupec číselné. |
| <xref:Microsoft.ML.Transforms.MissingValueIndicator> | Vytvořte logickou výstupního sloupce se stejným číslem sloty jako vstupní sloupec, ve kterém je výstupní hodnota true Pokud chybí hodnota v sloupci vstupní. |
| <xref:Microsoft.ML.Transforms.MissingValuesDropper> | Odebere NAs ze sloupce vektoru. |
| <xref:Microsoft.ML.Transforms.MissingValuesRowDropper> | Filtruje řádky, které obsahují chybějící hodnoty. |
| <xref:Microsoft.ML.Transforms.MissingValueSubstitutor> | Vytvoření výstupního sloupce stejného typu a velikosti vstupní sloupec, ve kterém chybí hodnoty jsou nahrazeny výchozí hodnotu nebo hodnotu mean/min/max (netextovými pouze pro sloupce). |

## <a name="normalization"></a>Normalizace

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BinNormalizer> | Hodnoty jsou přiřazeny do přihrádek equidensity a hodnota je namapována na jeho bin_number / number_of_bins. |
| <xref:Microsoft.ML.Transforms.ConditionalNormalizer> | Normalizujte sloupce pouze v případě potřeby. |
| <xref:Microsoft.ML.Transforms.GlobalContrastNormalizer> | Provede normalizaci globální kontrast vstupních hodnot: Y = (s * X - min) / D, kde je měřítku, s M je průměr a D je L2 norm nebo směrodatnou odchylku. | 
| <xref:Microsoft.ML.Transforms.LogMeanVarianceNormalizer> | Normalizuje dat na základě průměr vypočítaný a odchylky logaritmus data. |
| <xref:Microsoft.ML.Transforms.LpNormalizer> | Normalizujte vektory (řádky) jednotlivě podle jejich změny měřítka do jednotky norm (L2, L1 nebo LInf). Provádí následující operace na vektor X: Y = (X - min) / D, kde M je průměr a D je L2 norm, L1 norm nebo LInf norm. |
| <xref:Microsoft.ML.Transforms.MeanVarianceNormalizer> | Normalizuje dat na základě průměr vypočítaný a odchylky data. |
| <xref:Microsoft.ML.Transforms.MinMaxNormalizer> | Normalizuje na data vycházející z pozorovaných minimální a maximální hodnoty data. |
| <xref:Microsoft.ML.Transforms.SupervisedBinNormalizer> | Podobně jako <xref:Microsoft.ML.Transforms.BinNormalizer>, ale vypočítá podle korelace s popisek sloupce není equidensity přihrádky. Nová hodnota je bin_number / number_of_bins. |

## <a name="row-filters"></a>Filtry řádků

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowRangeFilter> | Filtry pro zobrazení dat na sloupce typu Single, Double nebo klíč (souvislé). Uchovává hodnoty, které jsou v rozsahu zadaného min/max. Hodnoty NaN vždy filtrují. Pokud je vstup typ klíče, min/max jsou považovány za procenta počet hodnot. |
| <xref:Microsoft.ML.Transforms.RowSkipAndTakeFilter> | Umožňuje omezení vstup na podmnožinu řádků volitelné posunem. Můžete použít k implementaci stránkování na data. |
| <xref:Microsoft.ML.Transforms.RowSkipFilter> | Umožňuje omezit vstup na podmnožinu řádků přeskočením počet řádků. |
| <xref:Microsoft.ML.Transforms.RowTakeFilter> | Umožňuje omezení vstup na podmnožinu řádků provedením prvních N řádků. |

## <a name="schema"></a>Schéma

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnConcatenator> | Zřetězí dva sloupce stejného typu položky. |
| <xref:Microsoft.ML.Transforms.ColumnCopier> | Duplicitní sloupce z datové sady.|
| <xref:Microsoft.ML.Transforms.ColumnDropper> | Zahodí sloupce z datové sady. |
| <xref:Microsoft.ML.Transforms.ColumnSelector> | Vybere sadu sloupců, vyřadit všechny ostatní. |
| <xref:Microsoft.ML.Transforms.ColumnTypeConverter> | Převede sloupec na jiný typ pomocí standardních převodů. |
| <xref:Microsoft.ML.Transforms.KeyToTextConverter> | KeyToValueTransform využívá KeyValues metadat pro mapování klíčů indexů na odpovídající hodnoty v metadatech KeyValues. |
| <xref:Microsoft.ML.Transforms.NGramTranslator> | Vytvoří kontejner počty ngrams (pořadí po sobě jdoucích hodnoty o délce 1-n) v dané vektor klíče. Dělá to tak vytváření slovník ngrams a jako index v kontejneru a s použitím id ve slovníku. | 
| <xref:Microsoft.ML.Transforms.OptionalColumnCreator> | Pokud zdrojový sloupec po deserializace neexistuje, vytvoří sloupec správný typ a výchozí hodnoty. |

## <a name="text-processing-and-featurization"></a>Snadné a zpracování textu

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CharacterTokenizer> | Znak objektově orientovaný tokenizátor, ve kterém se text je považován za posloupnost znaků. |
| <xref:Microsoft.ML.Transforms.TextFeaturizer> | Transformace, která se změní kolekce textové dokumenty do vektory čísly. Normalizovaná počty ngrams (aplikace word a/nebo znak) v dané tokenizovaná textu jsou vektory funkce. |
| <xref:Microsoft.ML.Transforms.TextToKeyConverter> | Převede vstupní hodnoty (slova, čísla, atd.) do indexu ve slovníku. |
| <xref:Microsoft.ML.Transforms.WordEmbeddings> | Transformace, který převádí vektory text tokenů číselné vektory pomocí předem vytrénovaných modelu. Další informace o postupu najdete v článku [vkládání slov](https://en.wikipedia.org/wiki/Word_embedding) stránky Wikipedia. |
| <xref:Microsoft.ML.Transforms.WordTokenizer> | Vstup do této transformace je text a výstup je vektor text obsahující slova (tokeny) v původní text. Oddělovač je místo, ale je možné zadat libovolný znak (nebo více znaků). |

## <a name="miscellaneous"></a>Různé

| Transformace | Definice |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ApproximateBootstrapSampler> | Přibližná bootstrap vzorkování. |
| <xref:Microsoft.ML.Transforms.BinaryPredictionScoreColumnsRenamer> | Binární predikcí, přejmenuje PredictedLabel a stanovíte jeho skóre sloupce se mají zahrnout název pozitivní třídy.|
| <xref:Microsoft.ML.Transforms.DataCache> | Ukládá do mezipaměti pomocí možnosti zadané mezipaměti. |
| <xref:Microsoft.ML.Transforms.DatasetScorer> | Získává datovou sadu s prediktivní model. |
| <xref:Microsoft.ML.Transforms.DatasetTransformScorer> | Získává datovou sadu s modelem transformace. |
| <xref:Microsoft.ML.Transforms.NoOperation> | Neprovádí žádnou akci. |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | Přidá sloupec s generované čísel pořadí. |
| <xref:Microsoft.ML.Transforms.ScoreColumnSelector> | Vybere pouze poslední skóre sloupce a dodatečné sloupce zadané v argumentech. |
| <xref:Microsoft.ML.Transforms.Scorer> | Změní model prediktivní model transformace. |
| <xref:Microsoft.ML.Transforms.SentimentAnalyzer> | Používá model které je předem vytrénované mínění ke stanovení skóre vstupního řetězce. |
| <xref:Microsoft.ML.Transforms.TrainTestDatasetSplitter> | Rozdělí nastaví datovou sadu do trénování a testování. |
