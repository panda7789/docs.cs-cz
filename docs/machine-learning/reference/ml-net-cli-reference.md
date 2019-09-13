---
title: Příkaz pro automatické učení v nástroji CLI ML.NET
description: Přehled, ukázky a Reference k příkazu pro automatický vlak v nástroji CLI ML.NET
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929204"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>Příkaz Auto-vlak v ML.NET CLI

> [!NOTE]
> Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.

`auto-train` Příkaz je hlavním příkazem, který poskytuje nástroj ml.NET CLI. Příkaz umožňuje vygenerovat kvalitní model ML.NET (soubor s serializovaným modelem. zip) a ukázkový C# kód pro spuštění nebo určení skóre modelu. Kromě toho se C# kód pro vytvoření nebo výuku modelu vygeneruje také pro vás, abyste mohli prozkoumat, jaký algoritmus a nastavení používá pro tento vygenerovaný "nejlepší model".

Tyto prostředky můžete vygenerovat z vlastních datových sad, aniž byste je museli kódovat sami, takže také zlepší vaši produktivitu, i když už znáte ML.NET.

V současné době jsou úlohy ML podporované rozhraním příkazového řádku ML.NET:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Pozdější Další úkoly strojového učení, například
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Příklad použití na příkazovém řádku:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` Příkaz vygeneruje následující prostředky:

- Serializovaný model. zip ("nejlepší model") je připravený k použití.
- C#kód pro spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).
- C#kód s školicím kódem, který slouží k vygenerování tohoto modelu (vzdělávací účely).

První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.) k tomu, aby se předpovědi s tímto generovaným modelem ML.

Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat, jaké konkrétní Trainer/algoritmus a Hyper-Parameters byly vybrány rozhraním příkazového řádku a modulem ML.NET AutoML.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>Příkaz Auto-vlak používá modul AutoML.

Rozhraní příkazového řádku používá modul ML.NET AutoML (balíček NuGet) k inteligentnímu vyhledávání nejlepších modelů kvality, jak je znázorněno v následujícím diagramu:

![Obrázek](./media/ml-net-automl-working-diagram.png "AutoML Engine pracuje v rozhraní příkazového řádku ml.NET")

Při spuštění nástroje ML.NET CLI pomocí příkazu auto-vlak-Command se zobrazí nástroj, který zkouší mnoho iterací s různými algoritmy a kombinacemi konfigurace.

## <a name="reference-for-auto-train-command"></a>Reference pro příkaz Auto-vlak

## <a name="examples"></a>Příklady

Nejjednodušší příkaz CLI pro problém binární klasifikace (AutoML bude muset odvodit většinu konfigurace z poskytnutých dat):

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Další jednoduchý příkaz CLI pro problém regrese:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Vytvoření a výuka modelu binární klasifikace s datovou sadou vlaků, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Name

`mlnet auto-train`– Vlaky s více modely (n) založené na zadané datové sadě a nakonec vyberou nejlepší model, uloží ho jako serializovaný soubor. zip a vygeneruje související C# kód pro bodování a školení.

## <a name="synopsis"></a>Stručný obsah

```console
> mlnet auto-train

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

Neplatné možnosti vstupu by měly způsobit, že nástroj rozhraní příkazového řádku vygeneruje seznam platných vstupů a chybové zprávy s vysvětlením, který ARG chybí, pokud se jedná o tento případ.

## <a name="options"></a>Možnosti

 ----------------------------------------------------------

`--task | --mltask | -T`řetezce

Jeden řetězec, který poskytuje problém k řešení ML. Například kterákoli z následujících úloh (rozhraní příkazového řádku bude nakonec podporovat všechny úlohy podporované v AutoML):

- `regression`– Vyberte, jestli se má pro předpověď číselné hodnoty použít model ML.
- `binary-classification`– Vyberte, jestli má výsledek modelu ML dvě možné kategorií logické hodnoty (0 nebo 1).
- `multiclass-classification`– Vyberte, jestli má výsledek modelu ML více kategorií možných hodnot.

