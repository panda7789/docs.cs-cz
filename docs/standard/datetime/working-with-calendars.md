---
title: Práce s kalendáři
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET Framework], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 67e0344dc3038096a5b2114790fbb0c343ba3e4f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="working-with-calendars"></a>Práce s kalendáři

Ačkoli hodnoty data a času představují konkrétní časový okamžik, je řetězcové vyjádření závislé na jazykové verzi a závisí jak na konvencích použitých k zobrazení hodnoty data a času podle konkrétní jazykové verze, tak na kalendáři používaném danou jazykovou verzí. V tomto tématu jsou zde popsány podporu kalendářích v rozhraní .NET a popisuje použití třídy kalendáře při práci s hodnotami data.

## <a name="calendars-in-net"></a>Kalendáře v rozhraní .NET

Všech kalendářů v rozhraní .NET jsou odvozeny od <xref:System.Globalization.Calendar?displayProperty=nameWithType> třídy, která poskytuje základní kalendář implementaci. Jeden z třídy, které dědí z <xref:System.Globalization.Calendar> třída je <xref:System.Globalization.EastAsianLunisolarCalendar> třídy, která je základní třída pro všechny lunasolární kalendáře. Rozhraní .NET zahrnuje následující implementací kalendáře:

* <xref:System.Globalization.ChineseLunisolarCalendar>, představuje Čínský lunasolární kalendáři.

* <xref:System.Globalization.GregorianCalendar>, která představuje gregoriánský kalendář. Tento kalendář se dále dělí do podtypů (například Arabské a Střední východ francouzština), které jsou definovány <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> výčtu. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Vlastnost určuje dílčí gregoriánském kalendáři.

* <xref:System.Globalization.HebrewCalendar>, která představuje hebrejského kalendáře.

* <xref:System.Globalization.HijriCalendar>, která představuje kalendáře hidžra.

* <xref:System.Globalization.JapaneseCalendar>, která představuje japonské kalendáři.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, která představuje japonské lunasolární kalendáři.

* <xref:System.Globalization.JulianCalendar>, která představuje juliánský kalendář.

* <xref:System.Globalization.KoreanCalendar>, která představuje Korejské kalendáři.

* <xref:System.Globalization.KoreanLunisolarCalendar>, která představuje Korejské lunasolární kalendáři.

* <xref:System.Globalization.PersianCalendar>, která představuje perského kalendáře.

* <xref:System.Globalization.TaiwanCalendar>, který představuje kalendář, Tchaj-wan.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, která představuje lunasolární kalendáře Tchaj-wan.

* <xref:System.Globalization.ThaiBuddhistCalendar>, která představuje Thajská budhistického kalendáře.

* <xref:System.Globalization.UmAlQuraCalendar>, která představuje ální Al Qura kalendáře.

Kalendář lze použít jedním ze dvou způsobů:

* Jako kalendář, který používá konkrétní jazyková verze. Každý <xref:System.Globalization.CultureInfo> objekt má aktuální kalendář, což je kalendář, který je aktuálně používá objekt. Řetězcové vyjádření hodnot data a času automaticky odrážejí aktuální jazykovou verzi a aktuální kalendář. Aktuálním kalendářem je obvykle výchozí kalendář dané jazykové verze. <xref:System.Globalization.CultureInfo> objekty mají také volitelné kalendáře, mezi které patří další kalendářích, které můžete použít tuto jazykovou verzi.

* Jako samostatný kalendář, který není závislý na konkrétní jazykové verzi. V takovém případě <xref:System.Globalization.Calendar> metody se používají k express kalendářních dat jako hodnoty, které odpovídají kalendáři.

Všimněte si, že šest kalendář třídy – <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, a <xref:System.Globalization.TaiwanLunisolarCalendar> – lze použít pouze jako samostatné kalendáře. Tyto kalendáře nepoužívá žádná jazyková verze jako výchozí kalendář nebo jako volitelný kalendář.

## <a name="calendars-and-cultures"></a>Kalendáře a jazykové verze

Každá jazyková verze má výchozí kalendář, který je definovaný <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Vlastnost vrací pole <xref:System.Globalization.Calendar> objekty, které určuje všech kalendářů podporuje konkrétní jazykové verze, včetně výchozí kalendář pro jazykovou verzi.

