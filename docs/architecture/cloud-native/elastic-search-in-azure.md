---
title: Elastické vyhledávání v aplikacích nativních pro cloud
description: Přečtěte si o přidávání funkcí elastického vyhledávání do aplikací nativních pro cloud.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 1bce255b6315006b11e0b6ac77040300f67ed984
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141286"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elastické vyhledávání v aplikaci nativní pro cloud

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch je distribuovaný vyhledávací a analytický systém, který umožňuje komplexní možnosti vyhledávání napříč různými typy dat. Je to open source a široce populární. Zvažte, jak následující společnosti integrovat Elasticsearch do jejich aplikace:

- [Wikipedie](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pro fulltextové a přírůstkové (vyhledávání při psaní) vyhledávání.
- [GitHub](https://www.elastic.co/customers/github) indexovat a vystavit více než 8 milionů repozitářů kódu.  
- [Docker](https://www.elastic.co/customers/docker) pro to, aby jeho kontejnerové knihovny zjistitelné.

Elastické vyhledávání je postaveno na fulltextovém vyhledávači [Apache Lucene.](https://lucene.apache.org/core/) Lucene poskytuje vysoce výkonné indexování dokumentů a dotazování. Indexuje data pomocí invertovaného indexovacího schématu – namísto mapování stránek na klíčová slova mapuje klíčová slova na stránky stejně jako glosář na konci knihy. Lucene má výkonné možnosti syntaxe dotazu a může dotazovat data podle:

- Termín (celé slovo)
- Předpona (spuštění-s word)
- Zástupný znak\*(pomocí filtrů " " nebo "?"
- Fráze (posloupnost textu v dokumentu)
- Logická hodnota (komplexní hledání kombinující dotazy)

Zatímco Lucene poskytuje nízkoúrovňové instalatérské práce pro vyhledávání, Elasticsearch poskytuje server, který sedí na vrcholu Lucene. Elasticsearch přidává funkce vyšší úrovně pro zjednodušení pracovní Lucene, včetně ROZHRANÍ RESTful API pro přístup k lucene indexování a vyhledávání funkce. Poskytuje také distribuovanou infrastrukturu schopnou masivní škálovatelnosti, odolnosti proti chybám a vysoké dostupnosti.

Pro větší cloudové nativní aplikace se složitými požadavky na vyhledávání je Elasticsearch k dispozici jako spravovaná služba v Azure. Microsoft Azure Marketplace obsahuje předem nakonfigurované šablony, které můžou vývojáři použít k nasazení clusteru Elastického vyhledávání v Azure.

Na webu Microsoft Azure Marketplace můžou vývojáři používat předkonfigurované šablony vytvořené k rychlému nasazení clusteru Elastického vyhledávání v Azure. Pomocí nabídky spravované Azure můžete nasadit až 50 datových uzlů, 20 koordinačních uzlů a tři vyhrazené hlavní uzly.

## <a name="summary"></a>Souhrn

Tato kapitola představila podrobný pohled na data v cloudových nativních systémech. Začali jsme kontrastním ukládáním dat v monolitických aplikacích se vzory ukládání dat v cloudových systémech. Podívali jsme se na datové vzory implementované v systémech nativních na cloudu, včetně dotazů napříč službami, distribuovaných transakcí a vzorců pro řešení velkoobjemových systémů. Kontrastovali jsme SQL s NoSQL daty. Podívali jsme se na možnosti úložiště dat dostupné v Azure, které zahrnují možnosti zaměřené na Microsoft i open source. Nakonec jsme diskutovali ukládání do mezipaměti a elastické vyhledávání v aplikaci nativní pro cloud.

### <a name="references"></a>Odkazy

- [Model dělení zodpovědnosti příkazů a dotazů (CQRS – Command and Query Responsibility Segregation)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Vzor získávání událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [RDBMSs vs. NoSQL databáze: Přehled](https://maxivak.com/rdbms-vs-nosql-databases/)

- [Proč není RDBMS Partition Tolerantní v Cap ověnčené teoretiku a proč je k dispozici?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Materialized View](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Vše, co opravdu potřebujete vědět o open source databázích](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Model kompenzační transakce](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Vzor ságy](https://microservices.io/patterns/data/saga.html)

- [Saga vzory | Jak implementovat obchodní transakce pomocí mikroslužeb](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Model kompenzační transakce](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Získání za 9-Ball: Cosmos DB konzistence úrovně vysvětlil](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Zkoumání různých typů NoSQL databází část II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [V databázích RDBMS, NoSQL a NewSQL. Rozhovor s Johnem Ryanem](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: Úplné porovnání](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH: Čtyři vlastnosti Kubernetes-Nativní databáze](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [Švábdb](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [JugabyteDB](https://www.yugabyte.com/)

- [Vitess (Rak.)](https://vitess.io/)

- [Elasticsearch: Definitivní průvodce](http://shop.oreilly.com/product/0636920028505.do)
  
- [Úvod do Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Předchozí](azure-caching.md)
>[další](resiliency.md) <!-- Next Chapter -->
