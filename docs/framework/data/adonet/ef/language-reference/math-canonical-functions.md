---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250311"
---
# <a name="math-canonical-functions"></a>Matematické kanonické funkce

Entity SQL obsahuje následující matematické kanonické funkce:
  
## <a name="absvalue"></a>ABS (hodnota)

Vrátí absolutní hodnotu `value`.

**Argumenty**

`Int16`A `Int32` ,,`Int64`, ,`Single`,a. `Double` `Byte` `Decimal`

**Návratová hodnota**

Typ `value`.

**Příklad**

`Abs(-2)`

## <a name="ceilingvalue"></a>Strop (hodnota)

Vrátí nejmenší celé číslo, které není menší než `value`.

**Argumenty**

A `Single`, `Double`a .`Decimal`

**Návratová hodnota**

Typ `value`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor (hodnota)

Vrátí největší celé číslo, které není větší než `value`.

**Argumenty**

A `Single`, `Double`a .`Decimal`

**Návratová hodnota**

Typ `value`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Napájení (hodnota, exponent)

Vrátí výsledek zadaný `value` na určenou `exponent`hodnotu.

**Argumenty**

|  |  |
|--|--|
|`value` | A `Int32, Int64, Double`, nebo `Decimal`. |
|`exponent` | A `Int64`, `Double`nebo .`Decimal` |

**Návratová hodnota**

Typ `value`.

**Příklad**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round (hodnota)

Vrátí celočíselnou část `value`zaokrouhlenou na nejbližší celé číslo.

**Argumenty**

A `Single`, `Double`a .`Decimal`

**Návratová hodnota**

Typ `value`.

**Příklad**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (hodnota; číslice)

Vrátí zaokrouhlit na nejbližší určený `digits`. `value`

**Argumenty**

|  |  |
|--|--|
|`value`|`Double`nebo `Decimal`.|
|`digits`|`Int16`nebo `Int32`.|

**Návratová hodnota**

Typ `value`.

**Příklad**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Zkrátit (hodnota, číslice)

Vrátí hodnotu `digits`, která je zkrácena na nejbližší určenou. `value`

**Argumenty**

|  |  |
|--|--|
|`value`|`Double`nebo `Decimal`.|
|`digits`|`Int16`nebo `Int32`.|

**Návratová hodnota**

Typ `value`.

**Příklad**

`Truncate(748.58,1)`  
  
 Tyto funkce budou v `null` případě zadaného `null` vstupu vráceny.  
  
 Ekvivalentní funkce jsou k dispozici ve spravovaném zprostředkovateli klienta Microsoft SQL. Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také:

- [Kanonické funkce](canonical-functions.md)
