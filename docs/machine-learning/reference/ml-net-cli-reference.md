---
title: Reference k příkazům rozhraní příkazového řádku ML.NET
description: Přehled, ukázky a Reference k příkazu pro automatický vlak v nástroji CLI ML.NET
ms.date: 12/18/2019
ms.openlocfilehash: 537f8d361c170378f5fe8cf454320831d7c8cbf2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449696"
---
# <a name="the-mlnet-cli-command-reference"></a>Reference k příkazům rozhraní příkazového řádku ML.NET

Příkaz `auto-train` je hlavním příkazem, který poskytuje nástroj ML.NET CLI. Příkaz umožňuje vygenerovat dobrý model ML.NET s využitím automatizovaného strojového učení (AutoML) a také ukázkový C# kód pro spuštění nebo určení skóre modelu. Kromě toho C# kód pro výuku modelu je vygenerován pro vás, abyste mohli prozkoumat algoritmus a nastavení modelu.

> [!NOTE]
> Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.

## <a name="overview"></a>Přehled

Příklad použití:

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

Příkaz `mlnet auto-train` generuje následující prostředky:

- Serializovaný model. zip ("nejlepší model") je připravený k použití.
- C#kód, který se má spustit, nebo vyhodnotit skóre generovaný model.
- C#kód s školicím kódem, který slouží ke generování tohoto modelu.

První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy a další) k tomu, aby předpovědi s modelem.

Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat konkrétní algoritmus a nastavení modelu.

## <a name="examples"></a>Příklady

Nejjednodušší příkaz CLI pro problém binární klasifikace (AutoML odvodí většinu konfigurace z poskytnutých dat):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Další jednoduchý příkaz CLI pro problém regrese:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Vytvoření a výuka modelu binární klasifikace s datovou sadou vlaků, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Možnosti příkazu

`mlnet auto-train` vlacích v závislosti na zadané datové sadě a nakonec vybírá nejlepší model, uloží ho jako serializovaný soubor. zip a vygeneruje související C# kód pro bodování a školení.

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

Neplatné možnosti vstupu způsobí, že nástroj rozhraní příkazového řádku vygeneruje seznam platných vstupů a chybovou zprávu.

## <a name="task"></a>Úkol

`--task | --mltask | -T` (String)

Jeden řetězec, který poskytuje problém k řešení ML. Například kterákoli z následujících úloh (rozhraní příkazového řádku bude nakonec podporovat všechny úlohy podporované v AutoML):

- `regression` – vyberte, jestli se má pro předpověď číselné hodnoty použít model ML.
- `binary-classification` – vyberte, jestli má výsledek modelu ML dvě možné kategorií logické hodnoty (0 nebo 1).
- `multiclass-classification` – vyberte, jestli má výsledek modelu ML více kategorií možných hodnot.

V tomto argumentu by měla být uvedena pouze jedna úloha ML.

## <a name="dataset"></a>Datová sada

`--dataset | -d` (String)

Tento argument poskytuje cestu k jedné z následujících možností:

- Odpověď *: soubor celé datové sady:* Pokud tato možnost používá a uživatel neposkytuje `--test-dataset` a `--validation-dataset`, pak se k ověřování modelu použije interní ověřování (k přeložení atd.) nebo automatizované přístupy k rozdělení dat. V takovém případě bude muset uživatel pouze zadat FilePath pro datovou sadu.

- *B: soubor datové sady školení:* Pokud uživatel také poskytuje datové sady pro ověřování modelu (pomocí `--test-dataset` a volitelně `--validation-dataset`), pak argument `--dataset` znamená, že má pouze "školicí sadu". Například při použití přístupu 80%-20% k ověření kvality modelu a získání metrik přesnosti bude mít "školicí datová sada" 80% dat a "testovací sada" bude obsahovat 20% dat.

## <a name="test-dataset"></a>Testovací datová sada

`--test-dataset | -t` (String)

Cesta k souboru, který odkazuje na soubor sady dat testu, například při použití 80%-20% přístupu při pravidelném ověřování, aby bylo možné získat metriky přesnosti.

Pokud používáte `--test-dataset`, vyžaduje se také `--dataset`.

Argument `--test-dataset` je nepovinný, pokud se nepoužívá--ověření-DataSet. V takovém případě musí uživatel použít tři argumenty.

## <a name="validation-dataset"></a>Ověření datové sady

`--validation-dataset | -v` (String)

Cesta k souboru, který odkazuje na soubor datové sady ověření. Datová sada ověření je volitelná, v každém případě.

Pokud používáte `validation dataset`, mělo by se jednat o toto chování:

- Jsou také požadovány argumenty `test-dataset` a `--dataset`.

- Datová sada `validation-dataset` slouží k odhadu chyby předpovědi pro výběr modelu.

- `test-dataset` se používá pro vyhodnocení chyby generalizace finálního zvoleného modelu. V ideálním případě by měl být testovací sada uchovávána v "trezoru" a musí být uvedena pouze na konci analýzy dat.

V podstatě při použití `validation dataset` a `test dataset`je fáze ověření rozdělená na dvě části:

1. V první části se jenom podíváte na vaše modely a vyberete nejlepší způsob, jak pomocí ověřovacích dat (= ověřování) vybrat nejvhodnější přístup.
2. Pak odhadnete přesnost vybraného přístupu (= test).

