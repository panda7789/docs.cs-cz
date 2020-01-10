---
title: 'Postupy: Vylepšení přesnosti modelu'
description: Naučte se zlepšit přesnost modelu.
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739584"
---
# <a name="improve-mlnet-model-accuracy"></a>Zvýšení přesnosti modelu ML.NET

Naučte se, jak zlepšit přesnost modelu.

## <a name="reframe-the-problem"></a>Přeorámování problému

V některých případech nemusí mít vylepšení modelu nic dělat s daty nebo technikami, které slouží ke výukě modelu. Místo toho se může stát, že budete požádáni o špatnou otázku. Zvažte, jak se podívat na problém z různých úhlů, a využijte data k extrakci latentních indikátorů a skrytých vztahů za účelem upřesnění otázky.

## <a name="provide-more-data-samples"></a>Poskytnutí dalších ukázek dat

Podobně jako u člověka se zvyšuje více školicích algoritmů, což je pravděpodobnost lepšího zvýšení výkonu. Jedním ze způsobů, jak zlepšit výkon modelu, je poskytnout více ukázek dat školení k algoritmům. Další data, která se z nich učí, jsou další případy, kdy je dokáže správně identifikovat.

## <a name="add-context-to-the-data"></a>Přidat kontext k datům

Význam jednoho datového bodu může být obtížné interpretovat. Vytváření kontextu kolem datových bodů pomáhá algoritmům a odborníkům na danou problematiku lépe rozhodovat. Například skutečnost, že dům má tři ložnicemi, nemá správnou indikaci jeho ceny. Pokud ale přidáte kontext a teď víte, že se nachází v dílčí městě mimo velkou metropolitní oblast, kde je průměrnou věkovou 38, průměrný příjem domácností je $80 000 a školy jsou v horním dvacátém percentilu a potom má algoritmus Další informace, které se zazákladem rozhodnutí. Všechny tyto kontexty je možné přidat jako vstup do modelu Machine Learning jako funkce.

## <a name="use-meaningful-data-and-features"></a>Použití smysluplných dat a funkcí

I když více ukázek dat a funkcí může pomoci zlepšit přesnost modelu, můžou také způsobit šum, protože ne všechna data a funkce jsou smysluplné. Proto je důležité pochopit, jaké funkce jsou ty, které mají největší dopad na rozhodnutí prováděná algoritmem. Používání technik, jako je třeba funkce permutace (PFI), může pomoci identifikovat tyto funkce nejdůležitějšími a nejen vysvětlovat model, ale také použít výstup jako metodu výběru funkce ke snížení množství funkcí s vysokou úrovní šumu v rámci školicích procesů.

Další informace o použití PFI najdete v tématu [vysvětlení modelu předpovědi pomocí funkce permutace důležitost](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

## <a name="cross-validation"></a>Křížové ověření

Křížové ověřování je technikou pro vyhodnocení školení a modelů, které rozdělí data do několika oddílů a navlakuje více algoritmů na těchto oddílech. Tento postup zvyšuje odolnost modelu tím, že podrží data z procesu školení. Kromě zlepšení výkonu u nezpracovaných pozorování v prostředích s omezenými daty může být účinný nástroj pro školení modelů s menší datovou sadou.

Další informace [o použití ověřování v ml.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) najdete na následujícím odkazu.

## <a name="hyperparameter-tuning"></a>Ladění hyperparametrů

Školení modelů strojového učení je iterativní a průzkumné proces. Například to, jaký je optimální počet clusterů při výuce modelu pomocí algoritmu K? Odpověď závisí na mnoha faktorech, například na struktuře dat. Hledání tohoto čísla by vyžadovalo experimentování s různými hodnotami pro k a pak vyhodnocení výkonu za účelem určení, která hodnota je nejlepší. Postup optimalizace těchto parametrů pro vyhledání optimálního modelu se nazývá ladění Hyper-parametru.

## <a name="choose-a-different-algorithm"></a>Zvolit jiný algoritmus

Úlohy strojového učení, jako je regrese a klasifikace, obsahují různé implementace algoritmu. Může se jednat o případ, kdy problém, který se snažíte vyřešit, a způsob, jakým jsou vaše data strukturovaná, není vhodný pro aktuální algoritmus. V takovém případě zvažte použití jiného algoritmu pro váš úkol, abyste zjistili, jestli se z vašich dat lépe učí.

Následující odkaz poskytuje další [pokyny, které algoritmus zvolit](../how-to-choose-an-ml-net-algorithm.md).
