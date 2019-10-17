---
title: Co je .NET for Apache Spark?
description: Přečtěte si o rozhraní .NET pro Apache Spark, bezplatném, open source a mezi platformami pro analýzu velkých objemů dat pro různé platformy, které zabírají Spark kdekoli, kde píšete kód .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: c31b50a20ac08bcde077e1e85ee915435a99fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395848"
---
# <a name="what-is-net-for-apache-spark"></a>Co je .NET for Apache Spark?

[Apache Spark](what-is-spark.md) je univerzální modul pro zpracování distribuovaných dat pro analýzy prostřednictvím rozsáhlých datových sad – obvykle terabajtů nebo petabajty dat. Díky rozhraní .NET pro Apache Spark, bezplatné, open source a podporu rozhraní .NET pro více platforem pro oblíbenou Open Source analýzu velkých objemů dat, teď můžete do aplikací pro velké objemy dat přidat sílu Apache Spark pomocí jazyků, které už znáte.

## <a name="why-choose-net-for-apache-spark"></a>Proč zvolit .NET pro Apache Spark?

.NET for Apache Spark umožňuje vývojářům využít prostředí .NET nebo základy kódu, aby se mohli zúčastnit celosvětovosti analýz velkých objemů dat. .NET for Apache Spark poskytuje rozhraní API pro vysoké výkon pro použití C# Sparku z a F#. Pomocí C# a F#můžete získat přístup k:

* Datový rámec a SparkSQL pro práci se strukturovanými daty
* Strukturované streamování Sparku pro práci s datovými proudy
* Spark SQL pro zápis dotazů pomocí syntaxe SQL
* Integrace služby Machine Learning pro rychlejší školení a předpovědi (tj. použití .NET pro Apache Spark společně s [ml.NET](http://dot.net/ml))

Rozhraní .NET pro Apache Spark je kompatibilní s .NET Standard, formální specifikace rozhraní .NET API, která jsou společná pro implementace v rozhraní .NET. To znamená, že můžete použít rozhraní .NET pro Apache Spark kdekoli napíšete kód .NET, který vám umožní znovu použít všechny znalosti, dovednosti, kód a knihovny, které už máte jako vývojář rozhraní .NET.

Rozhraní .NET pro Apache Spark běží na systémech Windows, Linux a macOS pomocí .NET Core. Také se spouští ve Windows pomocí .NET Framework. Své aplikace můžete nasadit do všech největších poskytovatelů cloudu, včetně Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks a datacihlů na AWS.

## <a name="net-for-apache-spark-architecture"></a>Architektura rozhraní .NET pro Apache Spark

Vazba C#/ F# jazyk na Spark je zapsána na nové vrstvě interoperability Spark, která nabízí snadnější rozšiřitelnost. Tato nová vrstva interoperability Spark byla napsaná pomocí osvědčených postupů pro jazykové rozšíření a optimalizuje pro interoperabilitu a výkon. Dlouhodobá tato rozšiřitelnost se dá použít k přidání podpory pro jiné jazyky ve Sparku.

> [!div class="mx-imgBorder"]
> @no__t – 0.NET pro Apache Spark architektury @ no__t-1

Informace o podpoře spolupráce pro jazykové rozšíření Spark z návrhu najdete v [části](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>.NET pro Apache Spark výkon

V porovnání s Pythonem a Scala pomocí [srovnávacího testu TPC-H](http://www.tpc.org/tpch/)využije .net pro Apache Spark ve většině případů dobře a je dvojnásobější, než Python, pokud je důležitý výkon funkce definovaný uživatelem. Pro zlepšení výkonu a srovnávací testy výkonu probíhá nepřetržité úsilí. 

Pokud chcete vlastní srovnávací testy, přečtěte si srovnávací testy dostupné v [rozhraní .NET pro Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>Plán .NET pro Apache Spark

Přečtěte si o krátkodobých a dlouhodobých plánech z oficiálního [rozhraní .NET pro Apache Spark plán](https://github.com/dotnet/spark/blob/master/ROADMAP.md).

## <a name="net-foundation"></a>.NET Foundation

Projekt .NET for Apache Spark je součástí [.NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Věcný

.NET for Apache Spark Team podporuje příspěvky, i žádosti GitHubu a žádosti o přijetí změn. Nejprve vyhledejte [existující problém](https://github.com/dotnet/spark/issues). Pokud nemůžete najít existující problém, [otevřete nový problém](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Další kroky

Vyzkoušejte .NET pro Apache Spark.
> [!div class="nextstepaction"]
> [Kurz: Začínáme s .NET pro Apache Spark](./tutorials/get-started.md)
