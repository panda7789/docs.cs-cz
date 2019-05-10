---
title: Průvodce ML.NET postupy
description: Zjistěte, jak provádět specifické úkoly, které vám pomůže s vlastní vytvoření řešení AI a Machine Learning integrace do svých aplikací .NET.
ms.custom: seodec18
ms.date: 03/01/2019
ms.openlocfilehash: 83188e65ccd02e6928cb4b87577105a75ee96245
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649151"
---
# <a name="net-machine-learning-how-to-guides"></a>Průvodce postupy .NET machine learning 

V části Průvodce ML.NET jak najdete rychlé odpovědi na běžné dotazy. V některých případech může být uvedena články ve více oddílů, aby se daly snadno najít.

## <a name="load-the-data"></a>Načtení dat

* [Načtení dat pomocí mnoho sloupců ze souboru CSV pro machine learning zpracování.](load-data-from-mult-column-csv-ml-net.md)

* [Načtení dat z více souborů pro machine learning zpracování.](load-data-from-multiple-files-ml-net.md)

* [Načíst data z textového souboru pro machine learning zpracování.](load-data-from-text-file-ml-net.md)

### <a name="prepare-the-data"></a>Příprava dat

* [Předběžné zpracování s normalizers používané k zpracování dat trénovací data.](normalizers-preprocess-data-ml-net.md)

## <a name="train-the-model"></a>Trénování modelu

* [Trénování modelu strojového učení s daty, která není v textovém souboru.](load-non-file-training-data-ml-net.md)

* [Trénování modelu strojového učení pomocí křížového ověření.](train-cross-validation-ml-net.md)

* [Trénování regresní model k predikci hodnotu pomocí ML.NET.](train-regression-model-ml-net.md)

### <a name="evaluate-the-model-quality"></a>Vyhodnocení kvalita modelu

* [Vypočítejte metriky pro vyhodnocení kvality modelu.](verify-model-quality-ml-net.md)

### <a name="model-explainability"></a>Model explainability

* [Určení funkcí důležitost modely s důležitostí funkce permutaci.](determine-global-feature-importance-in-model.md)

* [Pomocí funkcí tvar a zobecněn Additive modely pro model explainability.](use-gams-for-model-explainability.md)

### <a name="feature-engineering"></a>Návrh funkcí

* [Použijte vytváření funkcí k tréninku modelu na data zařazená do kategorií.](train-model-categorical-ml-net.md)

* [U textových dat s ML.NET použijte vytváření funkcí pro cvičení modelu.](train-model-textual-ml-net.md)

## <a name="run"></a>Spustit

* [Zkontrolujte hodnoty dočasných dat během zpracování kanálu ML.NET.](inspect-intermediate-data-ml-net.md)

* [Zprovoznění trénovaný model strojového učení v aplikacích.](consuming-model-ml-net.md)

* [Používejte PredictionFunction předpověď jeden po druhém.](single-predict-model-ml-net.md)

## <a name="probabilistic-infernet"></a>Probabilistic (Infer.NET)

* [Vytvoření hry shoda seznamu aplikaci pomocí Infer.NET a pravděpodobnostní programování.](matchup-app-infer-net.md)