Oddělení dat by proto mohlo být 80/10/10 nebo 75/15/10. Například:

- soubor `training-dataset` by měl mít 75% dat.
- soubor `validation-dataset` by měl mít 15% dat.
- soubor `test-dataset` by měl mít 10% dat.

V každém případě se tyto procentní podíly určí uživatelem pomocí rozhraní příkazového řádku, který poskytne soubory, které jsou už rozdělené.

## <a name="label-column-name"></a>Název sloupce popisku

`--label-column-name | -n` (String)

Pomocí tohoto argumentu je možné zadat konkrétní sloupec cíl/cíl (proměnnou, kterou chcete odhadnout) pomocí názvu sloupce nastaveného v záhlaví datové sady.

Tento argument se používá jenom pro úlohy pod dohledem ML, jako je například *problém s klasifikací*. Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.

## <a name="label-column-index"></a>Index sloupce popisku

`--label-column-index | -i` (int)

Pomocí tohoto argumentu se dá určit konkrétní sloupec cíl/cíl (proměnná, kterou chcete předpovědět), pomocí číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají na 1).

*Poznámka:* Pokud uživatel používá taky `--label-column-name`, `--label-column-name` je ten, který se používá.

Tento argument se používá jenom pro úlohu pod dohledem ML, jako je například *problém s klasifikací*. Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.

## <a name="ignore-columns"></a>Ignorovat sloupce

`--ignore-columns | -I` (String)

Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru DataSet, aby nebyly načteny a použity v školicích procesech.

Zadejte názvy sloupců, které chcete ignorovat. K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo ' ' (mezera). Můžete použít uvozovky pro názvy sloupců obsahující prázdné znaky (například "přihlášen").

Příklad:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Má hlavičku

`--has-header | -h` (bool)

Určete, zda mají soubory DataSet řádek záhlaví.
Možné hodnoty:

- `true`
- `false`

Výchozí hodnota je `true`, pokud tento argument není zadán uživatelem.

Aby bylo možné použít argument `--label-column-name`, musíte mít v souboru DataSet hlavičku a `--has-header` nastavit na `true` (což je ve výchozím nastavení).

## <a name="max-exploration-time"></a>Maximální doba průzkumu

`--max-exploration-time | -x` (String)

Ve výchozím nastavení je maximální doba průzkumu 30 minut.

Tento argument nastaví maximální dobu (v sekundách), po kterou má proces prozkoumat více školitelů a konfigurací. Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci. V tomto případě je skutečný čas potřebný čas k vytvoření jedné konfigurace modelu v rámci jedné iterace.

Čas potřebný pro iterace se může lišit v závislosti na velikosti datové sady.

## <a name="cache"></a>Mezipaměť

`--cache | -c` (String)

Pokud použijete ukládání do mezipaměti, načte se celá datová sada školení v paměti.

V případě malých a středně velkých datových sad může použití mezipaměti významně zlepšit výkon školení, což znamená, že doba přípravy může být kratší, než když mezipaměť nepoužíváte.

U rozsáhlých datových sad ale načítání všech dat v paměti může negativně ovlivnit vzhledem k tomu, že může dojít k dostatku paměti. Při školení s rozsáhlými soubory DataSet a nepoužíváte-li mezipaměť, bude ML.NET streamovat datové bloky dat z disku, když potřebuje načíst více dat během školení.

Můžete určit tyto hodnoty:

`on`: Vynutí použití mezipaměti při školení.
`off`: vynutí, aby se mezipaměť nepoužívala při výuce.
`auto`: v závislosti na heuristikách AutoML se mezipaměť použije nebo ne. Malé nebo střední datové sady budou obvykle používat mezipaměť a velké datové sady nebudou používat mezipaměť, pokud použijete možnost `auto`.

Pokud parametr `--cache` nezadáte, použije se ve výchozím nastavení mezipaměť `auto` konfigurace.

## <a name="name"></a>Název

`--name | -N` (String)

Název vytvořeného výstupního projektu nebo řešení. Pokud název nezadáte, použije se název `sample-{mltask}`.

Soubor modelu ML.NET (. Soubor ZIP) bude mít stejný název i.

## <a name="output-path"></a>Výstupní cesta

`--output-path | -o` (String)

Kořenové umístění/složka, do které se umístí vygenerovaný výstup Výchozí je aktuální adresář.

## <a name="verbosity"></a>Verbosity

`--verbosity | -V` (String)

Nastaví úroveň podrobností standardního výstupu.

Povolené hodnoty jsou:

- `q[uiet]`
- `m[inimal]` (ve výchozím nastavení)
- `diag[nostic]` (úroveň informací o protokolování)

Ve výchozím nastavení by měl nástroj rozhraní příkazového řádku při práci zobrazit určitou minimální odezvu (minimální), jako je třeba zmínku o tom, že funguje, a pokud je to možné, kolik času zbývá nebo kolik času bylo dokončeno.

## <a name="help"></a>Nápověda

`-h|--help`

Vytiskne nápovědu pro příkaz s popisem pro každý parametr příkazu.

## <a name="see-also"></a>Viz také

- [Postup instalace nástroje ML.NET CLI](../how-to-guides/install-ml-net-cli.md)
- [Přehled rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET](../tutorials/sentiment-analysis-cli.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
