---
title: Co je Tvůrce modelu a jak to funguje?
description: Jak automaticky trénování modelu strojového učení pomocí Tvůrce modelu ML.NET
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6f5bbe3c389e3ca42550a48ef3e6edbc963ac2e9
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410656"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co je Tvůrce modelu a jak to funguje?

Tvůrce modelu ML.NET je snadno pochopitelné grafické sady Visual Studio rozšíření vytvářet, trénovat a nasazovat vlastní modely strojového učení. 

Tvůrce modelu pomocí automatizovaných strojového učení (AutoML) a prozkoumejte algoritmů různých strojového učení a nastavení vám pomůžou najít ten, který nejlépe vyhovuje vaší situaci.

Není nutné znalosti machine learning použít Tvůrce modelu. Vše, co potřebujete je některá data a problém vyřešit. Tvůrce modelu generuje kód pro přidání modelu pro aplikace .NET.

![Model Tvůrce sady Visual Studio rozšíření uživatelské rozhraní animace](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Tvůrce modelu je aktuálně ve verzi Preview.

## <a name="scenarios"></a>Scénáře

Mnoho různých scénářích je možné přenést do Tvůrce modelu, pro generování model strojového učení pro vaši aplikaci.

Scénář je popis typu predikcí, které chcete provést s vašimi daty. Příklad:
- předpovídat budoucí produktu objem prodeje podle historická data o prodeji
- klasifikace mínění jako kladné nebo záporné podle zapracováním připomínek zákazníků
- zjistit, zda je podvodné transakce bankovnictví
- problémy zpětné vazby zákazníků směrovat správnému týmu ve vaší společnosti

V Tvůrci modelu, budete muset namapovat na váš scénář [ML.NET úloh](resources/tasks.md). Můžete použít Tvůrce modelu pro **regrese** (odhad čísla) a **klasifikace** (předpověď kategorie).

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Scénář, který machine learning je pro mě nejlepší?

Tvůrce modelu se dodává se šablonami pro analýzu mínění, klasifikace problému, predikce ceny a vlastní scénáře. Tyto šablony lze používat jako výchozí bod pro váš konkrétní scénář ML.NET.

#### <a name="sentiment-analysis-binary-classification"></a>Analýza zabarvení (binární klasifikace)

Analýza subjektivního hodnocení lze použít k predikci pozitivní nebo negativní zabarvení zpětné vazby od zákazníků. Je příkladem úloha binární klasifikace.

Binární klasifikace se používá ke kategorizaci dat do dvou tříd (Ano/Ne; úspěšného/neúspěšného; true/false; pozitivní nebo negativní). Je možné odpovědi na otázky jako:

- Tato e-mailu nevyžádané pošty je? (zjišťování nevyžádané pošty)
- Které žadatel může být nárok na členství? (aplikace prověřování)
- Účty, které nemusí platit faktury včas? (zmírnění rizik)
- Je podvodné transakci platební karty? (zjišťování možných podvodů)

Pokud vaše situace vyžaduje zařazení do dvou kategorií, tuto šablonu můžete použít s vlastním datovou sadou.
 
#### <a name="issue-classification-multiclass-classification"></a>Klasifikace problémů (vícetřídová klasifikace)

Klasifikace problému lze použít ke kategorizaci dopadům na zákazníky zpětnou vazbu (například na Githubu) pomocí problém názvu a popisu. Je příkladem úloha klasifikace víc tříd.

Klasifikace víc tříd lze použít ke kategorizaci dat do tří nebo více tříd. Je možné odpovědi na otázky jako:

- K oddělení by měl jsem směrovat lístek podpory? (Podpora směrování ticket)
- Co je Priorita problému zákazníka? (problém zákazníků stanovení priorit)
- Na jaké kategorie patří produkt? (klasifikace)
- Jaký typ dokumentu? (klasifikaci dokumentů a e-mailu)

Šablonu klasifikace problému můžete použít pro váš scénář, pokud chcete kategorizace dat do tří nebo více kategorií.

#### <a name="price-prediction-regression"></a>Předpověď ceny (regrese)

Predikce ceny lze použít k předvídání cen house pomocí umístění, velikost a dalších vlastností, z domu. Je příkladem úloh regrese.

Regrese se používá k předpovědi čísel. Je možné odpovědi na otázky jako:

- Jaká cena se domu prodávat pro? (cena predikcí)
- Po tom, jak dlouho bude mechanických částí vyžadovat údržbu? (prediktivní údržba)
- Co je vlhkost v tomto sušič? (monitorování počítačů)
- Co bude celkový roční prodeje pro tuto oblast? (Prognózování prodeje)

Pokud chcete předpovědět číselnou hodnotu s vlastním datovou sadu, můžete použít šablonu predikce ceny pro váš scénář.

#### <a name="custom-scenario-choose-your-task"></a>Vlastní scénáře (zvolte svůj úkol)

Vlastní scénář umožňuje zvolit vlastní úloha. Vyberte si scénáře, který je pro váš problém nejvhodnější.

Vlastní scénář umožňuje zvolit vlastní strojového učení úloh. V předchozím šablony šlo vyřešit úlohy strojového učení do scénáře: binární klasifikace, roc klasifikační nebo regresní. V této šabloně můžete ML úkol, který chcete používat s vašimi daty.

## <a name="data"></a>Data

Po namapování váš scénář na úkol, Tvůrce modelu požaduje zadání datové sady. Data se používají k trénování, vyhodnocení a vybrat nejlepší model pro váš scénář. Musíte také zvolit výstup, který chcete předpovědět.

### <a name="choose-the-output-to-predict-label"></a>Zvolte výstupní předpovědět (popisek)

Datová sada je tabulka řádků z příkladů školení a sloupců atributů. Každý řádek obsahuje:
- **popisek** (atribut, který chcete předpovědět)
- **funkce** (atributy, které se používají jako vstupy pro předpověď popisku).

Predikce ceny house scénáři může být funkce:
- podlahová dům
- počet ložnicemi a koupelny
- PSČ

Popisek je house historické ceny pro tento řádek Čtvereček záběrů, ložnici a koupelnové hodnot a PSČ.

![Tabulka zobrazující řádky a sloupce dat cena house s funkcemi skládající se z velikost místnosti PSČ a cena popisek](media/model-builder-data.png)

### <a name="data-formats"></a>Formáty dat

Tvůrce modelu umístí na datech následující omezení:

- Data musí být uložen v souboru (CSV nebo TSV řádku záhlaví), nebo databáze systému SQL server.
- Limit 1 GB na trénovací datové sady
- SQL server má limit 100 000 řádků pro školení
- Kopírují data z SQL serveru ze serveru do místního počítače před školení

### <a name="example-datasets"></a>Příklad datové sady

Pokud ještě nemáte vlastní data, vyzkoušejte jednu z těchto datových sad:

|Scénář|Úloha ML|Data|Popisek|Funkce|
|-|-|-|-|-|
|Predikce ceny|Regrese|[tarif data taxislužby města](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarif|Doba odezvy, vzdálenost|
|Detekce anomálií|Binární klasifikace|[produkt prodejních dat](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Prodej produktů|Měsíc|
|Analýza mínění|Binární klasifikace|[data webu komentář](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|Popisek (0 při negativní zabarvení, 1 při pozitivní)|Komentář, rok|
|Zjišťování možných podvodů|Binární klasifikace|[údajů o kreditních kartách](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Třídy (1 při podvodné, jinak 0)|Velikost, V1 – V28 (anonymizované funkce)|
|Klasifikace textu|Klasifikace víc tříd|[Data problém Githubu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Oblast|Název, popis|

## <a name="train"></a>Trénování

Jakmile vyberete scénář, data a popisek, trénovat Model Tvůrce modelu.

### <a name="what-is-training"></a>Co je školení?

Školení je o automatický proces, podle kterého Tvůrce modelu se naučíte modelu odpovědi na otázky pro váš scénář. Po školení, modelu provádět předpovědi s vstupních dat, které nebylo nikdy dříve. Například pokud jsou predikce ceny house a nové house pochází na trhu, můžete předpovídat cenu prodej.

Protože tvůrce modelu pomocí automatizovaných strojového učení (AutoML), nevyžaduje ladění od vás během cvičení nebo jakýkoli vstup.

### <a name="how-long-should-i-train-for"></a>Jak dlouho by měl trénování pro?

Můžete zadat čas školení. Obecně platí školení delší dobu vytváří přesnější modelu. Jak se zvyšuje velikost trénovací datové sady je také nutný více času školení. Následující tabulka uvádí některé pokyny čas školení pro datové sady, které zvětšení.

Velikost datové sady  | Typ datové sady       | Střední Čas k trénování
------------- | ------------------ | --------------
0 - 10 Mb     | Číselné a Text   | 10 sekund
10 - 100 Mb   | Číselné a Text   | 10 minut 
100 – 500 mb  | Číselné a Text   | 30 min 
500 - 1 Gb    | Číselné a Text   | 60 min 
1 Gb+         | Číselné a Text   | 3 hodiny + 

Přesný čas pro učení také závisí na:

- Typ sloupce tedy text vs číselné
- Typ machine learning úlohy (regrese nebo klasifikace)
- počet řádků, které jsou používané pro vzdělávání
- počet sloupců funkce používané pro vzdělávání

Tvůrce modelu je testovaná pro škálování s datovou sadou 1 TB, ale vytváření vysoce kvalitních modelu pro danou velikost datové sady může trvat až čtyři dny!

## <a name="evaluate"></a>Vyhodnocení

Hodnocení je proces použití trénovaný model pro predikci s novými daty testu a pak měření jak kvalitní predikcí se.

Tvůrce modelu rozdělí trénovacích dat do trénovací sady a testovací sady. Trénovacích dat (80 %) slouží k natrénování modelu a testovacích dat (20 %) se nachází zpět k vyhodnocení modelu.  Metriky pro vyhodnocení, závisí na úkolu ML. Další informace najdete v tématu [model metrik](resources/metrics.md).  

### <a name="sentiment-analysis-binary-classification"></a>Analýza zabarvení (binární klasifikace)

Je výchozí metriku pro binární klasifikaci problémy **přesnost**. Přesnost definuje poměr správné předpovědi, které váš model odešle přes testovací datové sady. **Blíže na 100 %, tím lepší je**.

Jiných metrik reportovaných, jako je AUC (oblasti pod křivkou), která měří true kladné rychlost vs. míru falešně pozitivních výsledků, musí být větší než 0,50 pro modely jako přijatelné. 

Další metriky, jako je F1 skóre je možné řídit rovnováhu mezi přesnosti (poměr správné předpovědí na celkové předpovědi této třídy) a spojené s vracením (podíl správné předpovědí na celkové skuteční členové této třídy).

### <a name="issue-classification-multiclass-classification"></a>Klasifikace problémů (vícetřídová klasifikace)

Metrika výchozí klasifikace víc tříd problémů **micro přesnost**. **Blíže na 100 %, tím lepší je**.

Problémy, kde se data rozdělená na více tříd existují dva druhy přesnost:

- Micro přesnost: zlomek předpovědi, které jsou správné napříč všemi instancemi. Ve scénáři klasifikace problému je přesnost micro podíl příchozí problémy, které přiřadit ke kategorii správné. 
- Přesnost – makro: průměrná přesnost na úrovni třídy. Ve scénáři klasifikace problému se měří přesnost pro každou kategorii a potom přesností kategorie zprůměrovány. Pro tuto metriku jsou uvedeny všechny třídy stejnou váhu. Nemusíte zajistit dokonalou vyvážené datových sad (pokud existují stejný počet příklady jednotlivých kategorií), micro přesnosti a správnosti – makro jsou stejné.


### <a name="price-prediction-regression"></a>Předpověď ceny (regrese)

Je výchozí metriku pro regresní problémy **RSquared**. 1 je nejlepší možnou hodnotou. Bližší RSquared je 1, tím větší je váš model.

Jiných metrik reportovaných, jako je například výpadek absolutní, spolehlivosti ztráty, a ztrátě RMS lze použít k pochopení vašeho modelu a porovná ho s jinými regresní modely. 

## <a name="improve"></a>Zlepšení

Pokud hodnotíte modelu výkon není tak dobré, jako je třeba chcete, můžete:

* Připravte na delší časové období. Další čas, modul automatizované machine learning vyzkoušet další algoritmy a nastavení.

* Přidejte další data. Objem dat někdy není dostatečná k trénování vysoce kvalitní model strojového učení. 

* Zajistit rovnováhu mezi daty. Pro úlohy klasifikace Ujistěte se, že cvičnou sadou je vyvažují mezi kategorií. Například, pokud máte čtyři třídy 100 příklady školení a dvě první třídy (značky 1 a značky 2) se používají pro 90 záznamy, ale další dvě (značky 3 a tag4) se používají pouze na zbývajících 10 záznamů, nedostatku dat může způsobit, že má corr je velmi obtížné váš model ectly předpovědět značky 3 a tag4.

## <a name="code"></a>Kód

Po fázi hodnocení Tvůrce modelu výstupy souboru modelu a kód, který vám umožní přidat model pro vaši aplikaci. Modely ML.NET se uloží jako soubor zip. Kód pro načtení a použití modelu je přidán jako nový projekt ve vašem řešení. Tvůrce modelu se taky přidaly ukázkovou aplikaci konzoly, kterou můžete spouštět a podívejte se váš model v akci.

Kromě toho Tvůrce modelu výstupy kód, který vygeneruje modelu, tak, že rozumíte kroky používají ke generování modelu. Také vám pomůže kód trénování modelu přeučování modelu s novými daty.

## <a name="whats-next"></a>Co dále?

Zkuste [predikce ceny nebo jakýkoli scénář regrese](tutorials/predict-prices-with-model-builder.md)
