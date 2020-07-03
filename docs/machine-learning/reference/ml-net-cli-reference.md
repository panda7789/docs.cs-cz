---
title: Reference k příkazům rozhraní příkazového řádku ML.NET
description: Přehled, ukázky a Reference k příkazu pro automatický vlak v nástroji CLI ML.NET
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 4c6cb1346c16f6162077d3414140d693de9e0d8c
ms.sourcegitcommit: 182c7b6c079ebcc0e1898dfd9e921b9ef472ea2c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85946938"
---
# <a name="the-mlnet-cli-command-reference"></a>Reference k příkazům rozhraní příkazového řádku ML.NET

`classification`Příkazy, `regression` a `recommendation` jsou hlavní příkazy, které poskytuje nástroj ml.NET CLI. Tyto příkazy umožňují generovat kvalitní modely ML.NET pro klasifikace, regrese a modely doporučení pomocí automatizovaného strojového učení (AutoML) a také ukázkového kódu jazyka C# ke spuštění nebo určení skóre modelu. Kromě toho kód jazyka C# pro výuku modelu je vygenerován pro vás, abyste mohli prozkoumat algoritmus a nastavení modelu.

> [!NOTE]
> Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.

## <a name="overview"></a>Přehled

Příklad použití:

```console
mlnet regression --dataset "cars.csv" --label-col price
```

`mlnet`Příkazy úkolu ml ( `classification` , a `regression` `recommendation` ) generují následující prostředky:

- Serializovaný model. zip ("nejlepší model") je připravený k použití.
- Kód jazyka C#, který se má spustit, nebo určit skóre vygenerovaného modelu
- Kód jazyka C# s školicím kódem, který se používá ke generování tohoto modelu.

První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy a další) k tomu, aby předpovědi s modelem.

Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat konkrétní algoritmus a nastavení modelu.

## <a name="examples"></a>Příklady

Nejjednodušší příkaz CLI pro problém klasifikace (AutoML odvodí většinu konfigurace z poskytnutých dat):

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

Další jednoduchý příkaz CLI pro problém regrese:

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

Vytvoření a výuka klasifikačního modelu s datovou sadou vlaků, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a>Možnosti příkazu

`mlnet`Příkazy úkolu ml ( `classification` , `regression` a `recommendation` ) procházejí několik modelů založených na zadaných možnostech DataSet a ml.NET CLI. Tyto příkazy také vyberou nejlepší model, uloží model jako serializovaný soubor. zip a vygenerují související kód jazyka C# pro bodování a školení.

### <a name="classification-options"></a>Možnosti klasifikace

Běh `mlnet classification` bude zaškolit klasifikační model. Tento příkaz vyberte, pokud chcete, aby model ML kategorizoval data do dvou nebo více tříd (např. mínění analýza).

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a>Možnosti regrese

Běh `mlnet regression` bude mít regresní model. Tento příkaz vyberte, pokud chcete, aby model ML předpovídat číselnou hodnotu (například předpověď ceny).

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a>Možnosti doporučení

Spuštění `mlnet recommendation` bude mít za to poučení s doporučením modelu.  Tento příkaz vyberte, pokud chcete, aby model ML doporučil položky uživatelům na základě hodnocení (např. doporučení produktu).

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

Neplatné možnosti vstupu způsobí, že nástroj rozhraní příkazového řádku vygeneruje seznam platných vstupů a chybovou zprávu.

## <a name="dataset"></a>Datová sada

`--dataset | -d`řetezce

Tento argument poskytuje cestu k jedné z následujících možností:

- Odpověď *: soubor celé datové sady:* Pokud se tato možnost používá a uživatel neposkytuje `--test-dataset` a `--validation-dataset` , pak se k ověřování modelu použije interní ověřování (k skládání atd.) nebo automatizované přístupy k rozdělení dat. V takovém případě bude muset uživatel pouze zadat FilePath pro datovou sadu.

- *B: soubor datové sady školení:* Pokud uživatel také poskytuje datové sady pro ověřování modelu (pomocí `--test-dataset` a volitelně `--validation-dataset` ), pak `--dataset` argument znamená, že má mít pouze "školicí datovou sadu". Například při použití přístupu 80%-20% k ověření kvality modelu a získání metrik přesnosti bude mít "školicí datová sada" 80% dat a "testovací sada" bude obsahovat 20% dat.

## <a name="test-dataset"></a>Testovací datová sada

`--test-dataset | -t`řetezce

Cesta k souboru, který odkazuje na soubor sady dat testu, například při použití 80%-20% přístupu při pravidelném ověřování, aby bylo možné získat metriky přesnosti.

Pokud používáte `--test-dataset` , `--dataset` je také nutné použít.

`--test-dataset`Argument je nepovinný, pokud se nepoužívá--ověření-DataSet. V takovém případě musí uživatel použít tři argumenty.

## <a name="validation-dataset"></a>Ověřovací datová sada

`--validation-dataset | -v`řetezce

Cesta k souboru, který odkazuje na soubor datové sady ověření. Datová sada ověření je volitelná, v každém případě.

Pokud používáte `validation dataset` , musí být toto chování:

- `test-dataset`Argumenty a `--dataset` jsou také požadovány.

- `validation-dataset`Datová sada se používá k odhadování chyby předpovědi pro výběr modelu.

- `test-dataset`Slouží k vyhodnocení chyby generalizace finálního zvoleného modelu. V ideálním případě by měl být testovací sada uchovávána v "trezoru" a musí být uvedena pouze na konci analýzy dat.

V podstatě při použití plus a je `validation dataset` `test dataset` fáze ověření rozdělena do dvou částí:

