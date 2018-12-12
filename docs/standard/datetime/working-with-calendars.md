---
title: Práce s kalendáři
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6f759523acab1a248b92c69b95227b878696bbf
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286582"
---
# <a name="working-with-calendars"></a>Práce s kalendáři

Ačkoli hodnoty data a času představují konkrétní časový okamžik, je řetězcové vyjádření závislé na jazykové verzi a závisí jak na konvencích použitých k zobrazení hodnoty data a času podle konkrétní jazykové verze, tak na kalendáři používaném danou jazykovou verzí. Toto téma se zabývá podporou pro kalendáře v rozhraní .NET a popisuje způsob používání tříd kalendáře při práci s hodnotami data.

## <a name="calendars-in-net"></a>Kalendáře v rozhraní .NET

Všechny kalendáře v rozhraní .NET jsou odvozeny z <xref:System.Globalization.Calendar?displayProperty=nameWithType> třídu, která zajišťuje implementaci základního kalendáře. Jeden z třídy, které dědí z <xref:System.Globalization.Calendar> třída je <xref:System.Globalization.EastAsianLunisolarCalendar> třídu, která je základní třídou pro všechny lunasolární kalendáře. .NET zahrnuje následující implementace kalendáře:

* <xref:System.Globalization.ChineseLunisolarCalendar>, která představuje Čínský lunasolární kalendář.

* <xref:System.Globalization.GregorianCalendar>, která představuje gregoriánský kalendář. Tento kalendář je dále rozdělen do podtypů (například arabština a francouzština – Střední východ), které jsou definovány <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> výčtu. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Vlastnost určuje podtyp gregoriánského kalendáře.

* <xref:System.Globalization.HebrewCalendar>, která představuje hebrejský kalendář.

* <xref:System.Globalization.HijriCalendar>, která představuje kalendář hidžra.

* <xref:System.Globalization.JapaneseCalendar>, která představuje japonský kalendář.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, která představuje Japonský lunasolární kalendář.

* <xref:System.Globalization.JulianCalendar>, která představuje juliánský kalendář.

* <xref:System.Globalization.KoreanCalendar>, která představuje korejský kalendář.

* <xref:System.Globalization.KoreanLunisolarCalendar>, která představuje Korejský lunasolární kalendář.

* <xref:System.Globalization.PersianCalendar>, která představuje perský kalendář.

* <xref:System.Globalization.TaiwanCalendar>, která představuje Tchajwanský kalendář.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, která představuje Tchajwanský lunasolární kalendář.

* <xref:System.Globalization.ThaiBuddhistCalendar>, která představuje thajský buddhistický kalendář.

* <xref:System.Globalization.UmAlQuraCalendar>, která představuje Kalendář Um-Al-Qura.

Kalendář lze použít jedním ze dvou způsobů:

* Jako kalendář, který používá konkrétní jazyková verze. Každý <xref:System.Globalization.CultureInfo> objekt mají aktuální kalendář, což je kalendář, který objekt právě používá. Řetězcové vyjádření hodnot data a času automaticky odrážejí aktuální jazykovou verzi a aktuální kalendář. Aktuálním kalendářem je obvykle výchozí kalendář dané jazykové verze. <xref:System.Globalization.CultureInfo> objekty mají také volitelné kalendáře, mezi které patří další kalendáře, které můžete použít jazykovou verzi.

* Jako samostatný kalendář, který není závislý na konkrétní jazykové verzi. V takovém případě <xref:System.Globalization.Calendar> metody se používají k vyjádření dat jako hodnot, které odpovídají kalendáři.

Všimněte si, že šest tříd kalendářů – <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, a <xref:System.Globalization.TaiwanLunisolarCalendar> – lze použít pouze jako samostatné kalendáře. Tyto kalendáře nepoužívá žádná jazyková verze jako výchozí kalendář nebo jako volitelný kalendář.

## <a name="calendars-and-cultures"></a>Kalendáře a jazykové verze

Jednotlivé jazykové verze mají výchozí kalendář, který je definovaný <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Vlastnost vrací pole <xref:System.Globalization.Calendar> , které určují všechny kalendáře podporované konkrétní jazykovou verzí, včetně výchozího kalendáře této jazykové verze.

