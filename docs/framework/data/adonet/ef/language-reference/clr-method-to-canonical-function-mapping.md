---
title: Metoda CLR pro mapování kanonických funkcí
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 16d447e82959f5ade7210b36dcf9d06bed9c9b00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605714"
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metoda CLR pro mapování kanonických funkcí

Entity Framework obsahuje sadu kanonické funkce, které implementují funkce, která je společná řada databázových systémů, jako jsou matematické funkce a zacházení s řetězci. To umožňuje vývojářům cílí na širokou škálu databázovými systémy. Při volání z dotazování technologie, jako je například technologie LINQ to Entities, tyto kanonické funkce jsou přeloženy na správné odpovídající funkce úložiště pro použitý zprostředkovatel. To umožňuje volání funkce být vyjádřeny v běžné formě napříč zdroji dat, poskytuje konzistentní dotazu prostředí v datových zdrojích. Bitové operace AND, OR, NOT a operátorů XOR jsou také namapované na kanonické funkce při operand je číselného typu. Pro logickou operandy, bitový AND, OR, NOT, a operátory XOR výpočetní logický operátor AND, OR, NOT a operace XOR svých operandů. Další informace najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).

U scénářů s LINQ dotazy na Entity Framework zahrnují určitá CLR metody mapování metod v podkladovém zdroji dat prostřednictvím kanonické funkce. Metoda volání v LINQ dotazu entity, které nejsou explicitně namapované na kanonické funkce způsobí modul runtime <xref:System.NotSupportedException> vyvolání výjimky.

## <a name="systemstring-method-static-mapping"></a>Metody System.String mapování (statické)