1. V první části se jenom podíváte na vaše modely a vyberete nejlepší způsob, jak pomocí ověřovacích dat (= ověřování) vybrat nejvhodnější přístup.
2. Pak odhadnete přesnost vybraného přístupu (= test).

Oddělení dat by proto mohlo být 80/10/10 nebo 75/15/10. Například:

- `training-dataset`soubor by měl mít 75% dat.
- `validation-dataset`soubor by měl mít 15% dat.
- `test-dataset`soubor by měl mít 10% dat.

V každém případě se tyto procentní podíly určí uživatelem pomocí rozhraní příkazového řádku, který poskytne soubory, které jsou už rozdělené.

## <a name="label-column"></a>Sloupec popisku

`--label-col`(int nebo String)

Pomocí tohoto argumentu je možné zadat konkrétní sloupec cíl/cíl (proměnnou, kterou chcete odhadnout) pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).

Tento argument se používá pro problémy *klasifikace* a *regrese* .

## <a name="item-column"></a>Sloupec položky

`--item-col`(int nebo String)

Sloupec Item (položka) obsahuje seznam položek, které uživatelé budou hodnotit (pro uživatele se doporučuje používat položky). Tento sloupec lze zadat pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).

Tento argument se používá pouze pro úkol *doporučení* .

## <a name="rating-column"></a>Sloupec hodnocení

`--rating-col`(int nebo String)

Sloupec hodnocení obsahuje seznam hodnocení, která jsou dána pro položky podle uživatelů. Tento sloupec lze zadat pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).

Tento argument se používá pouze pro úkol *doporučení* .

## <a name="user-column"></a>Sloupec uživatele

`--user-col`(int nebo String)

Sloupec uživatel má seznam uživatelů, kteří přidávají hodnocení položkám. Tento sloupec lze zadat pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).

Tento argument se používá pouze pro úkol *doporučení* .

## <a name="ignore-columns"></a>Ignorovat sloupce

`--ignore-columns`řetezce

Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru DataSet, aby nebyly načteny a použity v školicích procesech.

Zadejte názvy sloupců, které chcete ignorovat. K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo ' ' (mezera). Můžete použít uvozovky pro názvy sloupců obsahující prázdné znaky (například "přihlášen").

Příklad:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Má hlavičku

`--has-header`logick

Určete, zda mají soubory DataSet řádek záhlaví.
Možné hodnoty:

- `true`
- `false`

Rozhraní příkazového řádku ML.NET se pokusí tuto vlastnost detekovat, pokud tento argument není zadán uživatelem.

## <a name="train-time"></a>Doba vlaku

`--train-time`řetezce

Ve výchozím nastavení je maximální doba průzkumu nebo výuky 30 minut.

Tento argument nastaví maximální dobu (v sekundách), po kterou má proces prozkoumat více školitelů a konfigurací. Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci. V tomto případě je skutečný čas potřebný čas k vytvoření jedné konfigurace modelu v rámci jedné iterace.

Čas potřebný pro iterace se může lišit v závislosti na velikosti datové sady.

## <a name="cache"></a>Mezipaměť

`--cache`řetezce

Pokud použijete ukládání do mezipaměti, načte se celá datová sada školení v paměti.

V případě malých a středně velkých datových sad může použití mezipaměti významně zlepšit výkon školení, což znamená, že doba přípravy může být kratší, než když mezipaměť nepoužíváte.

U rozsáhlých datových sad ale načítání všech dat v paměti může negativně ovlivnit vzhledem k tomu, že může dojít k dostatku paměti. Při školení s rozsáhlými soubory DataSet a nepoužíváte-li mezipaměť, bude ML.NET streamovat datové bloky dat z disku, když potřebuje načíst více dat během školení.

Můžete určit tyto hodnoty:

`on`: Vynutí, aby se při výuce použila mezipaměť.
`off`: Vynutí, aby se mezipaměť nepoužívala při výuce.
`auto`: V závislosti na heuristikách AutoML se mezipaměť použije nebo ne. Malé nebo střední datové sady budou obvykle používat mezipaměť a velké datové sady nebudou používat mezipaměť, pokud použijete `auto` volbu.

Pokud parametr nezadáte `--cache` , `auto` použije se ve výchozím nastavení konfigurace mezipaměti.

## <a name="name"></a>Name

`--name`řetezce

Název vytvořeného výstupního projektu nebo řešení. Pokud název nezadáte, použije se název `sample-{mltask}` .

Soubor modelu ML.NET (. Soubor ZIP) bude mít stejný název i.

## <a name="output-path"></a>Výstupní cesta

`--output | -o`řetezce

Kořenové umístění/složka, do které se umístí vygenerovaný výstup Výchozí je aktuální adresář.

## <a name="verbosity"></a>Podrobnosti

`--verbosity | -v`řetezce

Nastaví úroveň podrobností standardního výstupu.

Povolené hodnoty jsou následující:

- `q[uiet]`
- `m[inimal]`(ve výchozím nastavení)
- `diag[nostic]`(úroveň informací o protokolování)

Ve výchozím nastavení by měl nástroj rozhraní příkazového řádku při práci zobrazit některé minimální zpětné vazby ( `minimal` ), jako je třeba zmínku o tom, že funguje, a pokud je to možné, kolik času zbývá nebo kolik času bylo dokončeno.

## <a name="help"></a>Nápověda

`-h |--help`

Vytiskne nápovědu pro příkaz s popisem pro každý parametr příkazu.

## <a name="see-also"></a>Viz také

- [Postup instalace nástroje ML.NET CLI](../how-to-guides/install-ml-net-cli.md)
- [Přehled rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET](../tutorials/sentiment-analysis-cli.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