Následující příklad ukazuje, <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastnosti. Vytvoří `CultureInfo` objekty pro Thajština (Thajsko) a kultury japonština (Japonsko) a zobrazuje výchozí a volitelné kalendáře. Všimněte si, že v obou případech se výchozí kalendář pro jazykovou verzi je také součástí <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekce.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendář aktuálně používán konkrétní <xref:System.Globalization.CultureInfo> objekt je definovaný jazykové <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. Jazykové <xref:System.Globalization.DateTimeFormatInfo> objekt je vrácen rutinou <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Když se vytvoří jazykovou verzi, výchozí hodnota je stejná jako hodnota <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. Můžete však změnit aktuální kalendář pro jazykovou verzi na libovolný kalendář, který součástí pole vráceného <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastnost. Pokud se pokusíte aktuální kalendář nastavit na kalendář, který není součástí <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> hodnotu vlastnosti <xref:System.ArgumentException> je vyvolána výjimka.

Následující příklad znázorňuje změnu kalendáře používaného jazykovou verzí Arabština (Saúdská Arábie). Nejdříve vytvoří <xref:System.DateTime> a zobrazí ji pomocí aktuální jazykové verze, – a který je v tomto případě Angličtina (Spojené státy) – a kalendář aktuální jazykové verze, (která je v tomto případě gregoriánský kalendář). Poté změní aktuální jazykovou verzi na verzi Arabština (Saúdská Arábie) a zobrazí datum pomocí výchozího kalendáře Um-al-Qura. Poté zavolá `CalendarExists` metodou ke zjištění, zda je kalendář hidžra podporován jazykovou verzí Arabština (Saúdská Arábie). Vzhledem k tomu, že kalendář je podporován, změní aktuální kalendář na kalendář Hidžra a znovu zobrazí datum. V obou případech je datum zobrazeno pomocí aktuálního kalendáře aktuální jazykové verze.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Data a kalendáře

S výjimkou konstruktorů, které obsahují parametr typu <xref:System.Globalization.Calendar> a umožňují prvku data (to znamená, měsíce, dne a roku) znázorňovat hodnoty v určeném kalendáři, obě <xref:System.DateTime> a <xref:System.DateTimeOffset> jsou hodnoty vždycky založena na gregoriánském kalendáři. To znamená, například, že <xref:System.DateTime.Year%2A?displayProperty=nameWithType> vlastnost vrátí v gregoriánském kalendáři, rok a <xref:System.DateTime.Day%2A?displayProperty=nameWithType> vlastnost vrátí v gregoriánském kalendáři den v měsíci.

> [!IMPORTANT]
> Je důležité mít na paměti, že existuje rozdíl mezi hodnotou data a řetězcovým vyjádřením tohoto data. První zmíněná položka je založena na gregoriánském kalendáři, druhá zmíněná položka pak vychází z aktuálního kalendáře konkrétní jazykové verze.

Následující příklad znázorňuje rozdíl mezi <xref:System.DateTime> vlastností a jejich odpovídající <xref:System.Globalization.Calendar> metody. V tomto příkladu je aktuální jazykovou verzí Arabština (Egypt) a aktuální kalendář je Um-al-Qura. A <xref:System.DateTime> hodnota nastavena na patnáctý den sedmého měsíce roku 2011. Je jasné, že to je interpretován jako gregoriánský kalendář, protože jsou tyto stejné hodnoty vrácené <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> při použití konvencí neutrální jazykové verze. Řetězcové vyjádření data, které je naformátováno pomocí konvencí aktuální jazykové verze, je 14/08/32, což odpovídá datu v kalendáři Um-al-Qura. Další členy `DateTime` a `Calendar` se používá k vrácení dne, měsíce a roku <xref:System.DateTime> hodnotu. V obou případech hodnoty vrácené funkcí <xref:System.DateTime> odrážejí hodnoty v gregoriánském kalendáři, zatímco hodnoty vrácené <xref:System.Globalization.UmAlQuraCalendar> odrážejí hodnoty v kalendáři kalendáři um-al-Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Vytvoření instance dat podle kalendáře

Protože <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty jsou založeny na gregoriánském kalendáři, je potřeba zavolat přetížený konstruktor obsahující parametr typu <xref:System.Globalization.Calendar> vytvořit instanci hodnoty data, pokud chcete použít hodnoty dne, měsíce nebo roku z jiného kalendáře. Můžete také zavoláním jednoho z přetížení kalendáři specifických <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metoda pro vytvoření instance <xref:System.DateTime> objektu na základě hodnot konkrétního kalendáře.

V následujícím příkladu je vytvořena instance <xref:System.DateTime> hodnotu předáním <xref:System.Globalization.HebrewCalendar> do objektu <xref:System.DateTime> konstruktor a druhá <xref:System.DateTime> pomocí volání <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metoda. Protože tyto dvě hodnoty jsou vytvořeny pomocí stejných hodnot z hebrejského kalendáře, volání <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> metody ukazuje dva <xref:System.DateTime> jsou hodnoty stejné.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Zobrazování dat v aktuálním kalendáři

