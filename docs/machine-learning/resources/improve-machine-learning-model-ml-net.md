---
title: 'Jak na to: Zlepšete přesnost modelu'
description: Přečtěte si, jak zlepšit přesnost modelu
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75739584"
---
# <a name="improve-mlnet-model-accuracy"></a>Zlepšete přesnost ML.NET modelu

Přečtěte si, jak zlepšit přesnost modelu.

## <a name="reframe-the-problem"></a>Přeformulovat problém

V některých případě může zlepšení modelu mít nic společného s daty nebo techniky používané k trénování modelu. Místo toho se může jen zeptat na špatnou otázku. Zvažte možnost podívat se na problém z různých úhlů a využít data k extrahování latentních indikátorů a skrytých vztahů, aby bylo možné tuto otázku upřesnit.

## <a name="provide-more-data-samples"></a>Poskytnutí dalších vzorků dat

Stejně jako lidé, čím více tréninkových algoritmů se zvyšuje pravděpodobnost lepšího výkonu. Jedním ze způsobů, jak zlepšit výkon modelu je poskytnout další ukázky trénovací data algoritmy. Čím více dat se učí, tím více případů je schopno správně identifikovat.

## <a name="add-context-to-the-data"></a>Přidání kontextu k datům

Význam jednoho datového bodu může být obtížné interpretovat. Vytváření kontextu kolem datových bodů pomáhá algoritmům i odborníkům na dané téma lépe rozhodovat. Například skutečnost, že dům má tři ložnice, sama o sobě nedává dobrý údaj o jeho ceně. Nicméně, pokud přidáte kontext a nyní víte, že je v příměstské čtvrti mimo hlavní metropolitní oblasti, kde průměrný věk je 38, průměrný příjem domácnosti je 80.000 dolarů a školy jsou v top 20. rozhodnutí. Všechny tyto kontexty lze přidat jako vstup do modelu strojového učení jako funkce.

## <a name="use-meaningful-data-and-features"></a>Použití smysluplných dat a funkcí

Přestože další vzorky dat a funkce mohou pomoci zlepšit přesnost modelu, mohou také zavést šum, protože ne všechna data a funkce jsou smysluplné. Proto je důležité pochopit, které funkce jsou ty, které nejvíce ovlivňují rozhodnutí provedená algoritmem. Použití technik, jako je Důležitost funkce permutace (PFI), může pomoci identifikovat tyto významné funkce a nejen pomoci vysvětlit model, ale také použít výstup jako metodu výběru funkce ke snížení množství hlučných funkcí, které jdou do procesu školení.

Další informace o použití PFI naleznete [v tématu Vysvětlení předpovědí modelu pomocí důležitosti funkce permutace](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

## <a name="cross-validation"></a>Křížové ověření

Křížové ověřování je technika trénování a vyhodnocení modelu, která rozděluje data do několika oddílů a trénuje více algoritmů na těchto oddílech. Tato technika zlepšuje robustnost modelu tím, že podrží data z tréninkového procesu. Kromě zlepšení výkonu na neviditelné pozorování, v prostředí s omezenými daty může být účinným nástrojem pro trénování modelů s menší datovou sadou.

Navštivte následující odkaz, kde se [dozvíte, jak používat křížové ověřování v ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>Ladění hyperparametrů

Tréninkové modely strojového učení je iterativní a průzkumný proces. Například jaký je optimální počet clusterů při trénování modelu pomocí algoritmu K-Means? Odpověď závisí na mnoha faktorech, jako je struktura dat. Nalezení tohoto čísla by vyžadovalo experimentování s různými hodnotami pro k a následné vyhodnocení výkonu k určení, která hodnota je nejlepší. Praxe ladění těchto parametrů najít optimální model se nazývá hyper-parametr tuning.

## <a name="choose-a-different-algorithm"></a>Výběr jiného algoritmu

Úlohy strojového učení, jako je regrese a klasifikace obsahují různé implementace algoritmů. Může se podařit, že problém, který se snažíte vyřešit, a způsob, jakým jsou data strukturována, nezapadá dobře do aktuálního algoritmu. V takovém případě zvažte použití jiného algoritmu pro váš úkol, abyste zjistili, zda se lépe učí z vašich dat.

Následující odkaz obsahuje další [pokyny, který algoritmus zvolit](../how-to-choose-an-ml-net-algorithm.md).
