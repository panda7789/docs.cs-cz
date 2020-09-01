---
title: Elasticsearch v cloudových nativních aplikacích
description: Přečtěte si, jak přidat funkce elastického vyhledávání do cloudových nativních aplikací.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 70d1925d6b8c7bbe515ee4f178513dc61212ebce
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271799"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elasticsearch v cloudové nativní aplikaci

Elasticsearch je distribuovaný systém vyhledávání a analýzy, který umožňuje komplexní možnosti vyhledávání napříč různými typy dat. Je to open source a široce populární. Vezměte v úvahu, jak následující společnosti integrují Elasticsearch do své aplikace:

- [Wikipedii](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pro fulltextové a přírůstkové vyhledávání (hledání při psaní).
- [GitHub](https://www.elastic.co/customers/github) pro indexování a vystavení více než 8 000 000 úložišť kódu.  
- [Docker](https://www.elastic.co/customers/docker) pro zjištění, že je knihovna kontejnerů zjistitelná.

Elasticsearch je postaven na začátku fulltextového vyhledávacího modulu [Apache Lucene](https://lucene.apache.org/core/) . Lucene nabízí vysoce výkonné indexování dokumentů a dotazování. Indexuje data pomocí obráceného indexového schématu – místo mapování stránek na klíčová slova mapuje klíčová slova na stránky stejně jako Glosář na konci knihy. Lucene má výkonné možnosti syntaxe dotazů a může dotazovat data podle:

- Termín (celé slovo)
- Prefix (začíná – s Wordem)
- Zástupný znak (pomocí \* filtrů "" nebo "?")
- Fráze (sekvence textu v dokumentu)
- Logická hodnota (složitá hledání kombinují dotazy)

I když Lucene nabízí pro hledání nízké úrovně, Elasticsearch poskytuje server, který je umístěný na Lucene. Elasticsearch přidává funkce vyšší úrovně, které zjednodušují práci s Lucene, včetně rozhraní RESTful API pro přístup k funkcím indexování a vyhledávání v aplikaci Lucene. Poskytuje taky distribuovanou infrastrukturu, která podporuje obrovské škálovatelnost, odolnost proti chybám a vysokou dostupnost.

Pro větší cloudové nativní aplikace s požadavky na hledání je Elasticsearch k dispozici jako spravovaná služba v Azure. Služba Microsoft Azure Marketplace funkce předkonfigurovaných šablon, které můžou vývojáři použít k nasazení clusteru Elasticsearch v Azure.

Z Microsoft Azure Marketplace můžou vývojáři využít předem nakonfigurované šablony, pomocí kterých můžete rychle nasadit cluster Elasticsearch v Azure. Pomocí nabídky spravované v Azure můžete nasadit až 50 datových uzlů, 20 koordinačních uzlů a tři vyhrazené hlavní uzly.

## <a name="summary"></a>Souhrn

V této části najdete podrobný přehled dat v systémech nativních pro Cloud. Začali jsme na rozdíl od ukládání dat v aplikacích v monolitické s využitím vzorů úložiště dat v nativních systémech cloudu. Prohlédli jsme se na vzorcích dat implementovaných v nativních systémech cloudu, včetně dotazů na různé služby, distribuovaných transakcí a vzorů, které se týkají systémů s vysokými objemy. NoSQL jsme na SQL data. Prohlédli jsme si možnosti úložiště dat dostupné v Azure, které obsahují možnosti orientované na Microsoft i open source. Nakonec jsme probrali ukládání do mezipaměti a Elasticsearch v cloudové nativní aplikaci.

### <a name="references"></a>Reference

- [Model dělení zodpovědnosti příkazů a dotazů (CQRS – Command and Query Responsibility Segregation)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Vzor zdroje událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [Proč není RDBMS odolný proti oddílu v CAP věta a proč je k dispozici?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Materialized View](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Všechno, co opravdu potřebujete znát o open source databázích](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Model kompenzační transakce](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Vzor Saga](https://microservices.io/patterns/data/saga.html)

- [Saga vzory | Implementace obchodních transakcí pomocí mikroslužeb](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Model kompenzační transakce](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Seznámení za 9 míč: vysvětlení úrovní konzistence Cosmos DB](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Zkoumání různých typů databází NoSQL část II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [V databázích RDBMS, NoSQL a NewSQL. Rozhovor s Jan Ryanou](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: úplné porovnání](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [POMLČKa: čtyři vlastnosti databáze Kubernetes-Native](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CockroachDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch: konečný průvodce](https://shop.oreilly.com/product/0636920028505.do)
  
- [Úvod do Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Předchozí](azure-caching.md) 
> [Další](resiliency.md) <!-- Next Chapter -->
