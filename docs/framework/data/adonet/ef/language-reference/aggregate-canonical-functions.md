---
title: Agregační kanonické funkce
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: f65557703070a43f586a668903d049a374ef70d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708971"
---
# <a name="aggregate-canonical-functions"></a>Agregační kanonické funkce

Agregace jsou výrazy, které snižují řadu vstupní hodnoty do například jednu hodnotu. Agregace se obvykle používají ve spojení s klauzulí GROUP BY vyberte výrazu a existují omezení ve kterém můžou použít.

## <a name="aggegate-entity-sql-canonical-functions"></a>Kanonické funkce Aggegate Entity SQL

Následují agregační kanonické funkce Entity SQL.

### <a name="avgexpression"></a>AVG(Expression)

Vrátí průměrnou hodnotu hodnot jiných než null.

**Argumenty**

`Int32`, `Int64`, `Double`, A `Decimal`.

**Návratová hodnota**

Typ `expression`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] 
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount(expression)

Vrátí velikost položky agregace, včetně hodnotu null a duplicitní hodnoty.

**Argumenty**

Libovolného typu.

**Návratová hodnota**

`Int64`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] 
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count(Expression) 

Vrátí velikost položky agregace, včetně hodnotu null a duplicitní hodnoty.

**Argumenty**

Libovolného typu.

**Návratová hodnota**

`Int32`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>Max(Expression)

Vrátí maximální hodnoty null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Návratová hodnota**

Typ `expression`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min(Expression)

Vrátí minimální hodnoty null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Návratová hodnota**

Typ `expression`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev(expression)

Vrátí směrodatnou odchylku nenulové hodnoty.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

A `Double`. `Null`, pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>StDevP(expression)

Vrací směrodatnou odchylku základního souboru hodnot.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>SUM(Expression)

Vrátí součet hodnoty null.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var(Expression)

Vrací odchylku všech hodnot jiných než null.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP(expression)

Vrací odchylku pro naplnění všechny nenulové hodnoty.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

A `Double`, nebo `null` Pokud jsou všechny vstupní hodnoty `null` hodnoty.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] 

Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Na základě kolekce agregace

Na základě kolekce agregace (kolekce funkcí) pracovat s kolekcí a vracet hodnotu. Například pokud objednávky je kolekce všechny objednávky, můžete vypočítat datum příjemce se následující výraz:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Výrazy v kolekci na základě agregace jsou vyhodnocovány v aktuálním oboru okolí překlad názvů.

## <a name="group-based-aggregates"></a>Agregace na základě skupin

Agregace na základě skupin se počítá v průběhu skupiny definované v klauzuli GROUP BY. Pro každou skupinu ve výsledku se počítá samostatné agregace pomocí elementů v každé skupině jako vstup do agregačního výpočtu. Při použití klauzule group by ve výrazu select může být k dispozici v projekci nebo order by – klauzule pouze seskupení názvy výrazů, agregace nebo konstantní výrazy.

Následující příklad vypočítá průměrné množství, řazení pro jednotlivé produkty:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Je možné mít agregace podle skupiny bez klauzule explicitní Group ve výrazu SELECT. V takovém případě všechny prvky jsou považovány za jednu skupinu. To je ekvivalentní zadání seskupení založené na konstantu. Vezměme si jako příklad následující výraz:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

To je ekvivalentní následujícímu zápisu:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Uvnitř agregace skupinové výrazy jsou vyhodnocovány v rámci oboru rozlišení názvů, které se staly viditelnými pro výraz klauzule WHERE.

Stejně jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], na základě skupin agregace můžete také určit všechny nebo odlišné modifikátor. Pokud není zadána odlišné modifikátor, duplicitní položky zanikne brány v agregační vstupní kolekce předtím, než je vypočítán agregace. Pokud je zadán modifikátorem všechny (nebo pokud není zadán žádný modifikátor), bez odstranění duplicit se provádí.  

## <a name="see-also"></a>Viz také:

- [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
