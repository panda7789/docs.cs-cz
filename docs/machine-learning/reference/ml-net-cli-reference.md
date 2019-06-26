---
title: Příkaz automaticky trénování v nástroji příkazového řádku ML.NET
description: Přehled ukázky a referenční informace pro příkaz automaticky trénování v nástroji ML.NET rozhraní příkazového řádku.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 73bae0165af76226152de322d2951086646a1a1d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397665"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>Příkaz "automaticky – train" v rozhraní příkazového řádku ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET rozhraní příkazového řádku a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.

`auto-train` Příkaz je hlavní příkaz poskytnutých nástrojem ML.NET rozhraní příkazového řádku. Tento příkaz umožňuje vygenerovat modelu ML.NET kvalitních (serializovaný model soubor .zip) plus v příkladu C# kód pro spuštění/určení skóre modelu. Kromě toho C# kód k vytvoření a trénování modelu také vygeneruje se pro vás Chcete-li zjistit, jaké algoritmus a nastavení používá pro, který vygeneruje "nejlepší model".

Tyto prostředky můžete vygenerovat z vlastní datové sady bez kódování sami, tak i v případě, že již znáte ML.NET také zlepšuje produktivitu.

V současné době nepodporuje rozhraní příkazového řádku ML.NET úlohy ML jsou:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Budoucnost: Další strojového učení úlohy, jako například
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Příklad použití na příkazovém řádku:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` Příkaz vytvoří následující prostředky:

- Serializovaný model soubor .zip ("nejlepší model") připravený k použití.
- C#vytvořit kód pro spuštění/skóre, které model (k následné predikci ve vašich aplikacích koncového uživatele pomocí tohoto modelu).
- C#kód s kódem školení sloužící ke generování tohoto modelu (výukové účely).

První dva prostředky lze použít přímo v aplikacích s koncovým uživatelem (webové aplikace ASP.NET Core, služby, aplikace klasické pracovní plochy, atd.) k následné predikci s generovanou modelu ML.

Třetí asset školení kód ukazuje, jaký kód ML.NET API rozhraní příkazového řádku použil tak moct trénovat vygenerovaný model, takže si můžete zjistit, jaké konkrétní trainer/algoritmus a hyperparametrů byly vybrány tak, že rozhraní příkazového řádku a modul ML.NET AutoML.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>Příkaz "automaticky – train" používá modul AutoML

Rozhraní příkazového řádku používá modul ML.NET AutoML (balíček NuGet) k vyhledání inteligentně nejlepší kvality modelů, jak je znázorněno v následujícím diagramu:

![Obrázek](./media/ml-net-automl-working-diagram.png "AutoML modul práci uvnitř rozhraní příkazového řádku ML.NET")

Při spuštění nástroje příkazového řádku ML.NET s "Automatické – train příkaz, zobrazí se vám nástroj při více iterací s využitím různých algoritmů a kombinace konfigurace.

## <a name="reference-for-auto-train-command"></a>Referenční informace pro příkaz "Automatické – train"

## <a name="examples"></a>Příklady

Nejjednodušší příkazu rozhraní příkazového řádku pro binárního klasifikačního problému (AutoML bude nutné odvodit většinu položek konfigurace z poskytnutá data):

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Jiné jednoduchého příkazu rozhraní příkazového řádku pro regresní problém:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Vytvoření a trénování modelu binární klasifikace s trénování datové sady, testovací datové sady a další přizpůsobení explicitní argumenty:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Name

`mlnet auto-train` -Trénovat různé modely (n iterací) podle zadané datové sady a nakonec vybere nejlepší model, uloží ho jako soubor ZIP serializovaná plus generuje související C# kód pro vyhodnocování a školení.

## <a name="synopsis"></a>Souhrn

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

Neplatné vstupní možnosti by neměly způsobit nástroj rozhraní příkazového řádku a vygenerovat seznam platné vstupy a chybová zpráva s vysvětlením které arg chybí, pokud je to tento případ.

## <a name="options"></a>Možnosti

 ----------------------------------------------------------

`--task | --mltask | -T` (string)

Jeden řetězec, který poskytuje ML problém vyřešit. Například některé z těchto úloh (příkazového řádku nakonec bude podporovat všechny úkoly, které jsou podporovány v AutoML):

- `regression` – Vyberte, pokud modelu ML se použije k předvídání číselnou hodnotu
- `binary-classification` – Vyberte, pokud výsledek modelu ML má dva možné zařazené do kategorií logické hodnoty (0 nebo 1).
- `multiclass-classification` – Vyberte, pokud modelu ML výsledek obsahuje více kategorií možných hodnot.

V budoucnu uvolňuje další ML úlohy a scénáře, jako `recommendations`, `clustering` a `ranking` bude podporovat.

 V tomto argumentu musí být zadána pouze jedna ML úloh.

 ----------------------------------------------------------

`--dataset | -d` (string)

Tento argument obsahuje cestu k jedné z následujících možností:

- *A: Soubor celé datové sady:* Pokud tuto možnost a uživatel neposkytuje `--test-dataset` a `--validation-dataset`, pak křížového ověření (k přeložení atd.) nebo automatizovaných datových rozdělit přístupy se interně používá k ověření modelu. Uživatel v takovém případě stačí muset zadat cestu datové sady.

- *B: Soubor trénovací datové sady:* Pokud uživatel také nabízí datové sady pro ověření modelu (pomocí `--test-dataset` a volitelně `--validation-dataset`), pak bude `--dataset` argument znamená, že stačí, když "trénovací datové sady". Například při použití 80 % 20 % přístup k ověření kvality modelu a získat metriky přesnosti, bude mít "trénovací datové sady" 80 % dat a "test dataset" bude mít 20 % data.

----------------------------------------------------------

`--test-dataset | -t` (string)

Cesta k souboru odkazující na soubor datové sady testů, například při použití 80 % 20 % přístup při provádění pravidelných ověření získat metriky přesnosti.

Pokud používáte `--test-dataset`, pak `--dataset` je také nutný.

`--test-dataset` Argument je nepovinný Pokud--ověření datová sada použije. V takovém případě musí uživatel použít tři argumenty.

----------------------------------------------------------

`--validation-dataset | -v` (string)

Cesta k souboru odkazující na soubor datové sady ověřování. Ověření datové sady je volitelný, v každém případě.

Pokud se používá `validation dataset`, by měla být chování:

- `test-dataset` a `--dataset` argumenty jsou povinné.

- `validation-dataset` Datová sada použije k odhadu chyba předpovědi modelu výběru.

- `test-dataset` Se používá pro účely posouzení chyby generalizace konečného zvolili modelu. V ideálním případě testovací sada nutné udržovat v "úložiště" a být přenesena pouze na konci analýza dat.

V podstatě při použití `validation dataset` plus `test dataset`, fázi ověřování je rozdělený do dvou částí:

1. V první části vám stačí podívejte se na vaše modely a vybrat nejvýkonnější přístupem pomocí ověření dat (tzn. ověření)
2. Potom odhadnout přesnost vybrané přístup (= test).

Oddělení dat může být proto, 80/10/10 nebo 75/15/10. Příklad:

- `training-dataset` soubor by měl mít 75 % data.
- `validation-dataset` soubor by měl mít 15 % této data.
- `test-dataset` soubor by měl mít 10 % data.

V každém případě tyto procenta bude rozhodnuto pomocí uživatele pomocí rozhraní příkazového řádku, který poskytne že soubory již rozdělit.

----------------------------------------------------------

`--label-column-name | -n` (string)

Díky tomuto argumentu konkrétní cíle a cílový sloupec (proměnné, kterou chcete předpovědět) lze zadat pomocí názvu sloupce nastavit v hlavičce datové sady.

Tento argument se používá pouze pro úkoly, jsou pod dohledem ML, jako *klasifikace problému*. Jej nelze použít bez dohledu ML úkoly, jako *clustering*.

----------------------------------------------------------

`--label-column-index | -i` (int).

Díky tomuto argumentu se dá nastavit konkrétní cíle a cílový sloupec (proměnné, kterou chcete předpovědět) s použitím sloupce číselného indexu v souboru datové sady (sloupec hodnoty indexů začínají 1).

*Poznámka:* Pokud uživatel používá také `--label-column-name`, `--label-column-name` je používán.

Tento argument se používá pouze pro pod dohledem ML úloh, jako *klasifikace problému*. Jej nelze použít bez dohledu ML úkoly, jako *clustering*.

----------------------------------------------------------

`--ignore-columns | -I` (string)

Díky tomuto argumentu můžete ignorovat existujících sloupců v souboru datové sady, nejsou načteny a využívané procesy trénování.

Zadejte názvy sloupců, které má být ignorována. Použití "," (čárkou mezera) nebo ". (místo) k oddělení více názvů sloupců. Pro názvy sloupců obsahující prázdné znaky (například "přihlášení") můžete použít uvozovky.

Příklad:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h` (bool)