V budoucnu se vydává další úlohy a scénáře v `recommendations`ml `clustering` , `ranking` jako například, a budou podporovány.

 V tomto argumentu by měla být uvedena pouze jedna úloha ML.

 ----------------------------------------------------------

`--dataset | -d`řetezce

Tento argument poskytuje cestu k jedné z následujících možností:

- *URČITÉHO Celý soubor datové sady:* Pokud se tato možnost používá a uživatel neposkytuje `--test-dataset` a `--validation-dataset`, pak se k ověřování modelu použije interní ověřování (k skládání atd.) nebo automatizované přístupy k rozdělení dat. V takovém případě bude muset uživatel pouze zadat FilePath pro datovou sadu.

- *B: Soubor datové sady školení:* Pokud uživatel také poskytuje datové sady pro ověřování modelu (pomocí `--test-dataset` a volitelně `--validation-dataset`), pak `--dataset` argument znamená, že má mít pouze "školicí datovou sadu". Například při použití přístupu 80%-20% k ověření kvality modelu a získání metrik přesnosti bude mít "školicí datová sada" 80% dat a "testovací sada" bude obsahovat 20% dat.

----------------------------------------------------------

`--test-dataset | -t`řetezce

Cesta k souboru, který odkazuje na soubor sady dat testu, například při použití 80%-20% přístupu při pravidelném ověřování, aby bylo možné získat metriky přesnosti.

Pokud používáte `--test-dataset` `--dataset` , je také nutné použít.

`--test-dataset` Argument je nepovinný, pokud se nepoužívá--ověření-DataSet. V takovém případě musí uživatel použít tři argumenty.

----------------------------------------------------------

`--validation-dataset | -v`řetezce

Cesta k souboru, který odkazuje na soubor datové sady ověření. Datová sada ověření je volitelná, v každém případě.

Pokud používáte `validation dataset`, musí být toto chování:

- Argumenty `test-dataset` a`--dataset` jsou také požadovány.

- `validation-dataset` Datová sada se používá k odhadování chyby předpovědi pro výběr modelu.

- `test-dataset` Slouží k vyhodnocení chyby generalizace finálního zvoleného modelu. V ideálním případě by měl být testovací sada uchovávána v "trezoru" a musí být uvedena pouze na konci analýzy dat.

V podstatě při použití `validation dataset` `test dataset`plus a je fáze ověření rozdělena do dvou částí:

1. V první části se jenom podíváte na vaše modely a vyberete nejlepší způsob, jak pomocí ověřovacích dat (= ověřování) vybrat nejvhodnější přístup.
2. Pak odhadnete přesnost vybraného přístupu (= test).

Oddělení dat by proto mohlo být 80/10/10 nebo 75/15/10. Příklad:

- `training-dataset`soubor by měl mít 75% dat.
- `validation-dataset`soubor by měl mít 15% dat.
- `test-dataset`soubor by měl mít 10% dat.

V každém případě se tyto procentní podíly určí uživatelem pomocí rozhraní příkazového řádku, který poskytne soubory, které jsou už rozdělené.

----------------------------------------------------------

`--label-column-name | -n`řetezce

Pomocí tohoto argumentu je možné zadat konkrétní sloupec cíl/cíl (proměnnou, kterou chcete odhadnout) pomocí názvu sloupce nastaveného v záhlaví datové sady.

Tento argument se používá jenom pro úlohy pod dohledem ML, jako je například *problém s klasifikací*. Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.

----------------------------------------------------------

`--label-column-index | -i`hmot

Pomocí tohoto argumentu se dá určit konkrétní sloupec cíl/cíl (proměnná, kterou chcete předpovědět), pomocí číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají na 1).

*Poznámka:* Pokud uživatel také používá `--label-column-name` `--label-column-name` , je ten, který se používá.

Tento argument se používá jenom pro úlohu pod dohledem ML, jako je například *problém s klasifikací*. Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.

