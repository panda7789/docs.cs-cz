---
title: Co je model builder a jak to funguje?
description: Jak používat ML.NET Model Builder automaticky trénovat model strojového učení
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344769"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co je model builder a jak to funguje?

ML.NET Model Builder je intuitivní grafické rozšíření Sady Visual Studio pro vytváření, trénování a nasazování vlastních modelů strojového učení.

Model Builder používá automatizované strojové učení (AutoML) k prozkoumání různých algoritmů a nastavení strojového učení, které vám pomohou najít ten, který nejlépe vyhovuje vašemu scénáři.

K používání modelového tvůrce nepotřebujete odborné znalosti strojového učení. Vše, co potřebujete, jsou nějaká data a problém k vyřešení. Tvůrce modelů generuje kód pro přidání modelu do aplikace .NET.

![Animace uživatelského rozhraní rozšíření Visual Studio tvůrce modelů](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Tvůrce modelů je momentálně ve verzi Preview.

## <a name="scenario"></a>Scénář

Můžete přinést mnoho různých scénářů model builder, generovat model strojového učení pro vaši aplikaci.

Scénář je popis typu předpověď, kterou chcete provést pomocí dat. Například:

- předpovědět budoucí objem prodeje produktů na základě historických údajů o prodeji
- klasifikovaly názory jako pozitivní nebo negativní na základě recenzí zákazníků
- zjistit, zda je bankovní transakce podvodná
- směrovat problémy se zpětnou vazbou od zákazníků ke správnému týmu ve vaší společnosti

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Který scénář strojového učení je pro mě ten pravý?

V Tvůrce modelů je třeba vybrat scénář. Typ scénáře závisí na typu předpověď, kterou se pokoušíte provést.

#### <a name="text-classification"></a>Klasifikace textu

Klasifikace se používá ke kategorizaci dat do kategorií.

![Diagram znázorňující příklady binární klasifikace včetně detekce podvodů, zmírnění rizika a screeningu aplikací](media/binary-classification-examples.png)

![Příklady klasifikace více tříd, včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit problémů zákazníků](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a>Predikce hodnoty

Regrese se používá k předvídání čísel.

![Diagram znázorňující příklady regresní ceny, jako je predikce cen, prognóza prodeje a prediktivní údržba](media/regression-examples.png)

#### <a name="image-classification"></a>Klasifikace obrázků

Klasifikace obrázků lze použít k identifikaci obrázků různých kategorií. Například různé typy terénu nebo zvířat nebo výrobní vady.

Scénář klasifikace obrázků můžete použít, pokud máte sadu obrázků a chcete je klasifikovat do různých kategorií.

#### <a name="recommendation"></a>Doporučení

Scénář doporučení předpovídá seznam navržených položek pro konkrétního uživatele na základě toho, jak podobné jsou jejich to se mi líbí a nelíbí ostatním uživatelům.

Scénář doporučení můžete použít, pokud máte sadu uživatelů a sadu "produktů", jako jsou položky k nákupu, filmy, knihy nebo televizní pořady, spolu se sadou "hodnocení" uživatelů těchto produktů.

## <a name="environment"></a>Prostředí

Model strojového učení můžete trénovat místně na počítači nebo v cloudu v Azure.

Při místním trénování pracujete v rámci omezení prostředků počítače (procesor, paměť a disk). Když trénujete v cloudu, můžete vertikálně navýšit kapacitu prostředků tak, aby splňovaly požadavky vašeho scénáře, zejména pro velké datové sady.

Místní školení je podporováno pro všechny scénáře.

Azure školení je podporována pro klasifikaci obrázků.

## <a name="data"></a>Data

Jakmile jste si vybrali scénář, Tvůrce modelů vás požádá o poskytnutí datové sady. Data se používají k trénování, vyhodnocení a výběru nejlepšího modelu pro váš scénář.

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

Tvůrce modelů podporuje datové sady ve formátech TSV, .csv, .txt a také ve formátu databáze SQL. Pokud máte soubor TXT, sloupce by `,`měly být odděleny pomocí aplikace nebo `;` a `/t` soubor musí mít řádek záhlaví.

Pokud je datová sada tvořena obrázky, `.jpg` `.png`jsou podporované typy souborů a .

Další informace naleznete v [tématu Načítání dat školení do Tvůrce modelů](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Zvolte výstup, který chcete předpovědět (popisek)

Datová sada je tabulka řádků příkladů školení a sloupců atributů. Každý řádek má:

- **popisek** (atribut, který chcete předpovědět)
- **(atributy,** které se používají jako vstupy k předvídání popisku).

Pro scénář předpověď ceny domu by funkce mohly být:

- čtvercový záběr domu
- počet ložnic a koupelen
- PSČ

Štítek je historická cena domu pro tuto řadu čtverečních záběrů, ložnice a koupelna hodnoty a PSČ.

![Tabulka zobrazující řádky a sloupce údajů o cenách domu s funkcemi skládajícími se z velikostních místností PSČ a cenový štítek](media/model-builder-data.png)

### <a name="example-datasets"></a>Ukázkové datové sady

Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:

|Scénář|Příklad|Data|Popisek|Funkce|
|-|-|-|-|-|
|Classification|Předvídání prodejních anomálií|[údaje o prodeji produktů](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Prodej produktů|Month|
||Předpovědět mínění o komentářích k webovým stránkám|[údaje o komentářích k webovým stránkám](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Popisek (0 při negativním sentimentu, 1 pozitivní)|Komentář, rok|
||Předpovídat podvodné transakce kreditní kartou|[Údaje o kreditní kartě](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Třída (1 v případě podvodného, 0 jinak)|Částka, V1-V28 (anonymizované funkce)|
||Předvídejte typ problému v úložišti GitHub|[Data problému GitHubu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Oblast|Název, popis|
|Predikce hodnoty|Předpovědět cenu jízdného taxi|[údaje o jízdném taxislužby](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Jízdné|Doba jízdy, vzdálenost|
|Klasifikace obrázků|Předpovědět kategorii problému|[obrázky květin](http://download.tensorflow.org/example_images/flower_photos.tgz)|Typ květiny: sedmikráska, pampeliška, růže, slunečnice, tulipány|Samotná obrazová data|
|Doporučení|Předvídejte filmy, které se někomu budou líbit|[hodnocení filmů](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|Uživatelé, Filmy|Ratings|

## <a name="train"></a>Trénování

Jakmile vyberete scénář, data a popisek, Tvůrce modelů trénuje model.

### <a name="what-is-training"></a>Co je trénink?

Školení je automatický proces, pomocí kterého Tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář. Po tréninu, váš model můžete předpovědět se vstupními daty, které dosud neviděl. Například, pokud jste předpovídají ceny domů a nový dům přichází na trh, můžete předpovědět jeho prodejní cenu.

Vzhledem k tomu, že Model Builder používá automatizované strojové učení (AutoML), nevyžaduje žádný vstup nebo ladění od vás během školení.

### <a name="how-long-should-i-train-for"></a>Na jak dlouho mám trénovat?

Tvůrce modelů používá AutoML k prozkoumání více modelů a vyhledá vám nejvýkonnější model.

Delší tréninkové období umožňují automatické kontrole prozkoumat další modely s širším rozsahem nastavení.

Níže uvedená tabulka shrnuje průměrnou dobu, kterou je třeba získat dobrý výkon pro sadu ukázkových datových sad v místním počítači.

|Velikost datové sady|Průměrná doba tréninku|
|------------|---------------------|
|0 - 10 MB|10 s|
|10 - 100 MB|10 min|
|100 - 500 MB|30 min|
|500 - 1 GB|60 min|
|1 GB+|3+ hodiny|

Tato čísla jsou pouze vodítkem. Přesná délka tréninku závisí na:

- počet prvků (sloupců), které se používají jako vstup do modelu
- typ sloupců
- úloha ML
- výkon procesoru, disku a paměti počítače používaného pro trénování

## <a name="evaluate"></a>Vyhodnotit

Hodnocení je proces měření toho, jak dobrý je váš model. Tvůrce modelů používá trénovaný model k předpovědi s nová testovací data a pak měří, jak dobré předpovědi jsou.

Tvůrce modelů rozdělí trénovací data do trénovací sady a testovací sady. Údaje o školení (80 %) se používá k trénování modelu a testovacích dat (20 %) je držen zpět k vyhodnocení modelu.

### <a name="how-do-i-understand-my-model-performance"></a>Jak rozumím výkonu modelu?

Scénář se mapuje na úlohu strojového učení. Každý úkol ML má vlastní sadu metrik hodnocení.

#### <a name="value-prediction"></a>Predikce hodnoty

Výchozí metrika pro problémy s předpovědí hodnot je RSquared, hodnota RSquared rozsahy mezi 0 a 1. 1 je nejlepší možná hodnota, nebo jinými slovy, čím blíže hodnota RSquared na 1, tím lépe váš model je výkon.

Další metriky hlášené, jako je absolutní ztráta, kvasitová ztráta a ztráta RMS jsou další metriky, které lze použít k pochopení toho, jak si model vede, a jeho porovnání s jinými modely předpovědi hodnot.

#### <a name="classification-2-categories"></a>Klasifikace (2 kategorie)

Výchozí metrika pro problémy s klasifikací je přesnost. Přesnost definuje podíl správné předpovědi modelu je dělat přes testovací datové sady. Čím blíže k 100% nebo 1,0, tím lépe.

Další hlášené metriky, například AUC (Plocha pod křivkou), která měří skutečně pozitivní míru vs. míra falešně pozitivních hodnot by měla být vyšší než 0,50, aby byly modely přijatelné.

Další metriky, jako je skóre F1, lze použít k řízení rovnováhy mezi přesností a odvoláním.

#### <a name="classification-3-categories"></a>Klasifikace (3+ kategorie)

Výchozí metrika pro klasifikaci více tříd je Mikro přesnost. Čím blíže je mikropřesnost na 100% nebo 1,0, tím lepší je.

Další důležitou metrikou pro klasifikaci více tříd je makropřesnost, podobná mikropřesnosti, čím blíže k 1.0, tím lépe. Dobrý způsob, jak přemýšlet o těchto dvou typech přesnosti je:

- Mikropřesnost: Jak často se příchozí jízdenka klasifikuje do správného týmu?
- Makropřesnost: Jak často je pro průměrný tým příchozí lístek pro jejich tým správný?

### <a name="more-information-on-evaluation-metrics"></a>Další informace o hodnotících metrikách

Další informace naleznete v tématu [metriky vyhodnocení modelu](resources/metrics.md).

## <a name="improve"></a>Zlepšit

Pokud skóre výkonu modelu není tak dobré, jak chcete, můžete:

- Trénujte delší dobu. S více času, automatizované strojové učení motor experimenty s více algoritmy a nastavení.

- Přidejte další data. Někdy množství dat není dostatečná pro trénování vysoce kvalitní model strojového učení.

- Vyvažte svá data. Pro úkoly klasifikace, ujistěte se, že sada školení je vyvážená mezi kategoriemi. Například pokud máte čtyři třídy pro 100 příklady školení a dvě první třídy (tag1 a tag2) se používají pro 90 záznamů, ale další dva (tag3 a tag4) se používají pouze na zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bojovat správně předpovědět tag3 nebo tag4.

## <a name="code"></a>kód

Po fázi vyhodnocení Tvůrce modelů vydělá soubor modelu a kód, který můžete použít k přidání modelu do aplikace. ML.NET modely jsou uloženy jako soubor zip. Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení. Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit, abyste viděli model v akci.

Kromě toho Tvůrce modelů vygeneruje kód, který vygeneroval model, takže můžete pochopit kroky použité ke generování modelu. Můžete také použít model trénovací kód pro přeškolit model s novými daty.

## <a name="whats-next"></a>Co dále?

[Instalace](how-to-guides/install-model-builder.md) rozšíření Visual Studio tvůrce modelů

Vyzkoušejte [predikci ceny nebo jakýkoli regresní scénář](tutorials/predict-prices-with-model-builder.md)
