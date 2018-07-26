---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: c61db6d977614b95ea507b38c3890f2da8228158
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199291"
---
# <a name="math-canonical-functions"></a>Matematické kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje matematické kanonické funkce.  
  
 V následující tabulce jsou uvedeny výpočty [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`Abs(value)`|Vrátí absolutní hodnotu `value`.<br /><br /> **Argumenty**<br /><br /> `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Abs(-2)`|  
|`Ceiling(value)`|Vrátí nejmenší celé číslo, které není menší než `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, a `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)] <br /><br /> [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(value)`|Vrátí největší celé číslo, které není větší než `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, a `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)] <br /><br /> [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(value, exponent)`|Vrátí výsledek zadaného `value` do zadaného `exponent`.<br /><br /> **Argumenty**<br /><br /> `value`: Celé `Int32, Int64, Double`, nebo `Decimal`.<br /><br /> `exponent`: Celé `Int64`, `Double`, nebo `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Power(748.58,2)`|  
|`Round(value)`|Vrátí celočíselnou část `value`, zaokrouhlený na nejbližší celé číslo.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, a `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Round(748.58)`|  
|`Round(value, digits)`|Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` nebo `Decimal`.<br /><br /> `digits`: `Int16` nebo `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Round(748.58,1)`|  
|`Truncate(value, digits)`|Vrátí `value`, došlo ke zkrácení na nejbližší zadaný `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` nebo `Decimal`.<br /><br /> `digits`: `Int16` nebo `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `value`.<br /><br /> **Příklad**<br /><br /> `Truncate(748.58,1)`|  
  
 Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.  
  
 Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