|Metody System.String (statické)|Kanonické funkce|
|-------------------------------------|------------------------|
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat (Concat (Concat (`str0`, `str1`), `str2`), `str3`)|
|Logická rovná se (řetězec `a`, řetězec `b`)|= – operátor|
|Logická IsNullOrEmpty (řetězec `value`)|(IsNull (`value`)) nebo má nesprávnou délku (`value`) = 0|
|Logická op_Equality (řetězec `a`, řetězec `b`)|= – operátor|
|Op_inequality – logická (řetězec `a` , řetězec `b`)|!= – operátor|
|Microsoft.VisualBasic.Strings.Trim(String `str`)|Trim (`str`)|
|Microsoft.VisualBasic.Strings.LTrim (řetězec `str`)|Ltrim(`str`)|
|Microsoft.VisualBasic.Strings.RTrim(String `str`)|RTrim (`str`)|
|Microsoft.VisualBasic.Strings.Len(String `expression`)|Délka (`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Vlevo (`str`, `Length`)|
|Microsoft.VisualBasic.Strings.Mid(String `str`, Int32 `Start`, Int32 `Length`)|Dílčí řetězec (`str`, `Start`, `Length`)|
|Microsoft.VisualBasic.Strings.Right(String `str`, Int32 `Length`)|Doprava (`str`, `Length`)|
|Microsoft.VisualBasic.Strings.UCase(String `Value`)|ToUpper (`Value`)|
|Microsoft.VisualBasic.Strings.LCase (řetězec)|ToLower (`Value`)|

## <a name="systemstring-method-instance-mapping"></a>Mapování metody System.String (Instance)

|Metody System.String (instance)|Kanonické funkce|Poznámky|
|---------------------------------------|------------------------|-----------|
|Obsahuje logická hodnota (řetězec `value`)|`this` NAPŘÍKLAD "%`value`%"|Pokud `value` není konstantní, a to se mapuje na IndexOf (`this`, `value`) > 0|
|Logická EndsWith (řetězec `value`)|`this` STEJNĚ JAKO `'` % `value`.|Pokud `value` není konstantní, a to se mapuje na pravém (`this`, délka (`value`)) = `value`.|
|Logická StartsWith (řetězec `value`)|`this` NAPŘÍKLAD "`value`%"|Pokud `value` není konstantní, a to se mapuje na IndexOf (`this`, `value`) = 1.|
|Délka|Délka (`this`)||
|Datový typ Int32 IndexOf (řetězec `value`)|IndexOf (`this`, `value`) + 1||
|System.String Insert(Int32 `startIndex`, String `value`)|Concat (Concat (podřetězec (`this`, 1, `startIndex`), `value`), dílčí řetězec (`this`, `startIndex`+ 1, délka (`this`)- `startIndex`))||
|System.String Remove(Int32 `startIndex`)|Dílčí řetězec (`this`, 1, `startIndex`)||
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (podřetězec (`this`, 1, `startIndex`), dílčí řetězec (`this`, `startIndex`  +  `count` + 1, délka (`this`) – (`startIndex` + `count`)))|Odebrat (`startIndex`, `count`) se podporuje jenom v případě `count` je celé číslo větší než nebo rovna 0.|
|System.String Replace(String `oldValue`, String `newValue`)|Nahraďte (`this`, `oldValue`, `newValue`)||
|System.String Substring(Int32 `startIndex`)|Dílčí řetězec (`this`, `startIndex` + 1, délka (`this`)- `startIndex`)||
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Dílčí řetězec (`this`, `startIndex` + 1, `length`)||
|System.String ToLower()|ToLower (`this`)||
|System.String ToUpper()|ToUpper (`this`)||
|System.String Trim()|Trim (`this`)||
|System.String TrimEnd(Char[] `trimChars`)|RTrim (`this`)||
|System.String TrimStart(Char[]`trimChars`)|LTrim (`this`)||
|Logická rovná se (řetězec `value`)|= – operátor||

## <a name="systemdatetime-method-static-mapping"></a>Metody System.DateTime mapování (statické)

|Metody System.DateTime (statické)|Kanonické funkce|Poznámky|
|---------------------------------------|------------------------|-----------|
|Logická rovná se (datum a čas `t1`, data a času `t2`)|= – operátor||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Logická op_Equality (datum a čas `d1`, data a času `d2`)|= – operátor||
|Logická op_GreaterThan (datum a čas `t1`, data a času `t2`)|> – operátor||
|Logická op_GreaterThanOrEqual (datum a čas `t1`, data a času `t2`)|> = – operátor||
|Op_inequality – logická (datum a čas `t1`, data a času `t2`)|!= – operátor||
|Logická op_LessThan (datum a čas `t1`, data a času `t2`)|< – operátor||
|Logická op_LessThanOrEqual (datum a čas `t1`, data a času `t2`)|< = – operátor||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval` jako DateInterval, \_<br /><br /> ByVal `DateValue` jako datový typ DateTime, \_<br /><br /> Optional ByVal `FirstDayOfWeekValue` As FirstDayOfWeek = VbSunday, \_<br /><br /> Optional ByVal `FirstWeekOfYearValue` As FirstWeekOfYear = VbFirstJan1 \_<br /><br /> ) Jako celé číslo||Další informace v části Funkce DatePart.|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year()||
|Microsoft.VisualBasic.DateAndTime.Month(DateTime `TimeValue`)|Month()||
|Microsoft.VisualBasic.DateAndTime.Day(DateTime `TimeValue`)|Day()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Second()||

## <a name="systemdatetime-method-instance-mapping"></a>Mapování metody System.DateTime (Instance)

|Metody System.DateTime (instance)|Kanonické funkce|
|-----------------------------------------|------------------------|
|Logická rovná se (datum a čas `value`)|= – operátor|
|Den|Den (`this`)|
|Hodina|Hodina (`this`)|
|Milisekundy|Milisekundy (`this`)|
|Minuta|Minuty (`this`)|
|Měsíc|Měsíc (`this`)|
|Sekunda|Druhý (`this`)|
|Rok|Rok (`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>Metody System.DateTimeOffset (Instance) mapování

Pro mapování `get` metod v uvedených vlastností.

|Metody System.DateTimeOffset (instance)|Kanonické funkce|Poznámky|
|-----------------------------------------------|------------------------|-----------|
|Den|Den (`this`)|Není podporováno pro SQL Server 2005.|
|Hodina|Hodina (`this`)|Není podporováno pro SQL Server 2005.|
|Milisekundy|Milisekundy (`this`)|Není podporováno pro SQL Server 2005.|
|Minuta|Minuty (`this`)|Není podporováno pro SQL Server 2005.|
|Měsíc|Měsíc (`this`)|Není podporováno pro SQL Server 2005.|
|Sekunda|Druhý (`this`)|Není podporováno pro SQL Server 2005.|
|Rok|Rok (`this`)|Není podporováno pro SQL Server 2005.|

> [!NOTE]
> <xref:System.DateTimeOffset.Equals%2A> Vrátí metoda `true` Pokud porovná s <xref:System.DateTimeOffset> jsou objekty shodné; `false` jinak. <xref:System.DateTimeOffset.CompareTo%2A> Metoda vrátí hodnotu 0, 1 nebo -1, v závislosti na tom, jestli se porovná s <xref:System.DateTimeOffset> objektu je rovno, větší než nebo menší než, v uvedeném pořadí.

## <a name="systemdatetimeoffset-method-static-mapping"></a>Metody System.DateTimeOffset mapování (statické)

Pro mapování `get` metod v uvedených vlastností.

|Metody System.DateTimeOffset (statické)|Kanonické funkce|Poznámky|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Není podporováno pro SQL Server 2005.|

## <a name="systemtimespan-method-instance-mapping"></a>Metody System.TimeSpan (Instance) mapování

Pro mapování `get` metod v uvedených vlastností.

|Metody System.TimeSpan (instance)|Kanonické funkce|Poznámky|
|-----------------------------------------|------------------------|-----------|
|hodiny|Hodina (`this`)|Není podporováno pro SQL Server 2005.|
|Milisekundy|Milisekundy (`this`)|Není podporováno pro SQL Server 2005.|
|Minut|Minuty (`this`)|Není podporováno pro SQL Server 2005.|
|sekundy|Druhý (`this`)|Není podporováno pro SQL Server 2005.|

> [!NOTE]
> <xref:System.TimeSpan.Equals%2A> Vrátí metoda `true` Pokud porovná s <xref:System.TimeSpan> jsou objekty shodné; `false` jinak. <xref:System.TimeSpan.CompareTo%2A> Metoda vrátí hodnotu 0, 1 nebo -1, v závislosti na tom, jestli se porovná s <xref:System.TimeSpan> objektu je rovno, větší než nebo menší než, v uvedeném pořadí.

### <a name="datepart-function"></a>Funkce DatePart

`DatePart` Funkce je namapován na jeden z několika různých kanonické funkce, v závislosti na hodnotě z `Interval`. Následující tabulka obsahuje mapování kanonických funkcí pro podporované hodnoty `Interval`:

|Hodnota intervalu|Kanonické funkce|
|--------------------|------------------------|
|DateInterval.Year|Year()|
|DateInterval.Month|Month()|
|DateInterval.Day|Day()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|Minute()|
|DateInterval.Second|Second()|

## <a name="mathematical-function-mapping"></a>Mapování matematické funkce

|CLR – metoda|Kanonické funkce|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|CEILING (`d`)|
|System.Decimal.Floor (Desítková `d`)|Dolní mez (`d`)|
|System.Decimal.Round(Decimal `d`)|Round (`d`)|
|System.Math.Ceiling (Desítková `d`)|CEILING (`d`)|
|System.Math.Floor (Desítková `d`)|Dolní mez (`d`)|
|System.Math.Round (Desítková `d`)|Round (`d`)|
|System.Math.Ceiling (Double `a`)|CEILING (`a`)|
|System.Math.Floor (Double `a`)|Dolní mez (`a`)|
|System.Math.Round (Double `a`)|Round (`a`)|
|System.Math.Round (Double hodnotu, Int16 číslic)|Round (hodnota číslic)|
|System.Math.Round (Double hodnotu, Int32 číslic)|Round (hodnota číslic)|
|System.Math.Round (desítková hodnota, Int16 číslic)|Round (hodnota číslic)|
|System.Math.Round (hodnotu Decimal, Int32, číslic)|Round (hodnota číslic)|
|System.Math.Abs (hodnotu Int16)|Abs(Value)|
|System.Math.Abs (hodnota Int32)|Abs(Value)|
|System.Math.Abs (hodnota Int64)|Abs(Value)|
|System.Math.Abs (bajtová hodnota)|Abs(Value)|
|System.Math.Abs (jedinou hodnotu)|Abs(Value)|
|System.Math.Abs (Double hodnota)|Abs(Value)|
|System.Math.Abs (desítková hodnota)|Abs(Value)|
|System.Math.Truncate (Double hodnotu, Int16 číslic)|Zkrátit (hodnota číslic)|
|System.Math.Truncate (Double hodnotu, Int32 číslic)|Zkrátit (hodnota číslic)|
|System.Math.Truncate (desítková hodnota, Int16 číslic)|Zkrátit (hodnota číslic)|
|System.Math.Truncate (desítková hodnota, Int32 číslic)|Zkrátit (hodnota číslic)|
|System.Math.Power (hodnota Int32, Int64 exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (Int32 hodnota, Double exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (hodnota Int32, Decimal exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (hodnota Int64, Int64 exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (hodnota Int64, Double exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (hodnota Int64, Decimal exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (Double hodnota, Int64 exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (dvojitá hodnota, Double exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (Double hodnota, exponent desetinné)|Napájení (hodnota, exponent)|
|System.Math.Power (desítková hodnota, Int64 exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (desítková hodnota, Double exponent)|Napájení (hodnota, exponent)|
|System.Math.Power (desítková hodnota, exponent desetinné)|Napájení (hodnota, exponent)|

## <a name="bitwise-operator-mapping"></a>Bitový operátor mapování

|Bitový operátor|Kanonické funkce pro operandy – datový typ Boolean|Kanonické funkce pro logickou operandy|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Bitový operátor AND|BitWiseAnd|op1 op2 a|
|Bitový operátor OR|BitWiseOr|op1 OR op2|
|Bitový operátor NOT|BitWiseNot|NOT(op)|
|Bitový operátor XOR|BitWiseXor|((op1 a NOT(op2)) OR (NOT(op1) a op2))|

## <a name="other-mapping"></a>Jiné mapování

|Metoda|Kanonické funkce|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>Viz také:

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