----------------------------------------------------------

`--ignore-columns | -I`řetezce

Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru DataSet, aby nebyly načteny a použity v školicích procesech.

Zadejte názvy sloupců, které chcete ignorovat. K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo ' ' (mezera). Můžete použít uvozovky pro názvy sloupců obsahující prázdné znaky (například "přihlášen").

Příklad:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h`logick

Určete, zda mají soubory DataSet řádek záhlaví.
Možné hodnoty jsou:

- `true`
- `false`

Výchozí hodnota je `true` , pokud uživatel nezadá tento argument.

Aby bylo možné použít `--label-column-name` argument, je nutné mít v souboru DataSet hlavičku a `--has-header` nastavit na `true` (což je ve výchozím nastavení výchozí).

----------------------------------------------------------

`--max-exploration-time | -x`řetezce

Ve výchozím nastavení je maximální doba průzkumu 30 minut.

Tento argument nastaví maximální dobu (v sekundách), po kterou má proces prozkoumat více školitelů a konfigurací. Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci. V tomto případě je skutečný čas potřebný čas k vytvoření jedné konfigurace modelu v rámci jedné iterace.

Čas potřebný pro iterace se může lišit v závislosti na velikosti datové sady.

----------------------------------------------------------

`--cache | -c`řetezce

Pokud použijete ukládání do mezipaměti, načte se celá datová sada školení v paměti.

V případě malých a středně velkých datových sad může použití mezipaměti významně zlepšit výkon školení, což znamená, že doba přípravy může být kratší, než když mezipaměť nepoužíváte.

U rozsáhlých datových sad ale načítání všech dat v paměti může negativně ovlivnit vzhledem k tomu, že může dojít k dostatku paměti. Při školení s rozsáhlými soubory DataSet a nepoužíváte-li mezipaměť, bude ML.NET streamovat datové bloky dat z disku, když potřebuje načíst více dat během školení.

Můžete zadat následující hodnoty:

`on`: Vynutí použití mezipaměti při školení.
`off`: Vynutí, aby se mezipaměť nepoužívala při výuce.
`auto`: V závislosti na heuristikách AutoML se mezipaměť použije nebo ne. Malé nebo střední datové sady budou obvykle používat mezipaměť a velké datové sady nebudou používat mezipaměť, pokud použijete `auto` volbu.

Pokud `--cache` parametr nezadáte, použije se ve výchozím nastavení `auto` konfigurace mezipaměti.

----------------------------------------------------------

`--name | -N`řetezce

Název vytvořeného výstupního projektu nebo řešení. Pokud název nezadáte, použije se název `sample-{mltask}` .

Soubor modelu ML.NET (. Soubor ZIP) bude mít stejný název i.

----------------------------------------------------------

`--output-path | -o`řetezce

Kořenové umístění/složka, do které se umístí vygenerovaný výstup Výchozí je aktuální adresář.

----------------------------------------------------------

`--verbosity | -V`řetezce

Nastaví úroveň podrobností standardního výstupu.

Povolené hodnoty jsou následující:

- `q[uiet]`
- `m[inimal]`(ve výchozím nastavení)
- `diag[nostic]`(úroveň informací o protokolování)

Ve výchozím nastavení by měl nástroj rozhraní příkazového řádku při práci zobrazit určitou minimální odezvu (minimální), jako je třeba zmínku o tom, že funguje, a pokud je to možné, kolik času zbývá nebo kolik času bylo dokončeno.

----------------------------------------------------------

`-h|--help`

Vytiskne nápovědu pro příkaz s popisem pro každý parametr příkazu.

----------------------------------------------------------

## <a name="see-also"></a>Viz také:

- [Postup instalace nástroje ML.NET CLI](../how-to-guides/install-ml-net-cli.md)
- [Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: Automatické generování binárního klasifikátoru pomocí rozhraní příkazového řádku ML.NET](../tutorials/mlnet-cli.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
