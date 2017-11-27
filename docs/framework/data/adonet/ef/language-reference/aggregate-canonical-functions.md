---
title: "Kanonické agregační funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5a5aea48b1c70c550641f3450dff16e57dd4f62b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="aggregate-canonical-functions"></a>Kanonické agregační funkce

Agregace jsou výrazy, které snížit řadu vstupní hodnoty do, například jednu hodnotu. Agregace se obvykle používá ve spojení s vyberte výrazu v klauzuli GROUP BY a existují omezení toho, kde je lze použít.

V následující tabulce jsou uvedeny agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.

| Funkce | Popis |
| -------- | ----------- |
| `Avg(expression)` | Vrátí průměr hodnot nesmí být nulová.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, A `Decimal`.<br><br>**Návratová hodnota**<br><br>Typ `expression`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)][!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)] |
| `BigCount(expression)` | Vrátí velikost agregace včetně hodnotu null a duplicitní hodnoty.<br><br>**Argumenty**<br><br>Libovolného typu.<br><br>**Návratová hodnota**<br><br>`Int64`.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)][!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)] |
| `Count(expression)` | Vrátí velikost agregace včetně hodnotu null a duplicitní hodnoty.<br><br>**Argumenty**<br><br>Libovolného typu.<br><br>**Návratová hodnota**<br><br>`Int32`.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)][!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)] |
| `Max(expression)` | Vrátí maximální hodnoty null.<br><br>**Argumenty**<br><br>A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Návratová hodnota**<br><br>Typ `expression`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)][!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)] |
| `Min(expression)` | Vrátí minimální hodnoty null.<br><br>**Argumenty**<br><br>A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Návratová hodnota**<br><br>Typ `expression`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)][!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)] |
| `StDev(expression)` | Vrací směrodatnou odchylku hodnot nesmí být nulová.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Návratová hodnota**<br><br>A `Double`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)][!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)] |
| `StDevP(expression)` | Vrací směrodatnou odchylku základního souboru všech hodnot.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Návratová hodnota**<br><br>A `Double`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)][!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)] |
| `Sum(expression)` | Vrátí součet hodnoty null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Návratová hodnota**<br><br>A `Double`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)][!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)] |
| `Var(expression)` | Vrací odchylku všech hodnot, které nejsou null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Návratová hodnota**<br><br>A `Double`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)][!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)] |
| `VarP(expression)` | Vrací odchylku základního souboru všech hodnot, které nejsou null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Návratová hodnota**<br><br>A `Double`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.<br><br>**Příklad** [!code-csharp [DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)][!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] |

Ekvivalentní funkce je k dispozici ve zprostředkovateli spravované klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Na základě kolekce agregace

Na základě kolekce agregace (funkce kolekce) fungují na kolekce a vrátit hodnotu. Například pokud objednávky je kolekce všechny objednávky, můžete vypočítat nejdřívější datum expedice s následující výraz:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Výrazy uvnitř agregace na základě kolekce vyhodnocují v aktuálním oboru vedlejším překlad názvů.

## <a name="group-based-aggregates"></a>Na základě skupiny agregace

Na základě skupiny agregace jsou vypočítávány přes skupinu podle definice v klauzuli GROUP BY. Pro každou skupinu ve výsledku samostatné agregace se počítá pomocí elementů v každé skupině jako vstup pro agregační výpočtu. Při klauzule group by se používá ve výrazu select, může být pouze seskupování názvy výrazů, agregací nebo konstantní výrazy v projekci nebo klauzuli ORDER by.

Následující příklad vypočítá průměrné množství pro každý produkt seřazené:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Je možné, že ve výrazu SELECT na základě skupiny agregace bez explicitní klauzuli group by. Všechny elementy v tomto případě jsou považovány za jednu skupinu. Jde o ekvivalent zadávání seskupení založené na konstanta. Využít, například následující výraz:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Jde o ekvivalent takto:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

V rámci oboru rozlišení názvů, která by byla viditelná pro výraz klauzule WHERE se vyhodnotí výrazy uvnitř agregace na základě skupiny.

Jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], na základě skupiny agregace můžete také určit, všech nebo odlišné modifikátor. Pokud odlišné modifikátor není zadaný, duplicitní položky jsou odstraněny z agregační vstupní kolekce, než agregace je počítaný. Pokud je zadán všechny – modifikátor (nebo pokud není zadán žádný modifikátor), se provádí žádné duplicitní odstranění.  

## <a name="see-also"></a>Viz také

[Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
