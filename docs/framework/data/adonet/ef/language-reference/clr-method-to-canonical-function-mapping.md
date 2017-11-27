---
title: "Metoda CLR pro mapování kanonické funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5d1e6a1cc362663be3aa6c6084f658eba25dfe54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metoda CLR pro mapování kanonické funkce
Rozhraní Entity Framework poskytuje sadu kanonické funkce, které implementují funkce, které jsou společné napříč mnoha systémy databáze, jako je například zacházení s řetězci a matematické funkce. To umožňuje vývojářům cíle širokou škálu databázovými systémy. Při volání z dotazování technologii, jako je technologie LINQ to Entities, tyto kanonické funkce jsou převedeny na správné odpovídající funkce úložiště pro použitý zprostředkovatel. To umožňuje volání funkce vyjádřeno v běžné formuláře napříč datových zdrojů, zajištění konzistentní dotazu prostředí napříč zdroje dat. Bitové operace AND, OR, NOT a XOR operátory jsou taky namapovaný na funkce kanonický po operand číselného typu. Pro logickou operandy, bitové operace AND, OR a NOT, a operátory XOR výpočetní logické AND, OR, ne a operace XOR operandy. Další informace najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
 Pro scénáře LINQ zahrnovat dotazy na Entity Framework mapování určité metod modulu CLR do metod v podkladovém zdroji dat prostřednictvím kanonické funkce. Metoda volání v dotazu LINQ dotazu entity, které nejsou explicitně namapované na kanonické funkce bude mít za následek runtime <xref:System.NotSupportedException> se došlo k výjimce.  
  
## <a name="systemstring-method-static-mapping"></a>Mapování (statické) System.String – metoda  
  
