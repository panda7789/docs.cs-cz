---
title: Agregační kanonické funkce
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251358"
---
# <a name="aggregate-canonical-functions"></a>Agregační kanonické funkce

Agregace jsou výrazy, které omezují řadu vstupních hodnot například na jedinou hodnotu. Agregace se obvykle používají ve spojení s klauzulí GROUP BY výrazu SELECT a existují omezení, kde je lze použít.

## <a name="aggregate-entity-sql-canonical-functions"></a>Agregační Entity SQL – kanonické funkce

Níže jsou uvedené agregační Entity SQL kanonické funkce.

### <a name="avgexpression"></a>Prům (výraz)

Vrátí průměr hodnot, které nejsou null.

**Argumenty**

A `Int32` ,`Int64`, a`Decimal`. `Double`

**Návratová hodnota**

Typ `expression` `null` nebo `null` , pokud jsou všechny vstupní hodnoty hodnotami.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount(expression)

Vrátí velikost agregace včetně null a duplicitních hodnot.

**Argumenty**

Libovolný typ.

**Návratová hodnota**

A `Int64`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count (výraz)

Vrátí velikost agregace včetně null a duplicitních hodnot.

**Argumenty**

Libovolný typ.

**Návratová hodnota**

A `Int32`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>Max (výraz)

Vrátí maximální hodnotu hodnot, které nejsou null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Návratová hodnota**

Typ `expression` `null` nebo `null` , pokud jsou všechny vstupní hodnoty hodnotami.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min (výraz)

Vrátí minimum hodnot, které nejsou null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Návratová hodnota**

Typ `expression` `null` nebo `null` , pokud jsou všechny vstupní hodnoty hodnotami.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev (výraz)

Vrací směrodatnou odchylku hodnot, které nejsou null.

**Argumenty**

A, `Int64`, ,.`Decimal` `Double` `Int32`

**Návratová hodnota**

A `Double`. `Null`, pokud jsou `null` všechny vstupní hodnoty hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>StDevP (výraz)

Vrátí směrodatnou odchylku pro populace všech hodnot.

**Argumenty**

A, `Int64`, ,.`Decimal` `Double` `Int32`

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>Sum (výraz)

Vrátí součet hodnot, které nejsou null.

**Argumenty**

A, `Int64`, ,.`Decimal` `Double` `Int32`

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var (výraz)

Vrátí odchylku všech hodnot, které nejsou null.

**Argumenty**

A, `Int64`, ,.`Decimal` `Double` `Int32`

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP (výraz)

Vrátí odchylku pro populace všech hodnot, které nejsou null.

**Argumenty**

A, `Int64`, ,.`Decimal` `Double` `Int32`

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

Ekvivalentní funkce jsou k dispozici ve spravovaném zprostředkovateli klienta Microsoft SQL. Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Agregace založené na kolekcích

Agregace založené na kolekcích (funkce kolekce) fungují na kolekcích a vracejí hodnotu. Například pokud jsou objednávky kolekcí všech objednávek, můžete vypočítat nejbližší datum expedice následujícím výrazem:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Výrazy uvnitř agregace založené na kolekcích jsou vyhodnocovány v rámci aktuálního oboru rozlišení názvu okolí.

## <a name="group-based-aggregates"></a>Agregace založené na skupinách

Agregace založené na skupinách se počítají na základě skupiny definované klauzulí GROUP BY. Pro každou skupinu ve výsledku se samostatné agregace vypočítávají pomocí prvků v každé skupině jako vstup agregačního výpočtu. Pokud je ve výrazu SELECT použita klauzule GROUP by, lze v klauzuli projekce nebo ORDER-by vyskytovat pouze názvy výrazů seskupení, agregace nebo konstantní výrazy.

Následující příklad vypočítá průměrné množství objednaného pro každý produkt:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

Je možné mít agregaci založenou na skupině bez explicitní klauzule GROUP by ve výrazu SELECT. V tomto případě jsou všechny prvky považovány za jednu skupinu. Jedná se o ekvivalent zadání seskupení na základě konstanty. Vezměte například následující výraz:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

To je ekvivalentní následujícímu:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Výrazy uvnitř agregace založené na skupinách jsou vyhodnocovány v rámci oboru překladu názvů, který by byl viditelný pro výraz klauzule WHERE.

Stejně jako v jazyce Transact-SQL, agregace založené na skupinách mohou také určovat modifikátor ALL nebo DISTINCT. Je-li zadán modifikátor DISTINCT, jsou duplicity z agregované vstupní kolekce odstraněny před vypočítáním agregace. Pokud je zadán modifikátor ALL (nebo pokud není zadán modifikátor), není provedeno žádné duplicitní eliminace.

## <a name="see-also"></a>Viz také:

- [Kanonické funkce](canonical-functions.md)
