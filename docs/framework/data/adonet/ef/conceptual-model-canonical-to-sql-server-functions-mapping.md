---
title: Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: f997fbf39f3dee07cc0d58a39fca779f55236606
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251682"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru
Toto téma popisuje, jak koncepční model kanonické funkce se mapují na odpovídající funkce SQL Server.  
  
## <a name="date-and-time-functions"></a>Funkce pro datum a čas  
 Následující tabulka popisuje mapování funkcí data a času:  
  
|Kanonické funkce|Funkce SQL Server|  
|-------------------------|--------------------------|  
|[AddDays (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime (rok, měsíc, den, hodina, minuta, sekunda)](./language-reference/date-and-time-canonical-functions.md)|V případě SQL Server 2000 a SQL Server 2005 `datetime` je na serveru vytvořena formátovaná hodnota. U SQL Server 2008 a novějších verzí `datetime2` se na serveru vytvoří hodnota.|  
|[CreateDateTimeOffset (rok, měsíc, den, hodina, minuta, druhý, TZoffset)](./language-reference/date-and-time-canonical-functions.md)|Na serveru se vytvoří formátovanáhodnota.`datetimeoffset`<br /><br /> Nepodporováno v SQL Server 2000 nebo SQL Server 2005.|  
|[CreateTime (Hour, Minute, Second)](./language-reference/date-and-time-canonical-functions.md)|Na serveru se vytvoří formátovanáhodnota.`time`<br /><br /> Nepodporováno v SQL Server 2000 nebo SQL Server 2005.|  
|[CurrentDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTime()`v SQLServer 2008.<br /><br /> `GetDate()`v SQLServer 2000 a SQLServer 2005.|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()`v SQL Server 2008.<br /><br /> Nepodporováno v SQL Server 2000 nebo SQL Server 2005.|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()`v SQLServer 2008. `GetUtcDate()`v SQL Server 2000 a SQL Server 2005.|  
|[DayOfYear (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes (DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Milisekunda (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minuta (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Zkrátit (výraz)](./language-reference/date-and-time-canonical-functions.md)|V případě SQL Server 2000 a SQL Server 2005 je na `datetime` serveru vytvořena zkrácená formátovaná hodnota. U SQL Server 2008 a novějších verzí se na `datetime2` serveru `datetimeoffset` vytvoří Zkrácená hodnota nebo.|  
|[Year (výraz)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Agregační funkce  
 Následující tabulka popisuje mapování agregačních funkcí:  
  
|Kanonické funkce|Funkce SQL Server|  
|-------------------------|--------------------------|  
|[Prům (výraz)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count (výraz)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min (výraz)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max (výraz)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev (výraz)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP (výraz)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum (výraz)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var (výraz)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP (výraz)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Matematické funkce  
 Následující tabulka popisuje mapování matematických funkcí:  
  
|Kanonické funkce|Funkce SQL Server|  
|-------------------------|--------------------------|  
|[ABS (hodnota)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Strop (hodnota)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor (hodnota)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Napájení (hodnota)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round (hodnota)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Zkrátit](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Funkce řetězce  
 V následující tabulce jsou popsány mapování funkcí pro řetězce:  
  
|Kanonické funkce|Funkce SQL Server|  
|-------------------------|--------------------------|  
|[Obsahuje (řetězec, cíl)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat (řetězec1, řetězec2)](./language-reference/string-canonical-functions.md)|řetězec1 + řetězec2|  
|[EndsWith (řetězec, cíl)](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Poznámka:** `CHARINDEX` Funkce vrátí `target` , zda `string` je uložena ve sloupci řetězce s pevnou délkou a `false` je konstanta. V tomto případě je prohledán celý řetězec, včetně všech koncových mezer. Možným řešením je zkrátit data v řetězci s pevnou délkou před předáním řetězce do `EndsWith` funkce, jako v následujícím příkladu:`EndsWith(TRIM(string), target)`|  
|[IndexOf (cíl, řetězec2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left (řetězec1, Length)](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Délka (String)](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim (String)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right (řetězec1, Length)](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim (řetězec)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace (řetězec1, řetězec2, String3)](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Reverse (String)](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim (řetězec)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith (řetězec, cíl)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring (řetězec, začátek, délka)](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower (řetězec)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper (String)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Bitové funkce  
 Následující tabulka popisuje mapování bitových funkcí:  
  
|Kanonické funkce|Funkce SQL Server|  
|-------------------------|--------------------------|  
|[BitWiseAnd (hodnota1, hodnota2)](./language-reference/bitwise-canonical-functions.md)|Hodnota1 & hodnota2|  
|[BitWiseNot (hodnota)](./language-reference/bitwise-canonical-functions.md)|~ hodnota|  
|[Bitový operátor (hodnota1, hodnota2)](./language-reference/bitwise-canonical-functions.md)|Hodnota1 &#124; hodnota2|  
|[BitWiseXor (hodnota1, hodnota2)](./language-reference/bitwise-canonical-functions.md)|Hodnota1 ^ hodnota2|
