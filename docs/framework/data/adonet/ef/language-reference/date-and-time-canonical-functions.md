---
title: Kanonické funkce pro datum a čas
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 3dd6c0da3f9851df7bb9725d9d6c08fef5a0d3d3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251098"
---
# <a name="date-and-time-canonical-functions"></a>Kanonické funkce pro datum a čas
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsahuje kanonické funkce data a času.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny kanonické funkce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] data a času. `datetime`<xref:System.DateTime> je hodnota.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Přidá zadaný `number` počet nanosekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMicroseconds(expression,number)`|Přidá zadaný `number` počet mikrosekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMilliseconds(expression,number)`|Přidá zadaný `number` počet milisekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddSeconds(expression,number)`|Přidá zadaný `number` počet sekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMinutes(expression,number)`|Přidá zadaný `number` počet minut `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddHours(expression,number)`|Přidá zadaný `number` počet hodin `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, nebo `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddDays(expression,number)`|Přidá zadaný `number` počet dní `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` nebo `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddMonths(expression,number)`|Přidá zadaný `number` počet měsíců `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` nebo `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`AddYears(expression,number)`|Přidá zadaný `number` počet roků `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` nebo `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Vrátí novou `DateTime` hodnotu jako aktuální datum a čas serveru v časovém pásmu serveru.<br /><br /> **Argumenty**<br /><br /> `year`, `month` ,`day`, ,`minute`: a`Int16` . `hour` `Int32`<br /><br /> `second`: `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Vrátí novou `DateTimeOffset` hodnotu jako aktuální datum a čas serveru relativně k koordinovanému univerzálnímu času (UTC).<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|Vrátí novou `Time` hodnotu jako aktuální čas.<br /><br /> **Argumenty**<br /><br /> `hour`a `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Návratová hodnota**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|`DateTime` Vrátí hodnotu jako aktuální datum a čas serveru v časovém pásmu serveru.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Vrátí aktuální datum, čas a posun jako `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|<xref:System.DateTime> Vrací hodnotu jako aktuální datum a čas serveru v časovém pásmu UTS.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime`.|  
|`Day(expression)`|Vrátí část `expression` `Int32` dne v rozsahu od 1 do 31.<br /><br /> **Argumenty**<br /><br /> `DateTime` A .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|Vrátí část `expression` `Int32` dne v rozsahu od 1 do 366, kde 366 je vráceno pro poslední den přestupného roku.<br /><br /> **Argumenty**<br /><br /> A `DateTime` .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|Vrátí rozdíl v nanosekundách mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, nebo`DateTimeOffset`. `Time` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|Vrátí rozdíl v milisekundách mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, nebo`DateTimeOffset`. `Time` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|Vrátí rozdíl v mikrosekundách mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, nebo`DateTimeOffset`. `Time` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|Vrátí rozdíl v sekundách mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, nebo`DateTimeOffset`. `Time` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|Vrátí rozdíl v minutách mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, nebo`DateTimeOffset`. `Time` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffHours(startExpression,endExpression)`|Vrátí rozdíl v hodinách mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, nebo`DateTimeOffset`. `Time` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffDays(startExpression,endExpression)`|Vrátí rozdíl ve dnech mezi `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` nebo .`DateTimeOffset` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|Vrátí rozdíl v měsících `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` nebo .`DateTimeOffset` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`DiffYears(startExpression,endExpression)`|Vrátí rozdíl v letech `startExpression` a. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` nebo .`DateTimeOffset` **Poznámka:** `startExpression` a`endExpression` musí být stejného typu. <br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|Vrátí počet minut, po který `datetimeoffset` je posun od času GMT. To je obvykle mezi + 780 a-780 (+ nebo-13 hodin). **Poznámka:**  Tato funkce je podporována pouze v SQL Server 2008. <br /><br /> **Argumenty**<br /><br /> A `DateTimeOffset`.<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`Hour(expression)`|Vrátí část `expression` `Int32` hodiny v rozsahu od 0 do 23.<br /><br /> **Argumenty**<br /><br /> `DateTime, Time` A .`DateTimeOffset`<br /><br /> **Příklad**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|Vrátí část `expression` `Int32` milisekund v rozsahu od 0 do 999.<br /><br /> **Argumenty**<br /><br /> `DateTime, Time` A .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.|  
|`Minute(expression)`|Vrátí část `expression` `Int32` minuty v rozsahu od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|Vrátí část `expression` `Int32` měsíce v rozsahu od 1 do 12.<br /><br /> **Argumenty**<br /><br /> A `DateTime` .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|Vrátí část `expression` `Int32` sekund v rozsahu od 0 do 59.<br /><br /> **Argumenty**<br /><br /> `DateTime, Time` A .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|`expression`Vrátí, s časovými hodnotami, které jsou zkráceny.<br /><br /> **Argumenty**<br /><br /> A `DateTime` .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.|  
|`Year(expression)`|Vrátí část `expression` roku `Int32` jako.`YYYY`<br /><br /> **Argumenty**<br /><br /> `DateTime` A .`DateTimeOffset`<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Tyto funkce budou v `null` případě zadaného `null` vstupu vráceny.  
  
 Ekvivalentní funkce jsou k dispozici ve spravovaném zprostředkovateli klienta Microsoft SQL. Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také:

- [Kanonické funkce](canonical-functions.md)