Metoda formátování data a času používá při konverzi dat do řetězců vždy aktuální kalendář. To znamená, že řetězcové vyjádření roku, měsíce a dne v měsíci odpovídá aktuálnímu kalendáři a nemusí nutně zohledňovat gregoriánský kalendář.

Následující příklad znázorňuje vliv aktuálního kalendáře na řetězcové vyjádření data. Nastaví aktuální jazykovou verzi Čínština (tradiční, Tchaj-wan) a vytvoří instanci hodnoty data. Poté zobrazí aktuální kalendář a datum, změní aktuální kalendář, který bude <xref:System.Globalization.TaiwanCalendar>a znovu zobrazí aktuální kalendář a datum. Při prvním zobrazení je datum vyjádřeno jako datum v gregoriánském kalendáři. Při druhém zobrazení je datum vyjádřeno jako datum v tchajwanském kalendáři.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Zobrazování dat v neaktuálním kalendáři

Představující datum pomocí neaktuálního kalendáře konkrétní jazykové verze není, musíte zavolat metody příslušného <xref:System.Globalization.Calendar> objektu. Například <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> převádí rok, měsíc a den na hodnoty, které odpovídají konkrétnímu kalendáři.

> [!WARNING]
> Vzhledem k tomu, že některé kalendáře neobsahují volitelné kalendáře žádné jazykové verze, vyžaduje zobrazení dat v těchto kalendářích vždy volání metod kalendáře. To platí pro všechny kalendáře, které jsou odvozeny z <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, a <xref:System.Globalization.PersianCalendar> třídy.

Následující příklad používá <xref:System.Globalization.JulianCalendar> objekt instance data, 9. ledna 1905 v gregoriánském kalendáři. Pokud je toto datum zobrazeno pomocí výchozího (gregoriánského) kalendáře, má podobu 22. ledna 1905. Volání jednotlivých <xref:System.Globalization.JulianCalendar> metody umožňují datum v gregoriánském kalendáři.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendáře a rozsah dat

Nejbližší datum podporované konkrétním kalendářem je označeno tohoto kalendáře <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> vlastnost. Pro <xref:System.Globalization.GregorianCalendar> třídy, je to datum 1. ledna 0001 n. l. Většina ostatních kalendářů v rozhraní .NET podporuje pozdější datum. Při pokusu o práci s hodnotou data a času, který předchází kalendáře nejstaršímu podporovanému datu <xref:System.ArgumentOutOfRangeException> výjimky.

Existuje však jedna důležitá výjimka. Výchozí (neinicializovaná) hodnota <xref:System.DateTime> objektu a <xref:System.DateTimeOffset> objekt rovná <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> hodnotu. Pokud se pokusíte naformátovat toto datum v kalendáři, která nepodporuje 1. ledna 0001 n. l. a nezadáte specifikátor formátu, použije metoda formátování namísto specifikátoru formátu "G" (vzor obecného formátu data/času) používá specifikátor formátu "s" (vzor seřaditelného formátu data/času). V důsledku toho operace formátování nevyvolá <xref:System.ArgumentOutOfRangeException> výjimky. Namísto toho vrátí nepodporované datum. To je znázorněno v následujícím příkladu, který zobrazuje hodnotu <xref:System.DateTime.MinValue?displayProperty=nameWithType> při aktuální jazyková verze nastavena na japonština (Japonsko) v japonském kalendáři a na Arabština (Egypt) v kalendáři Um-Al-Qura. Také nastaví aktuální jazykovou verzi Angličtina (Spojené státy) a volání <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metoda s každým z těchto <xref:System.Globalization.CultureInfo> objekty. V obou případech je datum zobrazeno pomocí seřaditelného vzorce data/času.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Práce s obdobími

Data v kalendářích jsou obvykle rozdělena do období. Ale <xref:System.Globalization.Calendar> třídy v rozhraní .NET nepodporují každé období definované kalendářem a většina <xref:System.Globalization.Calendar> třídy podporují pouze jediné období. Pouze <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar> třídy podporují větší počet období.