Následující příklad ukazuje <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastnosti. Vytvoří `CultureInfo` objektů pro thajštině (Thajsko) a kultur japonština (Japonsko) a zobrazí jejich výchozí a volitelné kalendáře. Všimněte si, že v obou případech výchozí kalendář pro jazykovou verzi jsou také obsaženy v <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekce.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendáře aktuálně používán konkrétní <xref:System.Globalization.CultureInfo> objektu je definována pro jazykovou verzi <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. Jazykové verze <xref:System.Globalization.DateTimeFormatInfo> objekt je vrácen rutinou <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Když je vytvořen jazykovou verzi, výchozí hodnota je stejná jako hodnota <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. Můžete však změnit aktuální kalendář pro jazykovou verzi na libovolný kalendář obsažené v poli vráceném <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastnost. Pokud se pokusíte nastavit aktuální kalendář do kalendáře, který není součástí <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> hodnotu vlastnosti <xref:System.ArgumentException> je vyvolána.

Následující příklad znázorňuje změnu kalendáře používaného jazykovou verzí Arabština (Saúdská Arábie). Nejprve vytvoří <xref:System.DateTime> hodnota a zobrazí pomocí - a to v tomto případě je angličtina (Spojené státy) - aktuální jazykovou verzi a aktuální jazykovou verzi kalendář, (která je v tomto případě gregoriánský kalendář). Poté změní aktuální jazykovou verzi na verzi Arabština (Saúdská Arábie) a zobrazí datum pomocí výchozího kalendáře Um-al-Qura. Potom zavolá `CalendarExists` metoda k určení, zda je kalendáře hidžra nepodporuje jazykovou verzi arabština (Saúdská Arábie). Vzhledem k tomu, že kalendář je podporován, změní aktuální kalendář na kalendář Hidžra a znovu zobrazí datum. V obou případech je datum zobrazeno pomocí aktuálního kalendáře aktuální jazykové verze.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Data a kalendáře

S výjimkou konstruktory, které obsahují parametr typu <xref:System.Globalization.Calendar> a povolit elementy datum (to znamená, měsíc, den a v roce), aby odrážela hodnoty v určené kalendáři, obě <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty jsou vždy založené na gregoriánském kalendáři. To znamená, například, že <xref:System.DateTime.Year%2A?displayProperty=nameWithType> vlastnost vrátí rok v gregoriánský kalendář a <xref:System.DateTime.Day%2A?displayProperty=nameWithType> vlastnost vrátí den v měsíci v gregoriánském kalendáři.

> [!IMPORTANT]
> Je důležité mít na paměti, že existuje rozdíl mezi hodnotou data a řetězcovým vyjádřením tohoto data. První zmíněná položka je založena na gregoriánském kalendáři, druhá zmíněná položka pak vychází z aktuálního kalendáře konkrétní jazykové verze.

Následující příklad ukazuje rozdíl mezi <xref:System.DateTime> vlastností a jejich odpovídajících <xref:System.Globalization.Calendar> metody. V tomto příkladu je aktuální jazykovou verzí Arabština (Egypt) a aktuální kalendář je Um-al-Qura. A <xref:System.DateTime> hodnota nastavena na patnáctého dne v měsíci sedmého 2011. Je jasné, že to interpretována jako gregoriánského, protože jsou tyto stejné hodnoty vrácené <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda, když používá pravidla neutrální jazykovou verzi. Řetězcové vyjádření data, které je naformátováno pomocí konvencí aktuální jazykové verze, je 14/08/32, což odpovídá datu v kalendáři Um-al-Qura. Další, členové `DateTime` a `Calendar` se používá k vrácení den, měsíc a rok <xref:System.DateTime> hodnotu. V každém případě vrácené hodnoty <xref:System.DateTime> členy podle hodnot v gregoriánském kalendáři, zatímco hodnoty vrácené <xref:System.Globalization.UmAlQuraCalendar> členové odrážejí hodnoty v kalendáři al-Qura Uum.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Vytvoření instance dat na základě kalendáře

Protože <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty jsou založeny na gregoriánský kalendář, musí volat přetížené konstruktor, který zahrnuje parametr typu <xref:System.Globalization.Calendar> k vytváření instancí hodnota kalendářního data, pokud chcete použít hodnoty den, měsíc nebo rok z různé kalendáře. Můžete také volání jednoho z přetížení konkrétní kalendáře <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metoda pro vytvoření instance <xref:System.DateTime> objektu na základě hodnot konkrétní kalendáře.

