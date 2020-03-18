---
title: odkaz příkazu ML.NET CLI
description: Přehled, ukázky a odkaz na příkaz automatického tácení v nástroji ML.NET CLI.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848922"
---
# <a name="the-mlnet-cli-command-reference"></a>Odkaz na příkaz ML.NET CLI

Příkaz `auto-train` je hlavním příkazem poskytovaným nástrojem ML.NET CLI. Příkaz umožňuje generovat kvalitní ML.NET modelu pomocí automatizovaného strojového učení (AutoML) a také v příkladu kódu Jazyka C# pro spuštění a skóre tohoto modelu. Kromě toho je generován kód Jazyka C# pro trénování modelu pro výzkum algoritmu a nastavení modelu.

> [!NOTE]
> Toto téma odkazuje na ML.NET cli a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiál může být může být možné změnit.

## <a name="overview"></a>Přehled

Příklad použití:

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

Příkaz `mlnet auto-train` generuje následující datové zdroje:

- Serializovaný model .zip ("nejlepší model") připravený k použití.
- C# kód ke spuštění/skóre, které vygenerovaly model.
- C# kód s trénovací kód slouží ke generování tohoto modelu.

První dva datové zdroje lze přímo použít ve vašich aplikacích pro koncové uživatele (ASP.NET základní webové aplikace, služby, desktopové aplikace a další) k předpovědi s modelem.

Třetí prostředek, trénovací kód, ukazuje, jaký ML.NET kód rozhraní API byl použit rozhraní matné rozhraní API k trénování generovaného modelu, takže můžete prozkoumat konkrétní algoritmus a nastavení modelu.

## <a name="examples"></a>Příklady

Nejjednodušší příkaz CLI pro problém binární klasifikace (AutoML odvodí většinu konfigurace z poskytnutých dat):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Další jednoduchý příkaz CLI pro regresní problém:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Vytvořte a trénujte model binární klasifikace s datovou sadou vlakových dat, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Volby příkazů

`mlnet auto-train`trénuje více modelů založených na poskytnuté datové sadě a nakonec vybere nejlepší model, uloží jej jako serializovaný soubor ZIP plus generuje související kód C# pro vyhodnocování a trénování.

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

Neplatné možnosti zadávání způsobí, že nástroj rozhraní se konstatování rozhraní A CLI vyzařuje seznam platných vstupů a chybovou zprávu.

## <a name="task"></a>Úkol

`--task | --mltask | -T`(řetězec)

Jeden řetězec poskytující problém ML k vyřešení. Například některý z následujících úkolů (příkaz příkazpříkaz příkazového konto nakonec bude podporovat všechny úkoly podporované v automatické ml):

- `regression`- Zvolte, zda bude model ML použit k předvídání číselné hodnoty
- `binary-classification`- Zvolte, zda má výsledek modelu ML dvě možné kategorie logických hodnot (0 nebo 1).
- `multiclass-classification`- Zvolte, zda má výsledek modelu ML více kategorických možných hodnot.

V tomto argumentu by měl být poskytnut pouze jeden úkol ML.

## <a name="dataset"></a>Datová sada

`--dataset | -d`(řetězec)

Tento argument poskytuje cestu k souboru jedné z následujících možností:

- *A: Celý soubor datové sady:* Pokud používáte tuto možnost a `--test-dataset` `--validation-dataset`uživatel neposkytuje a , pak křížové ověření (k-fold, atd.) nebo automatizované přístupy rozdělení dat budou použity interně pro ověření modelu. V takovém případě bude uživatel potřebovat pouze poskytnout cestu souboru datové sady.

- *B: Soubor trénovací datové sady:* Pokud uživatel také poskytuje datové sady pro `--test-dataset` ověření `--validation-dataset`modelu (pomocí a volitelně ), pak `--dataset` argument znamená mít pouze "trénovací datové sady". Například při použití 80 % - 20% přístup k ověření kvality modelu a získat metriky přesnosti, "trénovací datové sady" bude mít 80 % dat a "testovací datové sady" bude mít 20 % dat.

## <a name="test-dataset"></a>Testovací datová sada

`--test-dataset | -t`(řetězec)

Cesta k souboru směřující k souboru testovací datové sady, například při použití přístupu 80 % až 20 % při provádění pravidelných ověření za účelem získání metrik přesnosti.

Pokud `--test-dataset`používáte `--dataset` , pak je také nutné.

Argument `--test-dataset` je volitelný, pokud --validation-dataset se používá. V takovém případě musí uživatel použít tři argumenty.

## <a name="validation-dataset"></a>Ověřovací datová sada

`--validation-dataset | -v`(řetězec)

Cesta k souboru směřující k ověřovacímu souboru datové sady. Ověřovací datová sada je v každém případě volitelná.

Pokud používáte `validation dataset`, chování by mělo být:

- A `test-dataset` `--dataset` argumenty jsou také požadovány.

- Datová `validation-dataset` sada se používá k odhadu chyby předpovědi pro výběr modelu.

- Slouží `test-dataset` k posouzení chyby generalizace konečného zvoleného modelu. V ideálním případě by testovací sada měla být uložena v "trezoru" a měla by být vyvedena pouze na konci analýzy dat.

V podstatě, `validation dataset` při `test dataset`použití plus , fáze validace je rozdělena do dvou částí:

1. V první části se stačí podívat na své modely a vybrat nejvýkonnější přístup pomocí ověřovacích dat (=ověření)
2. Poté odhadnete přesnost zvoleného přístupu (=test).

