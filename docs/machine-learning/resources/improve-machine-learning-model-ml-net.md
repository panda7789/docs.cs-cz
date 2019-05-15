---
title: 'Postupy: Vylepšení přesnosti modelu'
description: Zjistěte, jak zlepšit přesnost modelu
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8bb47102ede8e135090b1381eb815dccd512e03d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557813"
---
# <a name="improve-mlnet-model-accuracy"></a>Zlepšit přesnost modelu ML.NET

Zjistěte, jak zlepšit přesnost modelu.

## <a name="reframe-the-problem"></a>Reframe problému

V některých případech zlepšení modelu může mít nic společného s daty nebo s techniky použít k trénování modelu. Místo toho stačí je, že nesprávné otázka je kladena. Vezměte v úvahu z různých úhlů pohledu na problém a využívat data k extrakci latentní ukazatele a skryté vztahy k zpřesnit dotaz.

## <a name="provide-more-data-samples"></a>Zadejte další ukázky data

Jako jsou lidé další trénování algoritmů získáte lepší výkon zvyšuje pravděpodobnost, že. Jedním způsobem, jak zlepšit výkon modelu je poskytnout další ukázky data školení na algoritmy. Čím více dat se naučí z více případů je schopen správně identifikovat.

## <a name="add-context-to-the-data"></a>Přidat kontext dat

Význam jednoho datového bodu může být obtížné interpretovat. Vytváření kontextu kolem datových bodů pomáhá algoritmy, stejně jako odborník na danou problematiku lépe rozhodovat. Například skutečnost, že domu má tři ložnicemi není sama o sobě udělit dobrá indikace toho jeho ceny. Ale pokud přidáte kontextu a teď už víte, že je v okolí detekovaná sousední mimo hlavní metropolitní oblasti, kde je 38 průměrný věk, průměrný příjem domácností $80,000 a školy jsou v nejvyššího percentilu 20. prosincem algoritmus má víc informací, které základní jeho rozhodnutí o. Všechny tohoto kontextu lze přidat jako vstup do modelu strojového učení jako funkce.

## <a name="use-meaningful-data-and-features"></a>Použití funkcí a smysluplná data

I když další ukázky data a funkce vám může pomoci zvýšit přesnost modelu, ale může také přinášejí šumu od nejsou všechna data a funkce mají smysl. Proto je důležité pochopit, jaké funkce jsou ty, které nejčastěji dopad rozhodnutí provedli pomocí algoritmu. Pomocí technik, jako je permutaci funkce význam (PFI) může pomoct identifikovat tyto důležité funkce a nejen pomoci s vysvětlením modelu ale použít i výstup jako metodu výběru funkcí a snížit množství hlučného funkce přicházející do procesu trénování.

Naučte se používat PFI návštěvou následujících [odkaz](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)

## <a name="cross-validation"></a>křížové ověření

Křížové ověření je školení a model hodnocení technika, která rozdělí data do několika oddílů a trénovat více algoritmy v těchto oddílech. Tento postup zlepšuje odolnost modelu tím, že se data z procesu trénování. Kromě vylepšení výkonu na neviditelný pozorování, v prostředí omezené dat může být efektivní nástroj pro trénování modelů s menší datové sady.

Navštivte následující odkaz na další [použití křížového ověření v ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>hyperparametrů

Trénování modelů strojového učení je iterativní a nahodilé proces. Například co je optimální počet clusterů, při cvičení modelu pomocí algoritmu K-Means? Odpověď závisí na mnoha faktorech, jako je například struktura dat. Hledání, že číslo by vyžadovaly experimentovat s různými hodnotami parametru k a potom hodnocení výkonu určit hodnotu, která je nejvhodnější. Postup ladění tyto parametry najít optimální model se nazývá hyperparametrické ladění.

## <a name="choose-a-different-algorithm"></a>Zvolte jiný algoritmus

Úlohy strojového učení jako regresní a klasifikace obsahovat různé implementace algoritmu. Možná v případě, že problém, který se snažíte vyřešit a způsob, jakým strukturovaná data se nevejde do aktuální algoritmus. V takovém případě zvažte použití různých algoritmů pro vaše úlohy zobrazíte, pokud se naučí lépe datům.

Pod následujícím odkazem najdete více [pokyny, které algoritmus zvolit](../how-to-choose-an-ml-net-algorithm.md).