Následující příklad vytvoří jednu <xref:System.DateTime> hodnotu předáním <xref:System.Globalization.HebrewCalendar> do objektu <xref:System.DateTime> konstruktoru a vytvoří druhý <xref:System.DateTime> hodnotu voláním <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metoda. Protože tyto dvě hodnoty, které jsou vytvořené pomocí stejné hodnoty z hebrejštinu kalendář, volání <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> metoda ukazuje, že dva <xref:System.DateTime> jsou hodnoty stejné.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Reprezentující data v kalendáři aktuální

Metoda formátování data a času používá při konverzi dat do řetězců vždy aktuální kalendář. To znamená, že řetězcové vyjádření roku, měsíce a dne v měsíci odpovídá aktuálnímu kalendáři a nemusí nutně zohledňovat gregoriánský kalendář.

Následující příklad znázorňuje vliv aktuálního kalendáře na řetězcové vyjádření data. Nastaví aktuální jazykovou verzi Čínština (tradiční, Tchaj-wan) a vytvoří instanci hodnoty data. Se potom zobrazí aktuální kalendář a datum, aktuální kalendář, který se změní <xref:System.Globalization.TaiwanCalendar>a zobrazí aktuální kalendář a data znovu. Při prvním zobrazení je datum vyjádřeno jako datum v gregoriánském kalendáři. Při druhém zobrazení je datum vyjádřeno jako datum v tchajwanském kalendáři.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Reprezentující data v kalendáři není aktuální.

Představují data pomocí kalendáře, který není aktuální kalendář konkrétní jazykové verzi, musí volat metody této <xref:System.Globalization.Calendar> objektu. Například <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody převést na hodnoty, které odráží konkrétní kalendářní rok, měsíc a den.

> [!WARNING]
> Vzhledem k tomu, že některé kalendáře neobsahují volitelné kalendáře žádné jazykové verze, vyžaduje zobrazení dat v těchto kalendářích vždy volání metod kalendáře. To platí všech kalendářů, které jsou odvozeny od <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, a <xref:System.Globalization.PersianCalendar> třídy.

Následující příklad používá <xref:System.Globalization.JulianCalendar> objekt, který chcete vytvořit instanci datum, 9. ledna 1905 v juliánský kalendář. Pokud je toto datum zobrazeno pomocí výchozího (gregoriánského) kalendáře, má podobu 22. ledna 1905. Volání do jednotlivých <xref:System.Globalization.JulianCalendar> metody povolit datum a nelze v juliánský kalendář.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendáře a rozsahů

Nejdřívější datum nepodporuje kalendář je indikován se kalendář <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> vlastnost. Pro <xref:System.Globalization.GregorianCalendar> třídy, že je 1. ledna 0001 C.E. datum Většina ostatních kalendářů v rozhraní .NET podporují později. Při pokusu o práci s datum a čas hodnotu, která předchází kalendář je nejdříve podporované vrátí datum <xref:System.ArgumentOutOfRangeException> výjimka.

Existuje však jedna důležitá výjimka. Hodnota výchozí (Neinicializovaný) <xref:System.DateTime> objektu a <xref:System.DateTimeOffset> objekt rovná <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> hodnotu. Pokud se pokusíte formátu toto datum v kalendáři, která nepodporuje 1. ledna 0001 C.E. a nezadáte specifikátor formátu, metoda formátování používá specifikátor formátu (seřaditelné datum a čas vzor) "s" místo "" (Obecné datum a čas vzor) specifikátor formátu. V důsledku toho formátování operaci nevyvolá výjimku <xref:System.ArgumentOutOfRangeException> výjimka. Namísto toho vrátí nepodporované datum. To je znázorněno v následujícím příkladu, který se zobrazí hodnota <xref:System.DateTime.MinValue?displayProperty=nameWithType> Pokud aktuální jazykové verze je nastavena japonština (Japonsko) s japonské kalendáře a arabština (Egypt) s ální Al Qura kalendáře. Také nastaví aktuální jazykové verze Angličtina (Spojené státy) a počet volání <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metoda s každým z těchto <xref:System.Globalization.CultureInfo> objekty. V obou případech je datum zobrazeno pomocí seřaditelného vzorce data/času.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Práce s období

Data v kalendářích jsou obvykle rozdělena do období. Ale <xref:System.Globalization.Calendar> třídy v rozhraní .NET nepodporují každých letopočtu definované kalendář a většina <xref:System.Globalization.Calendar> třídy podporují pouze jeden letopočtu. Pouze <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar> třídy podporují více období.

### <a name="eras-and-era-names"></a>Období a letopočtu názvy

