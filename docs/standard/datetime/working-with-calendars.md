---
title: Práce s kalendáři
ms.date: 04/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0113ef84c2b3e42f6d14d25747f7fdbb836a212
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59055310"
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
>  Období Reiwa, do nové éry v <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>, začíná 1. května 2019. Tato změna ovlivní všechny aplikace, které používají tyto kalendáře. Zobrazit další informace v následujících článcích:
> - [Zpracování do nové éry v japonské kalendáře v rozhraní .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), které dokumenty funkcí v rozhraní .NET pro podporu kalendářů a s větší počet období a popisuje osvědčené postupy pro použití při zpracování více období kalendáře.
> - [Příprava aplikace pro změnu japonské období](/windows/uwp/design/globalizing/japanese-era-change), který poskytuje informace o testování aplikací na Windows k zajištění jejich připravenosti změna éry.
> - [Souhrnné informace o nové éry japonské aktualizace pro rozhraní .NET Framework](https://support.microsoft.com/en-us/help/4477957/new-japanese-era-updates-for-net-framework), která uvádí seznam aktualizací pro rozhraní .NET Framework pro jednotlivé verze Windows, které souvisejí s novou éru japonský kalendář, poznámky k nové funkce rozhraní .NET Framework pro podporu více období a zahrnuje možná řešení hledejte v testování aplikací.

Období v většiny kalendáře označuje extrémně dlouhé časové období. V gregoriánském kalendáři například aktuálního období zahrnuje více než dva tisíciletí. Pro <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>dvě kalendáře, které podporují větší počet období, to není případ. Období odpovídá období císaře. Podpora pro větší počet období, zejména pokud horní limit počtu aktuálního období neznámý, představuje zvláštní problémy. 

### <a name="eras-and-era-names"></a>Období a názvy období

V rozhraní .NET, jsou celá čísla, která představují období podporovaná implementací konkrétního kalendáře v obráceném pořadí v uložené <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> pole. Aktuální období (což je období s nejnovější časový rozsah) je na pozici nula a pro <xref:System.Globalization.Calendar> odráží třídy, které podporují větší počet období, jednotlivé postupné pozice předchozímu období. Statické <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> vlastnost definuje index aktuálního období v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> pole; jedná se o konstantu, jejíž hodnota je vždycky nula. Jednotlivé <xref:System.Globalization.Calendar> třídy zahrnují také statická pole, která vrátí hodnotu aktuálního období. Jsou uvedeny v následující tabulce.

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

Název, který odpovídá konkrétního období lze načíst předáním období číslo, které má <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metody. V následujícím příkladu jsou voláním metod k načtení informací o podpoře období v <xref:System.Globalization.GregorianCalendar> třídy. Zobrazuje datum gregoriánský kalendář, který odpovídá 1. ledna druhého roku aktuálního období, jakož i datum gregoriánský kalendář, který odpovídá 1. ledna druhého roku, každého období podporované japonský kalendář.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Kromě toho řetězec „o“ vlastního formátu data a času obsahuje název období kalendáře v řetězcovém vyjádření data a času. Další informace najdete v tématu [řetězce formátu vlastní data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Vytvoření instance data s obdobím

Pro obě <xref:System.Globalization.Calendar> třídy, které podporují větší počet období, datum, které se skládá z konkrétního roku, měsícem a dnem v měsíci hodnota může být nejednoznačný. Například všechny období podporována <xref:System.Globalization.JapaneseCalendar> roky, jejichž omezení je 1. Pokud není období stanoveno, pak metody data a času a kalendáře obvykle předpokládají, že hodnoty patří do aktuálního období. Tato podmínka platí <xref:System.DateTime.%23ctor%2A> a <xref:System.DateTimeOffset.%23ctor%2A> konstruktorů, které zahrnují parametry typu <xref:System.Globalization.Calendar>, jakož i [JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) a [JapaneseLunisolarCalendar.ToDateTime ](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) metody. Následující příklad vytvoří datum, které představuje datum 1. ledna druhého roku neurčené období. Pokud příklad spustíte po období Reiwa aktuálního období, datum, je interpretován jako druhý rok Reiwa období. Období 令和, předchází roku v řetězec vrácený funkcí <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> metoda a odpovídá 1. ledna 2020, v gregoriánském kalendáři. (Období Reiwa začne do roku 2019 gregoriánského kalendáře).

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Ale pokud období se změní, záměr tohoto kódu stane nejednoznačný. Datum má představovat druhého roku aktuálního období, nebo je určený k reprezentaci druhý rok období Heisei období? Chcete-li předejít této nejednoznačnosti dvěma způsoby:

- Vytvořit instanci hodnoty data a času pomocí výchozího <xref:System.Globalization.GregorianCalendar> třídy. Potom můžete japonský kalendář nebo Japonský lunasolární kalendář pro řetězcové vyjádření data, jak ukazuje následující příklad.

   [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
   [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Volání metody data a času, který explicitně určuje období. To zahrnuje následující metody:

   - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Metodu <xref:System.Globalization.JapaneseCalendar> nebo <xref:System.Globalization.JapaneseLunisolarCalendar> třídy.

   - A <xref:System.DateTime> nebo <xref:System.DateTimeOffset> při analýze metody, jako například <xref:System.DateTime.Parse%2A>, <xref:System.DateTime.TryParse%2A>, <xref:System.DateTime.ParseExact%2A>, nebo <xref:System.DateTime.TryParseExact%2A>, který obsahuje řetězec, který má být analyzován a volitelně <xref:System.Globalization.DateTimeStyles> argument, pokud je aktuální jazyková verze Japonština Japonsko (" ja-JP") a kalendářem danou jazykovou verzi je <xref:System.Globalization.JapaneseCalendar>. Období musí být řetězec, který má být analyzován.

   - A <xref:System.DateTime> nebo <xref:System.DateTimeOffset> při analýze metody, která zahrnuje `provider` parametr typu <xref:System.IFormatProvider>. `provider` musí být buď <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi Japonština – Japonsko ("ja-JP"), jehož aktuálním kalendářem je <xref:System.Globalization.JapaneseCalendar> nebo <xref:System.Globalization.DateTimeFormatInfo> jehož <xref:System.Globalization.DateTimeFormatInfo.Calendar> vlastnost <xref:System.Globalization.JapaneseCalendar>. Období musí být řetězec, který má být analyzován.

   Následující příklad používá tři z těchto metod pro vytvoření instance datum a čas ve Meiji období, které začne na. 8 září 1868 a skončila 29. července 1912. 

   [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
   [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Při práci s kalendáře, které podporují větší počet období, *vždy* instance data pomocí gregoriánské datum nebo zadat období při vytváření instance datum a čas na základě tohoto kalendáře.

V zadání období do <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> metoda, zadejte index období ve kalendáře <xref:System.Globalization.Calendar.Eras> vlastnost. Pro kalendáře, jehož období se mohou změnit ale tyto indexy nejsou konstantní hodnoty; aktuální období je na pozici 0 a nejstarší období je v indexu `Eras.Length - 1`. Pokud do nové éry se přidá do kalendáře, indexy předchozích období zvýšit o jednu. Index odpovídající období můžete zadat následující:

- Kalendářních dat v rámci aktuálního období, vždy používejte v kalendáři <xref:System.Globalization.Calendar.CurrentEra> vlastnost.

- Kalendářních dat v rámci zadaného období, použijte <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> metodu pro načtení index, který odpovídá názvu zadaného období. To vyžaduje, aby <xref:System.Globalization.JapaneseCalendar> být aktuálním kalendářem <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi ja-JP.  (Tento postup funguje pro <xref:System.Globalization.JapaneseLunisolarCalendar> stejně, protože podporuje stejné období jako <xref:System.Globalization.JapaneseCalendar>.) Předchozí příklad znázorňuje tento přístup.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendáře, větší počet období a rozsahy kalendářních dat: Volný rozsah kontroly

Velmi podobně jako jednotlivé kalendáře máte podporovanou rozsahy kalendářních dat v období <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar> třídy také mají podporovány rozsahy. .NET použili striktní období rozsah kontroly k zajištění, že období konkrétní datum v rozsahu tohoto období. To znamená, pokud datum je mimo rozsah od zadaného období, vyvolá metoda <xref:System.ArgumentOutOfRangeException>. V současné době používá .NET volný rozsahové kontroluje ve výchozím nastavení. Aktualizace pro všechny verze rozhraní .NET zavedené volný období rozsah kontroly; Pokus o vytvoření instance období datum, která je mimo rozsah zadaného období "přetečení" do následujícího období a není vyvolána žádná výjimka.

Následující příklad se pokusí vytvořit instanci data v roce 65th Showa období, které začne na 25. prosince 1926 a skončila 7 ledna 1989. Toto datum odpovídá 9. ledna 1990, která je mimo rozsah období Showa ve <xref:System.Globalization.JapaneseCalendar>. Jak výstup z příkladu ukazuje, je datum zobrazeno pomocí příkladu 9 dne 1990, druhý rok období Heisei období.

   [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
   [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Pokud volný rozsah kontroly nežádoucí, můžete obnovit rozsah striktní kontroly různými způsoby v závislosti na verzi rozhraní .NET, na kterém běží vaše aplikace:

- **.NET Core:** Přidáním následujícího *. netcore.runtime.json* konfiguračního souboru:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
      } 
   }
   ```

- **.NET framework 4.6 nebo novější:** Můžete nastavit následující přepínač AppContext:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
     </runtime>
   </configuration>
   ```

- **Rozhraní .NET framework 4.5.2 nebo dříve:** Můžete nastavit následující hodnotu registru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Name | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   |Type | REG_SZ |
   |Value | 1 |

Pomocí kontroly striktní rozsahu povolená, předchozí příklad vyvolá <xref:System.ArgumentOutOfRangeException> a zobrazí se následující výstup:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>Zobrazování dat v kalendářích s obdobími více

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

V japonské kalendáře se nazývá první rok období Gannen (元年). Například namísto 1 období Heisei první rok období období Heisei lze popsat jako období Heisei Gannen. .NET přijímá tato konvence formátování operací s daty a časy naformátovaný jako následující standardní nebo vlastní formát data a času řetězce při jejich použití se službou <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi Japonština – Japonsko ("ja-JP") se <xref:System.Globalization.JapaneseCalendar> třídy:

- [Vzor dlouhého data](../base-types/standard-date-and-time-format-strings.md#LongDate), označený "D" data a času řetězec formátu.
- [Vzor úplného data dlouhý čas](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), uvedenými "F" data a času řetězec formátu.
- [Vzor krátkého formátu času úplné datum](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), uvedenými "f" data a času řetězec formátu.
- [Vzor roku a měsíce](../base-types/standard-date-and-time-format-strings.md#YearMonth), označený y "nebo"y"standardního formátu data a času řetězec.
- ["Ggy"年"" nebo "ggy年" [řetězec formátu vlastní data a času](../base-types/custom-date-and-time-format-strings.md).

Například následující příklad zobrazí datum v prvním roce období Heisei období ve <xref:System.Globalization.JapaneseCalendar> .

   [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
   [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Pokud toto chování nežádoucí v operacích formátování, můžete obnovit předchozí chování, které vždy představuje první rok období jako "1" místo "Gannen", pomocí tohoto postupu, v závislosti na verzi rozhraní .NET:

- **.NET Core:** Přidáním následujícího *. netcore.runtime.json* konfiguračního souboru:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
      } 
   }
   ```

- **.NET framework 4.6 nebo novější:** Můžete nastavit následující přepínač AppContext:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
     </runtime>
   </configuration>
   ```

- **Rozhraní .NET framework 4.5.2 nebo dříve:** Můžete nastavit následující hodnotu registru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Name | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   |Type | REG_SZ |
   |Value | 1 |

Díky podpoře gannen v operacích zakázané formátování v předchozím příkladu se zobrazí následující výstup:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET se také aktualizovala tak, že datum a čas operace analýzy řetězců obsahujících rok reprezentován jako "1" nebo Gannen nepodporuje. I když by neměl muset udělat, můžete obnovit předchozí chování rozpozná pouze "1" jako první rok období. Provedete to následujícím způsobem, v závislosti na verzi rozhraní .NET:

- **.NET Core:** Přidáním následujícího *. netcore.runtime.json* konfiguračního souboru:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
      } 
   }
   ```

- **.NET framework 4.6 nebo novější:** Můžete nastavit následující přepínač AppContext:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
     </runtime>
   </configuration>
   ```

- **Rozhraní .NET framework 4.5.2 nebo dříve:** Můžete nastavit následující hodnotu registru:

   |  |  |
   |--|--|  
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Name | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   |Type | REG_SZ |
   |Value | 1 | 

## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazování dat v jiném než gregoriánském kalendáři](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Ukázka: Nástroj pro rozsah týdnů kalendáře](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Třída kalendáře](xref:System.Globalization.Calendar)