> [!IMPORTANT]
>  A nové éry v <xref:System.Globlalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar> začíná 1. května 2019. Tato změna ovlivní všechny aplikace, které používají tyto kalendáře. Zobrazit [zpracování do nové éry v japonské kalendáře v rozhraní .NET](https://blogs.msdn.microsoft.com/dotnet/2018/11/14/handling-a-new-era-in-the-japanese-calendar-in-net/) Další informace a na zjištění, zda jsou vliv na vaše aplikace. Zobrazit [Příprava aplikace pro změnu japonské období](~/windows/uwp/design/globalizing/japanese-era-change) informace o testování aplikací na Windows k zajištění jejich připravenosti změna éry.

### <a name="eras-and-era-names"></a>Období a názvy období

V rozhraní .NET, jsou celá čísla, která představují období podporovaná implementací konkrétního kalendáře v obráceném pořadí v uložené <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> pole. Aktuální období je na pozici nula a pro <xref:System.Globalization.Calendar> odráží třídy, které podporují větší počet období, jednotlivé postupné pozice předchozímu období. Statické <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> vlastnost definuje index aktuálního období v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> pole; jedná se o konstantu, jejíž hodnota je vždycky nula. Jednotlivé <xref:System.Globalization.Calendar> třídy zahrnují také statická pole, která vrátí hodnotu aktuálního období. Jsou uvedeny v následující tabulce.

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

Název, který odpovídá konkrétního období lze načíst předáním období číslo, které má <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metody. V následujícím příkladu jsou voláním metod k načtení informací o podpoře období v <xref:System.Globalization.GregorianCalendar> třídy.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Kromě toho řetězec „o“ vlastního formátu data a času obsahuje název období kalendáře v řetězcovém vyjádření data a času. Další informace najdete v tématu [řetězce formátu vlastní data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Vytvoření instance data s obdobím

Pro obě <xref:System.Globalization.Calendar> třídy, které podporují větší počet období, datum, které se skládá z konkrétního roku, měsíce a dne v měsíci hodnota může být nejednoznačný, například všechna čtyři období <xref:System.Globalization.JapaneseCalendar> mít roky očíslovány od 1 do 15. Pokud není období stanoveno, pak metody data a času a kalendáře obvykle předpokládají, že hodnoty patří do aktuálního období. Chcete-li výslovně zadat období při vytváření instance data <xref:System.Globalization.Calendar> třídu, která podporuje větší počet období, můžete volat <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metoda. Tato metoda umožňuje explicitní zadání období a hodnoty roku, měsíce, dne, hodiny, minuty, sekundy a milisekundy v kalendáři.

V následujícím příkladu <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metoda pro vytvoření instance stejného data, prvního měsíce prvního dne druhého roku, v jednotlivých <xref:System.Globalization.JapaneseCalendar> třídy. Poté zobrazí datum v japonském a gregoriánském kalendáři. Volá také <xref:System.DateTime> konstruktoru pro ilustraci, že metody vytvářející hodnoty data bez zadání období vytvářejí data v aktuálním období.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Zobrazování dat v kalendářích s obdobími

Pokud <xref:System.Globalization.Calendar> objekt podporuje větší počet období a je aktuálním kalendářem objektu <xref:System.Globalization.CultureInfo> objektu, je období zahrnuto v řetězcovém vyjádření hodnoty data a času pro úplného data a času, dlouhého data a krátkého data. Následující příklad zobrazuje tyto vzorce dat, kdy je nastavena aktuální jazyková verze Japonština (Japonsko) a aktuálním kalendářem je japonský kalendář.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar> Třída je jedinou třídou kalendáře v rozhraní .NET, která podporuje data ve více než jednom období a může být aktuální kalendář <xref:System.Globalization.CultureInfo> objekt – konkrétně pak objektu <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi japonština (Japonsko).

Specifikátor vlastního formátu „o“ zahrnuje období ve výsledném řetězci všech kalendářů. Následující příklad používá vlastní řetězec formátu „MM-dd-rrrr g“ pro vyjádření období ve výsledném řetězci, pokud je aktuální kalendář nastaven na gregoriánský kalendář.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

V případech, kde je vyjádřena řetězec představující datum v kalendáři, který není aktuálním kalendářem <xref:System.Globalization.Calendar> třída zahrnuje <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> metodu, která je možné společně s <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody pro jednoznačně určit datum, jakož i období, do které patří. V následujícím příkladu <xref:System.Globalization.JapaneseLunisolarCalendar> třídy ilustraci. Uvědomte si však, že včetně smysluplného názvu nebo zkratky namísto celého čísla pro období ve výsledném řetězci vyžaduje vytvoření instance <xref:System.Globalization.DateTimeFormatInfo> objektu a ujistěte se, <xref:System.Globalization.JapaneseCalendar> jako aktuálního kalendáře. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Kalendáře nemůže být aktuálním kalendářem žádné jazykové verze, ale v tomto případě sdílet tyto dva kalendáře mají stejné období.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>Viz také:

* [Postupy: Zobrazování dat v jiném než gregoriánském kalendáři](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
* [Ukázka: Nástroj pro rozsah týdnů kalendáře](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