Zadejte, pokud soubory datové sady mají řádek záhlaví.
Možné hodnoty jsou:
- `true`
- `false`

Ve výchozím nastavení je hodnota `true` Pokud tento argument nezadá uživatel.

Chcete-li použít `--label-column-name` argument, musíte mít záhlaví v souboru datové sady a `--has-header` nastavena na `true` (což je ve výchozím nastavení).

----------------------------------------------------------

`--max-exploration-time | -x` (string)

Ve výchozím nastavení průzkum maximální doba je 30 minut.

Tento argument Nastaví maximální dobu (v sekundách) pro proces k prozkoumání více školitelé a konfigurace. Pokud zadaná doba je příliš krátká (třeba 2 sekundy) pro jednu iteraci, může být překročena nastavená doba. V tomto případě skutečný čas je čas potřebný k vytvoření jedné konfigurace modelu v jedné iterace.

Potřebná doba pro iterace se může lišit v závislosti na velikosti datové sady.

----------------------------------------------------------

`--cache | -c` (string)

Používáte-li ukládání do mezipaměti, bude celý trénovací datové sady načten v paměti.

Pro malé a středně velké datové sady může použití mezipaměti výrazně zlepšit výkon školení, což znamená, že čas školení může být kratší než není při použití mezipaměti.

