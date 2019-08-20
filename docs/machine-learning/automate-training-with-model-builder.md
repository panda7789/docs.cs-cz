---
title: Co je tvůrce modelů a jak to funguje?
description: Postup pro automatické učení modelu Machine Learning pomocí Tvůrce modelů ML.NET
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: a871c3a3751a93bdf0104c873215b164616f0664
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611461"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co je tvůrce modelů a jak to funguje?

ML.NET model Builder je intuitivní grafické rozšíření sady Visual Studio, které slouží k sestavování, výuce a nasazování vlastních modelů strojového učení.

Tvůrce modelů pomocí automatizovaného strojového učení (AutoML) zkoumá různé algoritmy a nastavení strojového učení, které vám pomůžou najít ten, který nejlépe vyhovuje vašemu scénáři.

K používání tvůrce modelů nepotřebujete odborné znalosti strojového učení. Potřebujete jenom některá data a problém, který je potřeba vyřešit. Tvůrce modelů generuje kód pro přidání modelu do vaší aplikace .NET.

![Animace uživatelského rozhraní rozšíření tvůrce modelů sady Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Tvůrce modelů je aktuálně ve verzi Preview.

## <a name="scenarios"></a>Scénáře

Můžete přenášet mnoho různých scénářů do Tvůrce modelů a vygenerovat pro svou aplikaci model strojového učení.

Scénář je popis typu předpovědi, kterou chcete použít pro vaše data. Příklad:
- Předpověď budoucího objemu prodejů produktů na základě historických dat o prodeji
- klasifikace zabarvení jako kladné nebo záporné na základě revizí zákazníků
- zjištění, zda je bankovní transakce podvodný
- směrování problémů s názory zákazníků na správný tým ve vaší společnosti

## <a name="choose-a-model-type"></a>Zvolit typ modelu

V Tvůrci modelů musíte vybrat typ modelu Machine Learning. Typ modelu závisí na tom, co se chystáte provést.

Pro scénáře, které předpovídá číslo, se zavolá `regression`typ modelu Machine Learning.

Pro scénáře, které předpovídá kategorii, je `classification`typ modelu. Existují dva typy klasifikace:
- kde jsou pouze 2 kategorie: `binary classification`.
- kde jsou tři nebo více kategorií: `multiclass classification`.

### <a name="which-model-type-is-right-for-me"></a>Který typ modelu je pro mě nejvhodnější?

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Předpověď kategorie (pokud jsou k dispozici pouze dvě kategorie)

Binární klasifikace se používá ke kategorizaci dat do dvou kategorií (ano/ne; úspěch/chyba; pravda/nepravda; kladné nebo záporné).

![Diagram znázorňující příklady binární klasifikace včetně zjišťování podvodů, zmírnění rizik a blokování aplikací](media/binary-classification-examples.png)

Analýza mínění se dá použít k předpovědi kladné nebo záporné míněníí zpětné vazby od zákazníků. Je příkladem binárního typu modelu klasifikace.

Pokud váš scénář vyžaduje klasifikaci ve dvou kategoriích, můžete použít tuto šablonu s vlastní datovou sadou.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Předpověď kategorie (pokud existují tři nebo více kategorií)

Pro kategorizaci dat do tří nebo více tříd lze použít klasifikaci s více třídami. 

![Příklady klasifikace s více třídami včetně klasifikace dokumentů a produktů, směrování lístků podpory a stanovení priorit zákaznických problémů](media/multiclass-classification-examples.png)

Klasifikace problému se dá použít ke kategorizaci vašich názorů zákazníků (například na GitHubu) s použitím názvu a popisu problému. Je to příklad typu klasifikační model s více třídami.

Šablonu klasifikace problému můžete použít pro váš scénář, pokud chcete rozdělit data do tří nebo více kategorií.

#### <a name="predict-a-number"></a>Předpovědět číslo

Regrese se používá k předpovědi čísel.

![Diagram znázorňující příklady regrese, jako je předpověď ceny, Prognóza prodeje a prediktivní údržba](media/regression-examples.png)

Předpověď cen se dá použít k předvídání cen za domácí ceny pomocí umístění, velikosti a dalších vlastností domu. Je příkladem typu regresní model.

Šablonu předpovědi cen můžete použít pro váš scénář, pokud chcete předpovědět číselnou hodnotu s vlastní datovou sadou.

#### <a name="custom-scenario-choose-your-model-type"></a>Vlastní scénář (vyberte typ modelu)

Vlastní scénář umožňuje ručně zvolit typ modelu.

## <a name="data"></a>Data

Po zvolení typu modelu bude tvůrce modelů požádán o poskytnutí datové sady. Data se používají ke školení, vyhodnocení a výběru nejlepšího modelu pro váš scénář.

![Diagram znázorňující kroky tvůrce modelů](media/model-builder-steps.png)

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

|Scénář|Typ modelu|Data|Popisek|Funkce|
|-|-|-|-|-|
|Předpověď ceny|nevýhody|[data taxislužby tarifů](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Vozov|Doba odezvy, vzdálenost|
|Detekce anomálií|binární klasifikace|[prodejní data produktu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Prodej produktu|Měsíčně|
|Analýza mínění|binární klasifikace|[data komentáře webu](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Popisek (0, pokud je negativní mínění, 1 Při kladném)|Komentář, rok|
|Zjišťování podvodů|binární klasifikace|[data platebních karet](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Třída (1, pokud je podvodný, 0 jinak)|Množství, V1-v28 (funkce Anonyme)|
|Klasifikace textu|klasifikace s více třídami|[Data o problému na GitHubu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Oblast|Název, popis|

## <a name="train"></a>Trénování

Když vyberete svůj scénář, data a popisek, tvůrce modelů navlakuje model.

### <a name="what-is-training"></a>Co je školení?

Školení je automatický proces, podle kterého tvůrce modelů učí váš model, jak odpovídat na otázky pro váš scénář. Po vyškolení může váš model předpovědi se vstupními daty, ke kterým se předtím neviděl. Pokud například předpovídáte ceny za dům a na trhu se nachází nová dům, můžete předpovědět její prodejní cenu.

Vzhledem k tomu, že tvůrce modelů používá automatizované Machine Learning (AutoML), nevyžaduje během školení žádné vstupy nebo ladění.

## <a name="evaluate"></a>Vyhodnotit

Vyhodnocení je proces použití výukového modelu k vytvoření předpovědi s novými testovacími daty a k měření toho, jak dobrý je předpovědi.

Tvůrce modelů rozdělí školicí data do sady školení a sady testů. Školicí data (80%) se používá ke školení vašeho modelu a testovacích dat (20%) se vrátí k vyhodnocení vašeho modelu. Tvůrce modelů používá metriky k měření toho, jak je model dobrý. Konkrétní použité metriky závisí na typu modelu. Další informace najdete v tématu [metriky vyhodnocení modelu](resources/metrics.md).

## <a name="improve"></a>Účely

Pokud vaše skóre výkonu vašeho modelu není tak dobré, jak chcete, můžete:

* Naučit se delší dobu. Pomocí automatizovaného strojového učení se navíc snaží vyzkoušet více algoritmů a nastavení.

* Přidejte další data. V některých případech se množství dat nestačí pro výuku vysoce kvalitního modelu strojového učení.

* Vyvážení dat Pro úlohy klasifikace se ujistěte, že je sada školení vyrovnávána napříč kategoriemi. Například pokud máte čtyři třídy pro 100 ukázky a dvě první třídy (značky 1 a značka2) se používají pro 90 záznamů, ale ostatní dvě (značka3 a tag4) se používají jenom u zbývajících 10 záznamů, nedostatek vyvážených dat může způsobit, že váš model bude bojovat do typu korespondenční ectly předpověď značka3 nebo tag4.

## <a name="code"></a>Kód

Po fázi vyhodnocení výstup tvůrce modelů vytvoří soubor modelu a kód, který můžete použít k přidání modelu do aplikace. Modely ML.NET se ukládají jako soubor zip. Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení. Tvůrce modelů také přidá ukázkovou konzolovou aplikaci, kterou můžete spustit pro zobrazení modelu v akci.

Kromě toho tvůrce modelů vypíše kód, který model vygeneroval, takže můžete pochopit postup, který se používá ke generování modelu. Můžete také použít kód školení modelu k revýuce modelu s novými daty.

## <a name="whats-next"></a>Co dále?

[Instalace](how-to-guides/install-model-builder.md) rozšíření pro tvůrce modelů sady Visual Studio

Vyzkoušejte [cenový odhad nebo jakýkoli scénář regrese](tutorials/predict-prices-with-model-builder.md) .
