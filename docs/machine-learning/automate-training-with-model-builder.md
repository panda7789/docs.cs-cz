---
title: Co je tvůrce modelů a jak to funguje?
description: Postup pro automatické učení modelu Machine Learning pomocí Tvůrce modelů ML.NET
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 4afdbfd1682a30647b09d05d51a5c73c214fe2bd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616926"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co je tvůrce modelů a jak to funguje?

ML.NET model Builder je intuitivní grafické rozšíření sady Visual Studio, které slouží k sestavování, výuce a nasazování vlastních modelů strojového učení.

Tvůrce modelů pomocí automatizovaného strojového učení (AutoML) zkoumá různé algoritmy a nastavení strojového učení, které vám pomůžou najít ten, který nejlépe vyhovuje vašemu scénáři.

K používání tvůrce modelů nepotřebujete odborné znalosti strojového učení. Potřebujete jenom některá data a problém, který je potřeba vyřešit. Tvůrce modelů generuje kód pro přidání modelu do vaší aplikace .NET.

![Animace uživatelského rozhraní rozšíření tvůrce modelů sady Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Tvůrce modelů je aktuálně ve verzi Preview.

## <a name="scenario"></a>Scénář

Můžete přenášet mnoho různých scénářů do Tvůrce modelů a vygenerovat pro svou aplikaci model strojového učení.

Scénář je popis typu předpovědi, kterou chcete použít pro vaše data. Například:

- Předpověď budoucího objemu prodejů produktů na základě historických dat o prodeji
- klasifikace zabarvení jako kladné nebo záporné na základě revizí zákazníků
- zjištění, zda je bankovní transakce podvodný
- směrování problémů s názory zákazníků na správný tým ve vaší společnosti

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Který scénář strojového učení je pro mě nejvhodnější?

V Tvůrci modelů je nutné vybrat scénář. Typ scénáře závisí na typu předpovědi, kterou se pokoušíte provést.

#### <a name="text-classification"></a>Klasifikace textu

Klasifikace se používá ke kategorizaci dat do kategorií.

![Diagram znázorňující příklady binární klasifikace včetně zjišťování podvodů, zmírnění rizik a blokování aplikací](media/binary-classification-examples.png)

![Příklady klasifikace s více třídami včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit zákaznických problémů](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a>Předpověď hodnoty

Regrese se používá k předpovědi čísel.

![Diagram znázorňující příklady regrese, jako je předpověď ceny, Prognóza prodeje a prediktivní údržba](media/regression-examples.png)

#### <a name="image-classification"></a>Klasifikace obrázků

Klasifikaci obrázku lze použít k identifikaci obrázků různých kategorií. Například různé typy terénu nebo zvířat nebo výrobní vady.

Můžete použít scénář klasifikace obrázku, pokud máte sadu imagí a chcete klasifikace imagí do různých kategorií.

#### <a name="recommendation"></a>Doporučení

Scénář doporučení předpovídá seznam navrhovaných položek pro konkrétního uživatele, a to na základě toho, jak se podobá a jako nelíbí jiným uživatelům.

Scénář doporučení můžete použít, pokud máte sadu uživatelů a sadu "produktů", například položky k nákupu, filmů, knihám nebo TELEVIZNÍm pořadům, spolu se sadou hodnocení těchto produktů pro uživatele.

## <a name="environment"></a>Prostředí

Svůj model strojového učení můžete na svém počítači nebo v cloudu v Azure vyškolit místně.

Při psaní v místním prostředí pracujete s omezeními prostředků počítače (CPU, paměť a disk). Když vytváříte výuku v cloudu, můžete škálovat prostředky tak, aby splňovaly požadavky vašeho scénáře, zejména pro velké datové sady.

Místní školení je podporováno pro všechny scénáře.

Pro klasifikaci imagí se podporuje školení Azure.

## <a name="data"></a>Data

Jakmile vyberete svůj scénář, tvůrce modelů vás vyzve k zadání datové sady. Data se používají ke školení, vyhodnocení a výběru nejlepšího modelu pro váš scénář.

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

Tvůrce modelů podporuje datové sady ve formátech. TSV,. csv,. txt a také ve formátu SQL Database. Pokud máte soubor. txt, sloupce by měly být oddělené pomocí `,` `;` nebo `/t` a soubor musí obsahovat řádek záhlaví.

Pokud je datová sada tvořena obrázky, podporované typy souborů jsou `.jpg` a `.png` .

Další informace najdete v tématu [načtení dat o školení do Tvůrce modelů](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Vyberte výstup, který chcete předpovědět (popisek)

Datová sada je tabulka řádků příkladů cvičení a sloupce atributů. Každý řádek má:

- **popisek** (atribut, který chcete předpovědět)
- **funkce** (atributy, které se používají jako vstupy pro předpověď popisku).

Pro scénář předpovědi pro domácí ceny můžou tyto funkce:

- čtvercové záběry domu
- počet ložnicemi a bathrooms
- PSČ

Popisek je cena za cenu na pracovišti pro tento řádek hodnot čtvercového záběru, Bedroom a koupeln a PSČ.

![Tabulka znázorňující řádky a sloupce údajů o cenách domu s funkcemi, které se skládají z poštovních místností – PSČ a popisek ceny](media/model-builder-data.png)

### <a name="example-datasets"></a>Příklady datových sad

Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:

|Scénář|Příklad|Data|Popisek|Funkce|
|-|-|-|-|-|
|Classification|Předpověď anomálií prodeje|[prodejní data produktu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Prodej produktu|Month|
||Předpověď mínění komentářů k webu|[data komentáře webu](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Popisek (0, pokud je negativní mínění, 1 Při kladném)|Komentář, rok|
||Předpověď falešných transakcí platebních karet|[data platebních karet](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Třída (1, pokud je podvodný, 0 jinak)|Množství, V1-v28 (funkce Anonyme)|
||Předpověď typu problému v úložišti GitHubu|[Data o problému na GitHubu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Oblast|Název, popis|
|Předpověď hodnoty|Předpověď ceny za taxislužby jízdné|[data taxislužby tarifů](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Vozov|Doba odezvy, vzdálenost|
|Klasifikace obrázků|Předpověď kategorie květu |[obrázky květin](http://download.tensorflow.org/example_images/flower_photos.tgz)|Typ květu: uzavřené, Dandelion, růže, slunečnice, Tulips|Samotná data obrázku|
|Doporučení|Předpověď filmů, které někdo bude chtít|[Hodnocení filmů](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|Uživatelé, filmy|Ratings|

## <a name="train"></a>Trénování

Když vyberete svůj scénář, data a popisek, tvůrce modelů navlakuje model.

### <a name="what-is-training"></a>Co je školení?

Školení je automatický proces, podle kterého tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář. Po vyškolení může váš model předpovědi se vstupními daty, ke kterým se předtím neviděl. Pokud například předpovídáte ceny za dům a na trhu se nachází nová dům, můžete předpovědět její prodejní cenu.

Vzhledem k tomu, že tvůrce modelů používá automatizované Machine Learning (AutoML), nevyžaduje během školení žádné vstupy nebo ladění.

### <a name="how-long-should-i-train-for"></a>Jak dlouho mám zaškolit?

Tvůrce modelů používá AutoML k prozkoumání více modelů, abyste si našli nejlepší výkon modelu.

Delší školicí období umožňují AutoML prozkoumat více modelů s širší škálou nastavení.

V následující tabulce najdete průměrnou dobu, jakou trvalo dosažení dobrého výkonu sady ukázkových datových sad na místním počítači.

|Velikost datové sady|Průměrná doba pro vlak|
|------------|---------------------|
|0-10 MB|10 sekund|
|10-100 MB|10 min|
|100 – 500 MB|30 min|
|500 – 1 GB|60 min.|
|1 GB +|3 hodiny|

Tato čísla jsou jenom orientační. Přesná délka školení závisí na:

- počet funkcí (sloupců), které se používají jako vstup do modelu
- typ sloupců
- úkol ML
- výkon procesoru, disku a paměti počítače, který se používá pro školení

## <a name="evaluate"></a>Vyhodnotit

Vyhodnocení je proces měření, jak dobrý je váš model. Tvůrce modelů používá trained model k vytváření předpovědi s novými testovacími daty a pak měří, jak dobrá předpovědi.

Tvůrce modelů rozdělí školicí data do sady školení a sady testů. Školicí data (80%) se používá ke školení vašeho modelu a testovacích dat (20%) se vrátí k vyhodnocení vašeho modelu.

### <a name="how-do-i-understand-my-model-performance"></a>Návody porozumět výkonu mého modelu?

Scénář se mapuje na úlohu strojového učení. Každá úloha ML má svou vlastní sadu metrik vyhodnocení.

#### <a name="value-prediction"></a>Předpověď hodnoty

Výchozí metrika pro problémy předpovědi hodnot je RSquared, hodnota RSquared rozsahů mezi 0 a 1. hodnota 1 je nejlepší možnou hodnotou nebo jinými slovy, které přiblíží hodnotu RSquared na 1, lepší váš model.

Další metriky nahlášené jako absolutní ztráta, čtvercová ztráta a ztráta služby RMS jsou další metriky, které lze použít k pochopení toho, jak model probíhá, a jeho porovnání s jinými modely předpovědi hodnot.

#### <a name="classification-2-categories"></a>Klasifikace (2 kategorie)

Výchozí metrika pro problémy s klasifikací je přesnost. Přesnost definuje poměr správných předpovědi, které model provádí přes testovací datovou sadu. Nejblíže k 100% nebo 1,0 tím lépe.

Jiné metriky nahlášené jako AUC (oblast pod křivkou), které měří skutečnou kladnou rychlost vs. falešně pozitivní sazba by měla být větší než 0,50, aby bylo možné modely akceptovat.

K řízení rovnováhy mezi přesností a odvoláním je možné použít další metriky, jako je například skóre F1.

#### <a name="classification-3-categories"></a>Klasifikace (3 + kategorie)

Výchozí metrika pro klasifikaci více tříd je mikropřesnost. Hodnota bližší pro mikropřesnost na 100% nebo 1,0 je lepší.

Další důležitou metrikou pro klasifikaci více tříd je přesnost na makro, podobně jako u mikropřesnosti blíž k 1,0. lepší je. Dobrým způsobem, jak se domnívat o těchto dvou typech přesnosti, je:

- Mikropřesnost: jak často se příchozí lístek klasifikuje do správného týmu?
- Přesnost maker: u průměrných týmů, jak často je příchozí lístek správný pro svůj tým?

### <a name="more-information-on-evaluation-metrics"></a>Další informace o metrikách vyhodnocení

Další informace najdete v tématu [metriky vyhodnocení modelu](resources/metrics.md).

## <a name="improve"></a>Účely

Pokud vaše skóre výkonu vašeho modelu není tak dobré, jak chcete, můžete:

- Naučit se delší dobu. Pomocí automatizovaného strojového strojového učení s větším využitím algoritmů a nastavení se s víc časem experimentuje.

- Přidejte další data. V některých případech se množství dat nestačí pro výuku vysoce kvalitního modelu strojového učení.

- Vyvážení dat Pro úlohy klasifikace se ujistěte, že je sada školení vyrovnávána napříč kategoriemi. Například pokud máte čtyři třídy pro 100 příkladů a dvě první třídy (značky 1 a značka2) se používají pro 90 záznamů, ale ostatní dvě (značka3 a tag4) se používají jenom u zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bude bojovat správně předpovědět značka3 nebo tag4.

## <a name="code"></a>Kód

Po fázi vyhodnocení výstup tvůrce modelů vytvoří soubor modelu a kód, který můžete použít k přidání modelu do aplikace. Modely ML.NET se ukládají jako soubor zip. Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení. Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit pro zobrazení modelu v akci.

Kromě toho tvůrce modelů vypíše kód, který model vygeneroval, takže můžete pochopit postup, který se používá ke generování modelu. Můžete také použít kód školení modelu k revýuce modelu s novými daty.

## <a name="whats-next"></a>Co dále?

[Instalace](how-to-guides/install-model-builder.md) rozšíření pro tvůrce modelů sady Visual Studio

Vyzkoušejte [cenový odhad nebo jakýkoli scénář regrese](tutorials/predict-prices-with-model-builder.md) .
