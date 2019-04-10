---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228767"
---
# <a name="math-canonical-functions"></a>Matematické kanonické funkce

Entita SQL obsahuje následující matematické kanonické funkce:
  
## <a name="absvalue"></a>Abs(Value)

Vrátí absolutní hodnotu `value`.

**Arguments**

`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.

**Návratová hodnota**

Typ `value`.

**Příklad**

`Abs(-2)`

## <a name="ceilingvalue"></a>CEILING(Value)

Vrátí nejmenší celé číslo, které není menší než `value`.

**Arguments**

A `Single`, `Double`, a `Decimal`.

**Návratová hodnota**

Typ `value`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor(Value)

Vrátí největší celé číslo, které není větší než `value`.

**Arguments**

A `Single`, `Double`, a `Decimal`.

**Návratová hodnota**

Typ `value`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Napájení (hodnota, exponent)

Vrátí výsledek zadaného `value` do zadaného `exponent`.

**Arguments**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`, Nebo `Decimal`. |
|`exponent` | `Int64`, `Double`, Nebo `Decimal`. |

**Návratová hodnota**

Typ `value`.

**Příklad**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round(Value)

Vrátí celočíselnou část `value`, zaokrouhlený na nejbližší celé číslo.

**Arguments**

A `Single`, `Double`, a `Decimal`.

**Návratová hodnota**

Typ `value`.

**Příklad**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (hodnota číslic)

Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` or `Decimal`.|
|`digits`|`Int16` or `Int32`.|

**Návratová hodnota**

Typ `value`.

**Příklad**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Zkrátit (hodnota číslic)

Vrátí `value`, došlo ke zkrácení na nejbližší zadaný `digits`.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` or `Decimal`.|
|`digits`|`Int16` or `Int32`.|

**Návratová hodnota**

Typ `value`.

**Příklad**

`Truncate(748.58,1)`  
  
 Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.  
  
 Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také:

- [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