Oddělení údajů by proto mohlo být 80/10/10 nebo 75/15/10. Například:

- `training-dataset`soubor by měl mít 75% dat.
- `validation-dataset`soubor by měl mít 15% dat.
- `test-dataset`soubor by měl mít 10% dat.

V každém případě budou tyto procenta rozhodovat uživatel pomocí rozhraní se kli, který poskytne soubory, které jsou již rozděleny.

## <a name="label-column-name"></a>Název sloupce popisku

`--label-column-name | -n`(řetězec)

Pomocí tohoto argumentu lze zadat konkrétní sloupec cíle/cíle (proměnnou, kterou chcete předpovědět) pomocí názvu sloupce nastaveného v záhlaví datové sady.

Tento argument se používá pouze pro úkoly ML pod dohledem, jako je *například problém klasifikace*. Nelze jej použít pro úlohy ML bez dohledu, jako je *clustering*.

## <a name="label-column-index"></a>Index sloupce popisku

`--label-column-index | -i`(int)

Pomocí tohoto argumentu lze zadat konkrétní sloupec cíle/cíle (proměnnou, kterou chcete předpovědět) pomocí číselného indexu sloupce v souboru datové sady (Hodnoty indexu sloupce začínají na 1).

*Poznámka:* Pokud uživatel také používá `--label-column-name`, `--label-column-name` je ten, který se používá.

Tento argument se používá pouze pro úkol ml pod dohledem, jako je *například problém klasifikace*. Nelze jej použít pro úlohy ML bez dohledu, jako je *clustering*.

## <a name="ignore-columns"></a>Ignorovat sloupce

`--ignore-columns | -I`(řetězec)

Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru datové sady, aby nebyly načteny a používány trénovacími procesy.

Zadejte názvy sloupců, které chcete ignorovat. K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo '' (mezera). U názvů sloupců obsahujících mezery (např.

Příklad:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Má záhlaví

`--has-header | -h`(bool)

Určete, zda mají soubory datové sady řádek záhlaví.
Možné hodnoty:

- `true`
- `false`

Výchozí hodnota je, `true` pokud tento argument není určen uživatelem.

Chcete-li použít `--label-column-name` argument, musíte mít záhlaví v souboru `--has-header` datové `true` sady a nastavit na (což je ve výchozím nastavení).

## <a name="max-exploration-time"></a>Maximální doba průzkumu

`--max-exploration-time | -x`(řetězec)

Ve výchozím nastavení je maximální doba průzkumu 30 minut.

Tento argument nastaví maximální čas (v sekundách) pro proces prozkoumat více školitelů a konfigurace. Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci. V tomto případě skutečný čas je požadovaný čas k vytvoření jedné konfigurace modelu v jedné iteraci.

Potřebný čas pro iterací se může lišit v závislosti na velikosti datové sady.

## <a name="cache"></a>Mezipaměť

`--cache | -c`(řetězec)

Pokud používáte ukládání do mezipaměti, bude celá trénovací datová sada načtena do paměti.

U malých a středních datových sad může použití mezipaměti výrazně zlepšit výkon školení, což znamená, že doba školení může být kratší než při nepoužívání mezipaměti.

U velkých datových sad však načítání všech dat v paměti může mít negativní dopad, protože může dojít k nedostatku paměti. Při trénování s velkými soubory datových sad a nepoužíváte mezipaměť, ML.NET bude streamování bloků dat z jednotky, když potřebuje načíst více dat při trénování.

Můžete určit tyto hodnoty:

`on`: Vynutí použití mezipaměti při trénování.
`off`: Vynutí, aby se mezipaměť při trénování nepoužívala.
`auto`: V závislosti na heuristici automatické homl bude mezipaměť použita či nikoli. Malé a střední datové sady obvykle používají mezipaměť a velké datové `auto` sady nebudou používat mezipaměť, pokud použijete volbu.

Pokud `--cache` parametr nezadáte, bude konfigurace `auto` mezipaměti použita ve výchozím nastavení.

## <a name="name"></a>Name (Název)

`--name | -N`(řetězec)

Název vytvořeného výstupního projektu nebo řešení. Pokud není zadán žádný `sample-{mltask}` název, bude použit název.

Soubor modelu ML.NET (. ZIP) dostane stejný název, stejně.

## <a name="output-path"></a>Výstupní cesta

`--output-path | -o`(řetězec)

Kořenové umístění/složka pro umístění generovaného výstupu. Výchozí je aktuální adresář.

## <a name="verbosity"></a>Podrobnosti

`--verbosity | -V`(řetězec)

Nastaví úroveň podrobností standardního výstupu.

Povolené hodnoty jsou následující:

- `q[uiet]`
- `m[inimal]`(ve výchozím nastavení)
- `diag[nostic]`(úroveň informací o protokolování)

Ve výchozím nastavení by měl nástroj zaokreslování vykazovat minimální zpětnou vazbu (minimální) při práci, například zmínku, že funguje a pokud je to možné, kolik času zbývá nebo kolik % času je dokončeno.

## <a name="help"></a>Nápověda

`-h|--help`

Vytiskne nápovědu pro příkaz s popisem pro parametr každého příkazu.

## <a name="see-also"></a>Viz také

- [Jak nainstalovat nástroj ML.NET CLI](../how-to-guides/install-ml-net-cli.md)
- [Přehled ML.NET CLI](../automate-training-with-cli.md)
- [Kurz: Analýza mínění pomocí ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
