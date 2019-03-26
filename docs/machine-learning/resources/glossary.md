---
title: Machine learning Glosář - ML.NET
description: Glosář důležité terminologie strojového učení, které jsou užitečné při vytváření vlastních modelů ML.NET.
ms.custom: seodec18
ms.date: 03/05/2019
ms.openlocfilehash: cc236aaa99fd8a7b05af666a5b96f657d8bd3ad4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410235"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Machine learning Glosář termínů důležité

V následujícím seznamu je kompilace podmínek důležité machine learning, které jsou užitečné při vytváření vlastních modelů ML.NET.

> [!NOTE]
> Tato dokumentace odkazuje na ML.NET, která je aktuálně ve verzi Preview. Materiál může být mohou změnit. Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

## <a name="accuracy"></a>Přesnost

V [klasifikace](#classification), přesnost je počet správně klasifikované položky rozdělené tak celkový počet položek v sadě testů. Je v rozsahu 0 (nejméně přesné) na hodnotu 1 (co nejvíce zpřesnili). Přesnost je jedním z metrik výkonu modelu. Zvažte ve spojení s [přesnost](#precision), [spojené s vracením](#recall), a [F skóre](#f-score).

## <a name="area-under-the-curve-auc"></a>Oblasti pod křivkou (AUC)

V [binární klasifikace](#binary-classification), metriku hodnocení, která je hodnota v oblasti pod křivkou, která ukazuje zeměpisný pravdivě pozitivní rychlost (na ose y) na míru falešně pozitivních výsledků (na ose x). Od 0,5 (nejhorších) do 1 (doporučené). Také oblasti pod křivkou roc s více TŘÍDAMI, například příjemce provozních charakteristik křivky. Další informace najdete v tématu [Receiver operating charakteristiku](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) článku na wikipedii.

## <a name="binary-classification"></a>Binární klasifikace

A [klasifikace](#classification) malá a velká where [popisek](#label) je pouze jedné ze dvou tříd. Další informace najdete v tématu [binární klasifikace](tasks.md#binary-classification) část [služby Machine learning úlohy](tasks.md) tématu.

## <a name="classification"></a>Klasifikace

Když se data používá k předpovědi kategorii, [pod dohledem strojového učení](#supervised-machine-learning) je volána úloha, klasifikace. [Binární klasifikace](#binary-classification) odkazuje na predikci pouze dvě kategorie (například klasifikaci obrázku jako obrázek "cat" nebo "pes). [Klasifikace víc tříd](#multiclass-classification) odkazuje na predikci více kategorií (například při klasifikaci obrázku jako obrázek konkrétní druh pes).

## <a name="coefficient-of-determination"></a>Koeficient spolehlivosti

V [regrese](#regression), metriku hodnocení, která určuje, jak dobře zapadá datového modelu. Rozsahu od 0 do 1. Hodnota 0 znamená, že data jsou náhodných nebo jinak nevejde do modelu. Hodnota 1 znamená, že model přesně odpovídá data. To se často označuje jako r<sup>2</sup>, R<sup>2</sup>, nebo spolehlivosti.

## <a name="feature"></a>Funkce

Měřitelné vlastnosti jev se měří, obvykle číselnou hodnotu (double). Funkce jsou označovány jako **funkce vector** a většinou uložena jako `double[]`. Funkce definují důležité charakteristiky jev se měří. Další informace najdete v tématu [funkce](https://en.wikipedia.org/wiki/Feature_(machine_learning)) článku na wikipedii.

## <a name="feature-engineering"></a>Návrh funkcí

Vytváření funkcí je proces, který zahrnuje definování sady [funkce](#feature) a vývoj softwaru, který vytváří vektory funkce z dostupných jev dat, například funkce extrakce. Další informace najdete v tématu [konstruování](https://en.wikipedia.org/wiki/Feature_engineering) článku na wikipedii.

## <a name="f-score"></a>F-skóre

V [klasifikace](#classification), vyhodnocení metriku, která vyrovnává [přesnost](#precision) a [spojené s vracením](#recall).

## <a name="hyperparameter"></a>Hyperparameter

Parametr algoritmu strojového učení. Mezi příklady patří počet stromů výuku v kurzech mooc rozhodovací les nebo velikost kroku sestupu algoritmu. Hodnoty *Hyperparameters* nastavují před trénování modelu a řídí proces hledání parametry funkce předpovědi, například porovnání body v rozhodovacím stromu nebo váhy v modelu lineární regrese . Další informace najdete v tématu [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) článku na wikipedii.

## <a name="label"></a>Popisek

Elementu, který chcete předpovědět s modelem machine learning. Například plemeno dog nebo budoucí ceny akcie.

## <a name="log-loss"></a>Ztráta protokolu

V [klasifikace](#classification), metriku hodnocení, který charakterizuje přesnost třídění. Menší ztráty protokolu je, přesnější třídění.

## <a name="mean-absolute-error-mae"></a>Střední absolutní chyba (MAE)

V [regrese](#regression), vyhodnocení metriky, které je průměrem všechny chyby modelu, kde je chyba modelu vzdálenost mezi předpokládané [popisek](#label) hodnota a hodnota správný popisek.

## <a name="model"></a>Model

Tradičně parametry pro funkci předpovědi. Například vah model lineární regrese nebo body rozdělení v rozhodovacím stromu. V ML.NET, model obsahuje všechny informace potřebné k předpovědi [popisek](#label) objektu doména (třeba image nebo text). To znamená, že ML.NET modely zahrnují snadné postup a také parametry pro funkci předpovědi.

## <a name="multiclass-classification"></a>Klasifikace víc tříd

A [klasifikace](#classification) malá a velká where [popisek](#label) je jedním ze tří nebo více tříd. Další informace najdete v tématu [klasifikace víc tříd](tasks.md#multiclass-classification) část [služby Machine learning úlohy](tasks.md) tématu.

## <a name="n-gram"></a>N-gram

Nové funkce extrakce schéma pro textová data: všechny posloupnost N slov se změní [funkce](#feature) hodnotu.

## <a name="numerical-feature-vector"></a>Numerické funkce vektoru

A [funkce](#feature) vektor, který se skládá pouze z číselných hodnot. To se podobá `double[]`.

## <a name="pipeline"></a>Kanál

Všechny operace nutné přizpůsobit model do datové sady. Kanál se skládá z importu dat, transformace, snadné a učení kroky. Jakmile se trénuje kanálu, změní se na model.

## <a name="precision"></a>Přesnost

V [klasifikace](#classification), přesnost pro třídu je počet položek správně předpovědět jako patřící do této třídy dělený celkový počet položek předpovědět jako patřící do třídy.

## <a name="recall"></a>Svolat

V [klasifikace](#classification), odvolání pro třídu je počet položek správně předpovědět jako patřící do této třídy dělený celkový počet položek, které ve skutečnosti patří do třídy.

## <a name="regression"></a>Regrese

A [pod dohledem strojového učení](#supervised-machine-learning) úloh, kde výstup je skutečné hodnoty, například, double. Příklady: předpověď cen akcií. Další informace najdete v tématu [regrese](tasks.md#regression) část [služby Machine learning úlohy](tasks.md) tématu.

## <a name="relative-absolute-error"></a>Relativní absolutní chyba

V [regrese](#regression), metriku hodnocení, která je součet všech absolutních chyb dělený součet vzdálenosti mezi správné [popisek](#label) hodnotami a průměrem všech opravte hodnoty popisků.

## <a name="relative-squared-error"></a>Relativní kvadratická chyba

V [regrese](#regression), metriku hodnocení, která je součet všech spolehlivosti absolutních chyb dělený součet kvadratických vzdálenosti mezi správné [popisek](#label) hodnotami a průměrem všech opravte hodnoty popisků.

## <a name="root-of-mean-squared-error-rmse"></a>Kořen střední spolehlivosti chyby (RMSE)

V [regrese](#regression), metriku hodnocení, která je druhá odmocnina průměru kvadratických chyb.

## <a name="supervised-machine-learning"></a>Technik strojového učení

Podtřída strojového učení, ve kterém požadovaný model předpovídá popisek dosud nezobrazený data. Mezi příklady patří klasifikace, regrese a strukturované předpovědi. Další informace najdete v tématu [pod dohledem learning](https://en.wikipedia.org/wiki/Supervised_learning) článku na wikipedii.

## <a name="training"></a>Školení

Proces identifikace [modelu](#model) pro danou trénovací datové sady. Pro lineární model to znamená vyhledání váhy. Strom zahrnuje identifikaci body rozdělení.

## <a name="transform"></a>Transformace

A [kanálu](#pipeline) komponenty, který transformuje data. Například z textu na vektorové čísel.

## <a name="unsupervised-machine-learning"></a>Bez dohledu strojového učení

Podtřída strojového učení, ve kterém požadovaný model najde v datech skryté (nebo latentní) struktury. Mezi příklady patří clusterů, tématu modelování a snížení. Další informace najdete v tématu [Supervize](https://en.wikipedia.org/wiki/Unsupervised_learning) článku na wikipedii.