|Metoda System.String (statické)|Kanonické funkce|  
|-------------------------------------|------------------------|  
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat (Concat (Concat (`str0`, `str1`), `str2`), `str3`)|  
|Logická hodnota rovná (řetězec `a`, řetězec `b`)|= – operátor|  
|Logická hodnota IsNullOrEmpty (řetězec `value`)|(IsNull (`value`)) nebo délka (`value`) = 0|  
|Logická hodnota op_Equality (řetězec `a`, řetězec `b`)|= – operátor|  
|Op_inequality – logická hodnota (řetězec `a` , řetězec `b`)|!= – operátor|  
|Microsoft.VisualBasic.Strings.Trim (řetězec `str`)|Trim (`str`)|  
|Microsoft.VisualBasic.Strings.LTrim (řetězec `str`)|LTrim (`str`)|  
|Microsoft.VisualBasic.Strings.RTrim (řetězec `str`)|RTrim (`str`)|  
|Microsoft.VisualBasic.Strings.Len (řetězec `expression`)|Délka (`expression`)|  
|Microsoft.VisualBasic.Strings.Left (řetězec `str`, Int32 `Length`)|Doleva (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.Mid (řetězec `str`, Int32 `Start`, Int32 `Length`)|Substring (`str`, `Start`, `Length`)|  
|Microsoft.VisualBasic.Strings.Right (řetězec `str`, Int32 `Length`)|Vpravo (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.UCase (řetězec `Value`)|ToUpper (`Value`)|  
|Microsoft.VisualBasic.Strings.LCase (řetězcovou hodnotu)|ToLower (`Value`)|  
  
## <a name="systemstring-method-instance-mapping"></a>Metoda System.String (Instance) mapování  
  
|Metoda System.String (instance)|Kanonické funkce|Poznámky|  
|---------------------------------------|------------------------|-----------|  
|Obsahuje logickou hodnotu (řetězec `value`)|`this`NAPŘÍKLAD ' %`value`%.|Pokud `value` není konstantní, to jsou mapovány na IndexOf (`this`, `value`) > 0|  
|Logická hodnota EndsWith (řetězec `value`)|`this`JAKO `'` % `value`.|Pokud `value` není konstantní, pak to mapuje vpravo (`this`, délka (`value`)) = `value`.|  
|Logická hodnota StartsWith (řetězec `value`)|`this`NAPŘÍKLAD '`value`%.|Pokud `value` není konstantní, to jsou mapovány na IndexOf (`this`, `value`) = 1.|  
|Délka|Délka (`this`)||  
|Int32 IndexOf (řetězec `value`)|IndexOf (`this`, `value`) – 1||  
|System.String Insert(Int32 `startIndex`, String `value`)|Concat (Concat (Substring (`this`, 1, `startIndex`), `value`), Substring (`this`, `startIndex`+ 1, délka (`this`)- `startIndex`))||  
|System.String Remove(Int32 `startIndex`)|Substring (`this`, 1, `startIndex`)||  
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (Substring (`this`, 1, `startIndex`), Substring (`this`, `startIndex`  +  `count` + 1, délka (`this`) – (`startIndex` + `count`)))|Odebrat (`startIndex`, `count`) je podporována pouze v případě `count` je celé číslo větší než nebo rovna 0.|  
ystém. Nahraďte řetězec (String `oldValue`, řetězec `newValue`)|Nahraďte (`this`, `oldValue`, `newValue`)||  
|System.String Substring(Int32 `startIndex`)|Substring (`this`, `startIndex` + 1, délka (`this`)- `startIndex`)||  
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring (`this`, `startIndex` + 1, `length`)||  
|System.String ToLower()|ToLower (`this`)||  
|System.String ToUpper()|ToUpper (`this`)||  
|System.String Trim()|Trim (`this`)||  
|System.String TrimEnd(Char[] `trimChars`)|RTrim (`this`)||  
|System.String TrimStart(Char[]`trimChars`)|LTrim (`this`)||  
|Logická hodnota rovná (řetězec `value`)|= – operátor||  
  
## <a name="systemdatetime-method-static-mapping"></a>Mapování (statické) System.DateTime – metoda  
  
|Metoda System.DateTime (statické)|Kanonické funkce|Poznámky|  
|---------------------------------------|------------------------|-----------|  
|Logická hodnota rovná (data a času `t1`, data a času `t2`)|= – operátor||  
|System.DateTime.Now|CurrentDateTime()||  
|System.DateTime.UtcNow|CurrentUtcDateTime()||  
|Logická hodnota op_Equality (data a času `d1`, data a času `d2`)|= – operátor||  
|Op_greaterthan – logická hodnota (data a času `t1`, data a času `t2`)|> – operátor||  
|Op_greaterthanorequal – logická hodnota (data a času `t1`, data a času `t2`)|>= – operátor||  
|Op_inequality – logická hodnota (data a času `t1`, data a času `t2`)|!= – operátor||  
|Op_lessthan – logická hodnota (data a času `t1`, data a času `t2`)|< – operátor||  
|Op_lessthanorequal – logická hodnota (data a času `t1`, data a času `t2`)|<= – operátor||  
|Microsoft.VisualBasic.DateAndTime.DatePart (_<br /><br /> ByVal `Interval` jako DateInterval,\_<br /><br /> ByVal `DateValue` jako DateTime,\_<br /><br /> Volitelné ByVal `FirstDayOfWeekValue` jako FirstDayOfWeek = VbSunday,\_<br /><br /> Volitelné ByVal `FirstWeekOfYearValue` jako První_týden_v_roce = VbFirstJan1\_<br /><br /> ) Jako celé číslo||Další informace v části Funkce DatePart.|  
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||  
|Microsoft.VisualBasic.DateAndTime.Year (data a času `TimeValue`)|Year()||  
|Microsoft.VisualBasic.DateAndTime.Month (data a času `TimeValue`)|Month()||  
icrosoft. VisualBasic.DateAndTime.Day (data a času `TimeValue`)|Day()||  
|Microsoft.VisualBasic.DateAndTime.Hour (data a času `TimeValue`)|Hour()||  
|Microsoft.VisualBasic.DateAndTime.Minute (data a času `TimeValue`)|MINUTE()||  
|Microsoft.VisualBasic.DateAndTime.Second (data a času `TimeValue`)|Second()||  
  
## <a name="systemdatetime-method-instance-mapping"></a>Metoda System.DateTime (Instance) mapování  
  
|Metoda System.DateTime (instance)|Kanonické funkce|  
|-----------------------------------------|------------------------|  
|Logická hodnota rovná (data a času `value`)|= – operátor|  
|Den|Den (`this`)|  
|Hodina|Hodina (`this`)|  
|Milisekund|Milisekund (`this`)|  
|Minuta|Minutu (`this`)|  
|Měsíc|Měsíc (`this`)|  
|Sekunda|Druhý (`this`)|  
|Rok|Rok (`this`)|  
  
## <a name="systemdatetimeoffset-method-instance-mapping"></a>Metoda System.DateTimeOffset (Instance) mapování  
 Pro mapování `get` metody na seznamu vlastností.  
  
|Metoda System.DateTimeOffset (instance)|Kanonické funkce|Poznámky|  
|-----------------------------------------------|------------------------|-----------|  
|Den|Den (`this`)|Není podporováno pro SQL Server 2005.|  
|Hodina|Hodina (`this`)|Není podporováno pro SQL Server 2005.|  
|Milisekund|Milisekund (`this`)|Není podporováno pro SQL Server 2005.|  
|Minuta|Minutu (`this`)|Není podporováno pro SQL Server 2005.|  
|Měsíc|Měsíc (`this`)|Není podporováno pro SQL Server 2005.|  
|Sekunda|Druhý (`this`)|Není podporováno pro SQL Server 2005.|  
|Rok|Rok (`this`)|Není podporováno pro SQL Server 2005.|  
  
> [!NOTE]
>  <xref:System.DateTimeOffset.Equals%2A> Metoda vrátí `true` Pokud porovná s <xref:System.DateTimeOffset> objekty jsou stejné; `false` jinak. <xref:System.DateTimeOffset.CompareTo%2A> Metoda vrátí hodnotu 0, 1 nebo -1, v závislosti na tom, jestli se porovná s <xref:System.DateTimeOffset> objektu je stejná, větší nebo menší než je v uvedeném pořadí.  
  
## <a name="systemdatetimeoffset-method-static-mapping"></a>Mapování (statické) System.DateTimeOffset – metoda  
 Pro mapování `get` metody na seznamu vlastností.  
  
|Metoda System.DateTimeOffset (statické)|Kanonické funkce|Poznámky|  
|---------------------------------------------|------------------------|-----------|  
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Není podporováno pro SQL Server 2005.|  
  
## <a name="systemtimespan-method-instance-mapping"></a>Metoda System.TimeSpan (Instance) mapování  
 Pro mapování `get` metody na seznamu vlastností.  
  
|Metoda System.TimeSpan (instance)|Kanonické funkce|Poznámky|  
|-----------------------------------------|------------------------|-----------|  
|Hodiny|Hodina (`this`)|Není podporováno pro SQL Server 2005.|  
|počet milisekund|Milisekund (`this`)|Není podporováno pro SQL Server 2005.|  
|minut|Minutu (`this`)|Není podporováno pro SQL Server 2005.|  
|Sekund|Druhý (`this`)|Není podporováno pro SQL Server 2005.|  
  
> [!NOTE]
>  <xref:System.TimeSpan.Equals%2A> Metoda vrátí `true` Pokud porovná s <xref:System.TimeSpan> objekty jsou stejné; `false` jinak. <xref:System.TimeSpan.CompareTo%2A> Metoda vrátí hodnotu 0, 1 nebo -1, v závislosti na tom, jestli se porovná s <xref:System.TimeSpan> objektu je stejná, větší nebo menší než je v uvedeném pořadí.  
  
### <a name="datepart-function"></a>Funkce DatePart  
 `DatePart` Funkce je namapovaný na jednu z několika různých kanonický funkcí, v závislosti na hodnotě `Interval`. V následující tabulce mapování kanonické funkce podporované hodnoty `Interval`:  
  
|Hodnota intervalu|Kanonické funkce|  
|--------------------|------------------------|  
|DateInterval.Year|Year()|  
|DateInterval.Month|Month()|  
|DateInterval.Day|Day()|  
|DateInterval.Hour|Hour()|  
|DateInterval.Minute|MINUTE()|  
|DateInterval.Second|Second()|  
  
## <a name="mathematical-function-mapping"></a>Mapování matematické funkce  
  
|CLR – metoda|Kanonické funkce|  
|----------------|------------------------|  
|System.Decimal.Ceiling (Decimal `d`)|CEILING (`d`)|  
|System.Decimal.Floor (Decimal `d`)|Floor (`d`)|  
|System.Decimal.Round (Decimal `d`)|Zaokrouhlí (`d`)|  
|System.Math.Ceiling (Decimal `d`)|CEILING (`d`)|  
|System.Math.Floor (Decimal `d`)|Floor (`d`)|  
|System.Math.Round (Decimal `d`)|Zaokrouhlí (`d`)|  
|System.Math.Ceiling (dvojité `a`)|CEILING (`a`)|  
|System.Math.Floor (dvojité `a`)|Floor (`a`)|  
|System.Math.Round (dvojité `a`)|Zaokrouhlí (`a`)|  
|System.Math.Round (dvojitá hodnota, Int16 číslic)|Zaokrouhlí (hodnota číslic)|  
|System.Math.Round (dvojitá hodnota, Int32 číslic)|Zaokrouhlí (hodnota číslic)|  
|System.Math.Round (desetinnou hodnotu, Int16 číslic)|Zaokrouhlí (hodnota číslic)|  
|System.Math.Round (desetinnou hodnotu, Int32, číslice)|Zaokrouhlí (hodnota číslic)|  
|System.Math.Abs (hodnotu Int16)|Abs(Value)|  
|System.Math.Abs (Int32 hodnota)|Abs(Value)|  
|System.Math.Abs (hodnotu Int64)|Abs(Value)|  
|System.Math.Abs (hodnota bajtu)|Abs(Value)|  
|System.Math.Abs (jedna hodnota)|Abs(Value)|  
|System.Math.Abs (hodnota typu Double)|Abs(Value)|  
|System.Math.Abs (desítková hodnota)|Abs(Value)|  
|System.Math.Truncate (dvojitá hodnota, Int16 číslic)|Zkrácení (hodnota číslic)|  
|System.Math.Truncate (dvojitá hodnota, Int32 číslic)|Zkrácení (hodnota číslic)|  
|System.Math.Truncate (desetinnou hodnotu, Int16 číslic)|Zkrácení (hodnota číslic)|  
|System.Math.Truncate (desetinnou hodnotu, Int32 číslic)|Zkrácení (hodnota číslic)|  
|System.Math.Power (hodnota Int32, Int64 exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (hodnota Int32, Double exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (hodnota Int32, Decimal exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (hodnotu Int64, Int64 exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (hodnotu Int64, Double exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (hodnotu Int64, Decimal exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (dvojitá hodnota, Int64 exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (dvakrát hodnotu Double exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (dvojitá hodnota, Decimal exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (desetinnou hodnotu, Int64 exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (desítková hodnota, Double exponent)|Napájení (hodnota, exponentu)|  
|System.Math.Power (desetinnou hodnotu, Decimal exponent)|Napájení (hodnota, exponentu)|  
  
## <a name="bitwise-operator-mapping"></a>Bitový operátor mapování  
  
|Bitový operátor|Kanonické funkce pro operandy logická hodnota|Kanonické funkce pro operandy Boolean|  
|----------------------|--------------------------------------------------|---------------------------------------------|  
|Bitový operátor AND|BitWiseAnd|op1 a op2|  
|Bitový operátor OR|BitWiseOr|op1 nebo op2|  
|Bitový operátor NOT|BitWiseNot|NOT(OP)|  
|Bitový operátor XOR|BitWiseXor|((op1 a NOT(op2)) OR (NOT(op1) a op2))|  
  
## <a name="other-mapping"></a>Jiné mapování  
  
|Metoda|Kanonické funkce|  
|------------|------------------------|  
|Guid.NewGuid()|NewGuid()|  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