Ale velkých datových sad, načítání všech dat v paměti může negativně vzhledem k tomu, že se mohou zobrazovat nedostatek paměti. Při školení s velkou datovou sadu souborů a bez použití mezipaměti ML.NET bude možné streamování bloky dat z jednotky když je nutné načíst větší množství dat. při školení.

Můžete zadat následující hodnoty:

`on`: Vynutí mezipaměti má být použit při školení.
`off`: Vynutí mezipaměti není pro použití při cvičení.
`auto`: V závislosti na AutoML heuristickými metodami mezipaměti se použije, nebo ne. Obvykle malé a střední datové sady využije mezipaměti a velkých datových sad nepoužije mezipaměti, pokud použijete `auto` podle výběru.

Pokud nezadáte `--cache` parametr a potom mezipaměti `auto` konfigurace se použije ve výchozím nastavení.

----------------------------------------------------------

`--name | -N` (string)

Název pro výstup vytvořený projekt nebo řešení. Pokud není zadán žádný název, název `sample-{mltask}` se používá.

Soubor modelu ML.NET (. Soubor ZIP) získáte stejný název, také.

----------------------------------------------------------

`--output-path | -o` (string)

Kořenové umístění/složky umístit vygenerovaný výstup. Výchozí je aktuální adresář.

----------------------------------------------------------

`--verbosity | -V` (string)

Nastaví úroveň podrobností ve standardním výstupu.

Povolené hodnoty jsou následující:

- `q[uiet]`
- `m[inimal]`  (ve výchozím nastavení)
- `diag[nostic]` (informace o úroveň protokolování)

Ve výchozím nastavení nástroj rozhraní příkazového řádku by se zobrazit některé minimální zpětnou vazbu (minimální) při práci, jako je uvedení, že funguje a pokud je to možné kolik času je left nebo co společnost % času dokončení.

----------------------------------------------------------

`-h|--help`

Vytiskne nápovědy pro příkaz s popisem pro každý příkaz parametr.

----------------------------------------------------------

## <a name="see-also"></a>Viz také:

- [Postup instalace nástroje rozhraní příkazového řádku ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku ML.NET](../tutorials/mlnet-cli.md)
- [Telemetrie v rozhraní příkazového řádku ML.NET](../resources/ml-net-cli-telemetry.md)
