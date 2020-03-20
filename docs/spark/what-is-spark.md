---
title: Co je Apache Spark?
description: Seznamte se s Apache Spark a scénáři velkých objemů dat.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458177"
---
# <a name="what-is-apache-spark"></a>Co je Apache Spark?

[Apache Spark](https://spark.apache.org/) je open source paralelní zpracování framework, který podporuje zpracování v paměti pro zvýšení výkonu aplikací, které analyzují velké objemy dat. Řešení pro velké objemy dat jsou navržena tak, aby zpracovávala data, která jsou příliš velká nebo složitá pro tradiční databáze. Spark zpracovává velké množství dat v paměti, což je mnohem rychlejší než alternativy založené na disku.

## <a name="common-big-data-scenarios"></a>Běžné scénáře velkých objemů dat

Architekturu velkých objemů dat můžete zvážit, pokud potřebujete ukládat a zpracovávat velké objemy dat, transformovat nestrukturovaná data nebo zpracovávat streamovaná data. Spark je univerzální distribuovaný procesorový modul, který lze použít pro několik scénářů velkých objemů dat.

### <a name="extract-transform-and-load-etl"></a>Extrakce, transformace a načtení (ETL)

[Extrahovat, transformovat a načíst (ETL)](/azure/architecture/data-guide/relational-data/etl) je proces shromažďování dat z jednoho nebo více zdrojů, úpravy dat a přesunutí dat do nového úložiště dat. Data lze transformovat několika způsoby, včetně:

* Filtrování
* Řazení
* Agregaci
* Připojení
* Čištění
* Odstranění duplicit
* Ověřování

### <a name="real-time-data-stream-processing"></a>Zpracování datových proudů v reálném čase

Streamování dat v reálném čase jsou data v pohybu. Telemetrie ze zařízení IoT, weblogy a clickstreams jsou všechny příklady streamování dat. Data v reálném čase mohou být zpracována za účelem poskytování užitečných informací, jako je například geoprostorová analýza, vzdálené monitorování a detekce anomálií. Stejně jako relační data můžete filtrovat, agregovat a připravovat streamovaná data před přesunutím dat do výstupníjím propadu. Apache Spark podporuje [zpracování datových proudů v reálném čase](/azure/architecture/data-guide/big-data/real-time-processing) prostřednictvím streamování [Spark](https://spark.apache.org/streaming/).

### <a name="batch-processing"></a>Dávkové zpracování

[Dávkové zpracování](/azure/architecture/data-guide/big-data/batch-processing) je zpracování velkých objemů dat v klidovém stavu. Můžete filtrovat, agregovat a připravit velmi velké datové sady pomocí dlouhotrvající úlohy paralelně.

### <a name="machine-learning-through-mllib"></a>Strojové učení prostřednictvím mllibu

Strojové učení se používá pro pokročilé analytické problémy. Počítač může použít existující data k prognóze nebo předvídání budoucího chování, výsledků a trendů. Knihovna strojového učení Apache Spark, [MLlib](https://spark.apache.org/mllib/), obsahuje několik algoritmů a nástrojů strojového učení.

### <a name="graph-processing-through-graphx"></a>Zpracování grafů přes GraphX

Graf je kolekce uzlů propojených hranami. Databázi grafů můžete použít, pokud máte hierarchická data nebo data s propojenými relacemi. Tato data můžete zpracovávat pomocí [rozhraní GraphX](https://spark.apache.org/graphx/) API Apache Spark.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>SQL a strukturované zpracování dat se Spark SQL

Pokud pracujete se strukturovanými (formátovanými) daty, můžete použít dotazy SQL v aplikaci Spark pomocí [Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Architektura Apache Spark

Apache Spark, který používá architekturu master/worker, má tři hlavní součásti: ovladač, vykonavatelé a správce clusteru.

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Ovladač

Ovladač se skládá z vašeho programu, jako je konzolová aplikace C# a relace Spark. Relace Spark převezme váš program a rozdělí jej na menší úkoly, které jsou zpracovány vykonavatelé.

### <a name="executors"></a>Exekutoři

Každý vykonavatel nebo pracovní uzel obdrží úlohu od ovladače a provede tuto úlohu. Prováděcí moduly jsou umístěny v entitě známé jako cluster.

### <a name="cluster-manager"></a>Správce clusteru

Správce clusteru komunikuje s ovladačem i prováděcími moduly s:

* Správa přidělení prostředků
* Spravovat rozdělení programů
* Spravovat spuštění programu

## <a name="language-support"></a>Podpora jazyků

Apache Spark podporuje následující programovací jazyky:

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>Zapalovací api

Apache Spark podporuje následující api:

* [Spark Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Spark Java API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Spark Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Spark R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), vestavěné funkce

## <a name="next-steps"></a>Další kroky

Zjistěte, jak můžete používat Apache Spark ve vaší aplikaci .NET. S rozhraním .NET pro Apache Spark mohou vývojáři se zkušenostmi s rozhraním .NET a obchodní logikou psát dotazy na velká data v c# a F#.
> [!div class="nextstepaction"]
> [Co je .NET pro Apache Spark](what-is-apache-spark-dotnet.md)
