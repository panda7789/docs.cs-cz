---
title: Metoda CLR pro mapování kanonických funkcí
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 6f14ad8d9e8f919fe820447cc991b102319b38d5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251229"
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metoda CLR pro mapování kanonických funkcí

Entity Framework poskytuje sadu kanonických funkcí, které implementují funkce, které jsou společné pro celou řadu databázových systémů, jako je například manipulace s řetězci a matematické funkce. To umožňuje vývojářům cílit širokou škálu databázových systémů. Při volání z technologie pro dotazování, jako je například LINQ to Entities, jsou tyto kanonické funkce přeloženy do správné odpovídající funkce úložiště pro používaného poskytovatele. To umožňuje, aby vyvolání funkcí bylo vyjádřeno ve společném formuláři napříč zdroji dat a poskytovalo konzistentní možnosti dotazování napříč zdroji dat. Operátory bitových operátorů AND, OR, NOT a XOR jsou také mapovány na kanonické funkce, pokud je operand číselným typem. U logických operandů operátory bitových operátorů AND, OR, NOT a XOR vypočítají operace logických operátorů AND, OR, NOT a XOR jejich operandů. Další informace najdete v tématu [kanonické funkce](canonical-functions.md).

Pro scénáře LINQ dotazy na Entity Framework zahrnují mapování určitých metod CLR na metody na podkladovém zdroji dat prostřednictvím kanonických funkcí. Jakákoli volání metody v LINQ to Entities dotaz, která nejsou explicitně mapována na kanonickou funkci, způsobí, že dojde <xref:System.NotSupportedException> k vyvolání běhové výjimky.

## <a name="systemstring-method-static-mapping"></a>Mapování metody System. String (static)

