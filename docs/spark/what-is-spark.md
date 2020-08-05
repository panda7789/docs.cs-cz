---
title: Co je Apache Spark?
description: Přečtěte si o scénářích Apache Spark a velkých objemů dat.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: cde66c4084b7c86e1b78d89c2bad94402dbd7d60
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555991"
---
# <a name="what-is-apache-spark"></a>Co je Apache Spark?

[Apache Spark](https://spark.apache.org/) je open source platforma pro paralelní zpracování, která podporuje zpracování v paměti pro zvýšení výkonu aplikací, které analyzují velké objemy dat. Řešení pro velké objemy dat jsou navržená tak, aby data, která jsou pro tradiční databáze moc velká nebo složitá. Spark zpracovává velké objemy dat v paměti, což je mnohem rychlejší než v případě alternativ na disku.

## <a name="common-big-data-scenarios"></a>Běžné scénáře s velkými objemy dat

Pokud potřebujete ukládat a zpracovávat velké objemy dat, transformovat nestrukturovaná data nebo zpracovávat streamovaná data, můžete zvážit architekturu velkých objemů dat. Spark je univerzální distribuovaný modul pro zpracování, který se dá použít pro několik scénářů velkých objemů dat.

### <a name="extract-transform-and-load-etl"></a>Extrakce, transformace a načtení (ETL)

[Extrakce, transformace a načítání (ETL)](/azure/architecture/data-guide/relational-data/etl) je proces shromažďování dat z jednoho nebo více zdrojů, úpravy dat a přesun dat do nového úložiště dat. Existuje několik způsobů, jak transformovat data, včetně:

* Filtrování
* Řazení
* Agregování
* Připojení
* Čistil
* Můžou
* Opětovné

### <a name="real-time-data-stream-processing"></a>Zpracování datových proudů v reálném čase

Streamování dat nebo dat v reálném čase jsou data v pohybu. V některých příkladech streamování dat jsou telemetrie ze zařízení IoT, Weblogs a stránkách. Data v reálném čase lze zpracovat za účelem poskytnutí užitečných informací, jako jsou geoprostorové analýzy, vzdálené monitorování a detekce anomálií. Stejně jako u relačních dat můžete filtrovat, agregovat a připravit streamovaná data, než data přesunete do výstupní jímky. Apache Spark podporuje [zpracování datových proudů v reálném čase](/azure/architecture/data-guide/big-data/real-time-processing) prostřednictvím [streamování Sparku](https://spark.apache.org/streaming/).

### <a name="batch-processing"></a>Dávkové zpracování

[Dávkové zpracování](/azure/architecture/data-guide/big-data/batch-processing) je zpracování velkých objemů dat v klidovém umístění. Můžete filtrovat, agregovat a připravit velmi velké datové sady s využitím dlouhotrvajících úloh paralelně.

### <a name="machine-learning-through-mllib"></a>Machine Learning prostřednictvím MLlib

Strojové učení slouží k pokročilým analytickým problémům. Počítač může používat stávající data k předpovědi nebo předpovědi budoucích chování, výsledků a trendů. [MLlib](https://spark.apache.org/mllib/)je knihovna strojového učení, která obsahuje několik algoritmů a nástrojů strojového učení. Apache Spark

### <a name="graph-processing-through-graphx"></a>Zpracování grafů prostřednictvím GraphX

Graf je kolekce uzlů, které jsou propojeny pomocí okrajů. Pokud máte hierarchická data nebo data s propojenými vztahy, můžete použít databázi grafu. Tato data můžete zpracovat pomocí rozhraní [GRAPHX](https://spark.apache.org/graphx/) API pro Apache Spark.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>SQL a strukturované zpracování dat pomocí Spark SQL

Pokud pracujete se strukturovanými (formátovanými) daty, můžete v aplikaci Spark použít dotazy SQL pomocí [Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Architektura Apache Spark

Apache Spark, která používá architekturu hlavního/pracovního procesu, má tři hlavní komponenty: ovladač, vykonavatelé a Správce clusteru.

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Ovladač

Ovladač se skládá z vašeho programu, například konzolové aplikace v jazyce C# a relace Spark. Relace Spark přebírá program a rozděluje ho do menších úloh, které jsou zpracovávány vykonavateli.

### <a name="executors"></a>Prováděcí moduly

Každý vykonavatel nebo pracovní uzel přijme úkol od ovladače a provede tuto úlohu. Vykonavatelé se nacházejí v entitě, která se označuje jako cluster.

### <a name="cluster-manager"></a>Správce clusteru

Správce clusteru komunikuje s ovladačem i s prováděcími moduly pro:

* Spravovat přidělení prostředků
* Spravovat rozdělení programu
* Správa provádění programu

## <a name="language-support"></a>Podpora jazyků

Apache Spark podporuje následující programovací jazyky:

* Scala
* Python
* Java
* SQL
* R
* Jazyky .NET (C#/F #)

## <a name="spark-apis"></a>Rozhraní Spark API

Apache Spark podporuje následující rozhraní API:

* [Rozhraní Spark Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Rozhraní Spark Java API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Rozhraní Spark Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Rozhraní Spark R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), integrované funkce

## <a name="next-steps"></a>Další kroky

Přečtěte si, jak můžete použít Apache Spark v aplikaci .NET. Díky rozhraní .NET pro Apache Spark můžou vývojáři s prostředím .NET a obchodní logikou zapisovat dotazy na velké objemy dat v jazycích C# a F #.
> [!div class="nextstepaction"]
> [Co je .NET pro Apache Spark](what-is-apache-spark-dotnet.md)
