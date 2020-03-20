---
title: Co je .NET for Apache Spark?
description: Získejte informace o rozhraní .NET pro Apache Spark, bezplatném open source a multiplatformním rámci pro analýzu velkých objemů dat, které odvádí Spark kamkoli, kam píšete kód .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458200"
---
# <a name="what-is-net-for-apache-spark"></a>Co je .NET for Apache Spark?

[Apache Spark](what-is-spark.md) je univerzální distribuovaný procesor ový modul pro analýzu velkých datových sad – obvykle terabajtů nebo petabajtů dat. S rozhraním .NET pro Apache Spark, bezplatnou, otevřenou a multiplatformní podporou .NET pro populární open source rámec pro analýzu velkých objemů dat, můžete nyní přidat sílu Apache Spark do vašich aplikací pro velké objemy dat pomocí jazyků, které už znáte.

## <a name="why-choose-net-for-apache-spark"></a>Proč zvolit rozhraní .NET pro Apache Spark?

.NET pro Apache Spark umožňuje vývojářům se zkušenostmi s rozhraním .NET nebo základy kódu k účasti ve světě analýzy velkých objemů dat. .NET pro Apache Spark poskytuje vysoce výkonná rozhraní API pro použití Spark z C# a F#. Pomocí c# a f#, můžete přistupovat:

* DataFrame a SparkSQL pro práci se strukturovanými daty.
* Spark Structured Streaming pro práci s streamovanými daty.
* Spark SQL pro psaní dotazů se syntaxí SQL.
* Integrace strojového učení pro rychlejší školení a predikci (to znamená použít rozhraní .NET pro Apache Spark vedle [ML.NET).](https://dot.net/ml)

.NET pro Apache Spark je kompatibilní s .NET Standard, formální specifikace rozhraní API .NET, které jsou společné napříč implementacemi .NET. To znamená, že můžete použít rozhraní .NET pro Apache Spark kdekoli, kde napíšete kód .NET, což vám umožní znovu použít všechny znalosti, dovednosti, kód a knihovny, které již máte jako vývojář .NET.

.NET pro Apache Spark běží na Windows, Linux a macOS pomocí .NET Core. Je také spuštěn v systému Windows pomocí rozhraní .NET Framework. Své aplikace můžete nasadit do všech hlavních poskytovatelů cloudu, včetně Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks a Databricks na AWS.

## <a name="net-for-apache-spark-architecture"></a>.NET pro architekturu Apache Spark

Vazba jazyka C#/ F# na Spark je napsána na nové vrstvě Interop Spark, která nabízí snadnější rozšiřitelnost. Tato nová vrstva Spark interop byl napsán pomocí osvědčených postupů pro rozšíření jazyka a optimalizuje pro interop a výkon. Dlouhodobě lze tuto rozšiřitelnost použít pro přidání podpory pro jiné jazyky ve Sparku.

> [!div class="mx-imgBorder"]
> ![.NET pro architekturu Apache Spark](media/dotnet-spark-architecture.png)

O podpoře interop pro rozšíření jazyka Spark se můžete dozvědět v [návrhu](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>.NET pro výkon Apache Spark

Ve srovnání s Pythonem a Scalou používajícím [benchmark TPC-H](http://www.tpc.org/tpch/)si rozhraní .NET pro Apache Spark ve většině případů vede dobře a je 2x rychlejší než Python, když je rozhodující výkon uživatelem definované funkce. Stále se snaží zlepšit a porovnat výkonnost.

Chcete-li provést vlastní srovnávací testy, podívejte se na srovnávací testy dostupné na [rozhraní .NET pro Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>.NET pro plán Apache Spark

Další informace o krátkodobých a dlouhodobých plánech z oficiálního [plánu .NET pro Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).

## <a name="net-foundation"></a>Nadace .NET

Projekt .NET pro Apache Spark je součástí [.NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Contributions (Příspěvky)

Tým .NET pro Apache Spark podporuje příspěvky, problémy githubu i žádosti o přijetí vyžádat. Nejprve vyhledejte [existující problém](https://github.com/dotnet/spark/issues). Pokud nemůžete najít existující problém, [otevřete nový problém](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Další kroky

Zkuste .NET pro Apache Spark.
> [!div class="nextstepaction"]
> [Kurz: Začínáme s rozhraním .NET pro Apache Spark](./tutorials/get-started.md)
