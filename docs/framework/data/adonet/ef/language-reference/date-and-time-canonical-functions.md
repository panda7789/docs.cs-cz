---
title: Datum a čas kanonické funkce
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 46a4b595ccdfcb1a6576ee8cb1e080f0d4b48123
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579989"
---
# <a name="date-and-time-canonical-functions"></a>Datum a čas kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje kanonické funkce date a time.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny na datum a čas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce. `datetime` je <xref:System.DateTime> hodnotu.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Přidá zadaný `number` z nanosekundách k `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMicroseconds(expression,number)`|Přidá zadaný `number` z mikrosekundách k `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMilliseconds(expression,number)`|Přidá zadaný `number` časový interval v milisekundách `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddSeconds(expression,number)`|Přidá zadaný `number` sady sekund `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMinutes(expression,number)`|Přidá zadaný `number` minut `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddHours(expression,number)`|Přidá zadaný `number` hodin `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddDays(expression,number)`|Přidá zadaný `number` dnů `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` nebo `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMonths(expression,number)`|Přidá zadaný `number` měsíců `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` nebo `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddYears(expression,number)`|Přidá zadaný `number` let `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` nebo `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Vrátí nový `DateTime` hodnotu jako aktuální datum a čas serveru v časovém pásmu serveru.<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`: `Int16` a `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Vrátí nový `DateTimeOffset` hodnotu jako aktuální datum a čas serveru vzhledem k koordinovaný univerzální čas (UTC).<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|Vrátí nový `Time` hodnotu jako aktuální čas.<br /><br /> **Argumenty**<br /><br /> `hour` a `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|Vrátí `DateTime` hodnotu jako aktuální datum a čas serveru v časovém pásmu serveru.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Vrátí aktuální datum, čas a posunu `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Vrátí <xref:System.DateTime> hodnotu jako aktuální datum a čas v časovém pásmu UTS serveru.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime`.|  
|`Day(expression)`|Vrátí část pro den z `expression` jako `Int32` od 1 do 31.<br /><br /> **Argumenty**<br /><br /> A `DateTime` a `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|Vrátí část pro den z `expression` jako `Int32` od 1 do 366, kde se 366 vrátí poslední den do přestupného roku.<br /><br /> **Argumenty**<br /><br /> A `DateTime` nebo `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|Vrátí rozdíl v nanosekundách, mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, nebo `Time`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|Vrátí rozdíl v milisekundách mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, nebo `Time`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|Vrátí rozdíl v mikrosekundách, mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, nebo `Time`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|Vrátí rozdíl v sekundách mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, nebo `Time`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|Vrátí rozdíl v řádech minut, mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, nebo `Time`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffHours(startExpression,endExpression)`|Vrátí rozdíl v hodinách mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, nebo `Time`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffDays(startExpression,endExpression)`|Vrátí rozdíl ve dnech mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` nebo `DateTimeOffset`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|Vrátí rozdíl v měsících, mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` nebo `DateTimeOffset`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`DiffYears(startExpression,endExpression)`|Vrátí rozdíl v letech, mezi `startExpression` a `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` nebo `DateTimeOffset`. **Poznámka:** `startExpression` a `endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|Vrátí počet minut, který `datetimeoffset` posun od GMT. Obvykle se jedná mezi +780 a-780 (+ nebo - 13 hodin). **Poznámka:**  Tato funkce je podporována pouze v systému SQL Server 2008. <br /><br /> **Argumenty**<br /><br /> A `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`Hour(expression)`|Vrátí hodinu část `expression` jako `Int32` mezi 0 a 23.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` a `DateTimeOffset`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|Vrátí část milisekund `expression` jako `Int32` rozsahu od 0 do 999.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` a `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.|  
|`Minute(expression)`|Vrátí část pro minuty z `expression` jako `Int32` mezi 0 a 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` nebo `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|Vrátí část pro měsíc z `expression` jako `Int32` od 1 do 12.<br /><br /> **Argumenty**<br /><br /> A `DateTime` nebo `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|Vrátí počet sekund část `expression` jako `Int32` mezi 0 a 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` a `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|Vrátí `expression`, s hodnotami času zkrácen.<br /><br /> **Argumenty**<br /><br /> A `DateTime` nebo `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`Year(expression)`|Vrátí část roku `expression` jako `Int32` `YYYY`.<br /><br /> **Argumenty**<br /><br /> A `DateTime` a `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.  
  
 Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také:
- [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