|System. String – metoda (static)|Kanonická funkce|
|-------------------------------------|------------------------|
|System. String Concat (řetězec `str0`, řetězec `str1`)|Concat (`str0`, `str1`)|
|System. String Concat (řetězec `str0`, řetězec `str1`, řetězec `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|
|System. String Concat (řetězec `str0`, řetězec `str1`, řetězec `str2`, řetězec `str03`)|Concat (Concat`str0`(, `str1`), `str2`); `str3`)|
|Logická hodnota se rovná ( `a`řetězec, `b`řetězec)|= – operátor|
|Boolean IsNullOrEmpty (řetězec `value`)|(IsNull (`value`)) nebo Length (`value`) = 0|
|Boolean op_Equality (řetězec `a`, řetězec `b`)|= – operátor|
|Boolean op_Inequality (řetězec `a` , řetězec `b`)|!= – operátor|
|Microsoft. VisualBasic. Strings. trim (řetězec `str`)|Trim (`str`)|
|Microsoft. VisualBasic. Strings. LTrim (řetězec `str`)|LTrim (`str`)|
|Microsoft. VisualBasic. Strings. RTrim (řetězec `str`)|RTrim (`str`)|
|Microsoft. VisualBasic. Strings. len (řetězec `expression`)|Délka (`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Left (`str`, `Length`)|
|Microsoft.VisualBasic.Strings.Mid(String `str`, Int32 `Start`, Int32 `Length`)|Podřetězec (`str`, `Start`, `Length`)|
|Microsoft. VisualBasic. Strings. Right (řetězec `str`, Int32 `Length`)|Right (`str`, `Length`)|
|Microsoft. VisualBasic. Strings. UCase (řetězec `Value`)|ToUpper (`Value`)|
|Microsoft. VisualBasic. Strings. LCase (hodnota řetězce)|ToLower (`Value`)|

## <a name="systemstring-method-instance-mapping"></a>System. String – mapování metody (instance)

|System. String – metoda (instance)|Kanonická funkce|Poznámky|
|---------------------------------------|------------------------|-----------|
|Logická hodnota obsahuje ( `value`String)|`this`LIKE%`value`%|Pokud `value` není konstanta, pak se tato mapa mapuje na IndexOf`this`( `value`,) > 0|
|Logická hodnota EndsWith ( `value`řetězec)|`this`LIKE `'` "% `value`|Pokud `value` není konstanta, pak je tato mapa pravá (`this`, Length (`value`)) = `value`.|
|Logická hodnota StartsWith ( `value`řetězec)|`this`PODOBNÝM`value`ZPŮSOBEM:%|Pokud `value` není konstanta, pak se tato mapa mapuje na IndexOf`this`( `value`,) = 1.|
|Časový|Délka (`this`)||
|Int32 IndexOf (String `value`)|IndexOf (`this`, `value`)-1||
|System. String Insert (Int32 `startIndex`; String `value`)|Concat (Concat (substring (`this`, 1, `startIndex`), `value`), podřetězec (`this`, `startIndex`+ 1, Length (`this`)- `startIndex`))||
|System. String Remove (Int32 `startIndex`)|Podřetězec (`this`, 1, `startIndex`)||
|System. String Remove (Int32 `startIndex`, Int32 `count`)|Concat (podřetězec (`this`, 1, `startIndex`), dílčí řetězec (`this`, `startIndex` `this` `count`  +  + 1, délka ()-(`startIndex` + `count`)))|Příkaz remove`startIndex`( `count`,) je podporován pouze `count` v případě, že je celé číslo větší nebo rovno 0.|
|System. String Replace ( `oldValue`String, `newValue`String)|Replace`this`( `oldValue`, `newValue`,)||
|System. String – podřetězec ( `startIndex`Int32)|Dílčí řetězec (`this`, `startIndex` + 1, délka (`this`)- `startIndex`)||
|Řetězec System. String (Int32 `startIndex`, Int32) `length`|Podřetězec (`this`, `startIndex` + 1, `length`)||
|System.String ToLower()|ToLower (`this`)||
|ToUpper () System. String ()|ToUpper (`this`)||
|System. String Trim ()|Trim (`this`)||
|System. String TrimEnd (Char [] `trimChars`)|RTrim (`this`)||
|System. String TrimStart (Char []`trimChars`)|LTrim (`this`)||
|Logická hodnota se rovná ( `value`String)|= – operátor||

## <a name="systemdatetime-method-static-mapping"></a>System. DateTime – metoda (static) – mapování

|System. DateTime – metoda (static)|Kanonická funkce|Poznámky|
|---------------------------------------|------------------------|-----------|
|Logická hodnota Equals ( `t1`DateTime, `t2`DateTime)|= – operátor||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Boolean op_Equality (DateTime `d1`, DateTime `d2`)|= – operátor||
|Boolean op_GreaterThan (DateTime `t1`, DateTime `t2`)|operátor >||
|Boolean op_GreaterThanOrEqual (DateTime `t1`, DateTime `t2`)|> = – operátor||
|Boolean op_Inequality (DateTime `t1`, DateTime `t2`)|!= – operátor||
|Boolean op_LessThan (DateTime `t1`, DateTime `t2`)|operátor <||
|Boolean op_LessThanOrEqual (DateTime `t1`, DateTime `t2`)|< = – operátor||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval` jako DateInterval,\_<br /><br /> ByVal `DateValue` jako DateTime,\_<br /><br /> Volitelné ByVal `FirstDayOfWeekValue` jako první_den_v_týdnu = vbSunday,\_<br /><br /> Volitelné ByVal `FirstWeekOfYearValue` jako první_týden_v_roce = vbFirstJan1\_<br /><br /> ) Jako celé číslo||Další informace najdete v části Funkce DatePart.|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year ()||
|Microsoft. VisualBasic. DateAndTime. month (DateTime `TimeValue`)|Month ()||
|Microsoft. VisualBasic. DateAndTime. Day (DateTime `TimeValue`)|Den ()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minuta ()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Sekunda ()||

## <a name="systemdatetime-method-instance-mapping"></a>System. DateTime Method (instance) – mapování

|System. DateTime – metoda (instance)|Kanonická funkce|
|-----------------------------------------|------------------------|
|Logická hodnota Equals ( `value`DateTime)|= – operátor|
|Den|Den (`this`)|
|Hodina|Hour (`this`)|
|Komponentu|Milisekunda`this`()|
|Minuta|Minuta`this`()|
|Měsíčně|Month (`this`)|
|Sekunda|Sekunda`this`()|
|Rok|Year (`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>System. DateTimeOffset – mapování metody (instance)

Mapování zobrazené pro `get` metody na uvedených vlastnostech.

|System. DateTimeOffset – metoda (instance)|Kanonická funkce|Poznámky|
|-----------------------------------------------|------------------------|-----------|
|Den|Den (`this`)|Nepodporováno v SQL Server 2005.|
|Hodina|Hour (`this`)|Nepodporováno v SQL Server 2005.|
|Komponentu|Milisekunda`this`()|Nepodporováno v SQL Server 2005.|
|Minuta|Minuta`this`()|Nepodporováno v SQL Server 2005.|
|Měsíčně|Month (`this`)|Nepodporováno v SQL Server 2005.|
|Sekunda|Sekunda`this`()|Nepodporováno v SQL Server 2005.|
|Rok|Year (`this`)|Nepodporováno v SQL Server 2005.|

> [!NOTE]
> Metoda vrátí `true` , zda jsou porovnávané <xref:System.DateTimeOffset> objekty stejné; <xref:System.DateTimeOffset.Equals%2A> `false` v opačném případě. Metoda vrátí 0, 1 nebo-1 v závislosti na tom, zda je rozdílový <xref:System.DateTimeOffset> objekt roven, větší než nebo menší než, v uvedeném pořadí. <xref:System.DateTimeOffset.CompareTo%2A>

## <a name="systemdatetimeoffset-method-static-mapping"></a>System. DateTimeOffset – mapování metody (static)

Mapování zobrazené pro `get` metody na uvedených vlastnostech.

|System. DateTimeOffset – metoda (static)|Kanonická funkce|Poznámky|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Nepodporováno v SQL Server 2005.|

## <a name="systemtimespan-method-instance-mapping"></a>Mapování metody System. TimeSpan (instance)

Mapování zobrazené pro `get` metody na uvedených vlastnostech.

|System. TimeSpan – metoda (instance)|Kanonická funkce|Poznámky|
|-----------------------------------------|------------------------|-----------|
|Hodin|Hour (`this`)|Nepodporováno v SQL Server 2005.|
|Milisekundy|Milisekunda`this`()|Nepodporováno v SQL Server 2005.|
|Minut|Minuta`this`()|Nepodporováno v SQL Server 2005.|
|Second|Sekunda`this`()|Nepodporováno v SQL Server 2005.|

> [!NOTE]
> Metoda vrátí `true` , zda jsou porovnávané <xref:System.TimeSpan> objekty stejné; <xref:System.TimeSpan.Equals%2A> `false` v opačném případě. Metoda vrátí 0, 1 nebo-1 v závislosti na tom, zda je rozdílový <xref:System.TimeSpan> objekt roven, větší než nebo menší než, v uvedeném pořadí. <xref:System.TimeSpan.CompareTo%2A>

### <a name="datepart-function"></a>Funkce DatePart

Funkce je namapována na jednu z několika různých normativních funkcí v závislosti na `Interval`hodnotě. `DatePart` V následující tabulce je uvedeno mapování kanonické funkce pro podporované hodnoty `Interval`:

|Hodnota intervalu|Kanonická funkce|
|--------------------|------------------------|
|DateInterval.Year|Year ()|
|DateInterval.Month|Month ()|
|DateInterval.Day|Den ()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|Minuta ()|
|DateInterval.Second|Sekunda ()|

## <a name="mathematical-function-mapping"></a>Mapování matematické funkce

|Metoda CLR|Kanonická funkce|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|Strop (`d`)|
|System. Decimal. Floor (desítková `d`)|Floor (`d`)|
|System. Decimal. Round (Decimal `d`)|Round (`d`) –|
|System. Math. strop (desetinné `d`číslo)|Strop (`d`)|
|System. Math. Floor (desítková `d`)|Floor (`d`)|
|System. Math. Round (desetinné `d`číslo)|Round (`d`) –|
|System. Math. strop (Double `a`)|Strop (`a`)|
|System. Math. Floor (Double `a`)|Floor (`a`)|
|System. Math. Round (Double `a`)|Round (`a`) –|
|System. Math. Round (dvojitá hodnota, číslice Int16)|Round (hodnota; číslice)|
|System. Math. Round (dvojitá hodnota, číslice Int32)|Round (hodnota; číslice)|
|System. Math. Round (desítková hodnota, číslice Int16)|Round (hodnota; číslice)|
|System. Math. Round (desítková hodnota, Int32, číslice)|Round (hodnota; číslice)|
|System. Math. ABS (hodnota Int16)|ABS (hodnota)|
|System. Math. ABS (hodnota Int32)|ABS (hodnota)|
|System. Math. ABS (hodnota Int64)|ABS (hodnota)|
|System. Math. ABS (hodnota Byte)|ABS (hodnota)|
|System. Math. ABS (jediná hodnota)|ABS (hodnota)|
|System. Math. ABS (hodnota typu Double)|ABS (hodnota)|
|System. Math. ABS (desítková hodnota)|ABS (hodnota)|
|System. Math. zkrátit (dvojitá hodnota, číslice Int16)|Zkrátit (hodnota, číslice)|
|System. Math. zkrátit (dvojitá hodnota, číslice Int32)|Zkrátit (hodnota, číslice)|
|System. Math. zkrátit (desítková hodnota, číslice Int16)|Zkrátit (hodnota, číslice)|
|System. Math. zkrátit (desítková hodnota, číslice Int32)|Zkrátit (hodnota, číslice)|
|System. Math. Power (hodnota Int32, exponent Int64)|Napájení (hodnota, exponent)|
|System. Math. Power (hodnota Int32, dvojitý exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (hodnota Int32, desítkový exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (hodnota Int64, exponent Int64)|Napájení (hodnota, exponent)|
|System. Math. Power (hodnota Int64, dvojité exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (hodnota Int64, desítkový exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (hodnota typu Double, exponent Int64)|Napájení (hodnota, exponent)|
|System. Math. Power (dvojitá hodnota, dvojitá exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (dvojitá hodnota, desítkový exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (desítková hodnota, Int64 exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (desítková hodnota, dvojitá exponent)|Napájení (hodnota, exponent)|
|System. Math. Power (desítková hodnota, desítkový exponent)|Napájení (hodnota, exponent)|

## <a name="bitwise-operator-mapping"></a>Mapování bitového operátoru

|Bitový operátor|Kanonická funkce pro nelogické operandy|Kanonická funkce pro logické operandy|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Bitový operátor AND|BitWiseAnd|OP1 a OP2|
|Bitový operátor OR|Bitový operátor|OP1 nebo OP2|
|Bitový operátor NOT|BitWiseNot|Ne (OP)|
|Bitový operátor XOR|BitWiseXor|((OP1 a NOT (OP2)) nebo (NOT (OP1) a OP2))|

## <a name="other-mapping"></a>Jiné mapování

|Metoda|Kanonická funkce|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>Viz také:

- [LINQ to Entities](linq-to-entities.md)