V rozhraní .NET, celá čísla, které představují období podporuje konkrétní kalendáře implementace jsou uložené v obráceném pořadí v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> pole. Aktuální letopočtu je indexem nula a pro <xref:System.Globalization.Calendar> třídy, které podporují více období, každý následných index odráží předchozí letopočtu. Statické <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> vlastnost definuje index aktuální letopočtu v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> pole; je konstanta, jehož hodnota je vždy nula. Jednotlivé <xref:System.Globalization.Calendar> třídy také zahrnovat statické pole, která vrátí hodnotu aktuální letopočtu. Jsou uvedeny v následující tabulce.

| Třída kalendáře                                        | Pole aktuálního období                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

Název, který odpovídá konkrétní letopočtu číslo můžete načíst pomocí předání letopočtu číslo, které má <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metoda. V následujícím příkladu volání těchto metod k načtení informací o podpoře letopočtu v <xref:System.Globalization.GregorianCalendar> třídy.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Kromě toho řetězec „o“ vlastního formátu data a času obsahuje název období kalendáře v řetězcovém vyjádření data a času. Další informace najdete v tématu [vlastní datum a čas řetězce formátu](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Data se letopočtu vytváření instancí

Pro dva <xref:System.Globalization.Calendar> třídy, které podporují více období, datum, které se skládá z konkrétní rok, měsíc a den v měsíci hodnota může být nejednoznačný, například všechny čtyři období z <xref:System.Globalization.JapaneseCalendar> mít číslované od 1 do 15 let. Pokud není období stanoveno, pak metody data a času a kalendáře obvykle předpokládají, že hodnoty patří do aktuálního období. K explicitnímu zadání posouzení při vytváření instance datum pro <xref:System.Globalization.Calendar> třídu, která podporuje více období, můžete volat <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metoda. Tato metoda umožňuje explicitní zadání období a hodnoty roku, měsíce, dne, hodiny, minuty, sekundy a milisekundy v kalendáři.

Následující příklad používá <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metoda pro vytvoření instance stejné datum prvního měsíce od druhého roku, v každém letopočtu nepodporuje první den <xref:System.Globalization.JapaneseCalendar> třídy. Poté zobrazí datum v japonském a gregoriánském kalendáři. Také voláním <xref:System.DateTime> konstruktor ukázat, že metody, které vytvoření hodnot data bez zadání letopočtu vytvořit kalendářních dat v aktuálním letopočtu.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Reprezentující data v kalendáři s období

Pokud <xref:System.Globalization.Calendar> objekt podporuje období a je aktuální kalendář <xref:System.Globalization.CultureInfo> objektu, letopočtu je součástí řetězcovou reprezentaci hodnoty datum a čas pro úplnou datum a čas, dlouhého data a krátkého data vzory. Následující příklad zobrazuje tyto vzorce dat, kdy je nastavena aktuální jazyková verze Japonština (Japonsko) a aktuálním kalendářem je japonský kalendář.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar> Třída je jediná třída kalendáře v rozhraní .NET, které obě data podporuje více než jeden letopočtu a který může být aktuální kalendář <xref:System.Globalization.CultureInfo> objekt – konkrétně z <xref:System.Globalization.CultureInfo> objekt, který reprezentuje japonština (Japonsko) jazykovou verzi.

Specifikátor vlastního formátu „o“ zahrnuje období ve výsledném řetězci všech kalendářů. Následující příklad používá vlastní řetězec formátu „MM-dd-rrrr g“ pro vyjádření období ve výsledném řetězci, pokud je aktuální kalendář nastaven na gregoriánský kalendář.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

V případech, kde je vyjádřen řetězec představující datum v kalendáři, který není aktuální kalendář <xref:System.Globalization.Calendar> zahrnuje třídy <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> metoda, která můžete použít společně s <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody jednoznačně označuje datum, jakož i letopočtu, do které patří. Následující příklad používá <xref:System.Globalization.JapaneseLunisolarCalendar> třída zajistit obrázek. Ale Všimněte si, že včetně smysluplný název nebo zkratka místo celé pro letopočtu ve výsledném řetězci vyžaduje, aby instanci můžete vytvořit <xref:System.Globalization.DateTimeFormatInfo> objektu a proveďte <xref:System.Globalization.JapaneseCalendar> jeho aktuální kalendáře. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Kalendář nemůže být aktuální kalendář všechny jazykové verze, ale v takovém případě dvou kalendářů sdílet stejné období.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>Viz také

[Postupy: zobrazování dat v jiném než gregoriánském kalendáři](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
[ukázka: Kalendář nástroj rozsah týden](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
